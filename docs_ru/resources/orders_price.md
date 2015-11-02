# Получение заказа

`POST https://vozovoz.ru/api/v1/orders`

Параметры запроса:

Имя | Тип | Описание
--- | --- | ---
services | [[Order.Service](orders_object.md#service)] | Услуги, участвующие в заказе
promoCode | string | Промокод
save | [Order.Status](#status) | Сохранять расчет

---

```js
HTTP/1.1 200 OK
{
    "data" : <объект Order>
}
```

Order - [объект заказа](orders_object.md), ограниченный полями `balance`, `cost`, `editing`, `services`

**Пример**

`POST https://vozovoz.ru/api/v1/orders/price`

```js
{
   "services": [
       {
           "type": "shipping",
           "from": { //От терминала
               "id": "e90f19de-0128-11e5-80c7-00155d903d03", //locationID
               "terminal": {
                   "id": "d01da881-f94a-11e4-80c7-00155d903d03" //terminalID
               }
           },
           "cargo": {
               "packages": {
                   "bag2": 1,
                   "safePackage": 1
               },
               "total": {
                   "all": {
                       "quantity": 2,
                       "volume": 0.11,
                       "weight": 0.9
                   },
                   "max": {
                       "height": 0.4,
                       "length": 0.7,
                       "width": 0.4,
                       "weight": 0.9
                   },
                   "noGab": {
                       "volume": 0,
                       "weight": 0
                   }
               }
           }
       },
       {
           "type": "deliveryTo",
           "to": { //До адреса
               "id": "e90f1820-0128-11e5-80c7-00155d903d03", //locationID
               "address": {
                   "address": "Варшавское шоссе, д, 1",
                   "dates": {
                       "from": "2015-10-28T14:00:00.000Z",
                       "to": "2015-10-28T18:00:00.000Z"
                   }
               }
           }
       }
   ]
}
```

LocationID для формирования объекта типа `Order.Location` можно получить из ресурса Locations. TerminalID можно получить из ресурса `Terminals`.

---

```js
{
   "data": {
       "services": [
           {
               "from": {
                   "id": "e90f19de-0128-11e5-80c7-00155d903d03",
                   "terminal": {
                        "id": "d01da881-f94a-11e4-80c7-00155d903d03"
                   }
               },
               "cost": {
                   "base": 410,
                   "discount": -10,
                   "total": 400,
                   "details": [
                       {
                           "id": "0e924061-6b65-49c8-9fc5-5b7532bb8108",
                           "name": "Перевозка между городами",
                           "cost": {
                               "base": 240,
                               "total": 230,
                               "discount": -10
                           }
                       },
                       {
                           "id": "266b2db2-9198-41cc-871a-c5855b35ccad",
                           "name": "Упаковка в мешок (70х120)",
                           "cost": {
                               "base": 80,
                               "total": 80,
                               "discount": 0
                           }
                       },
                       {
                           "id": "8cd85017-78bb-46f9-84ec-622b884a746a",
                           "name": "Упаковка в сейф-пакет",
                           "cost": {
                               "base": 90,
                               "total": 90,
                               "discount": 0
                           }
                       }
                   ],
                   "actions": [
                       {
                           "id": "73c2eb94-b8e7-11e4-80be-e15dd7ce905e",
                           "name": "002 Скидка 5% на МТ"
                       }
                   ]
               },
               "type": "shipping",
               "cargo": {
                   "total": {
                       "max": {
                           "width": 0.4,
                           "weight": 0.9,
                           "length": 0.7,
                           "height": 0.4
                       },
                       "noGab": {
                           "volume": 0,
                           "weight": 0
                       },
                       "all": {
                           "quantity": 2,
                           "volume": 0.11,
                           "weight": 0.9
                       }
                   },
                   "packages": {
                       "bag2": 1,
                       "safePackage": 1
                   }
               }
           },
           {
               "to": {
                   "address": {},
                   "id": "e90f1820-0128-11e5-80c7-00155d903d03"
               },
               "cost": {
                   "base": 250,
                   "discount": 0,
                   "total": 250,
                   "details": [
                       {
                           "id": "1f9ead3d-f5ce-4dff-b1f6-649707373104",
                           "name": "Отвоз груза клиенту",
                           "cost": {
                               "base": 250,
                               "total": 250,
                               "discount": 0
                           }
                       }
                   ]
               },
               "type": "deliveryTo"
           }
       ],
       "cost": {
           "total": 650
       },
       "balance": [],
       "editing": {
           "canBeCanceled": true,
           "services": true
       }
   }
}
```
