# keruald/database

This library offers a simple layer of abstraction for database operations.

## Configuration

To get a database instance, you need to pass configuration as an array.
The properties and values depend on the engine you want to use.

### MySQLi

|    Key   | Value                                |          |
|----------|--------------------------------------|:--------:|
| engine   | MySQLiEngine class reference         |          |
| host     | The MySQL hostname, e.g. "localhost" |          |
| username | The MySQL user to use for connection |          |
| password | The clear text password to use       |          |
| database | The default db to select for queries | optional |

For example:

```php
[
    'engine' => Keruald\Database\Engines\MySQLiEngine::class,
    'host' => 'localhost',
    'username' => 'app',
    'password' => 'someSecret',
    'database' => 'app',          // optional
]
```

## Legacy drivers

The mysql extension has been deprecated in PHP 5.7 and removed in PHP 7.
As such, this extension isn't supported anymore. You can use straightforwardly
replace 'MySQL' by 'MySQLi' as engine.

## Specialized drivers
### Blackhole

The blackhole engine does nothing and always returns `true` as query result.

This engine can be used for mocks:

  - directly, when database behavior does not matter
  - to build a mock by overriding behavior of query() or any other method

It can also be used with the loader, without any engine-specific configuration:

```php
[
    'engine' => Keruald\Database\Engines\BlackholeEngine::class,
]
```
