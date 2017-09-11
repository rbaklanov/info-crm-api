## Список филиалов организации
```GET http://infogroup.online/api/v1/mobile/branchesData?lang=ru```

### Заголовки
```Authorization: Bearer ACCESS_TOKEN```

Возвращает перечень филиалов организации авторизованного пользователя.

### Ответ
Успешный ответ приходит с кодом ```200 OK``` и содержит тело:
```
{
  [
    {
      "org_id": 1,
      "name": "Test Company 1 - Branch I",
      "logo": "http://infogroup.online/img/crm/avatar/logo200_50.png"
    },
    {
      "org_id": 2,
      "name": "Test Company 1 - Branch 2",
      "logo": "http://infogroup.online/img/crm/avatar/logo200_50.png"
    }
  ]
}
```


## Перечень услуг, оказываемых в филиале
```GET http://localhost:8000/api/v1/mobile/branchServices?branch_id=1&lang=ru```

где ```branch_id``` - идентификатор филиала.

### Заголовки
```Authorization: Bearer ACCESS_TOKEN```

Возвращает перечень услуг, которые оказывают сотрудники филиала с заданным идентификатором.

### Ответ
Успешный ответ приходит с кодом ```200 OK``` и содержит тело:
```
{
  [
    {
      "service_id": 5,
      "name": "eos",
      "description": "Recusandae id dolores molestiae. Occaecati officiis amet suscipit minus. Perferendis sunt maxime.",
      "price": 500,
      "duration": "02:00:00",
      "employees": [
        {
          "employee_id": 5,
          "name": "Adolfo Nitzsche"
        },
        {
          "employee_id": 2,
          "name": "Helena Fisher"
        }
      ]
    },

    {
      "service_id": 7,
      "name": "et",
      "description": "Ut deleniti et alias sed quo veritatis. Veritatis nesciunt aliquam repellat nesciunt enim.",
      "price": 500,
      "duration": "00:30:00",
      "employees": [
        {
          "employee_id": 4,
          "name": "Percival Pagac"
        }
      ]
    }
  ]
}
```
