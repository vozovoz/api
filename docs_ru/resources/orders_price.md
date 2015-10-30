# Получение заказа

`GET https://api.vozovoz.ru/v1/orders/[ID]`

Параметры запроса:

Имя | Тип | Описание
--- | --- | ---
id | string | Идентификатор заказа
services | [Order.Service](orders_object#service) | Номер заказа
promoCode | string | Промокод
save | boolean[Order.Status](#status) | Статус заказа
organization | [Order.Organization](#organization) | Организация, осуществляющая перевозку
dates | [Order.Dates](#dates) | Даты создания/обновления заказа
editing | [Order.Editing](#editing) | Конфигурация редактирования заказа
cost | [Order.Cost](#cost) | Стоимость
services | [Order.Services](#services) | Массив услуг

Возвращает:

```js
HTTP/1.1 200 OK
{
    "data" : [объект Order](order_object)
}
```