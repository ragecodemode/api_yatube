### api_yatube - CRUD для Yatube

Для взаимодействия с ресурсами опишите и настройте такие эндпоинты:
- api/v1/api-token-auth/ (POST): передаём логин и пароль, получаем токен.
- api/v1/posts/ (GET, POST): получаем список всех постов или создаём новый пост.
- api/v1/posts/{post_id}/ (GET, PUT, PATCH, DELETE): получаем, редактируем или удаляем пост по id.
- api/v1/groups/ (GET): получаем список всех групп.
- api/v1/groups/{group_id}/ (GET): получаем информацию о группе по id.
- api/v1/posts/{post_id}/comments/ (GET, POST): получаем список всех комментариев поста с id=post_id или создаём новый, указав id поста, который хотим прокомментировать.
- api/v1/posts/{post_id}/comments/{comment_id}/ (GET, PUT, PATCH, DELETE): получаем, редактируем или удаляем комментарий по id у поста с id=post_id.

### Настройка и запуск на ПК

Клонируем проект:

```
git clone https://github.com/ragecodemode/api_yatube.git
```

Переходим в папку с проектом:

```bash
cd api_yatube
```

Устанавливаем виртуальное окружение:

```bash
python -m venv venv
```

Активируем виртуальное окружение:

```bash
source venv/Scripts/activate
```

Устанавливаем зависимости:

```
python -m pip install --upgrade pip
```
```
pip install -r requirements.txt
```

Применяем миграции:

```
python yatube_api/manage.py makemigrations
```

```
python yatube_api/manage.py migrate
```

Создаем супер пользователя:

```
python yatube_api/manage.py createsuperuser
```

В папку с проектом, где файл settings.py добавляем файл .env куда прописываем наши параметры:

```
SECRET_KEY='Ваш секретный ключ'
ALLOWED_HOSTS='127.0.0.1, localhost'
DEBUG=True
```

Не забываем добавить в .gitingore файлы:

```
.env
.venv
```

Для запуска тестов выполним:

```
pytest
```

Запускаем проект:

```
python yatube_api/manage.py runserver
```

После чего проект будет доступен по адресу http://localhost/

Заходим в http://localhost/admin и создаем посты, группы, комментарии.
Тестировать и добавлять данные удобно после прохождения авторизации через Postman.
