
# Laravel 5.1 unixODBC driver

## Description
This package can be used in conjunction with unixodbc to connect to sql server from a Linux host server.

## Installation
This package is meant to work with an odbc.ini file. You will need to install and configure Microsoft unixodbc driver for Linux.
You can read how to do that here: http://jacksondean.net/connecting-to-microsoft-sql-server-with-php-from-centos-6-x7-x/

To Install this in your Laravel 5.1 app, open composer.json and add:

```json
 "require": {
        "barneshealthcare/odbc-driver": "dev-master"
    },
    "repositories" : [
        {
            "type": "git",
            "url": "git@github.com:BarnesHealthcare/odbc-driver.git"
        }
    ],
```

And then run:

`composer update`

Then, in your app/config directory, open app.php and find:

`Illuminate\Database\DatabaseServiceProvider::class`

And replace it with:

`Barneshc\UnixODBCDriver\UnixODBCServiceProvider::class`

Be sure to add the odbc driver with connection information to the `connections` array in `config/database.php` file like so:

```php
    'connections' => [
        'odbc' => [
            'driver' => 'odbc',
            'dsn' => 'MyDSNName',
            'grammar' => 'SQLServerGrammar',
            'username' => 'foo',
            'password' => 'bar',
            'database' => '',
        ],
    ],
```


