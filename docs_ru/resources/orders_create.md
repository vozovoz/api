# Создание заказа

`GET https://vozovoz.ru/api/v1/orders`

Параметры запроса:

Имя | Тип | Обязательный | Описание
--- | --- | ------------ | --------
services | [[Order.Service](orders_object.md#service)] | да | Услуги, участвующие в заказе
promoCode | string | нет | Промокод

---

```js
HTTP/1.1 201 Created
{
    "data": <объект Order>
}
```

Order — [объект заказа](orders_object.md)

**Создание заказа**

`POST https://vozovoz.ru/api/v1/orders`

```js
{
   "services": [
       {
           "type": "shipping",
           "from": {
               "id": "e90f19de-0128-11e5-80c7-00155d903d03", //locationId
               "terminal": {
                   "id": "d01da881-f94a-11e4-80c7-00155d903d03", //terminalId
                   "dates": {
                       "from":"2015-10-28T14:00:00.000Z"
                   }
               }
           },
           "counteragents": {
               "consignee": {
                   "type": "corporation",
                   "inn": "7718934641",
                   "kpp": "771801001",
                   "name": "ООО \"МОСКОВСКАЯ ТЕПЛОВАЯ КОМПАНИЯ\"",
                   "legalAddress": "107076, Москва г, Потешная ул, дом № 16",
                   "contactFullName": "Андрей",
                   "phoneNumbers": ["79214437201"]
               },
               "shipper": {
                   "type": "individual",
                   "needCargoReceiptCode": true,
                   "fullName": "Аверьянов Александрович Андрей",
                   "phoneNumbers": ["79052862477"]
               },
               "payer": {
                   "type": "corporation",
                   "inn": "7718934641",
                   "kpp": "771801001",
                   "name": "ООО \"МОСКОВСКАЯ ТЕПЛОВАЯ КОМПАНИЯ\"",
                   "legalAddress": "107076, Москва г, Потешная ул, дом № 16",
                   "contactFullName": "Андрей",
                   "phoneNumbers": ["79214437201"]
               }
           },
           "cargo": {
               "packages": {
                   "bag2": 1,
                   "box2": 1
               },
               "total": {
                   "all": {
                       "quantity": 2,
                       "volume": 0.2,
                       "weight": 0.9
                   },
                   "max": {
                       "height": 0.4,
                       "length": 4,
                       "width": 0.4,
                       "weight": 0.9
                   },
                   "noGab": {
                       "volume": 0.1,
                       "weight": 0.1
                   }
               }
           }
       },
       {
           "type": "deliveryTo",
           "to": {
               "id": "e90f1820-0128-11e5-80c7-00155d903d03", //locationId
               "address": {
                   "address": "Варшавское шоссе, д, 1",
                   "dates": {
                       "from": "2015-10-29T14:00:00.000Z",
                       "to": "2015-10-29T18:00:00.000Z"
                   }
               }
           }
       }
   ]
}
```

`locationId` для формирования объекта типа `Locatio`n можно получить из ресурса `Object.Locations`. `terminalId` можно получить из ресурса `Terminals`.

---

```js
{
   "data": {
       "id": "43c2a30d-7ca5-11e5-80d3-00155d189b02",
       "number": "500102232",
       "status": {
           "message": "Заказ оформлен",
           "description": "Заказ оформлен",
           "isTaken": false,
           "isGiven": false,
           "isCanceled": false,
           "isPaid": false,
           "canUserRequestDriverCallback": false
       },
       "editing": {
           "canBeCanceled": true,
           "services": true
       },
       "cost": {
           "total": 990
       },
       "services": [
           {
               "from": {
                   "id": "e90f19de-0128-11e5-80c7-00155d903d03",
                   "terminal": {
                       "dates": {
                           "from": "2015-10-28T14:00:00.000Z"
                       },
                       "id": "d01da881-f94a-11e4-80c7-00155d903d03"
                   }
               },
               "cost": {
                   "base": 487.5,
                   "discount": -2.5,
                   "total": 485,
                   "details": [
                       {
                           "id": "0e924061-6b65-49c8-9fc5-5b7532bb8108",
                           "name": "Перевозка между городами",
                           "cost": {
                               "base": 337.5,
                               "total": 335,
                               "discount": -2.5
                           }
                       },
                       {
                           "id": "799d33b6-f43d-478f-846d-b9e18cb1ddd5",
                           "name": "Упаковка в коробку (20х40х40)",
                           "cost": {
                               "base": 70,
                               "total": 70,
                               "discount": 0
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
                       }
                   ],
                   "actions": [
                       {
                           "id": "",
                           "name": ""
                       }
                   ]
               },
               "type": "shipping",
               "counteragents": {
                   "shipper": {
                       "type": "individual",
                       "fullName": "Аверьянов Александрович Андрей",
                       "needCargoReceiptCode": true,
                       "phoneNumbers": [
                           "79052862477"
                       ]
                   },
                   "payer": {
                       "type": "corporation",
                       "kpp": "771801001",
                       "inn": "7718934641",
                       "name": "ООО \"МОСКОВСКАЯ ТЕПЛОВАЯ КОМПАНИЯ\"",
                       "phoneNumbers": [
                           "79214437201"
                       ],
                       "contactFullName": "Андрей",
                       "legalAddress": "107076, Москва г, Потешная ул, дом № 16"
                   },
                   "consignee": {
                       "type": "corporation",
                       "kpp": "771801001",
                       "inn": "7718934641",
                       "name": "ООО \"МОСКОВСКАЯ ТЕПЛОВАЯ КОМПАНИЯ\"",
                       "phoneNumbers": [
                           "79214437201"
                       ],
                       "contactFullName": "Андрей",
                       "legalAddress": "107076, Москва г, Потешная ул, дом № 16"
                   }
               },
               "cargo": {
                   "total": {
                       "max": {
                           "width": 0.4,
                           "weight": 0.9,
                           "length": 4,
                           "height": 0.4
                       },
                       "noGab": {
                           "volume": 0.1,
                           "weight": 0.1
                       },
                       "all": {
                           "quantity": 2,
                           "volume": 0.2,
                           "weight": 0.9
                       }
                   },
                   "packages": {
                       "bag2": 1,
                       "box2": 1
                   }
               }
           },
           {
               "type": "deliveryTo",
               "to": {
                   "address": {
                       "dates": {
                           "from": "2015-10-29T14:00:00.000Z",
                           "to": "2015-10-29T18:00:00.000Z"
                       },
                       "address": "Варшавское шоссе, д, 1"
                   },
                   "id": "e90f1820-0128-11e5-80c7-00155d903d03"
               },
               "cost": {
                   "base": 506.25,
                   "discount": -1.25,
                   "total": 505,
                   "details": [
                       {
                           "id": "1f9ead3d-f5ce-4dff-b1f6-649707373104",
                           "name": "Отвоз груза клиенту",
                           "cost": {
                               "base": 506.25,
                               "total": 505,
                               "discount": -1.25
                           }
                       }
                   ]
               }
           }
       ]
   }
}
```
