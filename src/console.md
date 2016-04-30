# Console

[![alt return](https://raw.githubusercontent.com/fiesta-framework/Art/master/pics/signs.png) Main Menu](https://github.com/fiesta-framework/Docs/tree/3.1/#index)

- [Introduction](#introduction)
- [The framework commands](#info)
	- [Info](#info)
		- [Owner Infos](#owner-infos)
	- [Schema](#schema)
		- [Genarate Schema](#Genarate-Schema)
		- [Execute Schema](#execute-schema)
		- [Rollback Schema](#rollback-schema)
	- [Links](#links)

- [Creating user commands](#creating-user-commands)
	- [Generating commands](#generating-commands)
	- [Command structure](#command-structure)
	- [Input / Output](#input--output)
		- [Inputs](#inputs)


## Introduction

## The framework commands

### Info

	$ php pikia info

### Schema
#### Genarate Schema

	$ php pikia make:schema

#### Execute Schema

	$ php pikia exec:schema

#### Rollback Schema

	$ php pikia rollback:schema


## Creating user commands

### Generating commands

Pikia Framework allow's you to create your own console commands using the command `make:command` which will create command class in `app/console/commands`, the command require the name of the class and option for the key of the command:

	php pikia make:command newPersonCommand

In this exemple Pikia will create console command with the name of newPersonCommand and a key with the default value 'greeting'.

	php pikia make:command newPersonCommand --command=new:persone

In this exemple Pikia will create console command with the name of newPersonCommand and the key willhave the value 'new:persone'.

### Command Structure

Once the command created in `app/console/commands`, you should set **key** and **description** properties of the class, the description will be shown in `list` command.

The method `handle()` will be called once the user uses the command, you should put the script on the command inside this method :

```php
namespace Pikia\App\Console\Commands;

use Pikia\Kernel\Console\Command\Commands;

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

In this example, notice that the command is inside the namespace `Pikia\App\Console\Commands`, so any call of any class or method outside of this namespace should be preceded by `\` or you can use the namespace top of the file by using `use`.

The call of this command will be like that :

	$ php pikia say:hello youssef

Or like that : 

	$ php pikia say:hello youssef had



### Input / Output

#### Inputs

Any command created could be need some information from user, they called **inputs** it can be arguments or options, to define the inputs needed use `key` property on command class, The `key` property allows you to define the command name, arguments, and options.

```php
	/**
	 * The key of the console command.
	 *
	 * @var string
	 */
	protected $key = 'say:hello {name}';
```

In this example, the command name is **say:hello** and the argument is **name**

You may also make optional arguments : 
	
	email:send {user?}

