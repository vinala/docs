# Links

[![alt return](https://gitlab.com/lighty/Art/raw/master/Resources/signs.png) Main Menu](https://gitlab.com/lighty/Docs/tree/3.2/#index)

- [Introduction](#introduction)
- [Create link file](#create-link-file)
- [Using links](#using-links)
	- [Get link](#get-link)
	- [Set link while runtime](#set-link-while-runtime)

## Introduction

Vinala provides a new way to organise links whether from inside the application or outside in the internet also allows you to change links so easily by links surface

## Create link file

To create link file you should use **Lumos** command:

	$ php lumos make:link file_name

once the command executed, the link file will be stored in `app/link` path.

form more **Lumos** visite [here](https://gitlab.com/lighty/Docs/blob/3.3/src/lumos.md#lumos) 

by default the framework have the links files :

* `css` : for css files links
* `javascript` : for javascript files links
* `social` : for social media links
* `main` : for other links

## Using links
### Get link

To get link from links files you should use `get()` functions providing to it a key contains the file name dotted with the link index.

to get the facebook link from social file, the code look like this:

```php
<?php

$link = Link::get('social.facebook');
```

### Set link while runtime

You can set links while runtime by using `set()` functions providing to it two arguments , the first a key contains the file name dotted with the link index, the second is the link.

to set new link, we will use file even if it doesn't exists with an index:

```php
<?php

Link::set('something.google' , 'www.google.com');
```

