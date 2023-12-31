
# Проект Kittygram.
Сервис для людей, у которых есть коты, с возможнстью добавления фотографий и их достижений.

## Запуск проекта через Docker локально на своем компьютере.

Установите Docker, используя инструкции с официального сайта:
https://www.docker.com/products/docker-desktop

Клонируйте репозиторий с проектом на свой компьютер.
В терминале из рабочей директории выполните команду:
```
git clone git@github.com:<репозиторий>
```

В папке foodgram-project-react выполните команду:
```
docker-compose up -d --build
```
### Для работы с удаленным сервером (на linux):
* Выполните вход на свой удаленный сервер.

* Установите docker на сервер:
```
sudo apt install docker.io 
```
* Локально отредактируйте файл infra/nginx/.conf, в строке server_name впишите свой IP
* Скопируйте файлы docker-compose.yml и nginx.conf из коневой папки и папки infra на сервер:

* Для работы с Workflow добавьте в Secrets GitHub переменные окружения для работы:
    ```
    POSTGRES_USER = <имя пользователя БД>
    POSTGRES_PASSWORD = <пароль>
    POSTGRES_DB = <название базы данных>
    DB_NAME=<имя базы данных postgres>
    DB_HOST=<db>
    DB_PORT=<5432>
    
    SECRET_KEY = <Ключ django приложения>
    DEBUG=True
    ALLOWED_HOSTS = <ip_сервера,localhost,127.0.0.1,домен>
    ```
* Workflow состоит из четырех шагов:
     - Проверка кода на соответствие PEP8 и выполнение тестов, реализованных в проекте
     - Сборка и публикация образа приложения на DockerHub.
     - Автоматическое скачивание образа приложения и деплой на удаленном сервере.
     - Отправка уведомления в телеграм-чат.  
  

* После успешного развертывания проекта на удаленном сервере, можно выполнить:
    ```
    - id контейнера можно узнать через команду docker compose ps
    ```
    - входим в терминал:
     ```
    sudo docker exec -it <id контейнера> /bin/bash
    ```
    - Создать суперпользователя Django:
    ```
    python3 manage.py createsuperuser
    ```
