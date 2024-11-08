
### Как запустить backend приложение:

Форкнуть и клонировать репозиторий на компьютер и перейти в него в командной строке:
~~~bash
Ссылка исходного проекта: https://github.com/karpova-el-m/kittygram_final/
~~~
~~~bash
После скачивания: cd kittygram_final/
~~~

В корневой директории создать и открыть через редактор файл для сохранения переменных окружения:

~~~bash
nano .env
~~~

Добавить в файл переменные и сохранить:
~~~bash
SECRET_KEY=...
DEBUG=True/False
ALLOWED_HOSTS=127.0.0.1,localhost,84.252.136.172,kittygramhomework.zapto.org
~~~

Перейти в директорию backend:
~~~bash
cd backend/
~~~

Создать Docker volume:
~~~bash
docker volume create sqlite_data
~~~

Собрать образ из Dockerfile:
~~~bash
docker build -t taski_backend .
~~~

Запустить контейнер с Docker volume:
~~~bash
docker run --name taski_backend_container -p 8000:8000 -v sqlite_data:/data taski_backend
~~~

В отдельном окне терминала вновь запустить миграции:
~~~bash
docker exec taski_backend_container python manage.py migrate
~~~
