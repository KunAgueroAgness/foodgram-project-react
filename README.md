[![Foodgram workflow](https://github.com/KunAgueroAgness/foodgram-project-react/actions/workflows/foodgram_workflows.yml/badge.svg)](https://github.com/KunAgueroAgness/foodgram-project-react/actions/workflows/foodgram_workflows.yml)

# Продуктовый помощник Foodgram

***Foodgram*** - это сайт рецептов. Продуктовый помощник, позволяющий просматривать и создавать рецепты, добавлять их в
избранное, подписываться на авторов рецептов, формировать список покупок с ингредиентами для приготовления понравившихся
блюд.

Демо сайт доступен по этому [адресу](http://130.193.40.240/recipes)

### _Технологии_

```
- docker==6.0.0
- django==2.2.19
- django-colorfield==0.7.2
- django-cors-headers
- django-filter==2.4
- djangorestframework==3.12.4
- djoser==2.1.0
- drf-extra-fields
- gunicorn==20.0.4
- Pillow==8.3.1
- psycopg2-binary==2.8.6
- PyJWT==2.1.0
- python-dotenv==0.21.0
- requests==2.26.0
- sorl-thumbnail==12.7.0
- weasyprint
```

### _Описание_
***Foodgram*** - это сайт рецептов. Продуктовый помощник, позволяющий просматривать и создавать рецепты, добавлять их в
избранное, подписываться на авторов рецептов, формировать список покупок с ингредиентами для приготовления понравившихся
блюд.

### Запуск проекта с использованием Docker


### *Клонируйте репозиторий:*
```
git clone git@github.com:KunAgueroAgness/foodgram-project-react.git
```

### *Установите и активируйте виртуальное окружение:*
Win:
```
python -m venv venv
venv/Scripts/activate
```

Mac:
```
python3 -m venv venv
source venv/bin/activate
```

### *Установите зависимости из файла requirements.txt:*
```
pip install -r requirements.txt
```

### *Перейдите в директорию с файлом manage.py, создайте и примените миграции (python3 для Mac):*
```
cd backend
python manage.py makemigrations
python manage.py migrate
```

### *Создайте суперпользователя (python3 для Mac):*
```
python manage.py createsuperuser
```

### *Запустите сервер (python3 для Mac):*
```
python manage.py runserver
```

### *Чтобы запустить проект через докер:*
В папке **frontend** соберите образ docker `build -t YourDockerNickname/foodgram_frontend .`

В папке **infra** создайте файл **.env** и заполните его данными. Пример:
```
SECRET_KEY=YourSecretKeyFromDjangoProjectSettings
DEBUG=True
ALLOWED_HOSTS='*'
DB_ENGINE=django.db.backends.postgresql
DB_NAME=postgres
DB_USER=postgres
DB_PASSWORD=postgres
DB_HOST=db
DB_PORT=5432
```
Для работы с workflow и деплоем на сервер добавьте Github Secrets. Шаблон:
```
DB_ENGINE=django.db.backends.postgresql
DB_NAME=postgres
DB_USER=postgres
DB_PASSWORD=postgres
DB_HOST=db
DB_PORT=5432
DEBUG=True
DOCKER_PASSWORD=YourPassword
DOCKER_USERNAME=YourUsername

USER=ServerUsername
HOST=ServerIP
PASSPHRASE=GitPassphrase
SSH_KEY=SSHKey (для получения команда: cat ~/.ssh/id_rsa)

TELEGRAM_TO=YourTelegramID
TELEGRAM_TOKEN=BotToken
```
Далее в папке **infra** запустите команду `docker-compose up --build`

После сборки запустите миграции, соберите статику, создайте суперпользователя, подгрузите данные из копии бд:
```
docker-compose exec backend python manage.py makemigrations
docker-compose exec backend python manage.py migrate
docker-compose exec backend python manage.py collectstatic --no-input
docker-compose exec backend python manage.py loaddata dump.json
docker-compose exec backend python manage.py createsuperuser
```
Для остановки контейнера `docker-compose down -v`
</details>выполните:

   `docker pull shinigamiyoko/foodgram:final`

### Разработчик:
```
[Эльдар Сабирович](https://github.com/KunAgueroAgness)
```
