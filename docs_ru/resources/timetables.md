# Расписание доставки

## Расписание для сдачи груза на 7 дней вперед

`POST https://api.vozovoz.ru/v1/timetables/departure`

Параметры запроса:

Имя | Тип | Обязательный | Описание
--- | --- | ------------ | --------
locationId | string | если нет terminalId | Id населенного пункта (locationId), для которой необходимо получить расписание забора
terminalId | string | если нет locationId | ld терминала (terminalId), для которого необходимо получить расписание сдачи груза

---

```js
HTTP/1.1 200 OK
{
  "data": {
    "locationId": "f2a30387-0124-11e5-80c7-00155d903d03", //terminalId
    "dates": [
      {
        "from": "2015-10-28T13:44:17Z",
        "to": "2015-10-28T19:00:00Z",
        "courierArrivalTimeMinInterval": 3 //если locationId
      }
      ...
    ]
  }
}
```

## Расписание для получения груза на 3 дня вперед

`POST https://api.vozovoz.ru/v1/timetables/arrival`

Параметры запроса:

Имя | Тип | Обязательный | Описание
--- | --- | ------------ | --------
from | object | да | Место отправления: `locationId` - Id населенного пункта, обязателен, если нет terminalId, `terminalId` - ID терминала, обязателен, если нет locationId, `dates` - объект даты, обязателен, если есть locationId: `dates.to` - нижняя граница даты/времени отправления. Обязателен
to | object | да | Место получения: `locationId` - Id населенного пункта, обязателен, если нет terminalId, `terminalId` - ID терминала, обязателен, если нет locationId

---

```js
HTTP/1.1 200 OK
{
  "data": {
    "locationId": "f2a30387-0124-11e5-80c7-00155d903d03",//terminalId
    "dates": [
      {
        "from": "2015-10-28T13:44:17Z",
        "to":   "2015-10-28T19:00:00Z",
        "courierArrivalTimeMinInterval": 3 //если locationId
      }
      ...
    ]
  }
}
```
