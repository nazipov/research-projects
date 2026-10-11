---
id: 002
title: Бэкапы БД в свой S3 с автоматической проверкой восстановления
status: scored
added: 2026-10-11
updated: 2026-10-11
direction: micro-saas
scores:
  pays: 5
  b2b: 4
  frequency: 3
  competitor_gaps: 3
  mvp_solo: 4
  low_support: 3
  audience: 4
  owner_edge: 5
total: 31
---

# 002. Бэкапы БД в свой S3 с автоматической проверкой восстановления

## Проблема

Малые команды и фрилансеры бэкапят Postgres/MySQL скриптом `pg_dump | aws s3 cp` по cron. Скрипт ломается молча (PATH, права, переполнение диска), а восстановление никто не проверяет — о проблеме узнают, когда бэкап нужен. Open-source инструменты (pgBackRest, Barman) мощные, но сложные в настройке.

## Как решают сейчас

- Самописные скрипты на cron + S3.
- pgBackRest, Barman, Percona XtraBackup.
- Сервисы SimpleBackups, SnapShooter (куплен DigitalOcean), Datashelter, SqlBak.
- Встроенные бэкапы managed-БД, если база у облачного провайдера.

## Доказательства

- [DEV: 5 Ways Your Cron Jobs Are Failing Silently](https://dev.to/deadping/5-ways-your-cron-jobs-are-failing-silently-and-how-to-catch-them-2njp): разработчик обнаружил, что месяц бэкапов БД не работал, хотя cron выглядел активным.
- [Список рассылки PostgreSQL (2007)](https://postgresql.org/message-id/46B88630.80700%40zijn-digital.com): ночной pg_dump с восстановлением не работал месяц, никто не заметил — проблема давняя.
- [Kestra blueprint: Postgres backup to S3 with restore verify](https://kestra.io/blueprints/postgres-backup-s3-restore-verify): «непроверенный бэкап — это будущий простой»; спрос на автоматический restore drill.
- [MicroGaps: SimpleBackups validated $16K MRR](https://www.microgaps.com/gaps/2026-02-01-database-backup-automation): оценка автора — после покупки SnapShooter основным конкурентом остался SimpleBackups с оведжами; есть место для продукта за $9–29/мес (мнение, не отзыв пользователя).
- [Capterra: отзывы SimpleBackups](https://www.capterra.com.au/reviews/184422/simplebackups): жалобы на ценовую метрику (по размеру БД, а не объёму бэкапов) и на поштучную очистку бэкапов.

## Конкуренты

| Продукт | Цена | Слабые места (по отзывам) | Ссылка |
|---|---|---|---|
| SimpleBackups | Lite $49, Plus $99, Max $299 в мес. (сторонний снимок, май 2026); Capterra: от €34 | цена по размеру БД; оведжи $10 за 100 ГБ / 1 ТБ трафика; неудобная очистка | [xpay.sh](https://www.xpay.sh/saas-pricing/simplebackups-io/), [доки](https://simplebackups.com/docs/getting-started/account-and-billing/subscriptions) |
| SnapShooter (DigitalOcean) | бесплатно 1 ресурс в день, платно от $9 (по гайду вендора) | после покупки DO убраны часть провайдеров и хранилищ | [snapshooter.com](https://snapshooter.com/learn/backup-postgresql-to-backblaze-bash), [release notes](https://docs.digitalocean.com/release-notes/snapshooter/) |
| Datashelter | от €2 за сервер + €7/ТБ (по листингу, не проверено) | ? | [alternativeto](https://alternativeto.net/software/novabackup/?p=2) |
| pgBackRest / Barman | бесплатно | сложная настройка, нужны DevOps-навыки | [MicroGaps](https://www.microgaps.com/gaps/2026-02-01-database-backup-automation) |

## Оценка

| Критерий | Балл | Обоснование |
|---|---|---|
| 1. За решение платят | 5 | Несколько платных конкурентов с публичными ценами; SimpleBackups, по оценке MicroGaps, около $16K MRR |
| 2. Платит бизнес | 4 | Платят малые компании и агентства, чек $9–99/мес |
| 3. Регулярность боли | 3 | Бэкапы ежедневно, но острая боль — при сбое или восстановлении |
| 4. Слабости конкурентов | 3 | Жалобы на цену и тарификацию, ниша после ухода SnapShooter в DO; отзывов немного |
| 5. MVP в одиночку | 4 | Агент + S3 + restore в эфемерный контейнер: 3–4 недели |
| 6. Низкая поддержка | 3 | Высокая ответственность: проблемы с бэкапом — срочные обращения, доступ к чужим БД |
| 7. Доступность аудитории | 4 | r/selfhosted, r/PostgreSQL, Indie Hackers, клиенты Hetzner/VPS |
| 8. Преимущество владельца | 5 | Прямо DevOps: бэкапы, S3, контейнеры, мониторинг |
| **Итого** | **31/40** | |

## Идея решения

- Лёгкий агент (один бинарник или Docker) на сервере клиента: дамп Postgres/MySQL, шифрование, загрузка в S3 клиента (Hetzner, Backblaze, R2, AWS).
- Ключевое отличие: еженедельная автоматическая проверка восстановления в эфемерной БД со сравнением числа таблиц и строк, отчёт «бэкап восстанавливается».
- Фиксированная цена за сервер без оплаты за объём (хранилище клиента).
- Данные не проходят через наши серверы — меньше вопросов безопасности.

## Риски и открытые вопросы

- Ответственность: при неудачном восстановлении клиент винит сервис. Нужны чёткие условия.
- Restore-проверка требует вычислительных ресурсов: где её запускать — у клиента или у нас?
- Цифра $16K MRR у SimpleBackups из одного источника, проверить.

## Заметки

Можно объединить с 003: мониторинг cron как бесплатный вход, бэкапы как платный продукт.
