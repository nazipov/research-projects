---
id: 001
title: Мониторинг сроков SSL-сертификатов и доменов
status: scored
added: 2026-10-11
updated: 2026-10-11
direction: micro-saas
scores:
  pays: 4
  b2b: 4
  frequency: 3
  competitor_gaps: 2
  mvp_solo: 5
  low_support: 5
  audience: 4
  owner_edge: 4
  claude_code: 5
total: 36
---

# 001. Мониторинг сроков SSL-сертификатов и доменов

## Проблема

Сроки жизни публичных TLS-сертификатов сокращаются: с 15.03.2026 максимум 200 дней, с 15.03.2027 — 100 дней, с 15.03.2029 — 47 дней. Let's Encrypt сокращает сертификаты по умолчанию до 64 дней (февраль 2027) и с 04.06.2025 перестал рассылать письма об истечении сертификатов. Хуже всего приходится админам, у которых сертификаты стоят на сетевых устройствах и appliance без автоматизации, а также на внутренних сервисах, стендах и забытых поддоменах: такие сертификаты истекают незаметно, а браузеры при этом блокируют сайт полностраничным предупреждением.

## Как решают сейчас

- Автопродление (certbot, ACME-клиенты), но оно ломается молча.
- Проверка SSL внутри uptime-мониторов (Uptime Kuma, Better Stack, HetrixTools).
- Бесплатные сервисы (Red Sift Certificates Lite, его рекомендует сам Let's Encrypt) и платные (TrackSSL, Cert Spotter).
- Напоминания в календаре, которые теряются вместе с ушедшим сотрудником.

## Доказательства

- [Let's Encrypt: Ending Expiration Emails (январь 2025)](https://letsencrypt.org/2025/01/22/ending-expiration-emails/): уведомления об истечении прекращены с 04.06.2025, пользователей отправляют к сторонним мониторам.
- [Let's Encrypt: Expiration notification service has ended (июнь 2025)](https://letsencrypt.org/2025/06/26/expiration-notification-service-has-ended): подтверждение, что рассылка закрыта.
- [Getting an email when certificates are about to expire — форум Let's Encrypt](https://community.letsencrypt.org/t/getting-an-email-when-certificates-are-about-to-expire/246540): пользователи ищут замену уведомлениям.
- [Let's Encrypt ending notifications — LowEndSpirit](https://lowendspirit.com/discussion/9055/lets-encrypt-ending-notifications): обсуждение альтернатив; жалоба, что HetrixTools уведомляет только после истечения.
- [The Register: SSL/TLS certs to live no longer than 47 days by 2029](https://www.theregister.com/2025/04/14/ssl_tls_certificates/): график сокращения сроков (SC-081v3).
- [The Register, форум: sysadmins rage over cert lifespan cuts](https://forums.theregister.com/forum/all/2024/10/15/apples_security_cert_lifespan/): у админов «около 20 appliance-подобных сервисов» и устройства, которые нельзя автоматизировать.
- [Linuxiac: Let's Encrypt cuts lifetimes to 64 days in February 2027](https://linuxiac.com/lets-encrypt-to-cut-ssl-certificate-lifetimes-to-64-days-in-february-2027): скрипты с захардкоженными интервалами продления придётся пересматривать.

## Конкуренты

| Продукт | Цена | Слабые места (по отзывам) | Ссылка |
|---|---|---|---|
| TrackSSL | бесплатный тариф; платные «от $0.72 за домен» (по главной странице, точные цены тарифов не проверены) | только сертификаты, нет мониторинга доступности | [trackssl.com](https://trackssl.com/) |
| Red Sift Certificates Lite | бесплатно до 250 сертификатов | ? | [рекомендация Let's Encrypt](https://letsencrypt.org/2025/01/22/ending-expiration-emails/) |
| Cert Spotter (SSLMate) | ? | ? | [sslmate.com](https://sslmate.com/blog/post/introducing_new_certspotter) |
| HetrixTools | ? | уведомление приходит только после истечения (комментарий на форуме) | [LowEndSpirit](https://lowendspirit.com/discussion/9055/lets-encrypt-ending-notifications) |
| Uptime Kuma (self-hosted) | бесплатно | нужно держать на отдельной инфраструктуре | [LowEndSpirit](https://lowendspirit.com/discussion/9055/lets-encrypt-ending-notifications) |

## Оценка

| Критерий | Балл | Обоснование |
|---|---|---|
| 1. За решение платят | 4 | Есть платные TrackSSL, Cert Spotter, но рынок поджимают сильные бесплатные варианты |
| 2. Платит бизнес | 4 | Покупают агентства, MSP и ИТ-отделы; основной сценарий B2B |
| 3. Регулярность боли | 3 | Сейчас продление раз в 2–6 месяцев, к 2029 — ежемесячно; сама боль — редкий, но дорогой инцидент |
| 4. Слабости конкурентов | 2 | Конкретных жалоб в отзывах не найдено, есть бесплатный Red Sift до 250 сертификатов |
| 5. MVP в одиночку | 5 | TLS-проверка, WHOIS, алерты: 2–3 недели |
| 6. Низкая поддержка | 5 | Полностью self-service |
| 7. Доступность аудитории | 4 | r/sysadmin, r/selfhosted, форум Let's Encrypt, MSP-сообщества |
| 8. Преимущество владельца | 4 | TLS, ACME, мониторинг — близкая DevOps-область |
| 9. Реализуемо через Claude Code | 5 | Go-воркер, TLS/WHOIS-проверки, веб-панель: стандартный стек, легко покрыть тестами |
| **Итого** | **36/45** | |

## Идея решения

Не «ещё один SSL-чекер», а инвентарь сертификатов для эпохи коротких сроков:
- автообнаружение поддоменов через Certificate Transparency логи;
- агент или probe для внутренних сетей и appliance, недоступных снаружи;
- проверка, что продление действительно идёт (сертификат обновился к 2/3 срока), а не только дата истечения;
- сроки доменов (WHOIS/RDAP) в той же панели;
- алерты в Slack, Telegram, email; отчёты для MSP по клиентам.

Стек: Go-воркер для проверок, Postgres, простой веб-интерфейс.

## Риски и открытые вопросы

- Функция встроена почти во все uptime-мониторы — нужно чёткое отличие (внутренние сети, CT-обнаружение, MSP).
- Бесплатный Red Sift до 250 сертификатов покрывает малый бизнес.
- Готовы ли MSP платить отдельно, а не за всё-в-одном монитор? Проверить на интервью.

## Заметки

Таймер рынка: 15.03.2027 (100 дней) и 10.02.2027 (Let's Encrypt — 64 дня) создают поводы для маркетинга.
