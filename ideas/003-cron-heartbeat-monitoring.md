---
id: 003
title: Мониторинг cron-задач (heartbeat)
status: scored
added: 2026-10-11
updated: 2026-10-11
direction: micro-saas
scores:
  pays: 5
  b2b: 3
  frequency: 3
  competitor_gaps: 2
  mvp_solo: 5
  low_support: 5
  audience: 4
  owner_edge: 5
  claude_code: 5
total: 37
---

# 003. Мониторинг cron-задач (heartbeat)

## Проблема

Cron не проверяет, успешно ли выполнилась задача: при ненулевом коде выхода он просто ждёт следующего запуска. Задачи падают из-за другого PATH, исчезают при деплое вместе с перезаписанным crontab, а бэкапы и синхронизации неделями не работают, пока кто-то не заметит.

## Как решают сейчас

- Пинг внешнего heartbeat-сервиса в конце скрипта (Healthchecks.io, Cronitor, Dead Man's Snitch, Better Stack).
- Self-hosted Healthchecks (open source).
- Письма от cron на почту, которые никто не читает.

## Доказательства

- [DEV: 5 Ways Your Cron Jobs Are Failing Silently](https://dev.to/deadping/5-ways-your-cron-jobs-are-failing-silently-and-how-to-catch-them-2njp): месяц сбоев бэкапов при «активном» cron.
- [Runhooks: Why Cron Jobs Fail in Production](https://runhooks.app/blog/why-cron-jobs-fail-in-production/): короткий PATH, перезаписанный при деплое crontab, отсутствие уведомлений.
- [DEV: How to effectively monitor regular backups](https://dev.to/cronmonitor/how-to-effectively-monitor-regular-backups-3efc): сервис создан после того, как бэкап клиента молча не работал 11 дней (история вендора).
- [Хабр: мониторинг cron с алертами в Telegram средствами bash и curl](https://habr.com/en/articles/1007420): на русскоязычном рынке heartbeat часто делают самописно; в статье упоминается бесплатный PingZen.
- [Capterra: Healthchecks.io](https://www.capterra.com/p/249957/Healthchecksio/pricing/) и [Cronitor](https://www.capterra.com/p/276753/Cronitor/): платные конкуренты с публичными ценами.

## Конкуренты

| Продукт | Цена | Слабые места (по отзывам) | Ссылка |
|---|---|---|---|
| Healthchecks.io | бесплатно 20 задач; Supporter $5/мес; Business $20/мес (100 задач) | в отзывах в основном лимиты бесплатного тарифа | [Capterra](https://www.capterra.com/p/249957/Healthchecksio/pricing/), [freetier.co](https://freetier.co/compare/healthchecksio-vs-uptimerobot) |
| Cronitor | бесплатно 5 мониторов; $2/мес за монитор + $5/мес за пользователя | цена растёт с числом задач и пользователей | [CubeAPM review](https://cubeapm.com/blog/cronitor-pricing-review/) |
| Tracker.ru | ? (оплата в рублях, heartbeat входит в любой тариф) | ? | [tracker.ru](https://tracker.ru/features/heartbeat-monitoring?lang=en) |
| PingZen | бесплатно (по статье на Хабре) | ? | [Хабр](https://habr.com/en/articles/1007420) |
| Инди-клоны (DeadPing, CronPing, Runhooks, CronRadar, CronSafe) | ? | ? | [alternativeto](https://alternativeto.net/software/cronradar/about) |

## Оценка

| Критерий | Балл | Обоснование |
|---|---|---|
| 1. За решение платят | 5 | Несколько платных конкурентов с понятными ценами |
| 2. Платит бизнес | 3 | B2B, но щедрые бесплатные тарифы; типичный чек $5–20/мес |
| 3. Регулярность боли | 3 | Задачи ежедневные, но сбой обнаруживается редко |
| 4. Слабости конкурентов | 2 | Отзывы в основном положительные; рынок переполнен инди-клонами |
| 5. MVP в одиночку | 5 | Приём пингов + таймеры + алерты: 1–2 недели |
| 6. Низкая поддержка | 5 | Self-service, понятный продукт |
| 7. Доступность аудитории | 4 | r/devops, r/selfhosted, r/sysadmin, dev.to, HN |
| 8. Преимущество владельца | 5 | Прямой DevOps-опыт |
| 9. Реализуемо через Claude Code | 5 | HTTP-приём пингов, таймеры, алерты: типовой веб-сервис с автотестами |
| **Итого** | **37/45** | |

## Идея решения

В лоб не конкурировать. Возможные ниши:
- мониторинг Kubernetes CronJob и CI-расписаний без правки скриптов (через события кластера);
- русскоязычный рынок с оплатой в рублях и Telegram-алертами — уже есть Tracker.ru и PingZen, так что гео-пробела здесь нет;
- бесплатная воронка для идеи 002 (бэкапы).

## Риски и открытые вопросы

- Рынок насыщен: Healthchecks.io open source и даёт 20 задач бесплатно, есть десятки клонов.
- Высокая сумма баллов обманчива: легко построить, трудно отличиться и продать.
- Нужно найти конкретные жалобы на конкурентов (G2, Capterra 2–3 звезды) перед шортлистом.

## Заметки
