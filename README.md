
## REST API Documentation

Следующее Rest API работает в двух направлениях GET и POST. В этом API реализована аутентификация, не зарегестрированый пользователель не получит доступа к информации. Ендпоинт для доступа выглядит следующим образом >>> ``https://free2ask.tense.space/api/``. Для аутентификации нужны: 

| Cвойство | Описание |
| --- | --- |
| user_id | Уникальный id идентификатор пользователя |
| client_id | Идентификатор пользователя |
| token | Token создается из секретного ключа пользователя |

Таким образом доступ будет осуществлен в при следующих условиях: 
`` https://free2ask.tense.space/api/.../user_id/client_id/token``


Для тестов token временно не проверяется, потому все ниже изложенные операции можна провести с исходными данными:
`` https://free2ask.tense.space/api/.../2/2302``

## Resources
- Cities Resource
- Сontact center Resource
- Rules Resource
- Specialists Resource
- Users Resource
- Users Groups Resource
- Chatlog Resource

# Cities Resource
----------------

```
/api/cities-list/
```

### GET

Возвращает все города (Которые доступны пользователю) - всех специалистов которые закреплены за городом, их расписание и детальную информацию.

```
    GET https://free2ask.tense.space/api/cities-list/2/2302 HTTP/1.1
```    
### Ответ 

```
{
            "success": true,
            "code": "200",
            "message": "OK",
            "data": [{
                "id": 1,
                "title": "Tochka Opory",
                "slug": "Tochka Opory",
                "body": "desc",
                "meta_title": "meta title",
                "meta_description": "meta description",
                "status": 1,
                "created_at": {
                    "date": "2018-10-21 19:10:30.000000",
                    "timezone_type": 3,
                    "timezone": "UTC"
                },
                "updated_at": {
                    "date": "2018-10-23 09:23:43.000000",
                    "timezone_type": 3,
                    "timezone": "UTC"
                },
                "chat_id": "12345678",
                "specialists": [
                    {
                        "id": 1,
                        "first_name": "Aнтон",
                        "last_name": "Петрович",
                        "bio": "Информация про Антона петровича",
                        "phone": "342134123",
                        "created_at": {
                            "date": "2018-10-21 21:34:37.000000",
                            "timezone_type": 3,
                            "timezone": "UTC"
                        },
                        "updated_at": {
                            "date": "2018-10-21 21:34:37.000000",
                            "timezone_type": 3,
                            "timezone": "UTC"
                        },
                        "status": 1,
                        "email": "mail@gmail.com",
                        "schedule": [
                        {
                            "weekday": "Monday",
                            "open_from": "2018-10-21 09:00:00",
                            "open_to": "2018-10-21 14:00:00",
                            "dinner_time": "0",
                            "dinner_time_start": ""
                        }
                        ],
                        "chat_id": null
                    }
                    ],
                    "cover": {
                        "path":             "https://free2ask.tense.space/storage/app/uploads/public/5bc/ccf/195/5bcccf195edfd868344477.jpg",
                        "getContentType": "image/jpeg"
                    }
            }
            ]
}
```

## POST 

Создает новый город и выводит ответ с новой информацией.

| Cвойство | Описание |
| --- | --- |
| title | Название города |
| body | Описание города |
| status | Статус города (Активен - 1 / Не активен - 0) |
| cover | Изображение города |

```
    POST /api/add-city HTTP/1.1 title=New%20Service&body=A%20great%20service
```    
### Ответ
```

{
    "success": true,
    "code": "200",
    "message": "OK",
    "data": {
        "id": 3,
        "title": "demo city",
        "slug": null,
        "adress": null,
        "phone": null,
        "schedule": null,
        "longitude": null,
        "latitude": null,
        "created_at": "2018-11-14 03:03:45",
        "updated_at": "2018-11-14 03:03:45",
        "deleted_at": null,
        "map_link": null,
        "status": null
    }
}
```


# Сontact center Resource
----------------

```
/api/contact-center-list/
```

### GET

Возвращает все контакт центры (Которые доступны опубликованы) их расписание, локацию и детальную информацию.

```
    GET https://free2ask.tense.space/api/contact-center-list/2/2302 HTTP/1.1
```    
### Ответ 

```
{
    "success": true,
    "code": "200",
    "message": "OK",
    "data": [
        {
            "id": 1,
            "title": "demo location",
            "slug": "demo-location",
            "adress": "some demo address",
            "phone": "",
            "schedule": [],
            "longitude": null,
            "latitude": null,
            "created_at": {
                "date": "2018-10-22 22:10:01.000000",
                "timezone_type": 3,
                "timezone": "UTC"
            },
            "updated_at": {
                "date": "2018-10-22 22:11:48.000000",
                "timezone_type": 3,
                "timezone": "UTC"
            },
            "status": 1
        }
    ]
}
```

## POST 

Создает новый контактный центр и выводит ответ с новой информацией.

| Cвойство | Описание |
| --- | --- |
| title | Название центра |
| adress | Адрес центра |
| status | Статус центра (Активен - 1 / Не активен - 0) |
| phone | Телефон центра |

```
    POST /api/add-contact-center HTTP/1.1 title=New%20Service&body=A%20great%20service
```    
### Ответ
```

{
    "success": true,
    "code": "200",
    "message": "OK",
    "data": {
        "id": 3,
        "title": "demo center",
        "slug": null,
        "adress": null,
        "phone": null,
        "schedule": null,
        "longitude": null,
        "latitude": null,
        "created_at": "2018-11-14 03:03:45",
        "updated_at": "2018-11-14 03:03:45",
        "deleted_at": null,
        "map_link": null,
        "status": null
    }
}
```


# Rules Resource
----------------

