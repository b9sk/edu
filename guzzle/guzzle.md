### Показывает куки запроса
```php
$client = new \GuzzleHttp\Client(['cookies' => true]);
$r = $client->request('GET', 'http://httpbin.org/cookies');

$cookieJar = $client->getConfig('cookies');
$cookieJar->toArray();
```