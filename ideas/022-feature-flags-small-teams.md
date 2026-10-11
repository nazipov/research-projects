---
id: 022
title: Feature flags для маленьких команд
status: scored
added: 2026-10-11
updated: 2026-10-11
direction: micro-saas
scores:
  pays: 4
  b2b: 4
  frequency: 4
  competitor_gaps: 1
  mvp_solo: 4
  low_support: 4
  audience: 4
  owner_edge: 4
  claude_code: 5
total: 34
---

# 022. Feature flags для маленьких команд

## Проблема

LaunchDarkly берёт за место ($10/место/мес на Starter), а маленьким командам нужны простые флаги без governance-функций.

## Целевая аудитория

Команды из 2–10 разработчиков.

## Почему это больно

Переплата за ненужные функции; self-hosting Unleash требует времени и $75–120/мес хостинга.

## Как решают сейчас

- LaunchDarkly, ConfigCat, Flagsmith, Unleash, PostHog, Tggl

## Доказательства

- [Eppo: LaunchDarkly pricing](https://www.geteppo.com/blog/launchdarkly-pricing): Starter $10/место/мес (материал конкурента).
- [OSS Gap brief: feature flags](https://bullwinkle.js.org/oss-gap/briefs/2026-04-13-1702-feature-flags-config/): боль маленьких команд — цена, настройка и избыточность функций.
- [Tggl: Unleash vs LaunchDarkly](https://tggl.io/compare/unleash-vs-launchdarkly): self-hosting стоит $75–120/мес и времени инженеров.

## Конкуренты

| Продукт | Цена | Слабые места (по отзывам) | Ссылка |
|---|---|---|---|
| LaunchDarkly | Starter $10/место/мес | цена за место, избыточность | [Eppo](https://www.geteppo.com/blog/launchdarkly-pricing) |
| ConfigCat | без оплаты за место | ? | [Tggl](https://tggl.io/compare/flagsmith-vs-launchdarkly) |
| Flagsmith, Unleash | бесплатно / open source | self-hosting требует поддержки | [Tggl](https://tggl.io/compare/unleash-vs-launchdarkly) |

## Оценка

| Критерий | Балл | Обоснование |
|---|---|---|
| 1. За решение платят | 4 | Платные сервисы с ценами |
| 2. Платит бизнес | 4 | Команды разработчиков |
| 3. Регулярность боли | 4 | Используют ежедневно |
| 4. Слабости конкурентов | 1 | Много дешёвых и бесплатных альтернатив, включая open source |
| 5. MVP в одиночку | 4 | SDK + API + панель: 2–3 недели на одну-две платформы |
| 6. Низкая поддержка | 4 | Self-service |
| 7. Доступность аудитории | 4 | Dev-сообщества |
| 8. Преимущество владельца | 4 | Близко к DevOps |
| 9. Реализуемо через Claude Code | 5 | Стандартный стек |
| **Итого** | **34/45** | |

## Идея решения

Нет явного отличия от ConfigCat и Flagsmith.

## Монетизация

$10–49/мес за команду.

## Риски и открытые вопросы

- Пробела на рынке нет.

## Заметки

Записано, чтобы не возвращаться.
