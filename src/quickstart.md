# Quick Start

[![alt return](https://gitlab.com/lighty/Art/raw/master/Resources/signs.png) Main Menu](https://gitlab.com/lighty/Docs/tree/3.2/#index)

- [Installation](#installation)
	- [Install Composer](#install-composer)
	- [Install Lighty](#install-fiesta)
- [Apache](#apache)
- [Lighty Requirements](#fiesta-requirements)
- [Documentation](#documentation)
- [Development](#development)
- [Versions and Changelog](#versions-and-changelog)
- [Licence](#licence)

## Lighty

Lighty, a PHP Framework for web developers

### Installation

#### Install Composer

Lighty uses `Composer`, You can use Composer  to install Lighty and its dependencies.

First, download and install [Composer installer](https://getcomposer.org/)

#### Install Lighty

You can install Lighty via [Composer](https://getcomposer.org/) by running the command of Composer `create-project` in your terminal:

	composer create-project fiesta/fiesta projet_name --prefer-dist


###  Apache

Lighty comes with `.htaccess` file that uses URL rewriting, if you use Apache, Be sure you have enabled the extension `mod_rewrite`


### Lighty Requirements

Lighty has some system requirements:
* PHP >= 5.5
* Enabling The mod_rewrite Apache extension


### Documentation

We are working on Lighty documentation for every release version, you can take look or update the documentation of next release [here](https://gitlab.com/lighty/Docs/tree/3.2)


### Development

Lighty is open to the contributions of developers, the current released version of Lighty is `3.1` . However developers may instead opt to use the next beta version in [dev](https://gitlab.com/lighty/framework/tree/dev) branch aliased to `3.x-dev`.


### Versions and Changelog

you can find all Lighty releases [here](https://gitlab.com/lighty/framework/tags) also the change log [here](https://gitlab.com/lighty/framework/blob/dev/changes.md)


### Licence

The Lighty framework is open-sourced software licensed under the [MIT license](http://opensource.org/licenses/MIT)
