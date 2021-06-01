# Laravel Backblaze B2

[![Author](http://img.shields.io/badge/author-@marcandreappel-blue.svg?style=flat-square)](https://twitter.com/mhetreramesh)
[![Latest Version on Packagist](https://img.shields.io/packagist/v/marcandreappel/laravel-backblaze-b2.svg?style=flat-square)](https://packagist.org/packages/gliterd/laravel-backblaze-b2)
[![Software License][ico-license]](LICENSE.md)
[![Total Downloads](https://img.shields.io/packagist/dt/marcandreappel/laravel-backblaze-b2.svg?style=flat-square)](https://packagist.org/packages/gliterd/laravel-backblaze-b2)

Visit (https://secure.backblaze.com/b2_buckets.htm) and get your account id, application key.

The Laravel Backblaze B2 Storage Service Provider give provision for for laravel storage to use blackblaze as their storage system. It uses the [Backblaze B2 SDK](https://github.com/gliterd/backblaze-b2) & [Flysystem Adapter](https://github.com/gliterd/flysystem-backblaze) to communicate with the Backblaze b2 API.

## Install

Via Composer

``` bash
composer require marcandreappel/laravel-backblaze-b2
```
In your app.php config file add to the list of service providers:

``` php
\MarcAndreAppel\BackblazeB2\BackblazeB2ServiceProvider::class,
```
Add the following to your filesystems.php config file in the disks section:
```php
        'b2' => [
            'driver'         => 'b2',
            'accountId'      => env('B2_APPLICATION_KEY_ID'),
            'applicationKey' => env('B2_APPLICATION_KEY_SECRET'),
            'bucketName'     => env('B2_BUCKET_NAME'),
            'bucketId'       => env('B2_BUCKET_ID', ''),
        ],
```

## Using ApplicationKey instead of MasterKey
If you specify only the bucket name, your application key must be the master key.
However, if you specify both bucket name and bucket id, you do not need the master key and can use a single-bucket key.
Fetch your bucket id using the [b2 command line tool](https://www.backblaze.com/b2/docs/quick_command_line.html) `b2 get-bucket <bucketName>` 

## Usage

Just use it as you normally would use the Storage facade.

``` php
\Storage::disk('b2')->put('filename.txt', 'My important content');
```
and
``` php
\Storage::disk('b2')->get('filename.txt')
```

## Security

If you discover any security related issues, please use the issue tracker.
## Credits

- [Ramesh Mhetre][link-author]
- [All Contributors][link-contributors]

## License

The MIT License (MIT). Please see [License File](LICENSE.md) for more information.

[ico-version]: https://img.shields.io/packagist/v/gliterd/laravel-backblaze-b2.svg?style=flat-square
[ico-license]: https://img.shields.io/badge/license-MIT-brightgreen.svg?style=flat-square
[ico-downloads]: https://img.shields.io/packagist/dt/gliterd/laravel-backblaze-b2.svg?style=flat-square

[link-packagist]: https://packagist.org/packages/gliterd/laravel-backblaze-b2
[link-downloads]: https://packagist.org/packages/gliterd/laravel-backblaze-b2
[link-author]: https://github.com/marcandreappel
[link-contributors]: ../../contributors
