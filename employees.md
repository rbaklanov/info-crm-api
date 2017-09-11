## Список сотрудников
```GET http://infogroup.online/api/v1/mobile/branchEmployees?branch_id=1&lang=en```

где ```branch_id``` - идентификатор филиала.

### Заголовки
```Authorization: Bearer ACCESS_TOKEN```

Возвращает перечень сотрудников филиала с заданным идентификатором.

### Ответ
Успешный ответ приходит с кодом ```200 OK``` и содержит тело:
```JSON
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
```

## Свободное время для записи у сотрудника
```GET http://infogroup.online/api/v1/mobile/employeeFreeTime?employee_id=3&lang=ru```

где ```employee_id``` - идентификатор сотрудника.

### Заголовки
```Authorization: Bearer ACCESS_TOKEN```

Возвращает свободное время сотрудника филиала с заданным идентификатором для записи с текущего момента и до конца месяца.

### Ответ

Успешный ответ приходит с кодом ```200 OK``` и содержит тело:
```JSON
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

```
