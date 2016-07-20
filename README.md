# PHP extensions for Heroku

This repo maintains additional PHP extensions for the official [PHP Heroku buildpack](http://devcenter.heroku.com/articles/buildpacks).

## Usage

To use extensions provided by this repository, you only need to register it in your Heroku app:

```bash
$ heroku config:set HEROKU_PHP_PLATFORM_REPOSITORIES="https://incenteev-heroku-php-exts.s3.amazonaws.com/dist-cedar-14-stable/packages.json"
```

You can now require the extension in your composer.json.

## Supported extensions

Here is the list of extensions supported in this repository:

- amqp

## Maintenance

This repository is maintained by the Incenteev team.

Extensions will be added in it mainly based on the needs of Incenteev. However, community contributions are very welcome to add support for more extensions.
