# Laravel Github Actions

Laravel Github Actions sets up PHP CS Fixer and Builds for your Laravel application. The builds will run tests set in `phpunit.xml`.

## Github Action

We run the Github actions on push requests and pull requests for the master branch only. You can change that

```yml
on:
  # Trigger the workflow on push or pull request,
  # but only for the main branch
  # https://docs.github.com/en/actions/reference/workflow-syntax-for-github-actions
  push:
    branches:
      - main
  pull_request:
    branches:
      - main
```

## PHP CS Fixer

The `.php-cs-fixer.dist.php` is the latest PHP CS Fixer configuration file and works with PHP CS Fixer 3.0. This configuration file you can adjust to your liking.

## Composer Packages

We have done a basic setup with the `composer.json`. You can however just copy the composer `require-dev` packages over to your composer file or add them with require

```sh
composer require brianium/paratest
composer require friendsofphp/php-cs-fixer
composer require orchestra/testbench
composer require phpunit/phpunit
composer require vimeo/psalm
```

## Scripts

Scripts do run test bench, PHP Unit and Psalm have been added to composer:

```php
"psalm": "vendor/bin/psalm",
"test": "./vendor/bin/testbench package:test --parallel --no-coverage",
"test-coverage": "vendor/bin/phpunit --coverage-html coverage"
```
