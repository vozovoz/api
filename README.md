# Vozovoz API v1.0

Vozovoz API представляет REST-интерфейс для взаимодействия с сайтом [vozovoz.ru](https://vozovoz.ru/).
В качестве протокола передачи данных используется HTTPS.

Протестировать взаимодействия с API можно на [демо-сервере](https://demo.vozovoz.ru/).

<a name="content" />
## Содержание

* [Взаимодействие с ресурсами](docs_ru/general/resources.md)
  * [Получение коллекции объектов](docs_ru/general/resources_collection.md)
  * [Получение объекта](docs_ru/general/resources_object.md)
  * [Создание объекта](docs_ru/general/resources_create.md)
  * [Изменение объекта](docs_ru/general/resources_edit.md)
  * [Удаление объекта](docs_ru/general/resources_delete.md)
  * [Ошибки и коды ответов](docs_ru/general/resources_errors.md)
* Аутентификация
  * [Доступ к ресурсам](docs_ru/general/authentication_token.md)

<a name="resources" />
### Ресурсы

* Заказы
  * [Объект заказа](docs_ru/resources/orders_object.md)
  * [Получение заказа](docs_ru/resources/orders_get.md)
  * [Создание заказа](docs_ru/resources/orders_create.md)
  * [Редактирование заказа](docs_ru/resources/orders_edit.md)
  * [Расчет цены](docs_ru/resources/orders_price.md)
* [Населенные пункты](docs_ru/resources/locations.md)
* [Зоны доставки](docs_ru/resources/zones.md)
* [Терминалы](docs_ru/resources/terminals.md)
* [Контрагенты](docs_ru/resources/counteragents.md)
* [Расписание доставки](docs_ru/resources/timetables.md)
