'Описание проекта:

Проект Kittygram социальная сеть для обмена фотографиями. Проект состоит из бэкенд-приложения на Django и фронтенд-приложения на React. В Kittygram пользователи могут создавать, просматривать, редактировать и удалять записи. Запись може содержать в себе такую информацию как: имя котика, его возраст, окрас, фотография и достижения.

Технологии

Python 3.10

Django 3.2.3

Django REST Framework 3.12.4

Pillow 9.0.0

Gunicorn 20.1.0

Nginx 1.18.0

certbot 2.6.0

Как запустить проект:

Чтобы настроить проект к работе на удаленном сервере необходимо выполнить следующие шаги:

Клонируйте репозиторий проекта командой:
git clone https://github.com/kora21/infra_sprint1.git

Перейдите в дерикторию проекта и с активирванным вирутальным окружением загрузите зависимости командой:
pip install -r requirements.txt

Настройте базу данных, запустив миграции командой:
python manage.py migrate

Перед запуском WSGI-сервера измените строки в файле юнита, подставьте в 11 и 13 строки ваши пути до проекта. По умолчанию gunicorn использует следующий пути:
WorkingDirectory=/home/yc-user/infra_sprint1/backend/

 

ExecStart=/home/yc-user/infra_sprint1/backend/env/bin/gunicorn --bind 0.0.0.0:8030 kittygram_backend.wsgi

Запустите юнит WSGI-сервера командами в терминале Linux:
sudo systemctl start gunicorn

sudo systemctl enable gunicorn

Запустите веб- и обратный прокси-сервер Nginx
sudo systemctl start nginx

Далее Вам необходимо выполнить настройку Nginx, изменив пути размещения статики Kittygram. Настройка може включать в себя следующие шаги: I. Собрать статику фронтенд-приложения и разместить её в той директории, которую Nginx использует по умолчанию для доступа к статическим файлам. II. Собрать статику бэкенд-приложения и разместить её в директории, которую Nginx использует по умолчанию для доступа к статическим файлам.

Готово! Kittygram готов к использованию!

Автор: kora21
