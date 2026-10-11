---
id: 026
title: Помощь инди-разработчикам с правилом Google Play «12 тестеров на 14 дней»
status: scored
added: 2026-10-11
updated: 2026-10-11
direction: micro-saas
scores:
  pays: 4
  b2b: 3
  frequency: 1
  competitor_gaps: 3
  mvp_solo: 4
  low_support: 3
  audience: 5
  owner_edge: 2
  claude_code: 4
total: 29
---

# 026. Помощь инди-разработчикам с правилом Google Play «12 тестеров на 14 дней»

## Проблема

Личные аккаунты разработчиков, созданные после 13.11.2023, должны провести закрытое тестирование с 12 тестерами в течение 14 дней перед публикацией. Соло-разработчикам трудно найти тестеров, которые не отвалятся за две недели; если тестеров станет меньше 12, отсчёт начинается заново.

## Целевая аудитория

Соло-разработчики Android и Flutter с личными аккаунтами Google Play.

## Почему это больно

Публикация откладывается на недели; часть разработчиков платит случайным людям на Fiverr.

## Как решают сейчас

- Обмен тестерами в сообществах
- Платные сервисы: Testers Community, Ubertesters, PrimeTestLab, Fiverr
- Аккаунт организации (дорого и сложно)

## Доказательства

- [Android Authority: Google снизил требование с 20 до 12 тестеров](https://androidauthority.com/google-play-app-testing-requirement-3510580): правило подтверждено.
- [Level Up Coding: the 12-tester tax is killing solo devs](https://levelup.gitconnected.com/the-12-tester-tax-google-plays-closed-testing-rule-is-quietly-killing-solo-devs-2cea83c2e338): жалобы соло-разработчиков.
- [FlutterFlow community: как найти 12 тестеров на 14 дней](https://community.flutterflow.io/ask-the-community/post/how-can-i-get-12-testers-for-14-days-for-my-app-OSiPGbS6HLIwszD): прямой запрос.
- [Fiverr: 12 тестеров для Google Play](https://fiverr.com/jack_coplen/provide-12-testers-google-play-closed-testing-for-android-app-in-14-days-testing): за это уже платят.

## Конкуренты

| Продукт | Цена | Слабые места (по отзывам) | Ссылка |
|---|---|---|---|
| Testers Community | ? (возврат при отказе Google) | ? | [Trustpilot](https://de.trustpilot.com/review/testerscommunity.com) |
| Ubertesters | ? | материалы ещё про 20 тестеров | [Ubertesters](https://ubertesters.com/blog/experience-premium-closed-testing-get-20-testers-for-14-days-on-your-android-app/) |
| Fiverr-исполнители | ? | ненадёжность | [Fiverr](https://fiverr.com/jack_coplen/provide-12-testers-google-play-closed-testing-for-android-app-in-14-days-testing) |

## Оценка

| Критерий | Балл | Обоснование |
|---|---|---|
| 1. За решение платят | 4 | Платные сервисы и фриланс уже есть |
| 2. Платит бизнес | 3 | Инди-разработчики, разовый чек $15–50 |
| 3. Регулярность боли | 1 | Нужно один раз на аккаунт или приложение |
| 4. Слабости конкурентов | 3 | Жалобы на ненадёжность тестеров; рынок молодой |
| 5. MVP в одиночку | 4 | Биржа обмена тестерами с контролем активности: 2–3 недели |
| 6. Низкая поддержка | 3 | Споры о неактивных тестерах |
| 7. Доступность аудитории | 5 | r/androiddev, r/FlutterDev, FlutterFlow |
| 8. Преимущество владельца | 2 | Не DevOps |
| 9. Реализуемо через Claude Code | 4 | Веб-платформа + простое Android-приложение |
| **Итого** | **29/45** | |

## Идея решения

Биржа взаимного тестирования: разработчик тестирует чужие приложения и получает тестеров для своего; автоматический контроль, что тестер не удалил приложение. Платно — гарантия и ускорение.

## Монетизация

$19–49 за запуск. Разовая покупка, не MRR; для $10k/мес нужно 200–500 запусков в месяц.

## Риски и открытые вопросы

- Google может изменить правило или запретить «покупку» тестеров.
- Нет повторных покупок — нет MRR.

## Заметки


