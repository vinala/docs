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

## Methods details

### Global

#### root
The `root()` shortcut to get Application root path

```php
echo root();

// result : ../
```