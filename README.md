# Slim OPTIONS Middleware

Middleware to add an OPTIONS route to existing routes.

[![Build Status](https://travis-ci.com/subjective-php/slim-options-middleware.svg?branch=master)](https://travis-ci.com/subjective-php/slim-options-middleware)
[![Scrutinizer Code Quality](https://scrutinizer-ci.com/g/subjective-php/slim-options-middleware/badges/quality-score.png?b=master)](https://scrutinizer-ci.com/g/subjective-php/slim-options-middleware/?branch=master)
[![Coverage Status](https://coveralls.io/repos/github/subjective-php/slim-options-middleware/badge.svg?branch=master)](https://coveralls.io/github/subjective-php/slim-options-middleware?branch=master)

[![Latest Stable Version](https://poser.pugx.org/subjective-php/slim-options-middleware/v/stable)](https://packagist.org/packages/subjective-php/slim-options-middleware)
[![Latest Unstable Version](https://poser.pugx.org/subjective-php/slim-options-middleware/v/unstable)](https://packagist.org/packages/subjective-php/slim-options-middleware)
[![License](https://poser.pugx.org/subjective-php/slim-options-middleware/license)](https://packagist.org/packages/subjective-php/slim-options-middleware)

[![Total Downloads](https://poser.pugx.org/subjective-php/slim-options-middleware/downloads)](https://packagist.org/packages/subjective-php/slim-options-middleware)
[![Daily Downloads](https://poser.pugx.org/subjective-php/slim-options-middleware/d/daily)](https://packagist.org/packages/subjective-php/slim-options-middleware)
[![Monthly Downloads](https://poser.pugx.org/subjective-php/slim-options-middleware/d/monthly)](https://packagist.org/packages/subjective-php/slim-options-middleware)

## Requirements

Requires PHP 7.0 (or later).

## Composer
To add the library as a local, per-project dependency use [Composer](http://getcomposer.org)! Simply add a dependency on `subjective-php/slim-options-middleware` to your project's `composer.json` file such as:

```sh
composer require subjective-php/slim-options-middleware
```

## Contact
Developers may be contacted at:

 * [Pull Requests](https://github.com/subjective-php/slim-options-middleware/pulls)
 * [Issues](https://github.com/subjective-php/slim-options-middleware/issues)

## Project Build
With a checkout of the code get [Composer](http://getcomposer.org) in your PATH and run:

```sh
composer install
./vendor/bin/phpunit
./vendor/bin/phpcs
```
## Slim 3 Example
```php
require __DIR__ . '/vendor/autoload.php';

use SubjectivePHP\Slim\Middleware;

// This Slim setting is required for the middleware to work
$app = new Slim\App([
    "settings"  => [
        "determineRouteBeforeAppMiddleware" => true,
    ]
]);

// create the middleware
$optionsMiddleware = new Middleware\OptionsMiddleware('*', ['Authorization', 'Content-Type']);

$app->map(['GET', 'POST'], 'foos', function ($request, $response, $args) {
    return $response;
};

$app->add($optionsMiddleware);

$app->run();
```

#### Send an OPTIONS request to the API
```
curl -i -X OPTIONS http://example.org/foos
```
#### Response will be similar to
```
HTTP/1.1 200 OK
Access-Control-Allow-Headers: Authorization, Content-Type
Access-Control-Allow-Methods: GET, POST, OPTIONS
Access-Control-Allow-Origin: *
Content-Type: text/html; charset=UTF-8
Date: Mon, 22 Apr 2019 12:45:18 GMT
Server: Apache/2.4.18 (Ubuntu)
Content-Length: 0
Connection: keep-alive
```




