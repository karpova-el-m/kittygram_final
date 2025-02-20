
### Как запустить backend приложение:

1. Клонировать репозиторий на компьютер и перейти в него в командной строке:
```
Ссылка на код исходного проекта: https://github.com/karpova-el-m/kittygram_final/tree/project_code_review/
```

2. В корневой директории создать и открыть через редактор файл для сохранения переменных окружения. Добавьте в него необходимые переменные окружения. Убедитесь, что файл .env добавлен в .gitignore, чтобы предотвратить его попадание в систему контроля версий.
```
nano .env
```

3. Перейдите в директорию backend и установите зависимости:
```
cd backend/
```
```sh
pip install -r requirements.txt
```
4. Выполните миграции базы данных:
```sh
python manage.py migrate
```
5. Создайте суперпользователя:
```
python manage.py createsuperuser
```
6. Запустите сервер разработки:
```
python manage.py runserver
```

### Проект разработала:

Карпова Е.М. - https://github.com/karpova-el-m

Telegram - [@karpova_el_m](https://t.me/karpova_el_m)
