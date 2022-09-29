[![yamdb_final workflow](https://github.com/GoIAnton/yamdb_final/actions/workflows/yamdb_workflow.yml/badge.svg)](https://github.com/GoIAnton/yamdb_final/actions/workflows/yamdb_workflow.yml)

# api_yamdb
api_yamdb

### Описание:
Проект YaMDb собирает отзывы (Review) пользователей на произведения (Titles). 
Произведения делятся на категории: «Книги», «Фильмы», «Музыка». 
Список категорий (Category) может быть расширен администратором 
(например, можно добавить категорию «Изобразительное искусство» или «Ювелирка»).

Благодарные или возмущённые пользователи оставляют к произведениям текстовые отзывы (Review) и ставят произведению оценку в диапазоне от одного до десяти (целое число); из пользовательских оценок формируется усреднённая оценка произведения — рейтинг (целое число). На одно произведение пользователь может оставить только один отзыв.

## Проект исполнен в:

**Версия python** = 3.7
**Версия Django** = 2.2.16
**Версия Djangorestframework** = 3.12.4

### Как запустить проект: 

Клонировать репозиторий и перейти в него в командной строке:
```
git clone https://github.com/GoIAnton/yamdb_final.git
```

Переход в папку с docker-compose:
```
cd yamdb_final/
```

Запуск docker-compose:
```
docker-compose up
```

Миграции -> создание суперюзера -> собрать статику нужной папке:
```
docker-compose exec web python manage.py migrate
docker-compose exec web python manage.py createsuperuser
docker-compose exec web python manage.py collectstatic --no-input
```

### IP сервера: 

51.250.111.99

## API эндпоинты

Авторизация:
```http
  POST /api/v1/auth/signup/
  Регистрация пользователей и выдача токенов
```
```http
  POST /api/v1/auth/token/
  Получение JWT-токена в обмен на username и confirmation code.
```
___
Категории:
```http
  GET /api/v1/categories
  Категории (типы) произведений
```
```http
  POST /api/v1/categories
  Создать категорию
```
```http
  DELETE /api/v1/categories/{slug}/
  Удалить категорию.
```
___
Жанры:
```http
  GET /api/v1/genres/
  Получить список всех жанров.
```
```http
  POST /api/v1/genres/
  Добавить жанр.
```
```http
  DELETE /api/v1/genres/{slug}/
  Удалить жанр.
```
___
Объекты, произведения:
```http
  GET /api/v1/titles/
  Получить список всех объектов.
```
```http
  POST /api/v1/titles/
  Добавить новое произведение.
```
```http
  GET /api/v1/titles/{titles_id}/
  Информация о произведении
```
```http
  PUTCH /api/v1/titles/{titles_id}/
  Обновить информацию о произведении
```
```http
  DELETE /api/v1/titles/{titles_id}/
  Удалить произведение.
```
___
Отзывы к произведениям:
```http
  GET /api/v1/titles/{titles_id}/reviews/
  Получить список всех отзывов.
```
```http
  POST /api/v1/titles/{titles_id}/reviews/
  Добавить новый отзыв.
```
```http
  GET /api/v1/titles/{title_id}/reviews/{review_id}/
  Получить отзыв по id для указанного произведения.
```
```http
  PUTCH /api/v1/titles/{title_id}/reviews/{review_id}/
  Частично обновить отзыв по id.
```
```http
  DELETE /api/v1/titles/{titles_id}/reviews/{review_id}/
  Удалить отзыв по id
```
___
Комментарии к отзывам:
```http
  GET /api/v1/titles/{titles_id}/reviews/{review_id}/comments/
  Получить список всех комментариев к отзыву по id
```
```http
  POST /api/v1/titles/{titles_id}/reviews/{review_id}/comments/
  Добавить новый комментарий для отзыва.
```
```http
  GET /api/v1/titles/{title_id}/reviews/{review_id}/{comment_id}/
  Получить комментарий для отзыва по id.
```
```http
  PUTCH /api/v1/titles/{title_id}/reviews/{review_id}/{comment_id}/
  Частично обновить комментарий к отзыву по id.
```
```http
  DELETE /api/v1/titles/{title_id}/reviews/{review_id}/{comment_id}/
  Удалить комментарий к отзыву по id.
```
___
Пользователи:
```http
  GET /api/v1/users/
  Получить список всех пользователей.
```
```http
  POST /api/v1/users/
  Добавить нового пользователя.
```
```http
  GET /api/v1/users/{username}/
  Получить пользователя по username.
```
```http
  PUTCH GET /api/v1/users/{username}/
  Изменить данные пользователя по username.
```
```http
  DELETE /api/v1/users/{username}/
  Удалить пользователя по username.
```
```http
  GET /api/v1/users/me/
  Получить данные своей учетной записи
```
```http
  PUTCH /api/v1/users/me/
  Изменить данные своей учетной записи
```
___
Подробнее о работе эндпоинтов можно изучить в Redoc:
```http
  /redoc/
```


### Об авторе:

Начинающий бекэнд разработчик на Python
Мой github:
https://github.com/GoIAnton
