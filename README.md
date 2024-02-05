# Kittygram

[![Main Kittygram workflow](https://github.com/RavenIV/kittygram_final/actions/workflows/main.yml/badge.svg)](https://github.com/RavenIV/kittygram_final/actions/workflows/main.yml)

Социальная сеть для обмена фотографиями любимых домашних питомцев. 
Авторизованные пользователи могут добавлять, редактировать и удалять карточки собственных котиков,
а также смотреть карточки других пользователей.

## Стек технологий

Проект состоит из бэкенд-приложения на Django и фронтенд-приложения на React.

Бэкенд:

* Python (3.9)
* Django (3.2.3)
* Django REST framework (3.12.4)
* Djoser (2.1.0)

Фронтенд:

* Node.js
* React

## Запустить проект

Установить [Docker](https://www.docker.com/)

Клонировать репозиторий и перейти в него в командной строке:

```
git clone git@github.com:username/kittygram_final.git
```

```
cd kittygram_final
```

Скопировать содержание .env.example в .env

Собрать контейнеры и запустить проект из корневой директории:

```
docker compose -f docker-compose.production.yml up -d
```

Выполнить миграции:

```
docker compose -f docker-compose.production.yml exec backend python manage.py migrate
```

Собрать и перенести статику бэкенда:

```
docker compose -f docker-compose.production.yml exec backend python manage.py collectstatic
```

```
docker compose -f docker-compose.production.yml exec backend cp -r /app/collected_static/. /backend_static/static/
```

Проект будет доступен на странице http://localhost:9000/

## Переменные окружения

В файл .env также можно добавить:

* IP-адрес, доменное имя

```
ALLOWED_HOSTS=127.0.0.1, localhost, <your_host>, <domain_name>
```

* порта PostgreSQL в контейнере (по умолчанию 5432)

```
DB_PORT=0000
``` 

* для для запуска бэкенд-приложения в режиме разработки с использованием SQLite

```
DEBUG=True
``` 

Подробнее о запуске бэкенда можно посмотреть в README.md в директории backend.

