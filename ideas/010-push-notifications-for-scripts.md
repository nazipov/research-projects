---
id: 010
title: Приложение пуш-уведомлений из скриптов и вебхуков для маленьких команд (аналог Pushover/ntfy с дежурствами)
status: scored
added: 2026-10-11
updated: 2026-10-27
direction: mobile-app
scores:
  pays: 5
  b2b: 4
  frequency: 5
  competitor_gaps: 2
  mvp_solo: 4
  low_support: 4
  audience: 5
  owner_edge: 5
  claude_code: 3
total: 37
---

# 010. Приложение пуш-уведомлений из скриптов и вебхуков для маленьких команд (аналог Pushover/ntfy с дежурствами)

## Проблема

Разработчики, админы и маленькие команды хотят получать на телефон сообщения от своих скриптов, CI, бэкапов, мониторинга и бизнес-систем (новый заказ, упал сервер) одним `curl`/вебхуком. Своего мобильного приложения у них нет, а SMS дорогие. Важны надёжная и быстрая доставка, приоритеты (будить ночью или нет), подтверждение «принял» и эскалация на следующего, если никто не ответил.

## Целевая аудитория

Два сегмента (уточнено 2026-10-27):

1. **Внутренние уведомления команды (основной).** Команды 2–20 человек: стартапы, агентства, хостинг, интернет-магазины, ИТ-отделы малого бизнеса. Получатели — свои сотрудники и дежурные, которые готовы поставить одно приложение.
2. **Уведомления клиентам бизнеса вместо SMS (слабый).** Бизнес шлёт вебхук, а пуш получает его клиент. Проблема: клиент не поставит чужое приложение ради одного магазина, а у веб-пушей на iOS неудобная установка (см. риски).

## Почему это больно

- Пропущенный ночной алерт — простой сервиса и потеря денег.
- В 2025–2026 годах рынок перетряхнуло: Opsgenie (бесплатный тариф до 5 пользователей был популярен у маленьких команд) снят с продажи 4.06.2025 и отключается 5.04.2027; Grafana OnCall OSS заархивирован 24.03.2026.
- SMS дорожают: в США в январе и ноябре 2026 года выросли сборы операторов A2P, в РФ поставщики сообщают о росте счетов в 2–3 раза из-за пакетной тарификации (данные вендора).
- В РФ основной «бесплатный» канал алертов — Telegram-боты — с февраля 2026 года замедляется, WhatsApp заблокирован.

## Как решают сейчас

- Pushover: разовая покупка $5 на платформу, Teams — $5/польз./мес.
- ntfy.sh: open source, можно поднять у себя, Pro от $5/мес.
- Дежурства: PagerDuty, Opsgenie (до 2027), PagerTree, Spike.sh, SIGNL4, Better Stack, incident.io, GoAlert (self-hosted).
- Telegram-боты, Slack, почта, SMS через Twilio.

## Доказательства

