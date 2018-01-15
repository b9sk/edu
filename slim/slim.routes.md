
## Примеры pattern (первый аргумент $app->get)
* `/about` статическая страница
* `'/[{name}]'` необязательный аргумент
* `'/tag[/{num}]'` необязательный аргумент, захватывает обратный слеш

Аргументы передаются в `$args`, однако _query string_ сюда не попадает!


## Обработка query string
* `$request->getQueryParams()` параметры query string
* через middleware (см. middleware)
