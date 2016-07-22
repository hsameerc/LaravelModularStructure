# Laravel Modular Structure
## Documentation

* [Installation](#installation)
* [Getting started](#getting-started)
* [Usage](#usage)


<a name="installation"></a>
## Installation

The best way to install this package is through your terminal via Composer.

Add the following line to the `composer.json` file and fire `composer update`

```
"hsameerc/laravel-modular-structure": "dev-master"
```
Once this operation is complete, simply add the service provider to your project's `config/app.php`

#### Service Provider
```
Hsameerc\LaravelModularStructure\ModuleServiceProvider::class,
```

<a name="getting-started"></a>
## Getting started

The built in Artisan command `php artisan make:module name [--migration] [--translation]` generates a ready to use module in the `app/Modules` folder and a migration if necessary.

You can generate modules named with more than one word, like `foo-bar`.

This is how the generated module would look like:
```
laravel-project/
    app/
    |-- Modules/
        |-- FooBar/
            |-- Controllers/
                |-- FooBarController.php
            |-- Models/
                |-- FooBar.php
            |-- Views/
                |-- index.blade.php
            |-- Translations/
                |-- en/
                    |-- example.php
            |-- Requests/
                |-- FooBarRequest.php
            |-- routes.php
            |-- helper.php
                
```

<a name="usage"></a>
## Usage

The generated `RESTful Resource Controller` and the corresponding `routes.php` make it easy to dive in. In my example you would see the output from the `Modules/FooBar/Views/index.blade.php` when you open `laravel-project:8000/foo-bar` in your browser.


#### Disable modules
In case you want to disable one ore more modules, you can add a `modules.php` into your projects `app/config` folder. This file should return an array with the module names that should be **loaded**.
F.a:
```
return [
    'enable' => array(
        "customer",
        "jobs",
        "reporting",
    ),
];
```
In this case LaravelModularStructure would only load this three modules `customer` `jobs` `reporting`. Every other module in the `app/Modules` folder would not be loaded.

Laravel Modular Structure will load all modules if there is no modules.php file in the config folder.

You have to follow the `upper camel case` name convention for the module folder. If you had a `Modules/foo` folder you have to rename it to `Modules/Foo`. 

Also there are changes in the `app/config/modules.php` file. Now you have to return an array with the key `enable` instead of `list`.



## License

Laravel Modular Structure is licensed under the terms of the [MIT License](http://opensource.org/licenses/MIT)
(See LICENSE file for details).
