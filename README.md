# Async URLs

Fullstack-сервис для создания асинхронных заданий проверки URL. Backend и
frontend хранятся в независимых Git-репозиториях и подключены сюда как
submodules:

- [Backend](https://github.com/DanilaTravkov/async_urls-backend)
- [Frontend](https://github.com/DanilaTravkov/async_urls-frontend)

## Клонирование

```
git clone --recurse-submodules https://github.com/DanilaTravkov/async_urls.git
cd async_urls
```

Если репозиторий уже был клонирован без submodules:

```
git submodule update --init --recursive
```

## Запуск

Для запуска потребуется Docker с поддержкой Docker Compose.

Запустите frontend, backend и Redis одной командой из корня репозитория:

```
docker compose up --build
```

После запуска доступны:

- frontend — `http://localhost:5173`
- backend — `http://localhost:3000`
- Swagger UI — `http://localhost:3000/docs`

Остановить контейнеры:

```
docker compose down
```

Функциональность, которая была разработана с помощью использования ИИ:
- Создание тестов
- Автокомиты и review кода
- Документация

Без использования ИИ:

- Архитектура
- Выбор технологий
- Компоненты на бекенде и фронтенде (код взят из открытых источников и официальных документаций или написан вручную)
