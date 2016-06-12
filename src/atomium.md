## Atomium

Atomium is template engine shipped with Lighty

#### Comments

```php
{// 
	That's a comment
//}
```

```php
// This is one line comment
```

### Control Structures
#### Conditions
```php
@if($owner == "Youssef")
	true
@endfor
```

#### Loops

```php
@for($i = 0 ; $i < 10 ; $i++)
	The value is {{ $i }} 
@endfor
```


```php
@foreach($persons as $key => $person)
	The person is {{ $person }} 
@endforeach
```

```php
@while($i < 10)
	The value is {{ $i }} 
@endwhile
```