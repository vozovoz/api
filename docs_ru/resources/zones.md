# Терминалы доставки

## Объект `Zone`

Имя | Тип | Описание
--- | --- | --------
id | string | zoneID
name | string | Название
urlName | string | Название для URL-сегмента в адресной строке
zoom | number | Коэффициент масштабирования на карте
timezone | number | Часовой пояс UTC
hasTerminals | boolean | Наличие терминалов в зоне
isRegionalCenter | boolean | Зона является региональным центром
regionalCenterId | string | ID регионального центра
mainLocation | object | Основной населенный пункт в зоне: `id`
defaults | object | Значения по умолчанию для зоны: `address`, `terminalId`
conditions | object | Контактная информация: `phoneNumber`

## Получение списка зон

`GET https://vozovoz.ru/api/v1/cities`

---

```js
HTTP/1.1 200 OK
{
    "data" : [объект Zone],
    "meta" : {
        "limit" : [количество объектов],
        "offset": [начальная позиция],
        "total" : [общее количество объектов]
    }
}
```

Zone - [объект заказа](orders_object.md)
