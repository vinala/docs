## Atomium

Atomium is the simple, yet powerful template engine shipped with Lighty, it provides a way to make your code more clean and more elegent.

Unlike other popular PHP templating engines, Atomium does not restrict you from using plain PHP code in your views. All Atomium views are compiled into plain PHP code and cached until they are modified, meaning Atomium adds essentially zero overhead to your application. Atomium view files use the `.atom` file extension and are typically stored in the app/views directory.

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