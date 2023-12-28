# PHP CS Fixer Config

This repository provides a base configuration
for [`friendsofphp/php-cs-fixer`](http://github.com/FriendsOfPHP/PHP-CS-Fixer), which we use to verify and enforce a
single coding standard for PHP code.

### 📦 Requirements

The package requires PHP 8.0+ and follows the FIG standard PSR-4 to ensure a high level of interoperability between
shared PHP code.

### 📋 Features

- Defining your rules.
- Sharing your rules.
- Minimize risk rules.
- Scaffolding the repository.
- And much more!

### 🔧 Installation

Install the package with the below command:

```sh
composer require hitechnix/php-cs-fixer
```

### 📝 Usage

Now that the package is installed, create a configuration file called `.php_cs`, `.php_cs.php` or `.php-cs-fixer.php` at
the root of your project with the following contents:

```php
<?php

// Create a new CS Fixer Finder instance
$finder = PhpCsFixer\Finder::create()->in(__DIR__);

return Hitechnix\PhpCsFixer\Config::create()
    ->setFinder($finder);
```

Ignoring files and/or directories

- There will be certain situations where you might want to ignore certain files or directories to not be linted.
- Luckily, this is quite easy to achieve and all you need to do is to perform some calls on the CS Fixer Finder
  instance :)
- Here's a simple example where we ignore both files and directories:

```php
<?php

// Directories to not scan
$excludeDirs = [
    'vendor/',
];

// Files to not scan
$excludeFiles = [
    'config/app.php',
];

// Create a new CS Fixer Finder instance
$finder = PhpCsFixer\Finder::create()
    ->in(__DIR__)
    ->exclude($excludeDirs)
    ->ignoreDotFiles(true)
    ->ignoreVCS(true)
    ->filter(function (\SplFileInfo $file) use ($excludeFiles) {
        return ! in_array($file->getRelativePathName(), $excludeFiles);
    });

return Hitechnix\PhpCsFixer\Config::create()->setFinder($finder);
```

### 📨 Message

I hope you find this useful. If you have any questions, please create an issue.

### 🔐 Security

If you discover any security-related issues, please email support@hitechnix.com instead of using the issue tracker.

### 📖 License

This software is released under the [BSD 3-Clause][link-license] License.
Please see the [LICENSE](LICENSE) file or https://opensource.hitechnix.com/LICENSE.txt for more information.

[link-license]: https://opensource.org/license/bsd-3-clause