```
/api/rules-list/
```

### GET

Возвращает все опубликованные правила.

```
    GET https://free2ask.tense.space/api/rules-list/2/2302 HTTP/1.1
```    
### Ответ 

```
{
    "success": true,
    "code": "200",
    "message": "OK",
    "data": [
        {
            "id": 1,
            "title": "rule 1",
            "slug": "rule-1",
            "rule": "rule text",
            "created_at": {
                "date": "2018-10-21 19:14:59.000000",
                "timezone_type": 3,
                "timezone": "UTC"
            },
            "updated_at": {
                "date": "2018-10-21 19:14:59.000000",
                "timezone_type": 3,
                "timezone": "UTC"
            },
            "status": 1
        }
    ]
}
```

# Specialists Resource
----------------

```
/api/specialists-list/
```

### GET

Возвращает всех специалистов и информацию о них с привязкой к городам и расписанию.

```
    GET https://free2ask.tense.space/api/specialists-list/2/2302 HTTP/1.1
```    
### Ответ 

```
{
    "success": true,
    "code": "200",
    "message": "OK",
    "data": [
        {
            "id": 1,
            "first_name": "Aнтон",
            "last_name": "Петрович",
            "bio": "Информация про Антона петровича",
            "phone": "342134123",
            "created_at": {
                "date": "2018-10-21 21:34:37.000000",
                "timezone_type": 3,
                "timezone": "UTC"
            },
            "updated_at": {
                "date": "2018-10-21 21:34:37.000000",
                "timezone_type": 3,
                "timezone": "UTC"
            },
            "status": 1,
            "email": "mail@gmail.com",
            "schedule": [
                {
                    "weekday": "Monday",
                    "open_from": "2018-10-21 09:00:00",
                    "open_to": "2018-10-21 14:00:00",
                    "dinner_time": "0",
                    "dinner_time_start": ""
                }
            ],
            "cities": [
                {
                    "id": 1,
                    "title": "Tochka Opory",
                    "slug": "Tochka Opory",
                    "body": "desc",
                    "meta_title": "meta title",
                    "meta_description": "meta description",
                    "status": 1,
                    "created_at": {
                        "date": "2018-10-21 19:10:30.000000",
                        "timezone_type": 3,
                        "timezone": "UTC"
                    },
                    "updated_at": {
                        "date": "2018-10-23 09:23:43.000000",
                        "timezone_type": 3,
                        "timezone": "UTC"
                    },
                    "deleted_at": null,
                    "chat_id": "12345678"
                }
            ],
            "cover": {
                "path": "https://free2ask.tense.space/storage/app/uploads/public/5bc/cf0/eaa/5bccf0eaa9ed5835254100.jpg",
                "getContentType": "image/jpeg",
                "getFilename": "2018-10-18 19.24.11.jpg"
            }
        },
        {
            "id": 2,
            "first_name": "demo 222",
            "last_name": "demo",
            "bio": "demo",
            "phone": "demo",
            "created_at": {
                "date": "2018-11-14 00:03:53.000000",
                "timezone_type": 3,
                "timezone": "UTC"
            },
            "updated_at": {
                "date": "2018-11-14 00:03:53.000000",
                "timezone_type": 3,
                "timezone": "UTC"
            },
            "status": 1,
            "email": "demo",
            "schedule": [],
            "cities": [],
            "cover": {
                "path": null,
                "getContentType": null,
                "getFilename": null
            }
        }
    ]
}
}
```

## POST 

Создает нового специалиста и выводит ответ с новой информацией.

| Cвойство | Описание |
| --- | --- |
| first_name | Имя |
| last_name | Фамилия |
| bio | Описание |
| phone | Телефон |
| email | Почта |
| chat_id | Номер чата |

```
    POST /api/add-specialist HTTP/1.1 first_name=New%20Spec&last_name=A%20great%20spec
```    
### Ответ
```

{
    "success": true,
    "code": "200",
    "message": "OK",
    "data": {
        "id": 4,
        "first_name": "New Spec",
        "last_name": "A great spec",
        "bio": null,
        "phone": null,
        "created_at": "2018-11-14 03:32:33",
        "updated_at": "2018-11-14 03:32:33",
        "deleted_at": null,
        "status": null,
        "email": null,
        "schedule": null,
        "chat_id": null
    }
}
``` 

# Users Resource
----------------

```
/api/users-list/
```

### GET

Возвращает всех пользователей сервиса и информацию о них.

```
    GET https://free2ask.tense.space/api/users-list/2/2302 HTTP/1.1
```    


## POST 

Создает нового пользователя и выводит ответ с новой информацией.

| Cвойство | Описание |
| --- | --- |
| name | Имя |
| surname | Фамилия |
| password | Пароль |
| email | Почта |
| username | Имя пользователя |


```
    POST /api/add-user HTTP/1.1 name=New%20Spec&surname=A%20great%20spec
```    


# Users Groups Resource
----------------

```
/api/users-group-list/
```

### GET

Возвращает все группы пользователей и пользователей которые входят в них

```
    GET https://free2ask.tense.space/api/users-group-list/2/2302 HTTP/1.1
```    


# Chatlog Resource
----------------

```
/api/chatlog-list/
```

### GET

Возвращает log чатов

```
    GET https://free2ask.tense.space/api/chatlog-list/2/2302 HTTP/1.1
```    


## POST 

Создает нового пользователя и выводит ответ с новой информацией.

| Cвойство | Описание |
| --- | --- |
| specialist_id | Идентификатор специалиста |
| chat_id | Код чата |
| log | Лог чата |



```
    POST /api/add-chatlog HTTP/1.1 specialist_id=1&chat_id=2342342&log=testlog
```    
