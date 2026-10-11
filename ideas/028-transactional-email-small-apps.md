---
id: 028
title: Транзакционная почта для маленьких приложений после отмены бесплатного SendGrid
status: scored
added: 2026-10-11
updated: 2026-10-11
direction: micro-saas
scores:
  pays: 5
  b2b: 4
  frequency: 5
  competitor_gaps: 1
  mvp_solo: 3
  low_support: 2
  audience: 4
  owner_edge: 4
  claude_code: 4
total: 32
---

# 028. Транзакционная почта для маленьких приложений после отмены бесплатного SendGrid

## Проблема

27.05.2025 Twilio SendGrid закрыл бесплатный тариф: новые аккаунты получают 60-дневный пробный период, потом от $19.95 в месяц. Маленьким приложениям с парой сотен писем в месяц это дорого.

## Целевая аудитория

Инди-разработчики и маленькие приложения со 100–5,000 писем в месяц.

## Почему это больно

Минимум $20 в месяц только за письма сброса пароля.

## Как решают сейчас

- Amazon SES, Resend (500 писем бесплатно), Postmark, Mailgun, Brevo

## Доказательства

- [Rework: SendGrid vs Mailgun](https://resources.rework.com/tools/messaging-sms/sendgrid-vs-mailgun): бесплатный тариф закрыт 27.05.2025, далее от $19.95/мес.
- [DEV: SendGrid killed their free plan, so I built a $1/month alternative](https://dev.to/babu_munavarbasha/sendgrid-killed-their-free-plan-so-i-built-a-1month-sendgrid-alternative-instead-5750): разработчики ищут дешёвую замену.
- [Dreamlit: best SendGrid alternatives](https://dreamlit.ai/blog/best-sendgrid-alternatives): обзор замен.

## Конкуренты

| Продукт | Цена | Слабые места (по отзывам) | Ссылка |
|---|---|---|---|
| SendGrid | от $19.95/мес | нет бесплатного тарифа | [Rework](https://resources.rework.com/tools/messaging-sms/sendgrid-vs-mailgun) |
| Resend | бесплатно 500 писем/мес | ? | [SuprSend](https://www.suprsend.com/post/best-sendgrid-alternatives-developers) |
| Amazon SES, Postmark, Mailgun, Brevo | ? | ? | [Dreamlit](https://dreamlit.ai/blog/best-sendgrid-alternatives) |

## Оценка

| Критерий | Балл | Обоснование |
|---|---|---|
| 1. За решение платят | 5 | Много платных сервисов |
| 2. Платит бизнес | 4 | Разработчики и малый бизнес |
| 3. Регулярность боли | 5 | Письма уходят ежедневно |
| 4. Слабости конкурентов | 1 | Resend, SES, Postmark, Brevo закрывают потребность, в том числе бесплатно |
| 5. MVP в одиночку | 3 | Обёртка над SES — 2 недели; собственная доставляемость — нет |
| 6. Низкая поддержка | 2 | Проблемы доставляемости — тяжёлая поддержка |
| 7. Доступность аудитории | 4 | Dev-сообщества |
| 8. Преимущество владельца | 4 | Почтовая инфраструктура — DevOps |
| 9. Реализуемо через Claude Code | 4 | Обёртка над SES пишется легко |
| **Итого** | **32/45** | |

## Идея решения

Без явного отличия от Resend и SES.

## Монетизация

$1–10/мес.

## Риски и открытые вопросы

- Пробела на рынке нет; конкуренция с бесплатными тарифами.

## Заметки

Записано, чтобы не возвращаться.
