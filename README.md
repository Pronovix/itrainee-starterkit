# iTrainee starter kit

This repository is using Amazee's containers.

## Requirements

- Git
- Docker

## Install and start pygmy

> Only on Linux and macOS.

To install `pygmy`, run `gem install pygmy`.

This is only needed if you don't already have `pygmy` installed.

Start pygmy: `pygmy up`

## Setup the containers

1. Copy `docker-compose.unix.yml` or `docker-compose.windows.yml` as `docker-compose.override.yml`, depending on the
  host operating system.
1. Edit `docker-compose.yml` and replace all instances of **$PROJECT** with your preferred project name, e.g. **local**
1. Then run `docker-compose up --build -d`
1. `docker-compose run --rm cli sh -c 'composer install'`

## Setup the site

- Create your settings.local.php file:
  `cp web/sites/example.settings.local.php web/sites/default/settings.local.php`
- Create your settings.php file:
  `cp web/sites/default/default.settings.php web/sites/default/settings.php`
- Uncomment the inclusion of `settings.local.php` from the bottom of `web/sites/default/settings.php`.
- Add the following code to settings.local.php:

If you use MariaDB:

```php
$databases['default']['default'] = [
  'database' => 'drupal',
  'username' => 'drupal',
  'password' => 'drupal',
  'prefix' => '',
  'host' => 'mariadb',
  'port' => '3306',
  'namespace' => 'Drupal\\Core\\Database\\Driver\\mysql',
  'driver' => 'mysql',
];
```

If you use Postgres:

```php
$databases['default']['default'] = [
  'database' => 'drupal',
  'username' => 'drupal',
  'password' => 'drupal',
  'prefix' => '',
  'host' => 'postgres',
  'port' => '5432',
  'namespace' => 'Drupal\\Core\\Database\\Driver\\pgsql',
  'driver' => 'pgsql',
];
```

Add the following snippet as well.

```php
$settings['trusted_host_patterns'] = [
  '^$PROJECT.docker.amazee.io$',
  '^nginx.$PROJECT.docker.amazee.io$',
  '^nginx$',
  '^localhost$',
];


$config_directories['sync'] = '../config/sync';
```

After adding this snippet to `settings.local.php` look up the lagoon project name from
`docker-compose.yml` you've given previously (e.g. `local` in `local.docker.amazee.io`), and replace
`$PROJECT` with it.

## Usual commands

- `docker-compose run --rm cli sh`

  To run commands inside the container.

- `docker-compose up -d`

  Starts the containers.

- `docker-compose stop`

  Shuts down the containers (keeps the state).

- `docker-compose down`

  Destroys the containers (permanently deletes the state).
