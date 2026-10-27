---
id: 035
title: Замер участков по снимкам для смет ландшафтных и газонных компаний
status: scored
added: 2026-10-22
updated: 2026-10-22
direction: geo-data
scores:
  pays: 5
  b2b: 4
  frequency: 5
  competitor_gaps: 2
  mvp_solo: 3
  low_support: 4
  audience: 4
  owner_edge: 1
  claude_code: 4
total: 32
---

# 035. Замер участков по снимкам для смет ландшафтных и газонных компаний

## Проблема

Компании по стрижке газонов, уборке снега и ландшафтным работам считают цену по площади участка. Выезд на замер к каждому потенциальному клиенту съедает время, поэтому площадь меряют по снимкам с воздуха или спутника.

## Целевая аудитория

Малые подрядчики (1–20 человек) в США, Канаде, Австралии: газоны, удобрения, снег, мощение.

## Почему это больно

Каждая смета без выезда экономит час; при десятках запросов в неделю это главный инструмент продаж.

## Как решают сейчас

SatMeasure, SatQuote, SiteRecon, QuoteIQ MapMeasure, PropertyIntel (бывший Go iLawn), бесплатный калькулятор Jobber и Google Earth Pro.

## Доказательства

- [MyQuoteIQ: сравнение 2026](https://myquoteiq.com/best-satellite-measuring-software-lawn-care-2026/): PropertyIntel от $199/мес, QuoteIQ от $74.99/мес, SiteRecon от $39/польз./мес, Google Earth Pro бесплатно при <5 смет в неделю (блог конкурента).
- [Capterra: SatQuote](https://www.capterra.co.uk/software/1037665/satquote): SatMeasure $12.50/мес, SatMeasure+ $25/мес, SatQuote $50/мес.
- [Jobber: бесплатный калькулятор](https://www.getjobber.com/free-tools/lawn-care-cost-calculator/): обводка газона на снимке бесплатно.
- [Landscape Management](https://www.landscapemanagement.net/embracing-web-based-tools-to-measure-lawns/): подрядчики массово перешли на онлайн-замеры; инструмент работает не во всех случаях.

## Конкуренты

| Продукт | Цена | Слабые места (по отзывам) | Ссылка |
|---|---|---|---|
| SatMeasure / SatQuote | $12.50 / $25 / $50 в мес. | ? | [Capterra](https://www.capterra.co.uk/software/1037665/satquote) |
| SiteRecon | от $39/польз./мес | ? | [Capterra](https://www.capterra.com/p/276749/SiteRecon/alternatives/) |
| PropertyIntel (Go iLawn) | от $199/мес | дорого для соло | [MyQuoteIQ](https://myquoteiq.com/best-satellite-measuring-software-lawn-care-2026/) |
| Jobber калькулятор | бесплатно | только прикидка | [Jobber](https://www.getjobber.com/free-tools/lawn-care-cost-calculator/) |

## Оценка

| Критерий | Балл | Обоснование |
|---|---|---|
| 1. За решение платят | 5 | Много платных продуктов с открытыми ценами |
| 2. Платит бизнес | 4 | Подрядчики, $12–200/мес |
| 3. Регулярность боли | 5 | Сметы ежедневно |
| 4. Слабости конкурентов | 2 | Дешёвые и бесплатные варианты есть, жалоб не найдено |
| 5. MVP в одиночку | 3 | Ручная обводка — неделя, но автоопределение газона требует снимков 10–30 см (лицензия Nearmap/Google) и ML |
| 6. Низкая поддержка | 4 | Self-service |
| 7. Доступность аудитории | 4 | LawnSite, группы в Facebook, YouTube |
| 8. Преимущество владельца | 1 | Чужая область |
| 9. Реализуемо через Claude Code | 4 | Веб-стек + карты; ML-сегментация сложнее проверять |
| **Итого** | **32/45** | |

## Идея решения

Автоматическая сегментация газона, клумб и дорожек по адресу + смета по прайсу подрядчика + ссылка для клиента. Нужна высокая детализация: бесплатные спутники (10 м) не подходят.

## Монетизация

$19–49/мес. Путь к $10k MRR: ~300 клиентов. Расходы на снимки — главный риск маржи.

## Риски и открытые вопросы

- Условия Google Maps Platform и Nearmap на автоматический анализ снимков.
- Ниша переполнена; отличаться можно только точностью автозамера.
- Близкий рынок — замер крыш (EagleView, Roofr): [на GetApp жалуются на $15–38 за отчёт EagleView](https://www.getapp.com/construction-software/a/eagleview-roofing/), но нужна точность уклонов и есть Roofr за ~$10 — отдельной карточки не заводил.

## Заметки
