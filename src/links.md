# Links

## Introduction

Vinala provides a new way to organise links whether from inside the application or outside in the internet also allows you to change links so easily by links surface

## Create link file

To create link file you should use **Lumos** command:

	$ php lumos make:link file_name

once the command executed, the link file will be stored in `app/link` path.
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
$link = Link::get('social.facebook');
```

