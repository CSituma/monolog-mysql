## Laravel Monolog MySQL Handler.

MySQL driver for Laravel Monolog.

### Installation

~~~
composer require markhilton/monolog-mysql
~~~

You'll then need to run `composer install` to download it and have the autoloader updated.

Open up `config/app.php` and find the `providers` key.

~~~
'providers' => array(
    // ...
    Logger\Laravel\Provider\MonologMysqlHandlerServiceProvider::class,
);
~~~

Publish config using Laravel Artisan CLI.

~~~
php artisan vendor:publish
~~~

Migrate tables.

~~~
php artisan migrate
~~~

## Application Integration

In your application `bootstrap/app.php` add:

~~~php
$app->configureMonologUsing(function($monolog) use($app) {
    $monolog->pushHandler(new Logger\Monolog\Handler\MysqlHandler());
});
~~~

## Environment configuration

If you wish to change default table name to write the log into or database connection use following definitions in your .env file

DB_LOG_TABLE=logs
DB_LOG_CONNECTION=mysql

## Credits

Based on:

- [Pedro Fornaza] (https://github.com/pedrofornaza/monolog-mysql)
