# Ошибки

При возникновении любой ошибки, Vozovoz API возвращает в теле ответа JSON объект с корневым свойством message и другими необязательными полями.

**Пример**

```js
HTTP/1.1 400 Bad Request
{
  "message": "<Короткий текст ошибки>", //обязательно
  "description": "<Длинный текст ошибки>",
  "code": 21,
  "fields": {
    "from": {
      "address": {
        "error": "incorrectAddress", //обязательно
        "message": "<Доставка на этот адрес недоступна>", //обязательно
        "description": "<Длинный текст ошибки>"
      }
    }
  }
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

#### Внутренняя ошибка

```js
HTTP/1.1 500 Internal Server Error
{
    "message" : "Internal server error"
}
```

#### Технические работы

```js
HTTP/1.1 503 Service Unavailable
{
    "message" : "Maintenance"
}
```

