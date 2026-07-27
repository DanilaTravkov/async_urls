# Async URLs

Fullstack-сервис для создания асинхронных заданий проверки URL. Backend и
frontend хранятся в независимых Git-репозиториях и подключены сюда как
submodules:

- [Backend](https://github.com/DanilaTravkov/async_urls-backend)
- [Frontend](https://github.com/DanilaTravkov/async_urls-frontend)

## Клонирование

```powershell
git clone --recurse-submodules https://github.com/DanilaTravkov/async_urls.git
cd async_urls
```

Если репозиторий уже был клонирован без submodules:

```powershell
git submodule update --init --recursive
```

## Запуск

Установите зависимости отдельно в каждом приложении:

```powershell
pnpm.cmd --dir backend/async_jobs install
pnpm.cmd --dir frontend/async_jobs install
```

Запустите Redis:

```powershell
docker compose -f backend/async_jobs/docker-compose.yml up -d redis
```

Запустите backend:

```powershell
pnpm.cmd --dir backend/async_jobs run start:dev
```

В другом терминале запустите frontend:

```powershell
pnpm.cmd --dir frontend/async_jobs run dev
```

Backend по умолчанию доступен на `http://localhost:3000`, frontend — по адресу,
который выведет Vite.

## Работа с submodules

Изменения следует коммитить и отправлять из соответствующего дочернего
репозитория. После этого umbrella-репозиторий фиксирует новый commit submodule:

```powershell
git add backend/async_jobs
git commit -m "chore: update backend"
git push
```

Обновить оба submodules до ветки `main` можно так:

```powershell
git submodule update --remote --merge
git add backend/async_jobs frontend/async_jobs
git commit -m "chore: update submodules"
```
