# Ошибки

При возникновении любой ошибки, Vozovoz API возвращает в теле ответа JSON объект с корневым свойством error, code и другими необязательными полями.

**Пример**

```js
HTTP/1.1 401 Unauthorized
Content-Type: application/json;charset=UTF-8
Cache-Control: no-store
Pragma: no-cache

{
  "message": "Короткий текст ошибки", //обязательно
  "description": "Длинный текст ошибки",
  "code": 21,
  "fields": {
    "from": {
      "address": {
        "error": "incorrectAddress", //обязательно
        "message": "Доставка на этот адрес недоступна", //обязательно
        "description: "Длинный текст ошибки"
      }
    }
  }
}
```

#### Внутренняя ошибка

```js
HTTP/1.1 500 Internal Server Error
{
    "message" : "Internal server error"
}
```

#### Ресурс или объект не найден

```js
HTTP/1.1 404 Not Found
{
    "message" : "Resource not found"
}
```

#### Неправильный запрос

```js
HTTP/1.1 400 Bad Request
{
    "message" : "Bad request"
}
```

#### Нет доступа к ресурсу

```js
HTTP/1.1 403 Forbidden
{
    "message" : "Forbidden"
}
```

#### Технические работы

```js
HTTP/1.1 503 Service Unavailable
{
    "message" : "Maintenance"
}
```

