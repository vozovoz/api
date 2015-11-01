# Редактирование заказа

`PATCH https://vozovoz.ru/api/v1/orders/[ID]`

Параметры запроса:

Имя | Тип | Обязательный | Описание
--- | --- | ------------ | --------
services | [[Order.Service](orders_object.md#service)] | да | Услуги, участвующие в заказе
promoCode | string | нет | Промокод
phoneNumber | string | если пользователь не авторизован, или если у пользователя нет телефона | Телефонный номер автора заказа
smsCode | string | если пользователь не авторизован, или если у пользователя нет телефона | Смс-код подтверждения телефона

---

```js
HTTP/1.1 200 OK
{
    "data" : Order
}
```

Order - [объект заказа](orders_object.md), ограниченный полями `balance`, `cost`, `editing`, `services`
