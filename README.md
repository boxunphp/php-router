# router

FROM: nikic/fast-route

## Usage

两种配置方式

```php
$config = [
    ['method' => 'GET', 'route' => '/aaa[/{id:number}/{age}/ggg[/bbb[/ccc[/ddd]]]]', 'handler' => 'handlerA'],
    ['group' => '/bbb', 'routes' => [
        ['method' => 'GET', 'route' => '/uuu[/{id:number}/{age}/ggg[/bbb[/ccc[/ddd]]]]', 'handler' => 'handlerBU'],
        ['method' => 'GET', 'route' => '/iii[/{id:number}/{age}/ggg[/bbb[/ccc[/ddd]]]]', 'handler' => 'handlerBI'],
        ['method' => 'GET', 'route' => '/ooo[/{id:number}/{age}/ggg[/bbb[/ccc[/ddd]]]]', 'handler' => 'handlerBO'],
    ]],
    ['method' => 'GET', 'route' => '/ccc[/{id:number}]', 'handler' => 'handlerC'],
]; 
$router = new Router($config);
$uri = '/aaa/10000/18/ggg?a=AAA&b=BBB';
$router->dispatch($method, $uri);
```