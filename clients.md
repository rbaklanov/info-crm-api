 ## Данные клиента
 ```GET http://infogroup.online/api/v1/mobile/clientData?client_id=CLIENT_ID&lang=ru```
 где ```client_id``` - идентификатор клиента,
 
 ### Заголовки
 ```Authorization: Bearer ACCESS_TOKEN```
 
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
где ```search_str``` - строка поиска

### Заголовки
```Authorization: Bearer ACCESS_TOKEN```

Возвращает идентификаторы клиентов, удовлетворяющих условиям поиска.

 ### Ответ
 Успешный ответ приходит с кодом ```200 OK``` и содержит тело:
 ```PHP
 [
  6,
  10,
  14,
  21
]
