---
id: 014
title: Восстановление неудачных платежей Stripe для маленьких SaaS (dunning)
status: scored
added: 2026-10-11
updated: 2026-10-11
direction: micro-saas
scores:
  pays: 5
  b2b: 4
  frequency: 4
  competitor_gaps: 1
  mvp_solo: 5
  low_support: 4
  audience: 4
  owner_edge: 2
  claude_code: 5
total: 34
---

# 014. Восстановление неудачных платежей Stripe для маленьких SaaS (dunning)

## Проблема

Карты истекают и отклоняются, подписчики уходят непреднамеренно. Встроенные Smart Retries Stripe, по оценке вендоров, возвращают около 23% неудачных платежей, а специализированные инструменты — 50–70%. Крупные решения стоят $249–250 в месяц.

## Целевая аудитория

Соло-основатели и маленькие SaaS на Stripe с MRR $1k–30k.

## Почему это больно

Неудачные платежи, по разным оценкам, съедают 8.6% выручки и дают 20–40% всего оттока.

## Как решают сейчас

- Stripe Smart Retries и стандартные письма Stripe.
- Churnkey, Churn Buster, Baremetrics Recover, Stunning.
- Дешёвые инди-инструменты: Rebounce, Rebill, Recoupe, ChurnWard, Revive.
- Самописные n8n-сценарии.

## Доказательства

- [MicroGaps: failed Stripe payments drain 8.6% of revenue, tools cost $249/mo](https://www.microgaps.com/gaps/indie-saas-dunning-recovery): основатели не могут оправдать $250/мес за Churnkey или $249/мес за Churn Buster.
- [Indie Hackers: what failed cards cost a small SaaS at ten MRR levels](https://www.indiehackers.com/post/i-modeled-what-failed-cards-cost-a-small-saas-at-ten-mrr-levels-the-gap-between-stripe-retries-and-retries-plus-a-sequence-was-bigger-t-4ee530ae4a): разница между ретраями Stripe и полноценной цепочкой писем существенна; email в Stripe часто устаревший.
- [Indie Hackers: I discovered I was losing $3k/year to failed payments so I built a fix](https://www.indiehackers.com/post/i-discovered-i-was-losing-3k-year-to-failed-payments-so-i-built-a-fix-01ef1c9ac7): основатель сделал свой инструмент — значит, ниша уже заполняется.
- [DEV: I compared 6 dunning tools for Stripe SaaS](https://dev.to/astraedus/i-compared-6-dunning-tools-for-stripe-saas-heres-what-i-found-4n7b): цены от $19 (Rebill) до $249 (Churn Buster).

## Конкуренты

| Продукт | Цена | Слабые места (по отзывам) | Ссылка |
|---|---|---|---|
| Churnkey | от $250/мес (годовая оплата) | дорого для инди | [MicroGaps](https://www.microgaps.com/gaps/indie-saas-dunning-recovery) |
| Churn Buster | $249/мес | дорого для инди | [DEV](https://dev.to/astraedus/i-compared-6-dunning-tools-for-stripe-saas-heres-what-i-found-4n7b) |
| Baremetrics Recover | от $58/мес | нет SMS и in-app блокировок | [DEV](https://dev.to/astraedus/i-compared-6-dunning-tools-for-stripe-saas-heres-what-i-found-4n7b) |
| Rebounce | $3.50 / $14 / $39 в мес. | ? | [SourceForge](https://sourceforge.net/software/product/Rebounce/) |
| Rebill, Recoupe, ChurnWard | $19 / $29 / $29 в мес. | ? | [DEV](https://dev.to/astraedus/i-compared-6-dunning-tools-for-stripe-saas-heres-what-i-found-4n7b), [Indie Hackers](https://www.indiehackers.com/product/recoupe) |

## Оценка

| Критерий | Балл | Обоснование |
|---|---|---|
| 1. За решение платят | 5 | Много платных инструментов с публичными ценами |
| 2. Платит бизнес | 4 | SaaS-компании, чек $15–50/мес |
| 3. Регулярность боли | 4 | Неудачные платежи каждый месяц |
| 4. Слабости конкурентов | 1 | Утверждение «ничего нет за $19» опровергнуто: есть варианты от $3.50 до $29 |
| 5. MVP в одиночку | 5 | Stripe-вебхуки, цепочка писем, страница обновления карты: 2 недели |
| 6. Низкая поддержка | 4 | Self-service после подключения Stripe |
| 7. Доступность аудитории | 4 | Indie Hackers, X, r/SaaS |
| 8. Преимущество владельца | 2 | Биллинг и email-маркетинг, не DevOps |
| 9. Реализуемо через Claude Code | 5 | Стандартная интеграция со Stripe |
| **Итого** | **34/45** | |

## Идея решения

Подключение Stripe в один клик, умные ретраи по коду отказа, цепочка писем на правильный адрес, pre-dunning перед истечением карты. Ничего нового относительно существующих дешёвых инструментов.

## Монетизация

Процент от возвращённого (10–25%) или $19–49/мес. Для $10k MRR нужно 300–500 клиентов в переполненной нише.

## Риски и открытые вопросы

- Ниша переполнена дешёвыми инди-инструментами, которые появились за последний год.
- Stripe может улучшить встроенный dunning.

## Заметки

Пример того, как сумма баллов вводит в заблуждение: всё хорошо, кроме главного — пробела на рынке нет. Записано, чтобы не возвращаться.
