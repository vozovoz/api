# Населенные пункты

## Объект `Location`

Имя | Тип | Описание | значение
--- | --- | -------- | --------
id | string | locationID
type | string | Тип (например, "г")
name | string | Название
regions | object | Административные единицы, к которым принадлежит нас. пункт: `level` - уровень, `name` - название, `type` - тип (например, «край»)
urlName | string | Название для URL-сегмента в адресной строке
timezone | number | Часовой пояс UTC
zoom | number | Коэффициент масштабирования на карте
position | object | Расположение населенного пункта: `type` - тип расположения на карте (например «point»), `coordinates` - массив координат [долгота, широта]
zone | object | Зона доставки: `id` - zoneID, `name` - название
defaults | object | Значения по умолчанию для населенного пункта: `address` - адрес, `terminalId` - terminalID
insurance | object | Параметры страховки: `declaredCostMin` - минимальная объявленная стоимость, `declaredCostMax` - максимальная объявленная стоимость
contacts | object | Контакты Возовоз в населенном пункте: `phoneNumber` - телефонный номер
