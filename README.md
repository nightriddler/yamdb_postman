# yamdb_postman

Подготовка к тестам.

1. В папке с проектом ставим виртуальное окружение, зависимости и делаем миграции.

2. Создаем суперюзера (желательно с указанными параметрами чтобы ручками потом окружение не обновлять)

```
> python manage.py createsuperuser        
Username: admin
Email: admin@admin.ru
...
```

3. В постмане:
- в разделе `Collectons` импортируем `YaMDb API.postman_collection.json`.

- в разделе `Environments` импортируем `YaMDB_env.postman_environment.json`.

>Не забываем выбрать окружение установив напротив галочку.
>
>![select](/image/select_env.png)

Тесты.

1. Запускаем сервер.

2. Сперва нужно получить `confirmation_code`. Заходим в `Collectons` и отправляем запрос `auth/signup`. 
Код нужно найти и ручками вставить в `YaMDB_env` в переменную `confirmation_code`
> Не забудьте нажать `Save` после добавления.

3. Отправляем запрос на `auth/token`. Полученный токен автоматически подцепится к окружению. 
>Дальше эти ручки дергать не будем

3. Далее в `Collections` напротив `YaMDb API` жмем три точки и выбираем `Run collections`.

![run](/image/run.png)

Снимаем галочки с первых двух запросов `auth/signup` и `auth/token`.
> Чтобы сохранялись результаты запросов, ставим галочку `Persist responses for a session`

![prepare](/image/prepare.png)

Запускаем. 

![res](/image/res.png)

Если указан `Persist responses for a session`, то нажав на имя теста можно увидеть запрос

![check](/image/check.png)

Важно:
Тесты идут в хронологическом порядке, в конце все созданные объекты удаляются.  Проверяется схема ответов. Не проверяется бизнес-логика (пока).
 