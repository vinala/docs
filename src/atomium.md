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