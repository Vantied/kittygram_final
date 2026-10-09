# Kittygram — соцсеть для котиков с CI/CD

Сервис, где пользователи делятся фотографиями своих котиков и отмечают их достижения. Приложение упаковано в Docker-контейнеры и автоматически разворачивается на сервере при пуше в ветку main.

## Что сделано

- **Бэкенд** на Django REST Framework: котики (имя, цвет, год рождения, фото), достижения и связь многие-ко-многим между ними, аутентификация через Djoser.
- **Контейнеризация:** отдельные образы для бэкенда, фронтенда на React и шлюза Nginx, база PostgreSQL, статика и медиа хранятся в volumes.
- **CI/CD на GitHub Actions:** проверка кода flake8 и тесты pytest, тесты фронтенда, сборка трёх образов и публикация в Docker Hub, деплой на сервер по SSH и уведомление в Telegram об успешном деплое. Доступы к Docker Hub, серверу и боту хранятся в GitHub Secrets.

## Технологии

Python, Django, Django REST Framework, PostgreSQL, Nginx, Docker, Docker Compose, GitHub Actions, React.

## Как запустить локально

```bash
git clone https://github.com/Vantied/kittygram_final.git
cd kittygram_final
cp .env.example .env          # заполните значения
docker compose up -d --build
docker compose exec backend python manage.py migrate
docker compose exec backend python manage.py collectstatic
```

## Что я вынес из проекта

- Как собрать многоконтейнерное приложение и связать сервисы через Nginx.
- Как настроить полный пайплайн «тесты → сборка → деплой» без ручных действий.

## Автор

Иван Богатов — [GitHub](https://github.com/Vantied) · Telegram [@Ivan_bogatov55](https://t.me/Ivan_bogatov55)