- [ntfy: README](https://github.com/binwiederhier/ntfy): платные тарифы ntfy Pro от $5/мес.
- [ntfy docs: подписка с телефона](https://docs.ntfy.sh/subscribe/phone): без instant delivery сообщения приходят с задержкой «иногда на минуты или даже часы».
- [ntfy issue #1124](https://fr.github.com/binwiederhier/ntfy/issues): у self-hosted сервера проблемы с мгновенной доставкой на iOS.
- [Pushover for Teams](https://pushover.net/teams): $5 за пользователя в месяц или $60 в год.
- [Atlassian: эволюция IT operations](https://www.atlassian.com/blog/announcements/evolution-of-it-operations) и [Hyperping: Opsgenie end of life](https://hyperping.com/blog/opsgenie-end-of-life): продажи остановлены 4.06.2025, отключение 5.04.2027, несмигрированные данные удаляются; миграция в JSM может отключить Opsgenie через 120 дней.
- [Grafana OnCall OSS](https://grafana.com/docs/oncall/latest/set-up/open-source/): проект заархивирован 24.03.2026; пуши, SMS и звонки через Grafana Cloud для self-hosted больше не работают.
- [incident.io: PagerDuty для малых команд](https://incident.io/blog/best-pagerduty-alternatives-for-small-teams-2026): PagerDuty Professional $21/польз./мес, с дополнениями команда из 20 человек тратит ~$19 000/год (блог конкурента).
- [Rootly: альтернативы PagerDuty](https://rootly.com/blog/top-7-pagerduty-alternatives-in-2024-cost-effective-solutions-for-modern-teams): высокая цена — главная жалоба клиентов PagerDuty на G2 (блог конкурента).
- [Хабр: алерты в Telegram через Grafana OnCall](https://habr.com/en/articles/914790/comments): прямая отправка из Alertmanager в Telegram имеет существенные недостатки; в комментариях — нет сильной open source замены после архивации OnCall.
- [Sostav: Telegram под вопросом](https://www.sostav.ru/publication/telegram-pod-voprosom-82836.html) и [Коммерсантъ](https://kommersant.ru/doc/8499984): поэтапное замедление Telegram с февраля 2026, WhatsApp исключён из DNS 11.02.2026.
- [Twilio: изменение сборов T-Mobile, январь 2026](https://support.twilio.com/hc/en-us/articles/44609260499995-T-Mobile-Messaging-Carrier-Fee-Changes-January-2026) и [Signal House: сборы A2P в 2026](https://signalhouse.io/guides/a2p-carrier-fees-2026/): SMS в США дорожают, следующее повышение — 1.11.2026.
- [RBC Companies: вебинар «Безумные тарифы на SMS»](https://companies.rbc.ru/news/rt4j0DApIt/vebinar-bezumnyie-tarifyi-na-sms/): пакетная тарификация операторов с 2026 года, счета выросли в 2–3 раза (материал SMS-вендора).

## Конкуренты

| Продукт | Цена | Слабые места (по отзывам) | Ссылка |
|---|---|---|---|
| Pushover | $5 разово на платформу; Teams $5/польз./мес | нет дежурств и эскалаций по расписанию | [pushover.net](https://pushover.net/teams) |
| ntfy.sh | бесплатно / Pro от $5/мес | задержки без instant delivery; сложности с iOS при self-hosted | [GitHub](https://github.com/binwiederhier/ntfy), [docs](https://docs.ntfy.sh/subscribe/phone) |
| PagerTree | бесплатно до 5 польз.; Pro $10/польз./мес | ? | [xpay.sh](https://www.xpay.sh/saas-pricing/pagertree-platform/) |
| Spike.sh | Starter $7, Business $14 в мес. за пользователя | Starter — 100 алертов всего | [xpay.sh](https://www.xpay.sh/saas-pricing/spike-sh/) |
| SIGNL4 | $9 / $19 / $29 в мес. за пользователя | ? | [TrustRadius](https://www.trustradius.com/products/signl4/pricing) |
| PagerDuty | от $21/польз./мес + дополнения | дорого для малых команд | [incident.io](https://incident.io/blog/best-pagerduty-alternatives-for-small-teams-2026) |
| Opsgenie | бесплатно до 5 польз.; $9/$29 — продажи закрыты | закрывается 5.04.2027 | [Hyperping](https://hyperping.com/blog/opsgenie-end-of-life) |
| Gotify, GoAlert | бесплатно (self-hosted) | своя инфраструктура и свой SMS-провайдер | [incident.io](https://incident.io/blog/best-open-source-pagerduty-alternatives-2026) |

## Оценка

| Критерий | Балл | Обоснование |
|---|---|---|
| 1. За решение платят | 5 | Много платных продуктов с открытыми ценами: от $5 до $21+ за пользователя |
| 2. Платит бизнес | 4 | Команды платят за пользователя: 5 человек × $5–10 = $25–50/мес (было 3: раньше учитывались только одиночки) |
| 3. Регулярность боли | 5 | Уведомления каждый день |
| 4. Слабости конкурентов | 2 | Два закрытия (Opsgenie, Grafana OnCall OSS) вытесняют пользователей, но дешёвые альтернативы без жалоб уже есть (PagerTree бесплатно до 5, Pushover $5). Гео-пробел РФ может дать 3, если подтвердится (см. заметки) |
| 5. MVP в одиночку | 4 | HTTP API + APNs/FCM + приложение + простая эскалация: 3–4 недели |
| 6. Низкая поддержка | 4 | Self-service, но расписания дежурств и командные настройки дают вопросы (было 5) |
| 7. Доступность аудитории | 5 | r/selfhosted, r/devops, HN, Хабр |
| 8. Преимущество владельца | 5 | Прямо DevOps: алерты, вебхуки, дежурства |
| 9. Реализуемо через Claude Code | 3 | Бэкенд реализуется легко, но ядро — нативное приложение с фоновой доставкой APNs/FCM, критическими алертами iOS и ревью в сторах |
| **Итого** | **37/45** | Было 36 (2026-10-11) |

## Идея решения

Не клон Pushover, а «пуши для маленьких команд»: вебхук или `curl` → пуш всем подписанным на канал; кнопка «принял»; если никто не подтвердил за N минут — повторить громко (critical alert на iOS) или передать следующему по расписанию. Готовые интеграции: GitHub Actions, Uptime Kuma, Grafana/Alertmanager, Zabbix, формы и CRM (новый заказ, заявка). Импорт расписаний из Opsgenie. Цена плоская за команду, а не за пользователя. Хорошо связывается с идеями 001, 003 и 007: общий канал алертов.

## Монетизация

Бесплатно 1 пользователь; команда до 10 человек — $15–29/мес плоско, дальше $49. Путь к $10k MRR: ~400–600 команд. Инфраструктура: APNs и FCM бесплатны, бэкенд — до $50/мес на старте.

## Риски и открытые вопросы

- ntfy бесплатный и open source, PagerTree бесплатен до 5 пользователей — нужен явный плюс (надёжная доставка на iOS, эскалации, плоская цена).
- Уведомления клиентам вместо SMS (сегмент 2) как отдельный продукт не подходят: клиент не поставит чужое приложение; веб-пуши на iOS работают только после «добавить на экран Домой», подписки иногда «пропадают» ([MagicBell](https://www.magicbell.com/blog/pwa-ios-limitations-safari-support-complete-guide), [Pushpad](https://pushpad.xyz/blog/ios-special-requirements-for-web-push-notifications)); для кодов подтверждения уже есть Telegram Gateway за $0.01 ([Telegram](https://core.telegram.org/gateway)).
- Конкуренция с PagerDuty, Better Stack и incident.io, если продукт уходит в полноценное управление инцидентами.
- Для РФ: публикация в App Store и приём платежей из РФ требуют отдельной проверки; Android-пуши через FCM работают, но для части устройств нужен RuStore Push.

## Заметки

- 2026-10-27: дополнено по запросу владельца (пуши по вебхуку для маленьких команд без своего приложения и SMS). Пересчитаны критерии 1, 2, 6; сумма 36 → 37.
- Гео-пробел РФ не подтверждён: нужно проверить доступность и оплату PagerDuty, Pushover и Spike из РФ и поискать российские аналоги дежурств. Если их нет, критерий 4 можно поднять до 3.
- 2026-10-27: вариант с уведомлениями клиентам бизнеса через мессенджеры (WhatsApp, Max, LINE, Zalo) вынесен в [038](038-multichannel-webhook-notifications.md).
