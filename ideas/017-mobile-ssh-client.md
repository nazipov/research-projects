---
id: 017
title: Мобильный SSH-клиент с разовой покупкой
status: scored
added: 2026-10-11
updated: 2026-10-11
direction: mobile-app
scores:
  pays: 4
  b2b: 3
  frequency: 4
  competitor_gaps: 1
  mvp_solo: 3
  low_support: 4
  audience: 5
  owner_edge: 5
  claude_code: 3
total: 32
---

# 017. Мобильный SSH-клиент с разовой покупкой

## Проблема

Админам и разработчикам нужен SSH с телефона. Termius работает только по подписке, и цена растёт из года в год; Blink Shell перешёл на подписку и расстроил часть пользователей, купивших раньше.

## Целевая аудитория

DevOps-инженеры, сисадмины, разработчики, в 2026 году — ещё и пользователи AI-агентов для кода, которые управляют ими с телефона.

## Почему это больно

Подписка $60–119 в год за инструмент, которым пользуешься пару раз в неделю, кажется переплатой.

## Как решают сейчас

Termius, Blink Shell, Prompt 3, WebSSH, а в 2026 году — волна новых клиентов (TermAI, Moshi, TermRover, PocketShell, Onepilot).

## Доказательства

- [TermRover: Termius alternatives 2026](https://termrover.sh/blog/termius-alternatives/): у Termius только подписка, цена растёт год от года.
- [TermAI: Blink Shell vs Termius](https://termai.sh/blog/blink-shell-vs-termius): переход Blink на подписку расстроил часть давних пользователей.
- [ElmLabs: best mobile SSH app 2026](https://elmlabs.dev/en/blog/best-mobile-ssh-app-2026): сравнение Termius, Blink, Onepilot.
- [Moshi: best iOS terminal app 2026 for AI agents](https://getmoshi.app/articles/best-ios-terminal-app-coding-agent): новый спрос — управление AI-агентами через SSH и Mosh.

## Конкуренты

| Продукт | Цена | Слабые места (по отзывам) | Ссылка |
|---|---|---|---|
| Termius | Pro $10–15/мес или $60–119/год (источники расходятся) | только подписка, синхронизация только в платных тарифах | [TermRover](https://termrover.sh/blog/termius-alternatives/) |
| Blink Shell | $19.99/год (есть lifetime) | переход на подписку | [TermAI](https://termai.sh/blog/blink-shell-vs-termius) |
| Prompt 3 | $19.99/год или $99 lifetime (источники расходятся) | ? | [TermAI](https://termai.sh/blog/prompt-3-vs-termius) |
| TermRover, PocketShell | lifetime $79.99 / $99.99 | ? | [PocketShell](https://pocketshell.app/alternatives/termius/) |
| WebSSH | разовая ~$2.50 | только Apple | [блог](https://asepalazhari.com/blog/webssh-termius-alternative-apple-ecosystem) |

## Оценка

| Критерий | Балл | Обоснование |
|---|---|---|
| 1. За решение платят | 4 | Платные клиенты с ценами, но много дешёвых |
| 2. Платит бизнес | 3 | Специалисты, чек $20–100 в год |
| 3. Регулярность боли | 4 | Пользуются несколько раз в неделю |
| 4. Слабости конкурентов | 1 | Ниша «без подписки» уже занята, в 2026 году вышло множество новых клиентов |
| 5. MVP в одиночку | 3 | Эмуляция терминала и клавиатура на телефоне — сложная часть, даже с готовыми библиотеками |
| 6. Низкая поддержка | 4 | Техническая аудитория, self-service |
| 7. Доступность аудитории | 5 | r/selfhosted, r/sysadmin, HN |
| 8. Преимущество владельца | 5 | Прямой опыт владельца |
| 9. Реализуемо через Claude Code | 3 | Нативный UI терминала, ввод с клавиатуры и тесты на устройствах |
| **Итого** | **32/45** | |

## Идея решения

Не делать ещё один клиент. Если входить, то в нишу: SSH + управление AI-агентами для кода с телефона (уведомления о завершении задачи, быстрые ответы) — но и тут уже есть конкуренты.

## Монетизация

Разовая покупка $20–50 или $15–20/год. Инфраструктура $0.

## Риски и открытые вопросы

- Ниша переполнена; высокий балл держится на опыте владельца, а не на рынке.

## Заметки

Записано, чтобы не возвращаться.
