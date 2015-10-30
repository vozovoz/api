# Ошибки

При возникновении любой ошибки, Vozovoz API возвращает в теле ответа JSON объект с корневым свойством error, code и другими необязательными полями.

**Пример**

```js
HTTP/1.1 401 Unauthorized
Content-Type: application/json;charset=UTF-8
Cache-Control: no-store
Pragma: no-cache
{
  ["error":  "validation",]
  "code":    21,
  "message": "Bad request",
  ["url":    "http://api.vozovoz.ru/errors/21",]
  "fields":  [
    {
      "field":    "password",
      "error":    "isEmpty",
      ["message": "Password is empty"]
    },
    {
      "field": "email",
      "error": "exists"
    },
    {
      "field": "sex",
      "error": "isEmpty"
    },
    {
      "field": "login",
      "error": "exists"
    }
  ]
}
```

#### Внутренняя ошибка

```js
HTTP/1.1 500 Internal Server Error
{
    "error" : "Internal server error",
    "code"  : 10
}
```

#### Ресурс или объект не найден

```js
HTTP/1.1 404 Not Found
{
    "error" : "Resource not found",
    "code"  : 20
}
```

#### Неправильный запрос

```js
HTTP/1.1 400 Bad Request
{
    "error" : "Bad request",
    "code"  : 21
}
```

#### Нет доступа к ресурсу

```js
HTTP/1.1 403 Forbiden
{
    "error" : "Forbidden",
    "code"  : 22
}
```

#### Неподтвержденный пользователь

```js
HTTP/1.1 403 Forbiden
{
    "error" : "User not confirmed",
    "code"  : 25
}
```


#### Технические работы

```js
HTTP/1.1 503 Service Unavailable
{
    "error" : "Maintenance",
    "code"  : 11
}
```

