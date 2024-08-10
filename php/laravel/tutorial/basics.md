# Basics of Laravel

---
This will be following the tutorial by Jeffrey Way: [here](https://laracasts.com/series/30-days-to-learn-laravel-11)

It will not be a step-by-step guide through the tutorial but rather well-documented 
notes to keep track of crucial information.

---

### Starting 
Start your app
```shell
cd ~/your-apps-directory
php artisan serve
```
>   INFO Server running on [http://127.0.0.1:8000].

Can also access your app with `your-app-name.test` in the browser.

### Artisan
Use artisan to run commands for your application.
See all available commands with:
```shell
php artisan
```

### Help
Use the argument `help` for any of the commands
Example:
```shell
php artisan help make:model
```

### Make
Use make to scaffold your project's models, command, factory, etc.
Example, this will make a model and add the migration
```shell
php artisan make:model -m Post
```

### Migrate
Look at the available commands above to see what you might need.
Often times a good reset and re-run does the trick! You will need to re-seed though
WARNING: Don't do this in production code unless you have your data saved!
```shell
php artisan migrate:refresh
```

### Tinker REPL
Play around with your app in the php/laravel console! 

```shell
php artisan tinker
```

---
### Composer
Composer is a package manager.

A common install will be the debug toolbar,
[GitHub](https://github.com/barryvdh/laravel-debugbar)

```shell
composer require barryvdh/laravel-debugbar --dev
```

Make sure you `.env` file is set up with `APP_DEBUG=true`

---
### Custom Commands
Write your own custom commands. 
Commands are typically stored in the `app/Console/Commands` directory


[Docs](https://laravel.com/docs/11.x/artisan)

---
### Auto Namespace
Laravel handles giving namespaces to all files.

It is controlled inside of `composer.json`. 
You will see `App\\` for the name located at `app/` path.
```json
{
  "autoload": {
    "psr-4": {
      "App\\": "app/"
    }
  }
}
```

You can then see files load name spaces starting with app.
```injectablephp
namespace App\Models;
```

This will auto import what we need versus requiring them yourself.

---
### Providers
Inside of `AppServiceProvider.php` we can configure our app.

The `boot()` function will finish after all of your dependencies are finished loading.
For example if we'd like to turn off all lazy loading for our queries.
```injectablephp
Model::preventLazyLoading();
```

### Vendor
Vendor refers to any package that we pulled from composer.

```shell
php artisan vender:publish
```

Publish means fI want to publish any relevant assets, routes, files, or views 
to my application folder so that I can manually control and edit them.

For example, we can see a component with tailwind customization for pagination links.
But how do we edit those?
We could publish `laravel-pagination` to allow for customization.
It will copy the files from the package to your directory.

We can also configure our Provider to switch defaults without editing the file by:
Inside of `boot()`:
```injectablephp

Paginator::useBootstrapFive();
```