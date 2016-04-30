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

The method `handle()` will be called once the user uses the command, you should put the script on the command inside this method

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
	protected $key = 'greeting';


	/**
	 * The console command description.
	 *
	 * @var string
	 */
	protected $description = 'say hello to the world';


	/**
	 * Execute the console command.
	 *
	 * @return mixed
	 */
	public function handle()
	{
		 $this->write("What's up!"); 
	}
}
```

