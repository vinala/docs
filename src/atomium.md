## Atomium

[![alt return](https://gitlab.com/lighty/Art/raw/master/Resources/signs.png) Main Menu](https://gitlab.com/lighty/Docs/tree/3.2/#index)

- [Introduction](#introduction)
- [Generate Atomium views](#generate-atomium-views)
- [Layout](#layout)
- [Displaying Data](#displaying-data)


#### Introduction

Atomium is the simple, yet powerful template engine shipped with Lighty, it provides a way to make your code more clean and more elegent.

Unlike other popular PHP templating engines, Atomium does not restrict you from using plain PHP code in your views. All Atomium views are compiled into plain PHP code and cached until they are modified, meaning Atomium adds essentially zero overhead to your application. Atomium view files use the `.atom` file extension and are typically stored in the app/views directory.

#### Generate Atomium views

Lighty provides many ways to generate Atomium Views using Lumos and Panel, besides you can create them manually !

To use Lumos you should execute `make:view` command passingin first parametre the name or path where view stored, and the importnat is to pass `--atom` option : 

```shell
php lumos make:view layouts.userLayout.personeView --atom
```

#### Layout

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

#### Displaying Data

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


#### Comments

Atomium allows you to define comments in your views. However, unlike HTML comments, Blade comments are not included in the HTML returned by your application, comments could be one line or block of code :

```php
/// This is one line comment
```

```php
{// 
	Thats is block of code
//}
```



### Control Structures
#### Conditions
```php
<?php

@if($owner == "Youssef")
	true
@endfor
```

#### Loops

```php
<?php

@for($i = 0 ; $i < 10 ; $i++)
	The value is {{ $i }} 
@endfor
```


```php
<?php

@foreach($persons as $key => $person)
	The person is {{ $person }} 
@endforeach
```

```php
<?php

@while($i < 10)
	The value is {{ $i }} 
@endwhile
```