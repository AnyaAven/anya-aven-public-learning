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

### Tinker
Play around with the php console! 

```shell
php artisan tinker
```

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