# DumpRouter
Php routing class that handles get parameters and 'pretty urls' - Front controller pattern


application example: [findmyplace](https://github.com/mondial7/findmyplace)


## How to example

```php
// Don't forget to include the class!
require 'dump_router.php';	
```

### Optional settings

```php
// Optional
Dump_Router::setControllersExtension('.your_controller_extension'); // Default is ".php"

// Optional
Dump_Router::setDeaultController('not_found.php'); // Default is "404.php"
```


### Define routes

```php
// Second parameter is optional except for the home/landing
Dump_Router::route('/',[
'controller' => "landing"
]);

Dump_Router::route('about'); // Default controller name is the path segment name

Dump_Router::manyRoute(['about','login','register']); // Set as multiple routes as the command above

Dump_Router::route('shop', [
  'pretty_parameters' => ['category', 'product'] // Optional
]);

Dump_Router::route('product',[
  'controller' => "product_box" // Custom controller, to specify different controller name
])
```

### Define no routes --> paths that require normal behavoiur


```php
// http://example.com/app/###### will be loaded as normal url
Dump_Router::noRoute('app');

// Hint: you can do it with .htaccess buddy!
```

### Trigger Router

```php
// Second parameter is optional
Dump_Router::render($_SERVER['REQUEST_URI']);

Dump_Router::render($_SERVER['REQUEST_URI'], $controllers_directory_path); // Default dir is "./app/controllers/"
```


## Minimal example

```php
require 'dump_router.php';

Dump_Router::route('/',[
  'controller' => "landing"
]);

Dump_Router::render($_SERVER['REQUEST_URI']);
```


P.s. Do not forget to redirect all the request a single index.php ( [.htaccess](https://github.com/mondial7/DumpRouter/blob/master/.htaccess) )
