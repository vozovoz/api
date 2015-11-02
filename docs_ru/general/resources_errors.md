# Ошибки

При возникновении любой ошибки API возвращает в теле ответа JSON-объект с корневым свойством `message` и другими необязательными полями.

Если ошибка относится к конкретному полю в запросе, то в ответ добавится поле `fields`, повторяющее структуру объекта запроса до ошибочного поля.

**Пример**

```js
HTTP/1.1 400 Bad Request
{
  "error": "<id ошибки>",
  "message": "<Короткий текст ошибки>", // обязательно
  "description": "<Длинный текст ошибки>",
  "fields": {
    "from": {
      "address": {
        "error": "<id ошибки>", // обязательно
        "message": "<Доставка на этот адрес недоступна>", // обязательно
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
    "message" : "Bad Request"
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
    "message" : "Internal Server Error"
}
```

#### Технические работы

```js
HTTP/1.1 503 Service Unavailable
{
    "message" : "Maintenance"
}
```

