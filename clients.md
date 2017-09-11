## Данные клиента
```GET http://infogroup.online/api/v1/mobile/clientData?client_id=CLIENT_ID&lang=ru```

где ```client_id``` - идентификатор клиента.

### Заголовки
```Authorization: Bearer ACCESS_TOKEN```

Возвращает информацию о клиенте с заданным идентификатором.

### Ответ
Успешный ответ приходит с кодом ```200 OK``` и содержит тело:
```JSON
"name": "John Doe",
"phone": "скрыт",
"email": null,
"gender": "Мужской",
"discount": 0,
"birthday": null,
"comment": "Some additional info",
"total_bought": "0.0000",
"total_paid": "0.0000",
"online_reservation_available": 1
```

## Поиск клиента
```GET http://infogroup.online/api/v1/mobile/searchClient?search_str=960```

где ```search_str``` - строка поиска.

### Заголовки
```Authorization: Bearer ACCESS_TOKEN```

Возвращает идентификаторы клиентов, удовлетворяющих условиям поиска.

 ### Ответ
 Успешный ответ приходит с кодом ```200 OK``` и содержит тело:
 ```PHP
{
  [ 6, 10, 14, 21 ]
}
```

## Журнал записи
```GET http://infogroup.online/api/v1/mobile/appointmentsForDate?day=2017-02-27&lang=ru&client_id=23```

где ```day``` - день, за который необходимо получить журнал записи,
```client_id``` - идентификатор клиента (если ```client_id``` не указан возвращается информации обо всех записях на день для организации авторизованного пользователя).

### Заголовки
```Authorization: Bearer ACCESS_TOKEN```

Возвращает журнал записи за указанную дату для организации авторизованного пользователя.

### Ответ
Успешный ответ приходит с кодом ```200 OK``` и содержит тело:
```JSON
[
  {
    "note": "from widget",
    "state": "created",
    "service_sum": 500.00,
    "employee_name": "Adolfo Nitzsche",
    "employee_id": 5,
    "service_id": 12,
    "service_name": "molestiae",
    "client_id": 23,
    "client_name": "John Doe",
    "client_phone": "34343443",
    "client_email": null,
    "start": "2017-02-27 12:30:00",
    "end": "2017-02-27 13:00:00"
  }
]
```

## Создание клиента
```POST http://infogroup.online/api/v1/mobile/client```

где 

обязательные поля
```'name'``` - имя и фамилия клиента
```'phone'``` - номер телефона клиента,

опциональные поля:
```'email'``` - адрес электронной почты сотрудника.

### Заголовки
```Authorization: Bearer ACCESS_TOKEN```

Создает сотрудника с указанными реквизитами.

### Ответ
Успешный ответ приходит с кодом ```200 OK``` и содержит тело:
```
{
  "success": true,
  "error": ""
}

ИЛИ

{
  "success": false,
  "validation_errors": {
    "phone" : ["Incorrect phone format"],
    "email" : ["Incorrect email format"]
  }
}
```

## Редактирование клиента
```POST http://infogroup.online/api/v1/mobile/editClient```

где
обязательное поле:
```'client_id'``` - идентификатор клиента

Опциональные поля:
```'name'``` - новое имя и фамилия клиента
```'phone'``` - новый номер телефона клиента
```'email'``` - новый адрес электронной почты клиента

### Заголовки
```Authorization: Bearer ACCESS_TOKEN```

Позволяет изменить ФИО, номер телефона, email клиента с заданным id.

### Ответ
Успешный ответ приходит с кодом ```200 OK``` и содержит тело:
```
{
  "success": true,
  "error": ""
}

ИЛИ
{
  "success": false,
  "validation_errors":
  {
    "email":
    [
      "The email must be a valid email address."
    ],
    "phone":
    [
      "phone may contain only numbers and +-() signs"
    ]
  }
}

```

## Список клиентов
```GET http://infogroup.online/api/v1/mobile/clients?lang=ru&branch_id=1```

где ```branch_id``` - идентификатор филиала.

### Заголовки
```Authorization: Bearer ACCESS_TOKEN```

Возвращает перечень клиентов филиала с заданным идентификатором.

### Ответ
Успешный ответ приходит с кодом ```200 OK``` и содержит тело:
```
{
  [
    {
        "id": 1,
        "name": "Carlee Deckow",
        "phone": "609.514.9360"
    },
    {
        "id": 2,
        "name": "Lucio Littel",
        "phone": "418.490.8005"
    },
    {
        "id": 3,
        "name": "Montana Senger",
        "phone": "(912) 976-5820 x970"
    }
 ]
}
```
