# Терминалы доставки

## Объект `Terminal`

Имя | Тип | Описание
--- | --- | --------
id | string | Идентификатор терминала
type | string | Тип
name | string | Название
address | string | Адрес
urlName | string | Название для URL-сегмента в адресной строке
timezone | number | Смещение относительно UTC
note | string | Примечание
subway | string | Станция метро
position | object | Расположение населенного пункта: `type` — тип расположения на карте (`Point`), `coordinates` — массив координат (долгота, широта)
zone | object | Зона доставки: `id` — идентификатор зоны, `name` — название
location | object | Населенный пункт терминала: `id` — идентификатор населенного пункта, `name` — название, `type` — тип
conditions | [Conditions](#conditions) | Условия приема грузов
timetable | object | Расписание работы
files | object | Ссылки на файлы: `locationMap` — схема проезда, `photosArchive` — архив фотографий, `photos` — массив фотографий

### Объект <a name="conditions">`Conditions`</a>

Имя | Тип | Описание
--- | --- | --------
id | string | Идентификатор
type | string | Тип терминала
description | string | Описание ограничения
and | [[Conditions.condition](#conditions.condition)] | Массив условий И (каждое условие должно выполнятся)
or | [[[Conditions.condition](#conditions.condition)]] | Массив ИЛИ массивов условий И (может выполнятся только один массив условий И)

### Объект <a name="conditions.condition">`Conditions.condition`</a>

Имя | Тип | Описание
--- | --- | --------
value | [Conditions.condition.value](#conditions.condition.value) | Параметры условия
field | string | Поле, к которому применяется условие

### Объект <a name="conditions.condition.value">`Conditions.condition.value`</a>

##### Диапазон

Имя | Тип | Описание | Значение
--- | --- | -------- | --------
type | string | 'range' |
from | number | Значение ОТ включая | минимум 0
to | number | Значение ДО не включая | максимум ∞

##### Равенство

Имя | Тип | Описание
--- | --- | --------
type | string | 'value'
is | number/string | Сравниваемое значение

## Получение списка терминалов

`GET https://vozovoz.ru/api/v1/terminals`

Параметры запроса:

Имя | Тип | Обязательный | Описание
--- | --- | ------------ | --------
zoneId | string | нет | Id зоны, для которой необходимо получить терминалы

---

```js
HTTP/1.1 200 OK
{
  "data": [<объект Terminal>],
  "meta": <мета-информация>
}
```

Terminal — [объект терминала](terminals.md)

## Получение терминала

`GET https://vozovoz.ru/api/v1/terminals/<id>`

---

```js
HTTP/1.1 200 OK
{
  "data": <объект Terminal>
}
```

Terminal — [объект терминала](terminals.md)
