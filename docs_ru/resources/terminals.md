# Терминалы доставки

## Объект `Terminal`

Имя | Тип | Описание
--- | --- | --------
id | string | terminalID
type | string | Тип
name | string | Название
address | string | Адрес
urlName | string | Название для URL-сегмента в адресной строке
timezone | number | Часовой пояс UTC
note | string | Примечание
subway | string | Станция метро
position | object | Расположение населенного пункта: `type` - тип расположения на карте (например «point»), `coordinates` - массив координат [долгота, широта]
zone | object | Зона доставки: `id` - zoneID, `name` - название
location | object | Населенный пункт терминала: `id` - locationID, `name` - название нас. пункта, `type` - тип населенного пункта
conditions | object | Условия приема грузов: `type` - тип, `id` - id, `description` - описание `or` - ИЛИ, `and` - И
timetable | object | Расписание работы
files | object | Ссылки на файлы: `locationMap` - схема проезда, `photosArchive` - архив фотографий, `photos` - массив фотографий
