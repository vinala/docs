# Helpers

[![alt return](https://gitlab.com/lighty/Art/raw/master/Resources/signs.png) Main Menu](https://gitlab.com/lighty/Docs/tree/3.3/#index)

- [Introduction](#introduction)
- [Available Methods](#available-methods)
- [Methods details](#methods-details)
- [User Helpers](#user-helpers)

## 


----

## Introduction

Vinala includes a variety of global PHP helpers. Many of these functions are used by the framework itself; however, you are free to use them in your own applications if you find them convenient.

## Available Methods

- [Global](#global)
	- [root](#root)
	- [check](#check)
	- [path](#path)
	- [need](#need)
	- [needOnce](#needOnce)
	- [config](#config)
	- [view](#view)
	- [instance](#instance)
	- [statically](#statically)
- [Validation](#Validation)
	- [validate](#validate)
- [Surface](#Surface)
	- [cube](#cube)
	- [surface](#surface)
- [Debugging](#Debugging)
	- [d](#d)
	- [dc](#dc)
	- [trace](#trace)
	- [s](#s)
	- [map](#map)
	- [out](#out)
- [Screen](#Screen)
	- [clear](#clear)
	- [clean](#clean)
- [Exceptions](#Exceptions)
	- [abort](#abort)
	- [abort_if](#abort-if)
	- [exception_if](#exception-if)
	- [exception](#exception)
	- [log](#log)
- [Datetime](#Datetime)
	- [now](#now)
- [Arrays](#Arrays)
	- [array_get](#array-get)
	- [array_add](#array-add)
	- [array_collapse](#array-collapse)
	- [array_forget](#array-forget)
	- [array_has](#array-has)
	- [array_except](#array-except)
- [Strings](#Strings)
	- [trans / translate](#trans-/-translate)
	- [dot](#dot)
	- [e](#e)
	- [ee](#ee)
	- [str_contains](#str-contains)
- [Redirection](#Redirection)
	- [back](#back)
	- [redirect](#redirect)
- [HTTP](#HTTP)
	- [get](#get)
	- [post](#post)
	- [target](#target)
	- [call](#call)
	- [pass](#pass)
	- [request](#request)

## Methods Details

### Global

#### root
The `root()` shortcut returns a string contains the Application root path:

```php
<?php

echo root();

// result : ../
```

#### check
The `check()` shortcut return boolean for isset and not empty,
if the given variable is set and not empty the function will return true and vice versa

```php
<?php

$name = 'Youssef';

if(check($name)) // isset($name) && !empty($name)
{
	echo 'valide';
}
else
{
echo 'not valide';
}

// result : valide
```