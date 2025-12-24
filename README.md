# 📰 AI Content Generator API

Микросервис для автоматического создания статей в Telegram на основе актуальных новостей, с применением промпт-инжиниринга.

## 🎯 Задача

Авторам контента и SMM-специалистам нужен инструмент, чтобы:
- 📰 **Получать свежие новости** по любой теме в реальном времени
- 🤖 **Генерировать контент** (заголовок, мета-описание, полную статью) одним запросом
- 🚀 **Масштабировать** создание контента без ручной работы

Этот API делает именно это: за одну секунду превращает тему в готовую статью с актуальными примерами.

## 💡 Как это работает

```
Тема: "AI in Healthcare"
         ↓
   [Currents API] → Получаем 5 свежих новостей
         ↓
   [Промпт-инжиниринг] → Генерируем заголовок
         ↓
   [GPT-4o-mini] → Генерируем мета-описание
         ↓
   [Промпт с примерами] → Генерируем полную статью (1500+ символов)
         ↓
   Результат: готовый контент с актуальными примерами
```

## 🛠 Технический стек

| Компонент | Технология |
| :--- | :--- |
| **Backend** | FastAPI (async, production-ready) |
| **Server** | Uvicorn |
| **AI** | OpenAI API (GPT-4o-mini) |
| **News API** | Currents API (real-time news) |
| **Deployment** | Docker-ready (любой облак) |

## 🚀 Быстрый старт

### Локально

1. **Установите зависимости:**
   ```bash
   pip install -r requirements.txt
   ```

2. **Установите переменные окружения:**
   ```bash
   export OPENAI_API_KEY="sk-..."
   export CURRENTS_API_KEY="cur_..."
   ```

3. **Запустите сервис:**
   ```bash
   python app.py
   ```
   Сервис запустится на `http://localhost:8000`

### Тестирование API

```bash
curl -X POST "http://localhost:8000/generate-post" \
  -H "Content-Type: application/json" \
  -d '{"topic": "AI in Healthcare"}'
```

**Ответ:**
```json
{
  "title": "Революция в здравоохранении: как ИИ спасает жизни",
  "meta_description": "Узнайте, как AI трансформирует диагностику...",
  "post_content": "Медицина стоит на пороге... [1500+ символов]"
}
```

### На облачной платформе (Render, Railway)

1. Создайте репозиторий на GitHub
2. Подключите облачный сервис
3. Добавьте переменные окружения: `OPENAI_API_KEY`, `CURRENTS_API_KEY`
4. Деплойте!

## 📡 API Endpoints

| Метод | Endpoint | Описание |
| :--- | :--- | :--- |
| `POST` | `/generate-post` | Генерирует статью на тему |
| `GET` | `/` | Проверка состояния сервиса |
| `GET` | `/heartbeat` | Health check |

## ⚙️ Request/Response

**Request:**
```json
{
  "topic": "Квантовые вычисления"
}
```

**Response:**
```json
{
  "title": "string",
  "meta_description": "string",
  "post_content": "string (1500+ символов с примерами из новостей)"
}
```

## 🔑 Требуемые API ключи

- **OpenAI API** — [получить](https://platform.openai.com/api-keys)
- **Currents API** — [получить](https://currentsapi.services/)

## 🎓 Что демонстрируется

- ✅ **Промпт-инжиниринг** — структурированные промпты для конкретных результатов
- ✅ **API дизайн** — RESTful эндпоинты, обработка ошибок
- ✅ **Интеграции** — работа с внешними API (OpenAI, Currents)
- ✅ **Production-code** — async, error handling, environment variables
- ✅ **Масштабируемость** — готово к Docker и облачному деплою

## 🚨 Лимиты

- Currents API имеет free tier с лимитом запросов
- OpenAI запросы платные (используется GPT-4o-mini для экономии)

---

**Стек:** FastAPI · OpenAI GPT-4o-mini · Currents API · Python 3.9+


