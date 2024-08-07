## HERD

Native Laravel and PHP development environment for macOS

It provides everything that you need to get started with Laravel development. 

It ships with PHP, nginx, dnsmasq and Node.js.

---
### Download HERD
[Download](https://herd.laravel.com/)

Once downloaded, access herd in your applications.

Manage various `PHP` versions and run simultaneously.

---
### Using `laravel` binary command

Create a new project and follow all the defaults.
We will name it `example` but you can name it as you please!

```shell
cd ~
cd ~/Herd
laravel new example
```

As of Aug. 6th, 2024

| Question                                               | Answer         |
|--------------------------------------------------------|----------------|
| Would you like to install a starter kit?               | No starter kit |
| Which testing framework do you prefer?                 | Pest           |
| Would you like to initialize a Git repository?         | Yes            |
| Which database will your application use?              | SQLite         |
| Would you like to run the default database migrations? | Yes            |

### Test your app in the browser
In the browser put the name of your app and `.test` to view your app!
In this case that would be `example.test`

[Docs](https://herd.laravel.com/docs/1/getting-started/sites?ref=herd)

### Alternatives
You can use `Sail`, `Docker`, or any other app that enables the correct dependencies.

Previously used `homebrew`.