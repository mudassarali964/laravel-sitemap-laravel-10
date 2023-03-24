# Laravel Stripe Cashier - Laravel-10

<img width="1430" alt="Stripe_admin_dashboard" src="https://user-images.githubusercontent.com/55048197/224141687-f339bf49-a2d1-43f0-bf3d-8b8fc4cca61f.png">
<img width="1430" alt="stripe_all_plans" src="https://user-images.githubusercontent.com/55048197/224142319-ce162a15-5ed1-4fa1-9c16-294775690e47.png">
<img width="1430" alt="stripe_plans" src="https://user-images.githubusercontent.com/55048197/224142398-f8868629-0d6d-4e09-b89c-8f15cde5e80a.png">

## Installation

``` bash
# clone the repo
$ git clone https://github.com/mudassarali964/laravel-sitemap-laravel-10.git my-project

# go into app's directory
$ cd my-project

# install app's dependencies
$ composer install

```

### If you choice to use SQLite

``` bash

# create database
$ touch database/database.sqlite
```
Copy file ".env.example", and change its name to ".env".
Then in file ".env" replace this database configuration:
* DB_CONNECTION=mysql
* DB_HOST=127.0.0.1
* DB_PORT=3306
* DB_DATABASE=laravel_site_map
* DB_USERNAME=root
* DB_PASSWORD=

To this:

* DB_CONNECTION=sqlite
* DB_DATABASE=/path_to_your_project/database/database.sqlite

### If you choice to use PostgreSQL

1. Install PostgreSQL

2. Create user
``` bash
$ sudo -u postgres createuser --interactive
enter name of role to add: laravel
shall the new role be a superuser (y/n) n
shall the new role be allowed to create database (y/n) n
shall the new role be allowed to create more new roles (y/n) n
```
3. Set user password
``` bash
$ sudo -u postgres psql
postgres= ALTER USER laravel WITH ENCRYPTED PASSWORD 'password';
postgres= \q
```
4. Create database
``` bash
$ sudo -u postgres createdb laravel_site_map
```
5. Copy file ".env.example", and change its name to ".env".
   Then in file ".env" replace this database configuration:

* DB_CONNECTION=mysql
* DB_HOST=127.0.0.1
* DB_PORT=3306
* DB_DATABASE=laravel_site_map
* DB_USERNAME=root
* DB_PASSWORD=

To this:

* DB_CONNECTION=pgsql
* DB_HOST=127.0.0.1
* DB_PORT=5432
* DB_DATABASE=laravel_site_map
* DB_USERNAME=laravel
* DB_PASSWORD=password

### If you choice to use MySQL

Copy file ".env.example", and change its name to ".env".
Then in file ".env" complete this database configuration:
* DB_CONNECTION=mysql
* DB_HOST=127.0.0.1
* DB_PORT=3306
* DB_DATABASE=laravel_site_map
* DB_USERNAME=root
* DB_PASSWORD=

### Set APP_URL

> If your project url looks like: example.com/sub-folder
Then go to `my-project/.env`
And modify this line:

* APP_URL =

To make it look like this:

* APP_URL = http://example.com/sub-folder


### Next step

``` bash
# in your app directory
# generate laravel APP_KEY
$ php artisan key:generate

# generate some random post using tinker
$ php artisan tinker
$ App\Models\Post::factory()->count(30)->create()
$ exit

# run the command to generate our sitemap manually
$ php artisan sitemap:generate

# run database migration and seed
$ php artisan migrate:fresh --seed

# run the project
$ php artisan serve

http://127.0.0.1:8000/sitemap.xml

```

### spatie/laravel-sitemap Package
* Installation
``` bash
$ composer require spatie/laravel-sitemap
```
* Configuration Package - This will copy the default config to config/sitemap.php where you can edit it.
``` bash
$ php artisan vendor:publish --provider="Spatie\Sitemap\SitemapServiceProvider" --tag=sitemap-config
$ php artisan migrate
```
