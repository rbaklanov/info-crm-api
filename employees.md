## Список сотрудников
```GET http://infogroup.online/api/v1/mobile/branchEmployees?branch_id=1&lang=en```

где ```branch_id``` - идентификатор филиала.

### Заголовки
```Authorization: Bearer ACCESS_TOKEN```

Возвращает перечень сотрудников филиала с заданным идентификатором.

### Ответ
```JSON
Успешный ответ приходит с кодом ```200 OK``` и содержит тело:
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
