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
id | string | Идентификатор организации
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

#### Объект <a name="cost">`Order.Cost`</a>
 
Имя | Тип | Описание
--- | --- | ------
base | number | Базовая цена услуги
discount | number | Скидка
total | number | Итоговая цена (base + discount)
details | [Order.Cost.Discount](#cost.details) | Массив ценообразующих компонентов
actions | [Order.Cost.Action](#cost.action) | Массив влияющих на цену действий

#### Объект <a name="service.cost.details">`Order.Cost.Details`</a>
 
Имя | Тип | Описание
--- | --- | --------
id | string | Идентификатор услуги
name | string | Название
cost | [Order.Cost](#cost) | Цена без полей `details` и `actions`

#### Объект <a name="cost.action">`Order.Cost.Action`</a>
 
Имя | Тип | Описание
--- | --- | --------
id | string | Идентификатор услуги
name | string | Название

#### Объект <a name="cargo">`Order.Cargo`</a>
 
Имя | Тип | Описание
--- | --- | --------
type | string | Тип груза
hasCorrespondence | boolean | Корреспонденция
declaredCost | number | Заявленная стоимость груза
packages | [Order.Cargo.Packages](#cargo.packages) | Упаковка
total | [Order.Cargo.Total](#cargo.total) | Суммарные параметры

#### Объект <a name="cargo.packages">`Order.Cargo.Packages`</a>
 
Имя | Тип | Описание
--- | --- | --------
bag1 | integer | Мешок 55×105 см, шт.
bag2 | integer | Мешок 70×120 см, шт.
box1 | integer | Коробка 40×20×20 см, шт.
box2 | integer | Коробка 40×40×20 см, шт.
box3 | integer | Коробка 40×40×40 см, шт.
box4 | integer | Коробка 80×40×40 см, шт.
sealPackage | integer | Пломбирование, шт.
safePackage | integer | Сейф-пакет, шт.
hardPackageVolume | number | Жесткая упаковка, м³
extraPackageVolume | number | Дополнительная упаковка, м³
bubbleFilmVolume | number | Воздушно-пузырьковая пленка, м³

#### Объект <a name="cargo.total">`Order.Cargo.Total`</a>
 
Имя | Тип | Описание
--- | --- | --------
all | object | Общие:
&nbsp; volume | &nbsp; number | &nbsp; Объем, м³
&nbsp; weight | &nbsp; number | &nbsp; Вес, кг
&nbsp; quantity | &nbsp; integer | &nbsp; Количество, шт.
noGab | object | Негабарит:
&nbsp; volume | &nbsp; number | &nbsp; Объем, м³
&nbsp; weight | &nbsp; number | &nbsp; Вес, кг
max | object | Максимальные:
&nbsp; length | &nbsp; number | &nbsp; Длина, м
&nbsp; width | &nbsp; number | &nbsp; Ширина, м
&nbsp; height | &nbsp; number | &nbsp; Высота, м
&nbsp; weight | &nbsp; number | &nbsp; Вес, кг

#### Объект <a name="service">`Order.Service`</a>

В зависимости от типа услуги объект Order.Service может содержать различные поля

##### Услуга «Межтерминальная перевозка»

Имя | Тип | Описание | Значение
--- | --- | -------- | -------- 
type | string | Тип услуги | "shipping"
name | string | Название услуги
counteragents | [Counteragents](counteragents.md) |Контрагенты, участвующие в заказе
from | [Location](locations.md) | Место отправления
to | [Location](locations.md) | Место получения (терминал)
cargo | [Order.Cargo](#cargo) | Груз
cost | [Order.Cost](#service.cost) | Стоимость услуги

##### Услуга «Забор груза»

Имя | Тип | Описание | Значение
--- | --- | -------- | -------- 
type | string | Тип услуги | "deliveryFrom"
name | string | Название услуги
counteragents | [Counteragents](counteragents.md) | Контрагенты, участвующие в заказе
from | [Location](locations.md) | Место забора груза
cost | [Order.Cost](#service.cost) | Стоимость услуги

##### Услуга «Отвоз груза»

Имя | Тип | Описание | Значение
--- | --- | -------- | -------- 
type | string | Тип услуги | "deliveryTo"
name | string | Название услуги
counteragents | [Counteragents](counteragents.md) | Контрагенты, участвующие в заказе
to | [Location](locations.md) | Место отвоза груза
cost | [Order.Cost](#service.cost) | Стоимость услуги

##### Услуга «Ответственное хранение»

Имя | Тип | Описание | Значение
--- | --- | -------- | -------- 
type | string | Тип услуги | "paidStoring"
name | string | Название услуги
dates | object | Даты:
&nbsp; dates.from |&nbsp;  string |&nbsp;  начало начисления платы за хранение
counteragents | [Counteragents](counteragents.md) | Контрагенты, участвующие в заказе
cost | [Order.Cost](#service.cost) | Стоимость услуги

##### Услуга «Возврат сопроводительных документов»

Имя | Тип | Описание | Значение
--- | --- | -------- | -------- 
type | string | Тип услуги | "returnOfSupportingDocuments"
name | string | Название услуги
counteragents | [Counteragents](counteragents.md) | Контрагенты, участвующие в заказе
cost | [Order.Cost](#service.cost) | Стоимость услуги

#### Объект <a name="location">`Order.Location`</a>

Имя | Тип | Описание
--- | --- | --------
id | string | Идентификатор населенного пункта
type | string | Тип (например, "г" — город)
name | string | Название
address | [Order.Location.Address](#location.address) | Адрес
terminal | [Order.Location.Terminal](#location.terminal) | Терминал

#### Объект <a name="location.address">`Order.Location.Address`</a>

Имя | Тип | Описание
--- | --- | --------
address | string | Идентификатор населенного пункта
dates | object | Дата и время относительно часового пояса населенного пункта:
&nbsp; dates.from | &nbsp; [Date](../general/resources.md#format) | &nbsp; начальная дата
&nbsp; dates.to | &nbsp; [Date](../general/resources.md#format) | &nbsp; конечная дата
floor | number | Этаж
needWork | boolean | Погрузочно/разгузочные работы
hasLift | boolean | Грузовой лифт

#### Объект <a name="location.terminal">`Order.Location.Terminal`</a>

Имя | Тип | Описание
--- | --- | --------
id | string | terminalId
address | string | Адрес терминала
dates | object | Дата и время относительно часового пояса населенного пункта:
&nbsp; dates.from | &nbsp; [Date](../general/resources.md#format) | &nbsp; отправление
&nbsp; dates.to | &nbsp; [Date](../general/resources.md#format) | &nbsp; прибытие
