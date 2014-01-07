Hautelook Templated URI Router
==============================

Symfony2 UrlGenerator that provides a [RFC-6570][RFC-6570] compatible router and URL Generator.
Currently it is extremely naive, and incomplete.
However, it does what we need it to do. Contributions are welcome.

[![Build Status](https://secure.travis-ci.org/hautelook/TemplatedUriRouter.png?branch=master)](https://travis-ci.org/hautelook/TemplatedUriRouter)

## Installation

Run the following command (assuming you have composer.phar or composer binary installed), or
require `hautelook/templated-uri-router` to your `composer.json` and run `composer install`:

```bash
$ composer require "hautelook/templated-uri-router ~1.0"
```

## Usage

```yaml
# routing.yml
hautelook_demo_route:
    pattern: /demo
```

```php
use Hautelook\TemplatedUriRouter\Routing\Generator\Rfc6570Generator as TemplateGenerator;

$templateGenerator = new TemplateGenerator($routes, $context);
$templatedUri      = $templateGenerator->generate('hautelook_demo_route', array(
    'page'   => '{page}',
    'sort'   => array('{sort}'),
    'filter' => array('{filter}'),
));
```

This will produce a link similar to:

```
/demo{?page,sort%5B%5D*,filter%5B%5D*}
```

## Bundle

The symfony2 bundle lives at
[https://github.com/hautelook/TemplatedUriBundle](https://github.com/hautelook/TemplatedUriBundle).

[RFC-6570]: https://tools.ietf.org/html/rfc6570

