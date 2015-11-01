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
    "data" : Order
}
```

Order - [объект заказа](orders_object.md), ограниченный полями `balance`, `cost`, `editing`, `services`
