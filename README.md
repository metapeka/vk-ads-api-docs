# VK Ads API — Полная документация

[![License: MIT](https://img.shields.io/badge/License-MIT-yellow.svg)](https://opensource.org/licenses/MIT)
![Pages](https://img.shields.io/badge/страниц-231-blue)
[![VK Ads](https://img.shields.io/badge/VK_Ads-API_docs-0077FF?logo=vk)](https://ads.vk.com/en/doc/api)

> **Полный референс VK Ads API в Markdown** — 231 страница документации, спарсенная с официального сайта [ads.vk.com/en/doc/api](https://ads.vk.com/en/doc/api).
>
> Подходит для **локального поиска**, **работы в LLM/агентах**, **навигации по API эндпоинтам** и **понимания всех объектов VK Ads API**.

---

## Почему этот репозиторий?

Официальная документация VK Ads API — это JavaScript SPA без статических страниц. Её нельзя читать офлайн, гуглить по содержимому или дать AI-ассистенту как контекст.

Этот репозиторий решает проблему: **вся документация в plain Markdown**, который можно:

- 📖 Читать прямо на GitHub с поиском и навигацией
- 🔍 Грепать по терминам (`grep -r "ad_plans" .`)
- 🤖 Скармливать LLM-агентам как knowledge base
- 🌐 Конвертировать в любой формат (PDF, HTML, JSON)
- ⚡ Искать мгновенно — без ожидания загрузки SPA

---

## Структура

```
docs/api/
├── README.md                    ← этот файл
│
├── info/                        ← Информационные/вводные страницы
│   ├── Quick_start.md           Быстрый старт: создание кампании с нуля
│   ├── Add_banners.md           Добавление баннеров в группу
│   ├── Authorization.md         Авторизация OAuth2 / client_credentials
│   ├── Overview.md              Обзор API и концепций
│   ├── SharingKeys.md           Ключи для шаринга аудиторий
│   ├── SearchPhrases.md         Поисковые фразы
│   ├── SegmentParams.md         Параметры сегментов
│   └── Statistics.md            Работа со статистикой
│
├── resource/                    ← HTTP-эндпоинты (endpoints)
│   ├── ads/                     (27 стр.) Кампании, группы, баннеры, контент, ссылки
│   ├── audiences/               (20 стр.) Сегменты, счётчики, списки пользователей, гео
│   ├── users/                   ( 5 стр.) Пользователи, агентства, клиенты
│   ├── dictionaries/            (10 стр.) Регионы, ОС, операторы, приложения, справочники
│   ├── finance/                 ( 2 стр.) Транзакции, история списаний
│   ├── leadforms/               ( 9 стр.) Лид-формы: создание, экспорт, копирование
│   ├── subscriptions/           ( 2 стр.) Webhook-подписки
│   └── surveys/                 ( 7 стр.) Опросы: вопросы, респонденты, экспорт
│
└── object/                      ← Модели данных (data types)
    ├── ads/                     (42 стр.) AdPlan, AdGroup, Banner, Targetings и др.
    ├── audiences/               (27 стр.) Segment, SharingKey, LocalGeo и др.
    ├── users/                   (20 стр.) User, Agency, ManagerClient и др.
    ├── dictionaries/            (12 стр.) Region, MobileCategory, AppleApp и др.
    ├── finance/                 ( 2 стр.) Transaction, TransactionGroup
    ├── leadforms/               (20 стр.) LeadForm, LeadQuestion, Answer и др.
    ├── subscriptions/           ( 1 стр.) Subscription
    └── surveys/                 (17 стр.) Survey, Question, Condition, Answer
```

---

## Быстрый старт (для агентов и поиска)

### Поиск всех эндпоинтов

```bash
grep -r 'GET\|POST\|PUT\|DELETE' docs/api/resource/ --include="*.md"
```

### Поиск по ключевым словам

```bash
# Найти всё про таргетинг
grep -r "targetings\|Targetings" docs/api/object/ads/

# Найти описание конкретного объекта
cat docs/api/object/ads/Banner.md

# Найти эндпоинт
cat docs/api/resource/ads/AdPlans.md
```

### Дать как контекст LLM

Самый большой и полезный файл — `docs/api/object/ads/Targetings.md` (описание всех полей таргетинга).

Для компактной подачи агенту можно склеить эндпоинты вместе:

```bash
cat docs/api/resource/ads/*.md > /tmp/vk_ads_endpoints.md
```

---

## API на верхнем уровне

### Базовые URL

| Версия | Базовый URL |
|--------|------------|
| v1 | `https://ads.vk.com/api/v1/` |
| v2 | `https://ads.vk.com/api/v2/` |
| v3 | `https://ads.vk.com/api/v3/` |

### Аутентификация

Все запросы требуют заголовок `Authorization: Bearer {access_token}`.

Получение токена: `POST /api/v2/oauth2/token.json` с `grant_type=client_credentials`.

### Иерархия сущностей

```
AdPlan (кампания)
  ├── AdGroup (группа)
  │   ├── targetings
  │   ├── banners
  │   ├── content (изображения, видео, HTML5)
  │   ├── urls (ссылки)
  │   └── textblocks (тексты)
  └── ...
```

### Ключевые эндпоинты

| Эндпоинт | Методы | Описание |
|----------|--------|----------|
| `/api/v2/ad_plans.json` | GET, POST | Список/создание кампаний |
| `/api/v2/ad_plans/{id}.json` | GET, POST, DELETE | Кампания |
| `/api/v2/ad_groups.json` | GET, POST | Группы объявлений |
| `/api/v2/banners.json` | GET | Баннеры |
| `/api/v2/banners/{id}.json` | GET, POST, DELETE | Баннер |
| `/api/v2/content/{type}.json` | POST | Загрузка креативов |
| `/api/v2/statistics.json` | GET | Статистика |
| `/api/v2/budget.json` | GET | Бюджет кабинета |
| `/api/v2/regions.json` | GET | Справочник регионов |
| `/api/v2/targetings_tree.json` | GET | Дерево интересов |
| `/api/v2/remarketing/segments.json` | GET, POST | Сегменты аудиторий |
| `/api/v3/remarketing/users_lists.json` | GET, POST | Списки пользователей |
| `/api/v1/lead_ads/lead_forms.json` | GET, POST | Лид-формы |
| `/api/v3/subscription.json` | GET, POST | Webhook-подписки |
| `/api/v3/user.json` | GET, POST | Профиль пользователя |
| `/api/v2/agency/clients.json` | GET, POST | Клиенты агентства |
| `/api/v2/billing/transaction_groups.json` | GET | История транзакций |

---

## Связанные ресурсы

- 🎯 [MCP сервер VK Ads](https://www.npmjs.com/package/@theyahia/vk-ads-mcp) — AI-агент для работы с VK Ads API
- 🌐 [Официальная документация](https://ads.vk.com/en/doc/api) — оригинал (JavaScript SPA)
- 📦 [@theyahia/mcp-skills](https://github.com/theYahia/mcp-skills) — готовые AI-скиллы для маркетинга

---

## Лицензия

MIT. Данные спарсены из публичной документации VK Ads API. VK — зарегистрированный товарный знак VK Group.

---

_Собрано: 2026-06-03 · 231 файл · ~470 KB markdown_
