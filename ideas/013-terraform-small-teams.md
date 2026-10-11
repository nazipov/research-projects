---
id: 013
title: Terraform/OpenTofu для маленьких команд после отмены бесплатного HCP Terraform
status: scored
added: 2026-10-11
updated: 2026-10-11
direction: micro-saas
scores:
  pays: 4
  b2b: 5
  frequency: 4
  competitor_gaps: 2
  mvp_solo: 3
  low_support: 3
  audience: 4
  owner_edge: 5
  claude_code: 4
total: 34
---

# 013. Terraform/OpenTofu для маленьких команд после отмены бесплатного HCP Terraform

## Проблема

31.03.2026 HashiCorp закрыла legacy-бесплатный тариф HCP Terraform. Новый бесплатный ограничен 500 ресурсами и 1 параллельным запуском, платные тарифы — от $0.10 до $0.99 за ресурс в месяц. Один кластер EKS с сетью и IAM съедает 50–80 ресурсов. Маленьким командам нужно куда-то перенести state и PR-автоматизацию.

## Целевая аудитория

Стартапы и агентства из 2–10 инженеров с 1–3 облачными аккаунтами, которые жили на бесплатном Terraform Cloud.

## Почему это больно

Миграция state рискованна (удаление workspace необратимо), а per-resource цена растёт вместе с инфраструктурой без связи с ценностью.

## Как решают сейчас

- OpenTofu + S3/GCS-бэкенд + свой CI.
- Atlantis (self-hosted), Terrateam, OpenTaco (бывший Digger).
- Scalr, Spacelift, env0.

## Доказательства

- [HN: HashiCorp no longer offers a free plan for Terraform Cloud](https://news.ycombinator.com/item?id=46278994): обсуждение отмены бесплатного тарифа.
- [DEV: HCP Terraform Free Tier Ending — OpenTofu Migration Guide](https://dev.to/x4nent/hcp-terraform-free-tier-ending-opentofu-migration-guide-27ja): пользователи мигрируют.
- [AgentDeals: Terraform Cloud free tier removed](https://agentdeals.dev/terraform-cloud-free-tier-removed): лимит 500 ресурсов, цены за ресурс, 8 альтернатив.
- [env0: HCP Terraform free tier changed](https://www.env0.com/insights/hcp-terraforms-free-tier-changed-is-it-time-to-consider-a-terraform-cloud-alternative): один EKS-кластер — 50–80 ресурсов (блог конкурента).

## Конкуренты

| Продукт | Цена | Слабые места (по отзывам) | Ссылка |
|---|---|---|---|
| HCP Terraform | бесплатно до 500 ресурсов; $0.10–0.99 за ресурс/мес | цена за ресурс, 1 параллельный запуск | [AgentDeals](https://agentdeals.dev/terraform-cloud-free-tier-removed) |
| Terrateam | бесплатно (безлимит пользователей и запусков); Pro $224/мес | ? | [Toolradar](https://toolradar.com/tools/terrateam/pricing) |
| OpenTaco (Digger) | open source; Pro $49/пользователь, от 5 пользователей | ? | [Toolradar](https://toolradar.com/tools/digger/pricing) |
| Scalr | бесплатно ~50 запусков/мес; $0.99 за запуск (источники расходятся) | ? | [AgentDeals](https://agentdeals.dev/vendor/scalr) |

## Оценка

| Критерий | Балл | Обоснование |
|---|---|---|
| 1. За решение платят | 4 | Несколько платных платформ с ценами |
| 2. Платит бизнес | 5 | Инженерные команды, чек $50–200+/мес |
| 3. Регулярность боли | 4 | Изменения инфраструктуры еженедельно |
| 4. Слабости конкурентов | 2 | Жалобы в основном на HCP; Terrateam и OpenTaco бесплатно закрывают маленькие команды |
| 5. MVP в одиночку | 3 | Бэкенд state + блокировки + PR-планы + безопасность: скорее 4 недели, чем 2 |
| 6. Низкая поддержка | 3 | Сбой в state или apply — срочная поддержка, высокая ответственность |
| 7. Доступность аудитории | 4 | r/Terraform, HN, DevOps-чаты |
| 8. Преимущество владельца | 5 | Terraform — прямой опыт владельца |
| 9. Реализуемо через Claude Code | 4 | Стандартный бэкенд и GitHub App; нужна ручная проверка безопасности |
| **Итого** | **34/45** | |

## Идея решения

Managed state backend для OpenTofu/Terraform (HTTP backend с блокировками и версиями state) + GitHub Action, который пишет план в PR. Плоская цена за организацию, а не за ресурс. Импорт state из HCP одной командой.

## Монетизация

$29/мес за организацию до N workspaces, $99/мес — без лимитов. $10k MRR ≈ 100–350 команд. Инфраструктура дешёвая: state — это небольшие файлы.

## Риски и открытые вопросы

- Бесплатные Terrateam, OpenTaco и S3-бэкенд закрывают потребность — нужен заметный плюс (простая миграция, плоская цена, drift detection).
- Хранение state = доступ к секретам клиентов: высокие требования к безопасности, доверие трудно заработать соло.

## Заметки

Высокий балл держится на опыте владельца; рыночный пробел слабый.
