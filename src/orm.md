# ORM (Object-Relational Mapping) and Database Access

[![alt return](https://gitlab.com/lighty/Art/raw/master/Resources/signs.png) Main Menu](https://gitlab.com/lighty/Docs/tree/3.2/#index)

- [Introduction](#introduction)
- [Quick Example](#quick-example)
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

use Lighty\Kernel\MVC\ORM;

class mdlPerson extends ORM
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

Of course when you work with database you will need to get data from many tables and make relations between tables, for this reason, Lighty provide in its ORM system a quite simple way to relate between tables, For example, an article may have many comments, and belong to an author. Lighty can managing all this by using four Relations types : hasOne, hasMany, belongsTo, and belongsToMany:

| Relationship | Relations Type | Example                             |
|--------------|------------------|-------------------------------------|
| One to one   | hasOne           | A user has one and only one profile |
| One to many  | hasMany          | A user can have multiple articles.  |
| many to one  | belongsTo        | Many articles belong to a user      |
| many to many | belongsToMany    | Tags belong to many articles        |

Relations are defined during a method named by the other part of relation of your table object. Methods matching the relations type allow you to define the modelss in your application. For example, a User model might be associated with one Car. To define this relationship, we place a car method on the User model. The car method should return the results of the hasOne method on the base ORM model class:

```php
<?php

use Lighty\Kernel\MVC\ORM;

class User extends ORM
{
	/**
	* Name of the DataTable
	*/
	public static $table='users';

	/**
     * Get the car record associated with the user.
     */
	public function car()
	{
		return $this->hasOne("Cars");
	}
}
```

ORM assumes that the foreign key should have a value matching the id (or the custom $primaryKey) column of the parent. In other words, ORM will look for the value of the user's id column in the user_id by concat $table proprity with `_id` string to get column of the Car record. For example User table has a foreign key of a primary key of Car table, both columns should have primary key table name with `_id` string like `cars_id`.

If you would like the relationship to use a value other than id, you may pass a second and third argument to the hasOne method specifying your custom key, th second one is the column in model table, the third one is the colmun of the related table :

```php
<?php
class User extends ORM
{
	public function car()
	{
		return $this->hasOne("Cars");
	}
}
```

Lighty uses PHP magic, so to get the car of the user 1 you should just call the function you add in model **without brackets** :

```php
<?php

$car = User::find(1)->car;
```

#### Relation hasOne

Let’s imagine that we have a Users Table with a hasOne relationship to an Phones Table.

First, your database tables need to be keyed correctly. For a hasOne relationship to work, one table has to contain a foreign key that points to a record in the other. In this case the Phones table will contain a field called phones_id. The basic pattern is `Table name + "_id" string`:

| Relation            | Normal Schema   |
|---------------------|-----------------|
| Users hasOne Phones | phones.users_id |
| Phones hasOne Users | users.phones_id |

> It is not mandatory to follow Lighty conventions, you can override the use of any foreignKey in your associations definitions. Nevertheless sticking to conventions will make your code less repetitive, easier to read and to maintain.

If we had the UsersTable and PhonesTable classes made and UsersTable hasOne Phones relation, we could make the relation with the following code:

```php
<?php

public function user()
{
	return $this->hasOne("Users");
}
```

so if you use your own keys definitions without follow Lighty conventions, use the following code:

```php
<?php

public function phone()
{
	return $this->hasOne("Phones", "primary-key-of-users-table", "foreign-key-of-user-in-phones-table");
}
```

Possible keys for hasOne relation arrays include:

* **className** : the class name of the table being associated to the current model. If you’re defining a ‘User hasOne Phone’ relationship, the className key should equal ‘Phone’.
