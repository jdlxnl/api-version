# Intro
Enables you to create an API version prefix, and make it available in your code.

After installation you can:

```php

use Jdlx\ApiVersion\Facade\Version;

// get current version number as int
Version::number();

// Do something only for request to the old api
if(Version::before(2)){

}

// Do something only for request to the new api
if(Version::from(2)){

}
```

## Installation
```
composer require jdlxnl/api-version
```

Register the Facade
```php
 // app/Http/kernel.php
 // Add api midleware

   protected $middlewareGroups = [
        'api' => [
            SetApiVersion::class,
          ],
    ];

// app/Config/app.php

  'providers' => [
        ...
        App\Library\ApiVersion\Provider\ApiVersionServiceProvider::class
    ]

 // change base path for swagger
 // app/Http/Documentation/Server


// Add the option to the router
// routes/api.php
$apiRoutes = function () {
    // define routes
};
Route::group(['prefix' => '{version?}', 'where' => ['version' => 'v[0-9]+']], $apiRoutes);

```


