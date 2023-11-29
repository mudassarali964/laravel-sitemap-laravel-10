# Automatically Generate Sitemap in Laravel - Laravel-10

<img width="1440" alt="image" src="https://github.com/mudassarali964/laravel-sitemap-laravel-10/assets/55048197/74fab60c-7e81-485f-b017-f4f244b817e0">

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
$ php artisan migrate --seed
```

### Sitemap working

File: App/Console/Commands/GenerateSitemap (sitemap generating code)
Run the following command to create a new sitemap urls:
``` bash
$ php artisan sitemap:generate
```

It should be create a new file as sitemap.xml in the public directory (public_path('sitemap.xml') => public/sitemap.xml)
And now we can easily access the post related urls as:

http://127.0.0.1:8000/post/{slug}
http://127.0.0.1:8000/post/525
http://127.0.0.1:8000/post/758
