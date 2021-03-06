How to Install Redis at Laravel 5.5
====

Steps
----
- install redis di https://github.com/microsoftarchive/redis/releases/tag/win-3.2.100
- composer require predis/predis
- add .env
  - REDIS_HOST=127.0.0.1
  - REDIS_PASSWORD=null
  - REDIS_PORT=6379
  - REDIS_CLIENT=redis
  - REDIS_CACHE_DB=0

  - CACHE_DRIVER=redis

In Terminal, Type
----
- php artisan config:cache
- php artisan cache:clear

Add routes
----
- add routes/web.php
  - use Illuminate\Support\Facades\Redis;
  - Route::get("users_with_cache", "UserController@index");
  - Route::get("users_with_query", "UserController@getUser");

Install Package Debugger, for routing, JSON Response, Formatter Response (optional)
----
- composer require barryvdh/laravel-debugbar --dev
- add config/app.php
  - Barryvdh\Debugbar\ServiceProvider::class,
  - 'Debugbar' => Barryvdh\Debugbar\Facade::class,
- php artisan vendor:publish --provider="Barryvdh\Debugbar\ServiceProvider"

Fill table
----
- Fill User table with some data
- Type in browser like /*localhost/project/public/users_with_cache*/
- Type in browser like /*localhost/project/public/users_with_query*/
- Find the different of request time
