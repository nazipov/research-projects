---
id: 005
title: Telegram-бот расшифровки и пересказа голосовых сообщений
status: scored
added: 2026-10-11
updated: 2026-10-11
direction: telegram-bot
scores:
  pays: 3
  b2b: 2
  frequency: 5
  competitor_gaps: 2
  mvp_solo: 5
  low_support: 4
  audience: 3
  owner_edge: 2
  claude_code: 5
total: 31
---

# 005. Telegram-бот расшифровки и пересказа голосовых сообщений

## Проблема

Люди получают длинные голосовые и не могут их слушать на встрече или в шуме. Нужен текст, краткий пересказ и перевод. Встроенная расшифровка Telegram доступна только с Premium.

## Как решают сейчас

- Telegram Premium: встроенная расшифровка голосовых.
- Боты: summar.ee, Briefly, WhisperBot и десятки клонов; готовый исходный код таких ботов продают на Gumroad.

## Доказательства

- [Indie Hackers: Easy note taking using your voice in Telegram](https://www.indiehackers.com/post/easy-note-taking-using-your-voice-in-telegram-c832f58447): бот расшифровки с платой $2.99/нед или $9.99/мес, lifetime $27.99 (январь 2024).
- [SaaSHub: summar.ee](https://www.saashub.com/compare-summar-ee-vs-createwise-ai): расшифровка, пересказ и перевод; автор утверждает, что встроенная функция Premium медленнее и хуже.
- [Gumroad: VoiceFlow](https://gitshow.gumroad.com/l/vcalk): исходный код такого бота продаётся от $30 — порог входа почти нулевой.
- [Product Hunt: WhisperBot](https://www.producthunt.com/products/whisperbot): запуск почти без отклика.

## Конкуренты

| Продукт | Цена | Слабые места (по отзывам) | Ссылка |
|---|---|---|---|
| Telegram Premium | ? (встроено в подписку) | по словам конкурента, медленнее и хуже качеством | [SaaSHub](https://www.saashub.com/compare-summar-ee-vs-createwise-ai) |
| Бот с Indie Hackers | $9.99/мес (2024) | ? | [Indie Hackers](https://www.indiehackers.com/post/easy-note-taking-using-your-voice-in-telegram-c832f58447) |
| summar.ee | ? | ? | [SaaSHub](https://www.saashub.com/compare-summar-ee-vs-createwise-ai) |

## Оценка

| Критерий | Балл | Обоснование |
|---|---|---|
| 1. За решение платят | 3 | Есть платные боты с ценами, но нет данных о выручке; функция встроена в Premium |
| 2. Платит бизнес | 2 | В основном частные лица, чек $3–10/мес |
| 3. Регулярность боли | 5 | Голосовые приходят ежедневно |
| 4. Слабости конкурентов | 2 | Встроенная функция Telegram и много клонов; жалоб на них не найдено |
| 5. MVP в одиночку | 5 | Whisper + LLM + оплата Stars: около недели |
| 6. Низкая поддержка | 4 | Self-service, но вопросы по оплате и лимитам |
| 7. Доступность аудитории | 3 | B2C: виральность в чатах возможна, но платный маркетинг дорогой |
| 8. Преимущество владельца | 2 | Обычная разработка, DevOps не даёт преимущества |
| 9. Реализуемо через Claude Code | 5 | Бот + Whisper + LLM: небольшой объём кода, всё через API |
| **Итого** | **31/45** | |

## Идея решения

Бот в группы и Telegram Business: расшифровывает голосовые и кружки, делает пересказ и задачи из длинных сообщений. Оплата через Telegram Stars. Стек: Whisper API или локальная модель, LLM для пересказа.

## Риски и открытые вопросы

- Платформа сама закрывает функцию (Telegram Premium) — продукт может обнулиться одним обновлением.
- Переход в WhatsApp, скорее всего, закрыт: с 15.01.2026 Meta запретила в Business API универсальных ИИ-ассистентов ([Business Standard](https://www.business-standard.com/technology/tech-news/meta-bans-ai-chatbots-from-whatsapp-business-api-chatgpt-to-shut-down-jan-2026-125102200335_1.html)). Проверить, есть ли в самом WhatsApp встроенная расшифровка.
- Себестоимость: расшифровка через API съедает маржу при чеке $3–10.

## Заметки

Как самостоятельный продукт слабее 004. Можно встроить как функцию в 004: расшифровка голосовых от клиентов бизнеса.
