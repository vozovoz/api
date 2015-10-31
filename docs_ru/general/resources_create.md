# Создание объекта

Для создания объекта надо сделать POST запрос к ресурсу, передавая необходимые параметры в теле запроса

`POST https://vozovoz.ru/api/v1/[название ресурса]`

Обязательный заголовок:
`Content-Type: application/x-www-form-urlencoded;charset=UTF-8`

---

```js
HTTP/1.1 201 Created
{
    "data": [объект]
}
