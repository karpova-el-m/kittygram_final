## Проект Kittygram

> Проект Kittygram представляет собой интернет-ресурс, на котором владельцы котов могут размещать информацию о своих питомцах, включая фотографии.
> Проект был создан исключительно в учебных целях, и никакой практической пользы он не несет.

Позволяет:

* Реализовывать методы GET, POST, PATCH, DELETE для моделей Achievement и Cat;
* Авторизовываться и аутентифицироваться через Authtoken DRF;
* Разграничивать доступ для неавторизованных, авторизованных пользователей и авторов;
  
___

Стек инструментов и технологий, использованный в проекте:
* Python 3.9
* Django 3.2
* Django REST Framework 3.12.4
* API
* Authtoken DRF
* Docker-compose
* Nginx
* Pillow
* Gunicorn
___

### Как запустить проект на сервере (OS Linux):

Подключиться к удаленному серверу:
~~~bash
ssh -i путь_до_файла_с_SSH_ключом/название_файла_с_SSH_ключом имя_пользователя@ip_адрес_сервера
~~~

Установить Docker и Docker Compose для Linux, создать папку проекта и перейти в нее:
~~~bash
sudo apt update
sudo apt install curl
curl -fSL https://get.docker.com -o get-docker.sh
sudo sh ./get-docker.sh
sudo apt install docker-compose-plugin
mkdir kittygram_final
cd kittygram_final
~~~

Форкнуть и клонировать репозиторий на компьютер и перейти в него в командной строке:
~~~bash
Ссылка исходного проекта: https://github.com/karpova-el-m/kittygram_final/
~~~
~~~bash
После скачивания: cd kittygram_final/
~~~

Перенести на сервер в директорию kittygram_final/ файл docker-compose.production.yml. Со своего компьютера в директории kittygram_final/ выполните команду копирования:
~~~bash
scp -i path_to_SSH/SSH_name docker-compose.production.yml \
    username@server_ip:/home/username/taski/docker-compose.production.yml
~~~

В корневой директории создать и открыть через редактор файл для сохранения переменных окружения:

~~~bash
nano .env
~~~

Добавить в файл переменные и сохранить:
~~~bash
DB_HOST=db
DB_PORT=5432
POSTGRES_DB=kittygram
POSTGRES_USER=kittygram_user
POSTGRES_PASSWORD=kittygram_password
DB_NAME=kittygram
SECRET_KEY=...
DEBUG=True/False
ALLOWED_HOSTS=127.0.0.1,localhost,84.252.136.172,kittygramhomework.zapto.org
~~~

Запустить Docker Compose в режиме демона из корневой директории проекта:
~~~bash
sudo docker compose -f docker-compose.production.yml up -d 
~~~

Проверить, что все нужные контейнеры запущены:
~~~bash
sudo docker compose -f docker-compose.production.yml ps
~~~

Выполните миграции, соберите статические файлы бэкенда и скопируйте их в /backend_static/static/:
~~~bash
sudo docker compose -f docker-compose.production.yml exec backend python manage.py migrate
sudo docker compose -f docker-compose.production.yml exec backend python manage.py collectstatic
sudo docker compose -f docker-compose.production.yml exec backend cp -r /app/collected_static/. /backend_static/static/
~~~

### Пользовательские роли.

* Аноним — не может просматривать информацию о котиках.
* Аутентифицированный пользователь (user) — может просматривать всех котиков, дополнительно он может публиковать, редактировать и удалять информацию о своих котиках. * Эта роль присваивается по умолчанию каждому новому пользователю.
* Суперюзер Django — обладет правами администратора (admin)
#### Проект разработала:

* Карпова Е.М. - https://github.com/karpova-el-m

