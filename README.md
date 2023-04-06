# api_yamdb
![yamdb_workflow](https://github.com/ivanmtav/yamdb_final/workflows/yamdb_workflow/badge.svg)

Проект YaMDb собирает отзывы пользователей на произведения. Сами произведения в YaMDb не хранятся, здесь нельзя посмотреть фильм или послушать музыку.
Произведения делятся на категории, такие как «Книги», «Фильмы», «Музыка». Например, в категории «Книги» могут быть произведения «Винни-Пух и все-все-все» и «Марсианские хроники», а в категории «Музыка» — песня «Давеча» группы «Жуки» и вторая сюита Баха. Список категорий может быть расширен (например, можно добавить категорию «Изобразительное искусство» или «Ювелирка»). 
Произведению может быть присвоен жанр из списка предустановленных (например, «Сказка», «Рок» или «Артхаус»). 
Добавлять произведения, категории и жанры может только администратор.
Благодарные или возмущённые пользователи оставляют к произведениям текстовые отзывы и ставят произведению оценку в диапазоне от одного до десяти (целое число); из пользовательских оценок формируется усреднённая оценка произведения — рейтинг (целое число). На одно произведение пользователь может оставить только один отзыв.
Пользователи могут оставлять комментарии к отзывам.
Добавлять отзывы, комментарии и ставить оценки могут только аутентифицированные пользователи.

### Создайте файл .env
Пример:
```bash
DB_ENGINE=django.db.backends.postgresql
DB_NAME=postgres
POSTGRES_USER=postgres
POSTGRES_PASSWORD=postgres
DB_HOST=db
DB_PORT=5432
```

### Установка:
Клонировать репозиторий и перейти в него в командной строке:
```
git clone https://github.com/Ivanmatv/infra_sp2.git
```
```
cd infra_sp2
```

Запустить все контейнера командой:
```
docker-compose up -d --build
```

Выполнить миграции:
```
cd infra
```
```
docker-compose exec web python manage.py makemigrations reviews
```
``` 
docker-compose exec web python manage.py migrate 
```

Загружаем статику:
```bash
docker-compose exec web python manage.py collectstatic --no-input 
```

Запустив скрипт наполнить часть таблиц в БД:
```
docker-compose exec web python manage.py loaddata fixtures.json
```

Остановить работу всех контейнеров командой:
```
docker-compose down
```

### Примеры:
Когда вы запустите проект, по адресу http://localhost/redoc/ будет доступна документация для API Yatube. В документации описано, как должен работать ваш API. Документация представлена в формате Redoc.

В проекте доступны следующие эндпоинты: http://localhost/api/v1/auth/signup/ - Получение кода подверждения на email

{
    "email": "string",
    "username": "string"
}

http://localhost/api/v1/auth/token/ - Получение токена для авторизации

{
    "username": "string",
    "confirmation_code": "string"
}

http://localhost/api/v1/categories/ - Работа с категориями, доступны запросы Get, Post и Del

http://localhost/api/v1/genres/ - Работа с жанрами, доступны запросы Get, Post и Del

http://localhost/api/v1/titles/ - Работа со статьями , доступны запросы Get, Post, Patch и Del

http://localhost/api/v1/titles/{title_id}/reviews/ - Работа с отзывами , доступны запросы Get, Post, Patch и Del

http://localhost/api/v1/titles/{title_id}/reviews/{review_id}/comments/ - Работа с комментариями , доступны запросы Get, Post, Patch и Del

http://localhost/api/v1/users/ - Создание пользователя и получение информации о всех пользователях. Доступны запросы Get, Post

http://localhost/api/v1/users/{username}/ - Получение информации о конкретном пользователе и редактирование информации о нем. Доступны доступны запросы Get, Postm Del

http://localhost/api/v1/users/me/ - Получение и изменение своих данных, доступны запросы Get, Patch

### Использумые технологии:

- Python
- Django
- PyJWT
- Django Rest Framework
- Docker
- Nginx

### Авторы проекта:

https://github.com/Ivanmatv - Иван Матвеев

https://github.com/nikitaloskutov18 - Никита Лоскутов

https://github.com/Tilorn23 - Алексей Еремеев
