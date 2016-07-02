# Atomium & Templating Engine

[![alt return](https://gitlab.com/lighty/Art/raw/master/Resources/signs.png) Main Menu](https://gitlab.com/lighty/Docs/tree/3.2/#index)

- [Introduction](#introduction)
- [Generate Atomium views](#generate-atomium-views)
- [Layout](#layout)
- [Displaying Data](#displaying-data)
- [PHP Tags](#php-tags)
- [Execute PHP function](#execute-php-function)
- [Comments](comments)
- [Control Structures](#control-structures)
	- [If statements](#if-statements)
	- [Loops](#loops)
- [Calling Sub-Views](#calling-sub-views)
- [Translator](#translator)
- [CSS and JS](#css-and-js)

----


## Introduction

Atomium is the simple, yet powerful template engine shipped with Lighty, it provides a way to make your code more clean and more elegent.

Unlike other popular PHP templating engines, Atomium does not restrict you from using plain PHP code in your views. All Atomium views are compiled into plain PHP code and cached until they are modified, meaning Atomium adds essentially zero overhead to your application. Atomium view files use the `.atom` file extension and are typically stored in the app/views directory.

## Generate Atomium views

Lighty provides many ways to generate Atomium Views using Lumos and Panel, besides you can create them manually !

To use Lumos you should execute `make:view` command passingin first parametre the name or path where view stored, and the importnat is to pass `--atom` option : 

```shell
php lumos make:view layouts.userLayout.personeView --atom
```

for more details see [Lumos Documentation](https://gitlab.com/lighty/Docs/blob/3.2/src/lumos.md#lumos).

## Layout

Basically atomium file is html file ,merged with PHP code, but instead of using PHP tags we use atomium functions :

```html

<!-- Stored in app/views/layouts/welcome.atom -->

<html>
    <head>
        @exec(Html::title());
    </head>
    <body>
        <div class="container">
            @lang('welcome');
        </div>

        {{"Youssef Had"}}
    </body>
</html>
```

## Displaying Data

To display data you just need to use `{{ }}` tags, for exemple to show `"Hello World !"` string you need to implement this code : 

```html
<!-- Stored in app/views/hello.atom -->

{{"Hello World !"}}
```

if we want to display the contents of the `name` variable like so:

```html
<!-- Stored in app/views/yourName.atom -->

{{$name}}
```

You may also echo the results of any PHP function :

```html
<!-- Stored in app/views/now.atom -->

{{time()}}
```

> **Note**: Atomium {{ }} statements are automatically sent through PHP's htmlentities function to prevent XSS attacks.

## PHP Tags

Atomium Unlike other popular PHP templating engines, it allow's you to use PHP tags `<?php ?>` whenever you want.

in fact, you can use `{{{ }}}` Atomium tags to execute PHP code :

```php
<!-- Stored in app/views/script.atom -->

{{{
	$name = "Youssef";
	$lastName ="Had" ;
	//
	echo $name." ".$lastName;
}}}
```

## Execute PHP function

of course, sometimes you should execute functions, whether Lighty functions or PHP functions, those functions don't return any value to show, they just execute some process, to do so you could use `@assign` functions :

```php
@assign(die("error"));
```


## Comments

Atomium allows you to define comments in your views. However, unlike HTML comments, Atomium comments are not included in the HTML returned by your application, comments could be one line or block of code :

```php
/// This is one line comment
```

```php
{// 
	That's block of code
//}
```



## Control Structures

In addition to displaying data, Atomium also provides convenient short-cuts for common PHP control structures, such as conditional statements and loops. These short-cuts provide a very clean way of working with PHP control structures.

### If statements

You may construct `if` statements using the `@if`, `@elseif`, `@else`, and `@endif` tags. These directives function identically to their PHP counterparts:

```php
@if($owner == "Youssef") : 
	Hello Youssef
@elseif($owner == "Ayoub") : 
	Hello Ayoub
@else : 
	Hello guest
@endif;
```

> **Note**: `@if`, `@elseif`, `@else` tags ends with `:` and `@endif` tag ends with `;`

### Loops

In addition to conditional statements, Atomium provides simple directives for working with PHP's supported loop structures. Again, each of these directives functions identically to their PHP counterparts.


`For` loop match `@for` tag:
```
@for($i = 0 ; $i < 10 ; $i++):
	The value is {{ $i }} 
@endfor;
```

`Foreach` loop match `@foreach` tag:
```
@foreach($persons as $key => $person):
	The person is {{ $person }} 
@endforeach;
```

`While` loop match `@while` tag:
```
@while($i < 10):
	The value is {{ $i }} 
	{{{ $i++; }}}
@endwhile;
```
to break loops you should just use `@break;` keyword;


## Calling Sub-Views

Of Course you can include view inside another view, Atomium allows you to easily do that by `@sub` function :

```php
<div>
	@sub("sections.slider");
</div>
```

You may also pass an array of extra data to the included view:

```php
@sub("folder.view", ["key" => $value]);
```

## Translator

Atomium also help you to call translator words so easily by using `@lang` function :

```php
<div>
	@lang("hello"); Youssef ! /// result is "Hola Youssef" in spanish
</div>
```

## CSS and JS

You could intgrate JS files and CSS files stored in `app/resources` in css and js folder by `@css` and `@js` function, without add file extension and especially without HTML `link` or `script` tags:

```php
<head>
	@css("base"); 
	/// the CSS file is base.css and stored in app/resources/css/base.css

	@js("base"); 
	/// the JS file is base.js and stored in app/resources/js/base.js
</head>
```
