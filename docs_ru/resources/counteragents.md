# Контрагенты

## Объект `Counteragents`

Имя | Тип | Описание | значение
--- | --- | -------- | --------
payer | [Counteragent](#counteragent) |Плательщик
shipper | [Counteragent](#counteragent) |Отправитель
consignee | [Counteragent](#counteragent) |Получатель

## Объект <a name="counteragent">`Counteragent`</a>

#### Физическое лицо

Имя | Тип | Описание | значение
--- | --- | -------- | --------
id | string | counteragentId
type | string | тип | "individual"
fullName | string | ФИО
phoneNumbers | [string] | Массив телефонных номеров. Первый номер — основной
email | string | Электронная почта

#### Юридическое лицо

Имя | Тип | Описание | значение
--- | --- | -------- | --------
id | string | counteragentId
type | string | тип | "corporation"
inn | string | ИНН
kpp | string | КПП
name | string | Наименование
contactFullName | string | ФИО контактного лица
legalAddress | string | Юридический адрес
phoneNumbers | [string] | Массив телефонных номеров. Первый номер — основной
email | string | Электронная почта
