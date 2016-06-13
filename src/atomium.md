## Atomium

Atomium is template engine shipped with Lighty, it provides a way to make your code more clean and more elegent,

#### Comments

```php
<?php

{// 
	That's a comment
//}
```

```php
<?php

// This is one line comment
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