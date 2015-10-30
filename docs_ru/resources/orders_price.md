# Получение цены заказа

`GET https://api.vozovoz.ru/v1/orders/price`

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
    "data" : Order
}
```

Order - [объект заказа](orders_object.md), ограниченный полями `balance`, `cost`, `editing`, `services`

