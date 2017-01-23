# Shortcuts

[![alt return](https://gitlab.com/lighty/Art/raw/master/Resources/signs.png) Main Menu](https://gitlab.com/lighty/Docs/tree/3.3/#index)

- [Introduction](#introduction)
- [Available Methods](#available-methods)


----

## Introduction

Vinala includes a variety of global "shortcuts" PHP functions. Many of these functions are used by the framework itself; however, you are free to use them in your own applications if you find them convenient.

## Available Methods

- [Global](#global)
	- [root](#root)
	- check
	- path
	- need
	- needOnce
	- config
	- view
	- instance
	- statically
- Validation
	- validate
- Surface
	- cube
	- surface
- Debugging
	- d
	- dc
	- trace
	- s
	- map
	- out
- Screen
	- clear
	- clean
- Exceptions
	- abort
	- abort_if
	- exception_if
	- exception
	- log
- Datetime
	- now
- Arrays
	- array_get
	- array_add
	- array_collapse
	- array_forget
	- array_has
	- array_except
- Strings
	- trans / translate
	- dot
	- e
	- ee
	- str_contains
- Redirection
	- back
	- redirect
- HTTP
	- get
	- post
	- target
	- call
	- pass
	- request

## Methods details

### Global

#### root
The `root()` shortcut to get Application root path

```php
echo root();

// ../
```