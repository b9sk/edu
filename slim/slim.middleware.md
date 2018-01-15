```php
$app->add(function ($request, $response, $next) {

	$response->getBody()->write('BEFORE');
	var_dump($request->getUri()->getQuery());
	$response = $next($request, $response);
	$response->getBody()->write('AFTER');

	return $response;
});
```