## Список сотрудников
```GET http://infogroup.online/api/v1/mobile/branchEmployees?branch_id=1&lang=en```

где ```branch_id``` - идентификатор филиала.

### Заголовки
```Authorization: Bearer ACCESS_TOKEN```

Возвращает перечень сотрудников филиала с заданным идентификатором.

### Ответ
Успешный ответ приходит с кодом ```200 OK``` и содержит тело:
```
{
  [
    {
      "employee_id": 1,
      "name": "Eli Hansen",
      "avatar": "http://infogroup.online/img/crm/avatar/avatar100.jpg"
    },
    {
      "employee_id": 2,
      "name": "Helena Fisher",
      "avatar": "http://infogroup.online/img/crm/avatar/avatar100.jpg"
    }
  ]
}
```

## Свободное время для записи у сотрудника
```GET http://infogroup.online/api/v1/mobile/employeeFreeTime?employee_id=3&lang=ru```

где ```employee_id``` - идентификатор сотрудника.

### Заголовки
```Authorization: Bearer ACCESS_TOKEN```

Возвращает свободное время сотрудника с заданным идентификатором для записи с текущего момента и до конца месяца.

### Ответ

Успешный ответ приходит с кодом ```200 OK``` и содержит тело:
```
{
  [
    {
      "work_start": "2017-05-23 11:00:00",
      "work_end": "2017-05-23 15:00:00"
    },
    {
      "work_start": "2017-05-23 16:00:00",
      "work_end": "2017-05-23 20:00:00"
    }
  ]
}
```

## Создание записи к сотруднику
```POST http://infogroup.online/api/v1/mobile/appointment```

Обязательные поля:
```'client_name'``` - наименование клиента
```'client_phone'``` - номер телефона клиента
```'service_id'``` - идентификатор услуги
```'employee_id'``` - идентификатор сотрудника
```'date_from'``` - дата записи
```'time_from'``` - время записи
```'duration_hours'``` - длительность оказания услуги(в часах)
```'duration_minutes'``` - длительность оказания услуги(в минутах)

Опциональные поля:
```'client_email'``` - адрес электронной почты клиента
```'note'``` - заметка

### Заголовки
```Authorization: Bearer ACCESS_TOKEN```
```Content-Type: application/x-www-form-urlencoded```

Создает запись на услугу к сотруднику на заданную дату и время.

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
  "error": "Employee data error"
}

ИЛИ

{
  "success": false,
  "validation_errors": {
    "client_phone" : ["Incorrect phone format"],
    "date_from" : ["Date must be today or in future"]
}
```
