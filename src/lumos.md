# Lumos

[![alt return](https://gitlab.com/lighty/Art/raw/master/Resources/signs.png) Main Menu](https://gitlab.com/lighty/Docs/tree/3.3/#index)

- [Introduction](#introduction)
- [The framework commands](#info)
	- [Info](#info)
		- [Owner Infos](#owner-infos)
	- [Database](#database)
		- [Export Database](#export-database)
	- [Schema](#schema)
		- [Genarate Schema](#Genarate-Schema)
		- [Execute Schema](#execute-schema)
		- [Rollback Schema](#rollback-schema)
	- [Links](#links)

- [Creating user commands](#creating-user-commands)
	- [Generating commands](#generating-commands)
	- [Command structure](#command-structure)
	- [Shortcut Syntax](#shortcut-syntax)
	- [Input / Output](#input--output)
		- [Inputs](#inputs)
			- [Retrieving inputs](#retrieving-inputs)
		- [Output](#output)
			- [Writing in console](#writing-in-console)
			- [Display Table](#display-table)
	- [Question Helper](#question-helper)
		- [Asking the user for confirmation](#asking-the-user-for-confirmation)
		- [Asking the user for information](#asking-the-user-for-information)
		- [Asking the user for information with a list of choices](#asking-the-user-for-information-with-a-list-of-choices)
		- [Asking the user for hidden information](#asking-the-user-for-hidden-information)
		
## Introduction

Lumos (named after Harry Potter spell) is a command-lien interface shipped with Lighty, Lumos can create any of Lighty’s basic ingredients for your use while developing your application. It is driven by the powerful Symfony Console component. To view a list of all available Lumos commands, you may use the `list` command:
```shell
$ php lumos list
```	

## The framework commands

### Info

	$ php lumos info

### Database
#### Export Database
Lighty gives you the possibility to export database (structure and data) whenever you want.

Using Lumos command `save:database` : 
```shell
$ php lumos save:database
```
Lighty will generate sql file contains tables structure and data in `/database/backup` folder with name of timestamp.

### Schema
#### Genarate Schema

	$ php lumos make:schema

#### Execute Schema

	$ php lumos exec:schema

#### Rollback Schema

	$ php lumos rollback:schema


## Creating user commands

### Generating commands

Lighty Framework allow's you to create your own Lumos commands using the command `make:command` which will create command class in `app/console/commands`, the command require the name of the class and option for the key of the command:

```shell
php lumos make:command newPersonCommand
```

In this exemple Lighty will create Lumos command with the name of newPersonCommand and a key with the default value 'greeting'.

```shell
php lumos make:command newPersonCommand --command=new:persone
```

In this exemple Lighty will create Lumos command with the name of newPersonCommand and the key willhave the value 'new:persone'.

### Command Structure

Once the command created in `app/console/commands`, you should set **key** and **description** properties of the class, the description will be shown in `list` command.

The method `handle()` will be called once the user uses the command, you should put the script on the command inside this method :

```php
<?php 

namespace Lighty\App\Console\Commands;

use Lighty\Kernel\Console\Command\Commands;

class newCommand extends Commands
{
	
	/**
	 * The key of the console command.
	 *
	 * @var string
	 */
	protected $key = 'say:hello {name} {nickname?}';


	/**
	 * The console command description.
	 *
	 * @var string
	 */
	protected $description = 'say hello to someone';


	/**
	 * Execute the console command.
	 *
	 * @return mixed
	 */
	public function handle()
	{
		$name = $this->argument("name");
		$nickname = $this->argument("nickname");
		//
		$name = \Strings::firstUpper($name);
		$nickname = \Strings::firstUpper($nickname);
		//
		$this->write("Hello ".$name." ".$nickname); 
	}
}
```

In this example, notice that the command is inside the namespace `Lighty\App\Console\Commands`, so any call of any class or method outside of this namespace should be preceded by `\` sign or you can use the namespace top of the file by using `use`.

The call of this command will be like that :
```shell
$ php lumos say:hello youssef
```

Or like that : 
```shell
$ php lumos say:hello youssef had
```

### Shortcut Syntax

You do not have to type out the full command names. You can just type the shortest **unambiguous** name to run a command. So if there are non-clashing commands, then you can run **help** like this:
```shell
$ php lumos h
```

If you have commands using : to namespace commands then you just have to type the shortest unambiguous text for each part. If you have created the say:hello as shown in lumos documentation then you can run it with:
```shell
$ php lumos s:h Youssef
```

If you enter a short command that's ambiguous (there are more than one command that match), then no command will be run and some suggestions of the possible commands to choose from will be output.


### Input / Output

#### Inputs

Any command created could be need some information from user, they called **inputs** it can be arguments or options, to define the inputs needed use `key` property on command class, The `key` property allows you to define the command name, arguments, and options.

```php
<?php 

/**
 * The key of the console command.
 *
 * @var string
 */
protected $key = 'say:hello {name}';
```

In this example, the command name is **say:hello** and the argument is **name**

You may also make optional arguments : 

```php
<?php 

protected $key = 'say:hello {user?}';
```

Besides arguments, Lighty support another type of inputs, Options are prefixed by `--` like this :

```php
<?php 

protected $key = 'say:hello {user} {--man}';
```

In this example, the --man option may be specified when calling the Lumos command. If the --man option is passed, the value of the option will be true. Otherwise, the value will be false:

	$ php lumos say:hello youssef --man

You may also specify that the option should be assigned a value by the user, to do that you should make after the option `=` sign :

```php
<?php 

protected $key = 'say:hello {name} {--sex=}';
```

In this example, the user may pass a value for the option like so:
```shell
php lumos say:hello katherine --sex=women
```

You may also assign default values to options:

```php
<?php 

protected $key = 'say:hello {name} {--sex=men}';
```

You may give a descriptions to input arguments and options by separating the parameter from the description using a colon between two spaces ` : `

```php
<?php 

protected $key = 'say:hello {name : The first name} {nickName? : The last name} {--sex : The sex of the person}';
```

##### Retrieving inputs

While your command is executing, you will obviously need to access the values for the arguments and options accepted by your command. for that, you may use the `argument` and `option` methods:

To retrieve the value of an argument, use the `argument()` method:

```php
<?php 

/**
 * Execute the console command.
 *
 * @return mixed
 */
public function handle()
{
	$name = $this->argument("name");
}
```

Options may be retrieved just as easily as arguments using the `option()` method:

```php
<?php 

/**
 * Execute the console command.
 *
 * @return mixed
 */
public function handle()
{
	$day = $this->option("day");
}
```

#### Output

Before use Lumos you should specify your terminal, whether you use the cmd Windows terminal or the bash UNIX terminal, 
this has important influence into the output type.

To do so, you may edit the `terminal` property inside the file `config/console`, and set **cmd** for Windows cmd or **bash**.

##### Writing in console

To send output to the console, use the `write`, `line`, `info`, `comment`, `question` and `error` methods. Each of these methods will use the appropriate ANSI colors for their purpose.

To write in the same line use the method `write()`, to write in new line use the method `line()`:

```php
<?php 

/**
 * Execute the console command.
 *
 * @return mixed
 */
public function handle()
{
	// Write in new line...
	$this->line("this is new line");

	// Write in same line...
	$this->write("this is same line");
}
```

Besides these methods, you can display info and comments questions and errors, these methods change the color of the output:

```php
<?php 

/**
 * Execute the console command.
 *
 * @return mixed
 */
public function handle()
{
	// display in green
	$this->info("this is info");

	// display in yellow
	$this->comment("this is comment");

	// display in cyan
	$this->question("this is question");

	// display in red
	$this->error("this is error");
}
```
##### Display Table

The `table` method makes it easy to correctly format multiple rows / columns of data. Just pass in the headers and rows to the method. The width and height will be dynamically calculated based on the given data :

```php
<?php 

public function handle()
{
	$this->table( 
		['Name','Age','Country'],
        [
            ['Youssef', '27', 'Sweden'],
            ['Ayoub', '19', 'Morocco']
        ]
	);
}
```


### Question Helper

Lumos allows you to get information, passwords, response of questions, while the command executing.

#### Asking the user for confirmation

Suppose you want to confirm an action before actually executing it, `confirm` method will help you this :

```php
<?php 

/**
 * Execute the console command.
 *
 * @return mixed
 */
public function handle()
{
	// simple confirmation
	$ok = $this->confirm("Are you sure ? [y/n]");

	// confirmation with default value of false
	$ok = $this->confirm("Are you sure ? [y/n]" , false);
}

```

In this example, **confirm()** method will return true if user tape 'y' or 'yes' else 'n' or 'no' will return false, otherwise you can give default answer if user ignore the confirmation by passing true or false in second parameter.

#### Asking the user for information

You can also ask a question with more than a simple yes/no answer. For instance, if you want to know a
user name, you can add this to your command:

```php
<?php 

/**
 * Execute the console command.
 *
 * @return mixed
 */
public function handle()
{
	// simple question
	$name = $this->ask("What's your name ?");

	// question with default value of Joe
	$name = $this->ask("What's your name ?" , "Youssef");
}
```

In this example, **ask()** method will return the name of user, otherwise you can give default answer if user ignore the question by passing a name in second parameter.

#### Asking the user for information with a list of choices

If you have a predefined set of answers the user can choose from, you could use a `choice` method which
makes sure that the user can only enter a valid string from a predefined list:

```php
<?php 

/**
 * Execute the console command.
 *
 * @return mixed
 */
public function handle()
{
	$color = $this->choice("What's your favorite color ?" , ['blue' , 'red' , 'green' , 'yellow']);
}
```

#### Asking the user for hidden information

The `hidden` method is similar to ask, but the user's input will not be visible to them as they type in the console. This method is useful when asking for sensitive information such as a password : 

```php
<?php 

/**
 * Execute the console command.
 *
 * @return mixed
 */
public function handle()
{
	$color = $this->hidden("Please enter your password');
}
```