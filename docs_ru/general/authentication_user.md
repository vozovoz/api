# Получение ключа доступа пользователя

Для аутенфикации надо сделать POST-запрос на `https://vozovoz.ru/auth/token` c пользовательскими авторизационными данными.

Обязательный заголовок:

`Content-Type: application/x-www-form-urlencoded;charset=UTF-8`

Имя | Тип | Обязательный | Описание
--- | --- | ------------ | --------
grant_type | string | да | Тип аутенфикации. Значение должно быть `password`
username | string | да | Ник или эмейл
password | string | да | Пароль
client_id | integer | да | ID клиента
client_secret | string | для приложений | Секретный ключ клиента
device_token | string | нет | Device Token
time_zone | integer | нет | Device time zone

В случае удачной аутенфикации сервер возвращает JSON с параметрами:
* `access_token` - Токен, который следует передавать на закрытые ресурсы vozovoz.ru, чтобы получить к ним доступ
* `token_type` - Тип ключа доступа
* `expires_in` - Время жизни токена в секундах. После устаревания токена следует получить новый используя `refresh_token`
* `refresh_token` - Токен обновления для получения нового `access_token`

**Пример ответа**

```js
HTTP/1.1 200 OK
Content-Type: application/json;charset=UTF-8
Cache-Control: no-store
Pragma: no-cache

{
  "access_token" : "2YotnFZFEjr1zCsicMWpAA",
  "token_type":    "bearer",
  "expires_in":    3600,
  "refresh_token": "tGzv3JOkF0XG5Qx2TlKWIA",
}

```

В случае ошибки сервер возращает JSON с параметром `error` c возможными значениями:
* `invalid_request` - Запрос автризации не содержит необходимых параметров, или неверные значения параметров
* `invalid_client` - Ошибка аутенфикации клиента
* `invalid_grant` - Ошибка аутенфикации пользователя
* `unauthorized_client` - Клиенту не разрешено аутенфицироваться указанным в параметре grant_type способом.
* `unsupported_grant_type` - Указанный в параметре grant_type способ аутенфикации не поддерживается


**Пример ответа**

```js
HTTP/1.1 400 Bad Request
Content-Type: application/json;charset=UTF-8
Cache-Control: no-store
Pragma: no-cache

{
  "error" : "invalid_request"
}

```
