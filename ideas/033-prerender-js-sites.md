---
id: 033
title: Пререндеринг JS-сайтов для поисковых и ИИ-краулеров после подорожания Prerender.io
status: scored
added: 2026-10-17
updated: 2026-10-17
direction: micro-saas
scores:
  pays: 5
  b2b: 4
  frequency: 3
  competitor_gaps: 2
  mvp_solo: 4
  low_support: 3
  audience: 3
  owner_edge: 4
  claude_code: 5
total: 33
---

# 033. Пререндеринг JS-сайтов для поисковых и ИИ-краулеров после подорожания Prerender.io

## Проблема

Сайты на клиентском рендеринге (React/Vite SPA, сборки из Lovable, Bolt и т. п.) отдают краулерам пустую HTML-оболочку. Googlebot рендерит JS с задержкой, а GPTBot, ClaudeBot и PerplexityBot JS не выполняют вовсе, поэтому контент не попадает в ИИ-поиск. Стандартное решение — пререндер-сервис, и лидер ниши Prerender.io в 2025 году перевёл всех клиентов на новые тарифы без сохранения старых цен: у части клиентов счёт вырос в 2,5–3,5 раза.

## Целевая аудитория

Небольшие SaaS и маркетинговые сайты на SPA, агентства и фрилансеры, которые собирают сайты на React/Vue/Angular или в AI-конструкторах, e-commerce на headless-стеке.

## Почему это больно

Переход на SSR (Next.js, Nuxt) — это переписывание фронтенда. Без пререндера сайт теряет органический трафик и видимость в ИИ-ответах. После подорожания платят $350 в месяц вместо $99 или ищут замену в спешке.

## Как решают сейчас

- Prerender.io, SEO4Ajax, LovableHTML и другие хостинговые пререндеры.
- Self-hosted: open-source Prerender на Node или Rendertron (поддержка прекращена), Puppeteer-скрипты.
- Переписывание на SSR/SSG; Lovable с мая 2026 по умолчанию создаёт проекты на SSR и отдаёт краулерам готовый HTML.

## Доказательства

- [Trustpilot: Prerender.io](https://fr-be.trustpilot.com/review/prerender.io): отзывы за ноябрь 2025 — рост с $99 до $350 в месяц, примерно в 3,5 раза, взамен предложили только временную скидку.
- [Prerender docs: changes to prerender pricing](https://docs.prerender.io/docs/changes-to-prerender-pricing): новые тарифы, все клиенты переведены до 17 ноября 2025 без сохранения старых цен, бесплатный план и годовая оплата убраны.
- [Prerender docs: pricing update, September 2026](https://docs.prerender.io/docs/pricing-update-2026): с 15 сентября 2026 ещё одно изменение тарифов — Starter $59, Growth $169, Pro $419 (по поисковой выдаче, страница напрямую не открылась).
- [G2: Prerender reviews](https://g2.com/products/prerender/reviews): «+250% price increase without anything more», жалобы на кеширование пустых страниц.
- [Passionfruit: JavaScript rendering and AI crawlers](https://getpassionfruit.com/blog/javascript-rendering-and-ai-crawlers-can-llms-read-your-spa): GPTBot, ClaudeBot и PerplexityBot видят только исходный HTML (вендорский источник).
- [Starter Story: Prerender.io](https://www.starterstory.com/how-to-bootstrap-saas-company): соло-основатель довёл сервис до $2,5M ARR за 5 лет — спрос на категорию подтверждён.

## Конкуренты

| Продукт | Цена | Слабые места (по отзывам) | Ссылка |
|---|---|---|---|
| Prerender.io | Starter $49/мес по G2, $59 с 15.09.2026 по docs | резкий рост цен без сохранения старых, пустые страницы в кеше | [G2](https://www.g2.com/products/prerender/pricing) |
| SEO4Ajax | от $52/мес, бесплатно 1000 страниц (по сравнению Prerender) | ? | [Prerender](https://prerender.io/?p=4115) |
| LovableHTML | $9–99/мес (по сравнению Prerender) | ? | [Prerender](https://prerender.io/?p=6603) |
| Rendertron, open-source Prerender | бесплатно, свой хостинг | нужно держать headless Chrome самому | [Prerender](https://prerender.io/?p=6579) |

## Оценка

| Критерий | Балл | Обоснование |
|---|---|---|
| 1. За решение платят | 5 | Несколько платных сервисов с понятными ценами; Prerender.io — $2,5M ARR |
| 2. Платит бизнес | 4 | SaaS, агентства, магазины; чек $10–100+/мес |
| 3. Регулярность боли | 3 | Сервис работает постоянно, но боль ощущается при счёте и падении индексации |
| 4. Слабости конкурентов | 2 | Жалобы на лидера есть, но дешёвые альтернативы (LovableHTML от $9, SEO4Ajax) уже есть, жалоб на них не найдено; AI-конструкторы переходят на SSR |
| 5. MVP в одиночку | 4 | Пул headless Chrome + кеш + middleware для Cloudflare Workers/nginx: 2–4 недели |
| 6. Низкая поддержка | 3 | Подключение к разным стекам и разбор «почему не индексируется» требуют поддержки |
| 7. Доступность аудитории | 3 | SEO-сообщества, сообщества Lovable/Bolt, r/webdev; запросы «prerender.io alternative» |
| 8. Преимущество владельца | 4 | Ядро — инфраструктура: пул браузеров, очереди, кеш, CDN |
| 9. Реализуемо через Claude Code | 5 | Стандартный бэкенд и прокси, проверяется автотестами |
| **Итого** | **33/45** | |

## Идея решения

Пререндер с прозрачной ценой за количество закешированных страниц, а не за рендеры; готовые интеграции (Cloudflare Worker, nginx, Netlify/Vercel middleware); отдельный отчёт «что видят GPTBot/ClaudeBot» как входная бесплатная проверка. Стек: Playwright-пул, Redis/S3-кеш, очередь перерендеринга по sitemap.

## Монетизация

Подписка $9–49/мес по числу страниц, агентский тариф на много доменов. Инфраструктура: headless Chrome дорог по CPU, но кеш с редким перерендером укладывается в $100–200/мес на первые сотни клиентов.

## Риски и открытые вопросы

- Рынок сжимается: фреймворки и AI-конструкторы переходят на SSR по умолчанию.
- Google официально считает dynamic rendering временным обходом.
- Стоимость CPU при росте числа страниц; защита от злоупотребления (сервис как бесплатный скрейпер).
- Нужен проход по Reddit и сообществам Lovable за свежими жалобами на альтернативы.

## Заметки

Найдено через Starter Story (история Prerender.io).
