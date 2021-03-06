# Введение


*Последнее обновление: 24.06.2022*

Wildberries API предосталвяет продавцам возможность управления магазином и получения оперативной и статистической информации по протоколу HTTP RestAPI.

Описание API предоставляется в формате [Swagger](https://swagger.io/) (Open API) и может быть использовано для импорта в другие инструменты (такие как PostMan) или генерации клиентского кода на различных языках программирования с помощью [Swagger CodeGen](https://swagger.io/tools/swagger-codegen/)

Для ручной проверки API вы можете использовать:
- Под ОС Windows - [PostMan](https://www.postman.com/)
- Под ОС Linux - [curl](https://curl.se/) 


# Поддержка

Техническая поддержка осуществляется через [чат техподдержки](https://seller.wildberries.ru/service-desk-v2/requests/history), доступный в личном кабинете продавца. При создании нового обращения в техподдержку используйте категорию API.

Новости и изменения, касающиеся API, публикуются в [новостной ленте WildBerries](https://seller.wildberries.ru/news) с тегом `#API`.

Также готовятся к публикации Release Notes по API на сайте. После их выхода будет осуществлен соответствующий анонс. 

# Авторизация

Вызов любого метода API должен быть авторизован. Авторизация осуществляется по ключам API, которые владелец продавца (главный пользователь) самостоятельно генерирует в своем личном кабинете в разделе [Профиль --> Настройки --> Доступ к API (для статистики)](https://seller.wildberries.ru/supplier-settings/access-to-api) и [Профиль --> Настройки --> Доступ к новому API (для остальных методов)](https://seller.wildberries.ru/supplier-settings/access-to-new-api)

! Ссылка на новый АПИ

Ключ должен передаваться в каждом HTTP-запросе. В зависимости от группы методов API, которые вы используете, ключ передается:
- В запросе (query) через параметр `key` для методов статистики
- В заголовке `Authorization` HTTP-запроса для остальных методов

## Генерация ключа:

**Генерация ключа API возможна только для владельца продавца**. Остальные пользователи продавца не могут управлять ключами API.

- Зайдите в [ЛК продавца](https://seller.wildberries.ru)
- Для генерации ключа API для методов статистики перейдите в раздел [Профиль --> Настройки --> Доступ к API](https://seller.wildberries.ru/supplier-settings/access-to-api)
- Для генерации ключа API для остальных методов (всех кроме статистики) перейдите в раздел [Профиль --> Настройки --> Доступ к новому API](https://seller.wildberries.ru/supplier-settings/access-to-api)


# Форматы

## Дата и время

Во многих методах API дата и время передаются в запросе или присутствуют в ответе. Во всех случаях API придерживается правила передавать дату и время в формате [RFC3339](https://datatracker.ietf.org/doc/html/rfc3339). 
<br>
В большинстве случаев вы можете передать дату или дату со временем. Если время не указано, оно принимается равным 00:00:00. Время можно указывать с точностью до секунд или миллисекунд. 
Литера `Z` в конце строки означает часовой пояс UTC. При ее отсутствии время считается в часовом поясе МСК (UTC+3).
<br>
Примеры:
- `2019-06-20`
- `2019-06-20T00:00:00Z`
- `2019-06-20T23:59:59`
- `2019-06-20T00:00:00.12345Z`
- `2019-06-20T00:00:00.12345`
- `2017-03-25T00:00:00`

# Каталоги API

## Статистика

Содержит методы получения статистики по заказам, продажам и остаткам на складах.

