**THIS PACKAGE HASN'T BEEN RELEASED, DO NOT USE YET**

# Artisan Tinker in your browser

[![Latest Version on Packagist](https://img.shields.io/packagist/v/spatie/web-tinker.svg?style=flat-square)](https://packagist.org/packages/spatie/:package_name)
[![Build Status](https://img.shields.io/travis/spatie/web-tinker/master.svg?style=flat-square)](https://travis-ci.org/spatie/:package_name)
[![Quality Score](https://img.shields.io/scrutinizer/g/spatie/web-tinker.svg?style=flat-square)](https://scrutinizer-ci.com/g/spatie/:package_name)
[![Total Downloads](https://img.shields.io/packagist/dt/spatie/web-tinker.svg?style=flat-square)](https://packagist.org/packages/spatie/:package_name)

Artisan's tinker command is a great way to tinker with your application in the terminal. Unfortunately running a few lines of code, making edits, and copy/pasting code can be bothersome. Wouldn't it be great to tinker in the browser?

This package will add a route to your application where you can tinker to your heart's content.

![Screenshot of web tinker](TODO: add screenshot)

## 🚨 A word to the wise 🚨

This package can run arbritary code. Unless you know what you are doing, you should never install or use this in a production environment, or any environment where you handle real world data.

## Installation

You can install the package via composer:

```bash
composer require spatie/laravel-web-tinker --dev
```

Next, you must publish the assets from this package by running this command.

```bash
php artisan web-tinker:install
```

Optionally, you can publish the config file of the package.

```bash
php artisan vendor:publish --provider="Spatie\WebTinker\WebTinkerServiceProvider" --tag="config"
```

This is the content that will be published to `config/web-tinker.php`

```php
return [
    
    /*
     * The web tinker page will be available on this path.
     */
    'path' => '/tinker',

    /*
     * If light hurts you eyes, set this to true.
     */
    'dark_theme' => false,


    /*
     * By default this package will only run in local development.
     * Do not change this, unless you know what your are doing.
     */
    'enabled' => env('APP_ENV') === 'local',
];
```

## Usage

By default this package will only run in a local environment.

Visit `/tinker` in your local environment of you app to view the tinker page.


## Authorization

Should you want to run this in another environment (we do not recommend this), there are two steps you must perform.

1. You must register a `viewWebTinker` ability. A good place to do this is in the `AuthServiceProvider` that ships with Laravel.

```php
public function boot()
{
    $this->registerPolicies();

    Gate::define('viewWebTinker', function ($user = null) {
        // return true if access to web tinker is allowed
    });
}
```

2. You must set the `enabled` config variable in `web-tinker` to `true`.

### Testing

``` bash
composer test
```

### Changelog

Please see [CHANGELOG](CHANGELOG.md) for more information on what has changed recently.

## Contributing

Please see [CONTRIBUTING](CONTRIBUTING.md) for details.

### Security

If you discover any security related issues, please email freek@spatie.be instead of using the issue tracker.

## Postcardware

You're free to use this package, but if it makes it to your production environment we highly appreciate you sending us a postcard from your hometown, mentioning which of our package(s) you are using.

Our address is: Spatie, Samberstraat 69D, 2060 Antwerp, Belgium.

We publish all received postcards [on our company website](https://spatie.be/en/opensource/postcards).

## Credits

- [Freek Van der Herten](https://github.com/freekmurze)
- [Marcel Pociot](https://github.com/mpociot)
- [All Contributors](../../contributors)

## Support us

Spatie is a webdesign agency based in Antwerp, Belgium. You'll find an overview of all our open source projects [on our website](https://spatie.be/opensource).

Does your business depend on our contributions? Reach out and support us on [Patreon](https://www.patreon.com/spatie). 
All pledges will be dedicated to allocating workforce on maintenance and new awesome stuff.

## License

The MIT License (MIT). Please see [License File](LICENSE.md) for more information.
