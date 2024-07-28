[![.github/workflows/main.yml](https://github.com/ViolettaValieva/kittygram_final/actions/workflows/main.yml/badge.svg)](https://github.com/ViolettaValieva/kittygram_final/actions/workflows/main.yml)

![Nginx](https://img.shields.io/badge/nginx-%23009639.svg?style=for-the-badge&logo=nginx&logoColor=white) ![JavaScript](https://img.shields.io/badge/javascript-%23323330.svg?style=for-the-badge&logo=javascript&logoColor=%23F7DF1E) ![Python](https://img.shields.io/badge/python-3670A0?style=for-the-badge&logo=python&logoColor=ffdd54) ![Django](https://img.shields.io/badge/django-%23092E20.svg?style=for-the-badge&logo=django&logoColor=white) ![DjangoREST](https://img.shields.io/badge/DJANGO-REST-ff1709?style=for-the-badge&logo=django&logoColor=white&color=ff1709&labelColor=gray) ![Postgres](https://img.shields.io/badge/postgres-%23316192.svg?style=for-the-badge&logo=postgresql&logoColor=white) ![Docker](https://img.shields.io/badge/docker-%230db7ed.svg?style=for-the-badge&logo=docker&logoColor=white) ![GitHub](https://img.shields.io/badge/github-%23121011.svg?style=for-the-badge&logo=github&logoColor=white) ![GitHub Actions](https://img.shields.io/badge/github%20actions-%232671E5.svg?style=for-the-badge&logo=githubactions&logoColor=white)

## Описание проекта

Kittygram — социальная сеть для обмена фотографиями котов и их достижений.

## Стек

- Python 3.9
- Django 3.2.3
- Django REST framework 3.12.4
- JavaScript
- Nginx
- Docker compose

## Запуск

Cоздайте папку проекта `kittygram`:

    ```bash
    mkdir kittygram
    cd kittygram
    ```

Создайте файл .env и заполните его своими данными по примеру.

    ```bash
    POSTGRES_DB=kittygram
    POSTGRES_USER=kittygram_user
    POSTGRES_PASSWORD=kittygram_password
    DB_NAME=kittygram
    DB_HOST=db
    DEBUG=False
    SECRET_KEY=django_secret_key_example
    ```
В папку проекта скопируйте файл `docker-compose.production.yml` и запустите его:

    ```bash
    sudo docker compose -f docker-compose.production.yml up
    ```

Произойдет скачивание образов, создание и включение контейнеров, создание томов и сети.

## Миграции, сбор статистики

После запуска нужно выполнить сбор статистики и миграции. Статистика фронтенда собирается во время запуска контейнера, после чего он останавливается. 

```bash
sudo docker compose -f [имя-файла-docker-compose.yml] exec backend python manage.py migrate

sudo docker compose -f [имя-файла-docker-compose.yml] exec backend python manage.py collectstatic

sudo docker compose -f [имя-файла-docker-compose.yml] exec backend cp -r /app/collected_static/. /static/static/
```

теперь проект доступен на: 

```
http://localhost:9000/
```

## Остановка

В окне, где был запуск **Ctrl+С** или в другом окне:

```bash
sudo docker compose -f docker-compose.yml down
```

## Автор

Виолетта Валиева https://github.com/ViolettaValieva
