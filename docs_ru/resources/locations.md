# Населенные пункты

## Объект `Location`

Имя | Тип | Описание
--- | --- | --------
id | string | Идентификатор населенного пункта
type | string | Тип (например, "г")
name | string | Название
regions | object | Административные единицы, к которым принадлежит нас. пункт: `level` - уровень, `name` - название, `type` - тип (например, «край»)
urlName | string | Название для URL-сегмента в адресной строке
timezone | number | Смещение относительно UTC
zoom | number | Коэффициент масштабирования на карте
position | object | Расположение населенного пункта: `type` - тип расположения на карте (например «point»), `coordinates` - массив координат [долгота, широта]
zone | object | Зона доставки: `id` - zoneId, `name` - название
defaults | object | Значения по умолчанию для населенного пункта: `address` - адрес, `terminalId` - идентификатор терминала
insurance | object | Параметры страховки: `declaredCostMin` - минимальная объявленная стоимость, `declaredCostMax` - максимальная объявленная стоимость
contacts | object | Контакты Возовоз в населенном пункте: `phoneNumber` - телефонный номер
address | [Location.Address](#address) | Адрес
terminal | [Location.Terminal](#terminal) | Терминал

#### Объект <a name="address">`Location.Address`</a>

Имя | Тип | Описание
--- | --- | --------
address | string | Идентификатор населенного пункта
dates | object | Дата и время относительно часового пояса населенного пункта:
&nbsp; dates.from | &nbsp; [Date](resources.md#format) | &nbsp; начальная дата
&nbsp; dates.to | &nbsp; [Date](resources.md#format) | &nbsp; конечная дата
floor | number | Этаж
needWork | boolean | Погрузочно/разгузочные работы
hasLift | boolean | Грузовой лифт

#### Объект <a name="terminal">`Location.Terminal`</a>

Имя | Тип | Описание
--- | --- | --------
id | string | terminalId
address | string | Адрес терминала
dates | object | Дата и время относительно часового пояса населенного пункта:
&nbsp; dates.from | &nbsp; [Date](resources.md#format) | &nbsp; отправление
&nbsp; dates.to | &nbsp; [Date](resources.md#format) | &nbsp; прибытие

## Получение списка населенных пунктов

`GET https://vozovoz.ru/api/v1/locations`

Параметры запроса:

Имя | Тип | Обязательный | Описание
--- | --- | ------------ | --------
zoneId | string | нет | Id зоны, для которой необходимо получить населенные пункты
hasTerminals | boolean | нет | Наличие терминала в населенном пункте

---

```js
HTTP/1.1 200 OK
{
  "data" : [<объект Location>],
  "meta" : <мета-информация>
}

```

Location - [объект населенного пункта](locations.md)

## Получение списка населенных пунктов по названию

`GET https://vozovoz.ru/api/v1/locations/autocomplete?query='<строка запроса>'`

Параметры запроса:

Имя | Тип | Описание
--- | --- | --------
query | string | строка с названием населенного пункта

---

```js
HTTP/1.1 200 OK
{
  "data" : [<объект Location>],
  "meta" : <мета-информация>
}

```

Location - [объект населенного пункта](locations.md)
