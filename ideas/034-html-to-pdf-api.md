---
id: 034
title: API генерации PDF из HTML
status: scored
added: 2026-10-17
updated: 2026-10-17
direction: micro-saas
scores:
  pays: 5
  b2b: 4
  frequency: 4
  competitor_gaps: 2
  mvp_solo: 5
  low_support: 4
  audience: 3
  owner_edge: 3
  claude_code: 5
total: 35
---

# 034. API генерации PDF из HTML

## Проблема

Приложениям нужно выдавать счета, отчёты, договоры и билеты в PDF. Держать у себя headless Chrome или wkhtmltopdf неудобно: память, шрифты, обновления, таймауты на serverless. Поэтому разработчики платят внешнему API за конвертацию HTML в PDF.

## Целевая аудитория

Разработчики SaaS, интернет-магазинов и внутренних систем; no-code-сборщики (Zapier, Make, Bubble), которым нужен PDF по шаблону.

## Почему это больно

Генерация PDF нужна ежедневно, а самостоятельный рендер ломается на serverless и при росте нагрузки. Готовые сервисы на больших объёмах дорогие: у DocRaptor 50 000 PDF в месяц — только через отдел продаж.

## Как решают сейчас

- Хостинговые API: PDFShift, DocRaptor, Api2Pdf, Doppio, DocuGenerate.
- Self-hosted: Gotenberg, Puppeteer/Playwright, wkhtmltopdf, Prince (лицензия от $2500/год).

## Доказательства

- [Starter Story: PDFShift](https://www.starterstory.com/convert-html-to-pdf): соло-разработчик, API конвертации HTML в PDF; $3,6k MRR в 2020, в эпизоде октября 2025 — $8,5k в месяц на оплате за использование.
- [Starter Story: How I doubled revenue to $6.5K/month](https://www.starterstory.com/stories/how-i-doubled-revenue-to-6-5k-month-in-one-year): рост PDFShift до $6,5k MRR к январю 2021, каналы — Quora и Product Hunt.
- [Api2Pdf: сравнение с DocRaptor](https://www.api2pdf.com/alternatives/docraptor-alternative-compare-docraptor-with-api2pdf-com-for-html-to-pdf-conversion/): DocRaptor называют «одним из самых дорогих»; $75 за 1000 PDF против $1.49 у Api2Pdf (данные конкурента).
- [DocRaptor: сравнение с Prince](https://docraptor.com/prince): цены от $15/мес, лицензия Prince от $2500/год.

## Конкуренты

| Продукт | Цена | Слабые места (по отзывам) | Ссылка |
|---|---|---|---|
| DocRaptor | от $15/мес; 1000 PDF за $75 по данным Api2Pdf | дорого на объёмах, крупные объёмы через продажи | [DocRaptor](https://docraptor.com/prince) |
| Api2Pdf | $1.49 за 1000 PDF (по сайту вендора) | ? | [Api2Pdf](https://www.api2pdf.com/alternatives/docraptor-alternative-compare-docraptor-with-api2pdf-com-for-html-to-pdf-conversion/) |
| PDFShift | ? | ? | [Capterra](https://www.capterra.com/p/184246/PDFShift/reviews/?page=2) |
| Gotenberg, Puppeteer | бесплатно, свой хостинг | нужно держать браузер самому | [Toolradar](https://toolradar.com/alternatives/docraptor) |

## Оценка

| Критерий | Балл | Обоснование |
|---|---|---|
| 1. За решение платят | 5 | Много платных API с ценами; PDFShift — $8,5k/мес у одного человека |
| 2. Платит бизнес | 4 | Разработчики и компании, оплата за использование |
| 3. Регулярность боли | 4 | Документы генерируются ежедневно |
| 4. Слабости конкурентов | 2 | Жалобы только на цену DocRaptor, и то от конкурента; есть очень дешёвый Api2Pdf и бесплатный Gotenberg |
| 5. MVP в одиночку | 5 | Обёртка над Chromium с очередью и хранилищем: 1–2 недели |
| 6. Низкая поддержка | 4 | Self-service API, вопросы в основном по вёрстке под печать |
| 7. Доступность аудитории | 3 | SEO по запросам «html to pdf api», маркетплейсы Zapier/Make, RapidAPI |
| 8. Преимущество владельца | 3 | Масштабирование браузерного пула — инфраструктурная задача, но не DevOps-продукт |
| 9. Реализуемо через Claude Code | 5 | API, проверяется автотестами (сравнение PDF) |
| **Итого** | **35/45** | |

## Идея решения

Сам по себе ещё один HTML→PDF API не выделяется. Возможные клинья: шаблоны документов с данными (счета, сертификаты) и визуальным редактором для no-code; гарантированное хранение и подпись PDF; дешёвый тариф для EU с хранением данных в ЕС.

## Монетизация

Оплата за использование: $9–49/мес за пакеты документов. Инфраструктура: пул Chromium на 1–2 VPS, $40–100/мес на старте.

## Риски и открытые вопросы

- Ниша насыщена, ценовое давление (Api2Pdf, Gotenberg).
- Рост зависит от SEO, которое у лидеров сложилось годами.
- Нужны отзывы на 2–3 звезды о PDFShift, Doppio, Api2Pdf, чтобы найти реальную дыру.

## Заметки

Найдено через Starter Story (история PDFShift).
