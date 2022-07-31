спринт 15 

Как запустить проект:
Клонируйте репозиторий infra_sp2 и сохраните в нём свой проект с API

Cоздать и активировать виртуальное окружение

Установить зависимости из файла requirements.txt

Запустить приложение в контейнерах:
docker-compose up -d --build

Выполнить миграции:
docker-compose exec web python manage.py migrate

Создать суперпользователя:
docker-compose exec web python manage.py createsuperuser

Собрать статику:
docker-compose exec web python manage.py collectstatic --no-input

Остановить приложение в контейнерах:
docker-compose down -v

Запуск pytest:
при запущенном виртуальном окружении
cd infra_sp2 && pytest

Документация API с примерами:
/redoc/

шаблон наполнения env-файла
.env
DB_ENGINE=<...> # указываем, что работаем с postgresql
DB_NAME=<...> # имя базы данных
POSTGRES_USER=<...> # логин для подключения к базе данных
POSTGRES_PASSWORD=<...> # пароль для подключения к БД (установите свой)
DB_HOST=<...> # название сервиса (контейнера)
DB_PORT=<...> # порт для подключения к БД
SECRET_KEY=<...> # ключ из settings.py

создайть дамп (резервную копию) базы:
docker-compose exec web python manage.py dumpdata > fixtures.json 