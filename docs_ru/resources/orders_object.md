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
cost | [Order.Cost](#cost) | Стоимость (только поле total)
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

#### Объект <a name="organization">`Order.Organization`</a>
 
Имя | Тип | Описание
--- | --- | ------
id | string | organizationID
name | string | Название

#### Объект <a name="dates">`Order.Dates`</a>
 
Имя | Тип | Описание
--- | --- | ------
created | string | Дата создания заказа
updated | string | Дата обновления заказа
arrivalFrom | string | Верхняя граница по времени прибытия груза
arrivalTo | string | Нижняя граница по времени прибытия груза

#### Объект <a name="editing">`Order.Editing`</a>
 
Имя | Тип | Описание
--- | --- | ------
canBeCanceled | string | Заказ может быть отменен
fields | boolean | Поля, доступные для редактирования

#### Объект <a name="service.cost">`Order.Cost`</a>
 
Имя | Тип | Описание
--- | --- | ------
base | number | Базовая цена услуги
discount | number | Скидка
total | number | Итоговая цена (base + discount)
details | [Order.Cost.Discount](#service.cost.details) | Массив ценообразующих компонентов
actions | [Order.Cost.Action](#service.cost.action) | Массив влияющих на цену действий:

#### Объект <a name="service.cost.details">`Order.Cost.Details`</a>
 
Имя | Тип | Описание
--- | --- | --------
id | string | Id услуги
name | string | Название
cost | object | Цена
&nbsp; cost.base | &nbsp; number | &nbsp; Базовая
&nbsp; cost.discount | &nbsp; number | &nbsp; Скидка
&nbsp; cost.total | &nbsp; number | &nbsp; Итоговая цена (base + discount)

#### Объект <a name="service.cost.action">`Order.Cost.Action`</a>
 
Имя | Тип | Описание
--- | --- | --------
id | string | Id услуги
name | string | Название

#### Объект <a name="service">`Order.Service`</a>

В зависимости от типа услуги, объект тип Order.Service может содержать различные поля

##### Услуга «Межтерминальная доставка»

Имя | Тип | Описание | Значение
--- | --- | -------- | -------- 
type | string | Тип услуги | "shipping"
name | string | Название услуги
sortIndex | number | Индекс сортировки |
counteragents | [Counteragents](counteragents.md) | Контрагенты, участвующие в заказе
from | [Location](locations.md) | Место отправления
to | [Location](locations.md) | Место получения
cargo | [Order.Cargo](#cargo) | Груз
cost | [Order.Cost](#service.cost) | Стоимость услуги

##### Услуга «Забор груза»

Имя | Тип | Описание | Значение
--- | --- | -------- | -------- 
type | string | Тип услуги | "deliveryFrom"
name | string | Название услуги
sortIndex | number | Индекс сортировки |
counteragents | [Counteragents](counteragents.md) | Контрагенты, участвующие в заказе
from | [Location](locations.md) | Место забора груза
cost | [Order.Cost](#service.cost) | Стоимость услуги

##### Услуга «Отвоз груза»

Имя | Тип | Описание | Значение
--- | --- | -------- | -------- 
type | string | Тип услуги | "deliveryTo"
name | string | Название услуги
sortIndex | number | Индекс сортировки |
counteragents | [Counteragents](counteragents.md) | Контрагенты, участвующие в заказе
to | [Location](locations.md) | Место отвоза груза
cost | [Order.Cost](#service.cost) | Стоимость услуги

##### Услуга «Ответственное хранение»

Имя | Тип | Описание | Значение
--- | --- | -------- | -------- 
type | string | Тип услуги | "paidStoring"
name | string | Название услуги
sortIndex | number | Индекс сортировки
dates | object | Даты:
&nbsp; dates.from |&nbsp;  object |&nbsp;  начало начисления платы за хранение
counteragents | [Counteragents](counteragents.md) | Контрагенты, участвующие в заказе
cost | [Order.Cost](#service.cost) | Стоимость услуги

##### Услуга «Сбор за ценность груза»

Имя | Тип | Описание | Значение
--- | --- | -------- | -------- 
type | string | Тип услуги | ""
name | string | Название услуги
sortIndex | number | Индекс сортировки
counteragents | [Counteragents](counteragents.md) | Контрагенты, участвующие в заказе
cost | [Order.Cost](#service.cost) | Стоимость услуги

##### Услуга «Возврат сопроводительных документов»

Имя | Тип | Описание | Значение
--- | --- | -------- | -------- 
type | string | Тип услуги | "returnOfSupportingDocuments"
name | string | Название услуги
sortIndex | number | Индекс сортировки
counteragents | [Counteragents](counteragents.md) | Контрагенты, участвующие в заказе
cost | [Order.Cost](#service.cost) | Стоимость услуги
