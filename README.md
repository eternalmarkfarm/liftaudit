# LiftAudit (MVP scaffold)

Каркас проекта для MVP: `Next.js + FastAPI + worker + Redis + Nginx`.

## Структура
- `frontend` — веб-интерфейс и личный кабинет.
- `backend` — API и бизнес-логика.
- `worker` — фоновые задачи проверки документов.
- `infra` — деплой и инфраструктурные конфиги.

## Важно про PostgreSQL
PostgreSQL не запускается в Docker Compose, используется внешний сервер.
Заполните `.env` на основе `.env.example` и укажите:
- `POSTGRES_HOST`
- `POSTGRES_PORT`
- `POSTGRES_DB`
- `POSTGRES_USER`
- `POSTGRES_PASSWORD`
- `DATABASE_URL` (опционально, если удобнее одной строкой)

## Локальный запуск
1. Создать `.env`:
```bash
cp .env.example .env
```
2. Заполнить реальные данные внешней PostgreSQL.
3. Запустить:
```bash
docker compose -f infra/docker-compose.yml up --build
```
4. Проверка:
- frontend через `http://localhost/`
- API health через `http://localhost/api/health`

## Бэкап PostgreSQL
Скрипт:
```bash
./infra/scripts/backup_postgres.sh
```
Требует установленных `pg_dump` и переменных окружения PostgreSQL.
