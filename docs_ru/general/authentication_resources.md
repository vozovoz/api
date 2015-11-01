# Доступ к ресурсам

Для получения доступа к ресурсам vozovoz.ru, необходимо передать `access_token` в заголовке `Authorization`:

```js
GET https://api.vozovoz.ru/[название ресурса] HTTP/1.1
Host: api.vozovoz.ru
Authorization: Bearer [access_token]
```

vozovoz.ru API также поддерживает передачу параметра `access_token` в URI и теле POST-запроса.

При обращении без `access_token` приходит ответ:

```js
HTTP/1.1 401 Unauthorized
WWW-Authenticate: Bearer realm="vozovoz.ru API v1"
```

Возможные ошибки авторизации:

* `invalid_request` - Неправильно сформированный запрос. Ответ HTTP 400 (Bad Request)
* `invalid_token` - Переданный `access_token` истек или анулирован. Ответ HTTP 401 (Unauthorized)
* `insufficient_scope` - Переданный `access_token` не обладает требуемыми привилегиями. Ответ HTTP 403 (Forbidden).

Пример:

```js
HTTP/1.1 401 Unauthorized
WWW-Authenticate: Bearer realm="vozovoz.ru API v1"
error="invalid_token"
```
