# Объект `Order`

Имя | Тип | Описание
--- | --- | ---
id | string | Идентификатор заказа
number | string | Номер заказа
promoCode | string | Промокод
status | [Order.Status](#status) | Статус заказа
organization | [Order.Organization](#organization) | Организация, осуществляющая перевозку
dates | [Order.Dates](#dates) | Даты создания/обновления заказа
editing | [Order.Editing](#editing) | Конфигурация редактирования заказа
cost | [Order.Cost](#cost) | Стоимость
services | [[Order.Service](#service)] | Массив услуг
 
#### Объект <a name="status">`Order.Status`</a>
 
Имя | Тип | Описание
--- | --- | ------
message | string | Краткое описание статуса
description | string | Полное описание статуса
isTaken | boolean | Заказ принят
isGiven | boolean | Заказ выдан
isCanceled | boolean | Заказ отменен
isPaid | boolean | Заказ оплачен
canUserRequestDriverCallback | boolean | Возможность запроса звонка от водителя

#### Объект <a name="service">`Order.Service`</a>

В зависимости от типа услуги, объект тип Order.Service может содержать различные поля
 
##### Услуга «Межтерминальная доставка»

Имя | Тип | Описание | Значение
--- | --- | -------- | -------- 
type | string | Тип услуги | `shipping`
name | string | Название услуги
sortIndex | number | Индекс сортировки |
counteragents | object | Контрагенты, участвующие в заказе:
counteragents.payer | [Counteragent](counteragent) | плательщик
counteragents.shipper | [Counteragent](counteragent) | отправитель
counteragents.consignee | [Counteragent](counteragent) | получатель
from | [Location](location) | Место отправления
to | [Location](location) | Место получения
cargo | [Order.Cargo](#cargo) | Груз
cost | [Order.Service.Cost](#service.cost) | Стоимость услуги
