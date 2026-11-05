## API-запрос: авторизация пользователя

### General info

Запрос отправляется при попытке авторизации пользователя через форму
входа CRM.

  Параметр       Значение
  -------------- ---------------------------------------
  Method         `POST`
  Endpoint       `https://stellantis.autocrm.ru/login`
  Protocol       HTTP/2
  Content-Type   `application/x-www-form-urlencoded`
  Тип запроса    Отправка HTML-формы (`document`)


### Request
#### Headers

``` 
Content-Type: application/x-www-form-urlencoded
Origin: https://stellantis.autocrm.ru
Referer: https://stellantis.autocrm.ru/login
```

Указаны только заголовки, необходимые для понимания запроса. Остальные
браузерные заголовки (`sec-*`, `User-Agent`, `Accept-Encoding` и тд)
опущены.

#### Body

Формат: `x-www-form-urlencoded`

  Параметр                Значение           Назначение
  ----------------------- ------------------ ---------------------
  `_csrf`                 `{{csrf_token}}`   CSRF-токен формы
  `LoginForm[email]`      `{{email@mail.ru}}`        Email пользователя
  `LoginForm[password]`   `{{thepassword123}}`     Пароль пользователя

Пример тела запроса в URL-encoded формате:

``` 
_csrf={{csrf_token}}&LoginForm%5Bemail%5D={{email@mail.ru}}&LoginForm%5Bpassword%5D={{thepassword123}}
```

#### cURL

``` 
curl -i -X POST "https://stellantis.autocrm.ru/login" \
  -H "Content-Type: application/x-www-form-urlencoded" \
  -H "Origin: https://stellantis.autocrm.ru" \
  -H "Referer: https://stellantis.autocrm.ru/login" \
  --data-urlencode "_csrf={{csrf_token}}" \
  --data-urlencode "LoginForm[email]={{email}}" \
  --data-urlencode "LoginForm[password]={{password}}"
```

### Response

``` 
HTTP/2 200
Content-Type: text/html; charset=UTF-8
Cache-Control: no-store, no-cache, must-revalidate
```

  Параметр           Фактическое значение
  ------------------ ---------------------------------------
  Status Code        `200 OK`
  Content-Type       `text/html; charset=UTF-8`
  Cache-Control      `no-store, no-cache, must-revalidate`



### Примечания

-   CSRF-токен и учётные данные заменены переменными: реальные значения не публикую в открытом репозитории.
-   Статус `200 OK` сам по себе не подтверждает успешную авторизацию.


