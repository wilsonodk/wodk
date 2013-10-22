# Wodk Library

A utility library intended to be used with the [Wodk Web App][] scaffolding.

+ [Wodk_DB][]
> A [MySQLi][] wrapper class with query formatting, table prefixing and "prepared" queries. 

+ [Wodk_Logger][]
> A very simple logger that writes to disk.

+ [Wodk_TwigExtensions][]
> A few [Twig][] filters that help with the [Wodk Web App][].


### Getting Started

In your `composer.json`:
```json
{
    "repositories": [
        {
            "type": "git",
            "url": "https://github.com/wilsonodk/wodk"
        }
    ],
    "require": {
        "wodk/wodk": "vX.Y.Z"
    }
}
```

In your application:
```php
// After installing with Composer, autoload the Wodk classes.
require_once 'vendor/autoload.php';
```


## Author

Wilson Wise

(c) 2012 Wilson Wise. All rights reserved.



[Wodk_DB]: https://github.com/wilsonodk/wodk/wiki/Wodk-DB
[Wodk_Logger]: https://github.com/wilsonodk/wodk/wiki/Wodk-Logger
[Wodk_TwigExtensions]: https://github.com/wilsonodk/wodk/wiki/Wodk-TwigExtensions
[MySQLi]: http://us1.php.net/manual/en/book.mysqli.php
[Twig]: http://twig.sensiolabs.org/
