# php-router
PHP路由

## Usage

两种配置方式

```php
$config = [
    '/abc/:id' => '/abc',
    '/abc/def/:id' => '/abc/def',
    '/abc/def/:category/:id' => '/abc/category',
];
$router = Router::getInstance()->init($config);
$uri = '/abc/10';
$router->route($uri);
```

```php
$config = [
    'abc' => [
        ['pattern' => '/abc/(:int)', 'keys' => ['id'], 'uri' => '/abc'],
        ['pattern' => '/abc/def/(:int)', 'keys' => ['id'], 'uri' => '/abc/def'],
        ['pattern' => '/abc/def/(:string)/(:int)', 'keys' => ['category', 'id'], 'uri' => '/abc/category'],
    ],
    'bca' => [
        ['pattern' => '/bca/(:int)', 'keys' => ['id'], 'uri' => '/bca'],
        ['pattern' => '/bca/def/(:int)', 'keys' => ['id'], 'uri' => '/bca/ijh'],
        ['pattern' => '/bca/def/(:string)/(:int)', 'keys' => ['category', 'id'], 'uri' => '/bca/plk'],
    ],
];
$router = Router::getInstance()->setConfig($config);
$uri = '/abc/10';
$router->route($uri);
```