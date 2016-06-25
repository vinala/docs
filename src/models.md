# ORM (Object-Relational Mapping)

[![alt return](https://gitlab.com/lighty/Art/raw/master/Resources/signs.png) Main Menu](https://gitlab.com/lighty/Docs/tree/3.2/#index)

- [Management](#management)
	- [Creating Models](#creating-models)
- [CRUD](#crud-create-read-update-delete)
	- [Insert new data](#insert-new-data)
	- [Read and get data](#read-and-get-data)
	- [Update and edit data](#update-and-edit-data)
	- [Delete data](#delete-data)

----
> `Class` : Lighty\Kernel\MVC\Model

----

### Introduction

In Lighty working with data could be done by MVC structure, Lighty built-in ORM specializes in relational databases by creating objects, These objects we call them `models`, they provide access to collections of data. They allow you to save new records, modify/delete existing ones, it's like if Lighty create virtual copy of your database tables to use in your application, cleanly and quite easy, all models are stored in `app/models` folder.

Before we get started exploring the ORM, make sure your database connection is well configured.

### Quick Example

To get started you don’t have to write any code. If you’ve configured the connection between Lighty and your database in `config/database.php` file you can just start using the ORM. For example if we wanted to load some data from our persons table the model will be so :

```php
<?php

use Lighty\Kernel\MVC\Model\Model;

class mdlPerson extends Model
{
	//Name of the table in database
	public static $table='persons';
}
```
In these example the model class is `mdlPerson` while the data table is `persons` without prefix, so the instance of mdlPerson will have in its property the columns of data table:

```php
<?php

	$person = new mdlPerson(1);
	echo $person->firstName;
	echo $person->lastName;
```

### Creating Models

Lighty gives you two ways to create models using Lighty Panel or Lumos.

To create models using Lumos, you need to execute `make:model` command and pass to it three parameters `fileName`, `className`, `tableName`.
the first is the name of the file in models folder, the second is the class used in php script, Ex : mdlPersonne, the third id the name of data table in the database to work with. 

```shell
$ php lumos make:model cars mdlCars tbl_cars
```
in this exemple Lumos will create model and name the file 'cars' in models folder, and the class is 'mdlCars', the data table will be 'tbl_cars'.

for more details see [Lumos Documentation](https://gitlab.com/lighty/Docs/blob/3.2/src/lumos.md#lumos).
	
### CRUD (create, read, update, delete)

#### Insert new data

To insert a new record in the database, simply create a new model instance, set attributes on the model, then use the `add()` method:

```php
<?php

use Lighty\Core\MVC\Controller\Controller;

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

use Lighty\Core\MVC\Controller\Controller;

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

use Lighty\Core\MVC\Controller\Controller;

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

use Lighty\Core\MVC\Controller\Controller;

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

### Relations
