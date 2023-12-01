# Kittygram


## Описание

Cоциальная сеть для обмена фотографиями домашних животных. Состоит из бэкенд-приложения на Django и фронтенд-приложения на React. 

Поддерживает регистрацию и авторизацию, можно добавить нового питомца на сайт или изменить существующего, а также просмотреть записи других пользователей.


## Технологии

- Python 3.7
- Django
- Django REST Framework
- PostgreSQL
- Node.js
- React
- Gunicorn
- Nginx
- Docker
- GitHub Actions


## Как развернуть проект локально

1. Клонируйте репозиторий и перейдите в него в командной строке:
```bash
  git clone https://github.com/ArnoSimonian/kittygram.git
  cd kittygram
```

2. В папке ```kittygram/``` создайте файл ```.env``` с переменными окружения, следуя образцу заполнения:

```bash
  POSTGRES_DB=kittygram
  POSTGRES_USER=kittygram_user
  POSTGRES_PASSWORD=kittygram_password
  DB_NAME=kittygram
  DB_HOST=db
  DB_PORT=5432
```

3. Соберите и запустите докер-контейнеры через Docker Compose:

```bash
  docker compose up --build
```

## Как развернуть проект на сервере

Создайте папку ```kittygram/``` с файлом ```.env``` в домашней директории вашего сервера. Образец заполнения файла приведен выше.

```bash
  cd ~
  mkdir kittygram
  nano kittygram/.env
```

Настройте в nginx перенаправление запросов на порт 9000:

```bash
  location / {
        proxy_pass http://127.0.0.1:8000;
  }
```

Получите HTTPS-сертификат для доменного имени:
```sh
  sudo certbot --nginx
```
Добавьте в Secrets на GitHub Actions следующие переменные:

`DOCKER_USERNAME` _#  логин на Docker Hub_

`DOCKER_PASSWORD` _# пароль на Docker Hub_

`SSH_KEY` _# закрытый SSH-ключ для подключения к серверу_

`SSH_PASSPHRASE` _# пароль от этого ключа_

`USER` _#и мя пользователя на сервере_

`HOST` _# IP-адрес сервера_

`TELEGRAM_TO` _# ID телеграм-аккаунта для сообщений об успешном деплое_

`TELEGRAM_TOKEN` _# токен телеграм-бота_


При отправке коммита в ветку `main` с помощью `push` будет выполнен полный деплой проекта. Подробности в файле [main.yml](https://github.com/ArnoSimonian/kittygram/blob/main/.github/workflows/main.yml).


## Автор

Арно Симонян [@ArnoSimonian](https://www.github.com/ArnoSimonian)
