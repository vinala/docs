[![alt hhhhhh](https://raw.githubusercontent.com/fiesta-framework/Art/master/pics/arrows.png) Return](https://github.com/fiesta-framework/Docs/tree/3.1/)

- [CRUD](#crud-create-read-update-delete)
	- [Insert new data](#insert-new-data)
	- [Read and get data](#read-and-get-data)

	

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

#### Read and get data

There are many ways to get data from database using primary key or other row value by where clause.

To get the data using the primary key, you can pass parameter contains a primary key value in model instance :

```php
<?php

use Fiesta\Core\MVC\Controller\Controller;

class ctrlPerson extends Controller
{

	/**
	 * Get the resource by id
	 */

	public static function show($id)
	{
		$person = new Person($id);
		return $person;
	}
}

```

In this example, we pass a parameter contains the primary key to show method and we pass it again to Person model instance, then we return the result
