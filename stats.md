## Статистика за день
```GET http://infogroup.online/api/v1/mobile/dailyStatistics?day=2017-03-19&lang=ru```

где ```day``` - дата получения информации.

### Заголовки
```Authorization: Bearer ACCESS_TOKEN```

Возвращает:
1) Кол-во клиентов за день, чел; 
2) Средняя заполненность по мастерам, % = общее время оказания услуг/общее рабочее время мастеров *100% ; 
3) Записей на сумму, руб; 
4) Оказано услуг на сумму, руб. 
5) Поступлений в кассу, руб. 
6) Средний чек, руб.

### Ответ
Успешный ответ приходит с кодом ```200 OK``` и содержит тело:
```
{
  "employee_stats": {
    "1": {
      "utilization": 34
    },
    "2": {
      "utilization": 0
    },
    "4": {
      "utilization": 0
    },
    "5": {
      "utilization": 0
    },
    "6": {
      "utilization": 0
    },
    "7": {
      "utilization": 0
    },
    "8": {
      "utilization": 0
    },
    "9": {
      "utilization": 0
    },
    "10": {
      "utilization": 0
    },
    "11": {
      "utilization": 0
    },
    "12": {
      "utilization": 0
    }
  },
  "clients_count": 3,
  "appointments_sum": 1937.5,
  "services_sum": 1937.5,
  "payed_sum": 1937.5,
  "average_receipt": 645.83
}
```
