# Получение ключа доступа клиентского приложения

Речь идет о способе авторизации путем передачи [client credentials](http://tools.ietf.org/html/draft-ietf-oauth-v2-21#section-4.4)

Для аутенфикации надо сделать POST-запрос на `https://vozovoz.ru/auth/token` c авторизационными данными клиента в заголовке `Authorization` (метод Http Basic Authentication).

Обязательные заголовки:

```js
Content-Type: application/x-www-form-urlencoded;charset=UTF-8
Authorization: Basic [закодированная строка с данными клиента]
```

Строка авторизации формируется следующим образом:

`base64(client_id + ":" + client_secret)`

Параметры запроса:

Имя | Тип | Описание
--- | --- | ------
grant_type | string | Тип аутенфикации. Значение должно быть `client_credentials`
client_id | integer | ID клиента

В случае удачной аутенфикации сервер возвращает JSON с параметрами:

* `access_token` - Токен который следует передавать на закрытые ресурсы vozovoz.ru чтобы получить к ним доступ
* `token_type` - Тип ключа доступа
* `expires_in` - Время жизни токена в секундах. После устаревания токена следует получить новый используя `refresh_token`

**Пример ответа**

```js
HTTP/1.1 200 OK
Content-Type: application/json;charset=UTF-8
Cache-Control: no-store
Pragma: no-cache

{
  "access_token": "2YotnFZFEjr1zCsicMWpAA",
  "token_type":   "bearer",
  "expires_in":   3600
}
```

В случае ошибки сервер возращает JSON с параметром error c возможными значениями:

* `invalid_request` - Запрос автризации не содержит необходимых параметров, или неверные значения параметров
* `invalid_client` - Ошибка аутенфикации клиента
* `invalid_grant` - Ошибка аутенфикации пользователя
* `unauthorized_client` - Клиенту не разрешено аутенфицироваться указанным в параметре `grant_type` способом.
* `unsupported_grant_type` - Указанный в параметре `grant_type` способ аутенфикации не поддерживается

**Пример ответа**

```js
HTTP/1.1 400 Bad Request
Content-Type: application/json;charset=UTF-8
Cache-Control: no-store
Pragma: no-cache

{
    "error": "invalid_request"
}
```
