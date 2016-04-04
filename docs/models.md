[![alt return](https://raw.githubusercontent.com/fiesta-framework/Art/master/pics/signs.png) Main Menu](https://github.com/fiesta-framework/Docs/tree/3.1/)

- [CRUD](#crud-create-read-update-delete)
	- [Insert new data](#insert-new-data)
	- [Read and get data](#read-and-get-data)
	- [Update and edit data](#update-and-edit-data)
	- [Delete data](#delete-data)
	


	

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

#### Update and edit data

To update an exist record in the database, simply get a new model instance by primary key, set attributes on the model, then use the `edit()` method:

```php
<?php

use Fiesta\Core\MVC\Controller\Controller;

class ctrlPerson extends Controller
{

	/**
	 * Update the specified resource in storage.
	 */

	public static function insert($Id,$firstName,$lastName)
	{
		$person = new Person($Id);
		$person->firstName=$firstName;
		$person->lastName=$lastName;
		return $person->edit();
	}
}

```

In this example, we use three parameters, the first one is the primary key and second and third one for first and last name, first we get data by model instance by primary key, and assign other parameters to firstName and lastName attribute of Person model instance,then we call edit method to update the record in database table.

#### Delete data

To delete an exist record in the database, simply get a new model instance by primary key,  then use the `delete()` method of the model:

```php
<?php

use Fiesta\Core\MVC\Controller\Controller;

class ctrlPerson extends Controller
{
	/**
	 * Delete the specified resource in storage.
	 */

	public static function delete($id)
	{
		$person = new Person($id);
		return $person->delete();
	}
}

```

In this example, we pass a parameter contains the primary key to delete method and we pass it again to Person model instance, then we call delete method to remove the record from database.
