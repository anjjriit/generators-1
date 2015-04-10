# Laravel 5 File Generators

Custom Laravel 5 File Generators with config and publishable stubs.
This package can be used by anyone at any given time, but keep in mind that it is optimized for my personal custom workflow.
It may not suit your workflow, but please let me know if I can help optimize this package.

To be honest, the idea behind this package is not to suit everyone's needs.
I focus more on the stubs, so that anyone can publish the stubs and update them to suit your need.

## Commands
```bash
php artisan generate:publish-stubs
php artisan generate:migration
php artisan generate:migration:pivot
php artisan generate:seed
php artisan generate:model
php artisan generate:controller
php artisan generate:view
php artisan generate:view:index
php artisan generate:view:add_edit
php artisan generate:view:show
```

### Options *(in development)*
- It is available for `generate:controller`
`--plain` This will generate an empty file (only file structure, no code)
`--force` This will overide the existing file, if it exist

The migration and seed commands are from [Jeffrey Way's package](https://github.com/laracasts/Laravel-5-Generators-Extended)

## Installation

Update your project's `composer.json` file.

```js
"require-dev": {
	"bpocallaghan/generators": "dev-master"
}
```

Download latest code from github via `composer update`

```batch
composer update --dev
```

Include the service provider within `app/config/app.php`.

```php
'providers' => [
    'Bpocallaghan\Generators\GeneratorsServiceProvider',
];
```

Run `artisan` command to see the new commands.

```bash
php artisan
```

## Examples

- [Migrations](#migrations)
- [Pivot Tables](#pivot-tables)
- [Models](#models)
- [Database Seeders](#database-seeders)
- [Controllers](#controllers)
- [Views](#views)
- Resource *coming soon*
- [Configuration](#configuration)

*would like to add a --plain option for the commands*

### Migrations

```
php artisan generate:migration create_users_table
php artisan generate:migration create_posts_table --schema="title:string, body:text, slug:string:unique, published_at:date"
```

- [More](https://github.com/laracasts/Laravel-5-Generators-Extended#migrations-with-schema)

### Pivot Tables

```
php artisan generate:migration:pivot tags posts
```

- [More](https://github.com/laracasts/Laravel-5-Generators-Extended#pivot-tables)

### Models

```
php artisan generate:model Region
```

### Database Seeders

```
php artisan generate:seed users
```

- [More](https://github.com/laracasts/Laravel-5-Generators-Extended#database-seeders)

### Controllers

```
php artisan generate:controller RegionsController
php artisan generate:controller Geopgraphy\RegionsController
```
### Views

```
php artisan generate:view posts
php artisan generate:view posts.comments
php artisan generate:view:index posts
php artisan generate:view:index posts.comments
php artisan generate:view:add_edit posts
php artisan generate:view:add_edit posts.comments
php artisan generate:view:show posts
php artisan generate:view:show posts.comments
```

The `.` will be used as a folder seperator, `posts.comments` will be `/resources/views/posts/comments/`

`generate:views`
This will generate an empty view file.

`generate:views:index`
This will generate an `index.blade.php` file with index / list boilerplate code.

`generate:views:add_edit`
This will generate an `add_edit.blade.php` file with the create and edit form boilerplate code.

`generate:views:show`
This will generate a `show.blade.php` file with the show resource boilerplate code.

### Configuration

```
php artisan generate:publish-stubs
```

This will copy the config file to `/config/generators.php`.
Here you can change the default location of the stubs

This will also copy all the stubs to `/resources/stubs/`.
Here you can overide the skeleton of the files to suit your personal workflow / boilerplate code.
