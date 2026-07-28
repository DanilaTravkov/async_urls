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

Для запуска потребуются:

- Node.js `>=20.19` или `>=22.12`
- pnpm
- Docker с поддержкой Docker Compose

Установите зависимости отдельно в каждом приложении:

```
pnpm --dir backend/async_jobs install
pnpm --dir frontend/async_jobs install
```

Запустите Redis:

```
docker compose -f backend/async_jobs/docker-compose.yml up -d redis
```

Запустите backend:

```
pnpm --dir backend/async_jobs run start:dev
```

В другом терминале запустите frontend:

```
pnpm --dir frontend/async_jobs run dev
```

При стандартном локальном запуске создавать файлы `.env` не требуется:
приложения используют предусмотренные в конфигурации значения по умолчанию.
Доступные переменные окружения перечислены в файлах `.env.example` каждого
приложения.

После запуска доступны:

- frontend — `http://localhost:5173`
- backend — `http://localhost:3000`
- Swagger UI — `http://localhost:3000/docs`

## Работа с submodules

Изменения следует коммитить и отправлять из соответствующего дочернего
репозитория. После этого umbrella репозиторий фиксирует новый commit submodule:

```
git add backend/async_jobs
git commit -m "chore: update backend"
git push
```

Обновить оба submodules до ветки `main` можно так:

```
git submodule update --remote --merge
git add backend/async_jobs frontend/async_jobs
git commit -m "chore: update submodules"
```

Функциональность, которая была разработана с помощью использования ИИ:
- Создание тестов
- Автокомиты и review кода
- Документация

Без использования ИИ:

- Архитектура
- Выбор технологий
- Компоненты на бекенде и фронтенде (код взят из открытых источников и официальных документаций или написан вручную)
