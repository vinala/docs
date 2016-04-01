### CRUD (create, read, update, delete) 

#### Insert new data

To insert a new record in the database, simply create a new model instance, set attributes on the model, then use the `add()` method:

```php
<?php

use Fiesta\Core\MVC\Controller\Controller;

class ctrlPerson extends Controller
{

	/**
	 * Insert newly created resource in storage.
	 */

	public static function insert($firstName,$lastName)
	{
		$person = new Person;
		$person->firstName=$firstName;
		$person->lastName=$lastName;
		return $person->add();
	}
}

```

In this example, we use two parameters for first and last name and assign them to firstName and lastName attribute of Person model instance,then we call add method to insert the record into database table.