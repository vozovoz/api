# Создание объекта

Для создания объекта надо сделать POST-запрос к ресурсу, передавая необходимые параметры в теле запроса.

`POST https://vozovoz.ru/api/v1/[название ресурса]`

Обязательный заголовок:
`Content-Type: application/json; charset=utf-8`

---

```js
HTTP/1.1 201 Created
{
    "data": [объект]
}
```

**Пример**

```
POST https://vozovoz.ru/api/v1/news

{
    "title":       "Новость 1",
    "description": "Краткое описание новости 1"
}
```

---

```js
HTTP/1.1 201 Created
{
    "data": {
        "id":          1,
        "title":       "Новость 1",
        "description": "Краткое описание новости 1"
    }
}
```
