# Views

[![alt return](https://gitlab.com/lighty/Art/raw/master/Resources/signs.png) Main Menu](https://gitlab.com/lighty/Docs/tree/3.3/#index)

- [Views](#views)
	- [Creating a view](#calling-a-view)
	- [Calling a view](#calling-a-view)
	- [Pass values to a view](#pass-values-to-a-view)
	- [Storing a view](#storing-a-view)
- [Smarty Templating](#smarty-templating)

## Views

Views consist of your application HTML and PHP in an elegant way that manipulates the controllers in your application, all views are stored in the directory `resources/views`.

A simple view might look like this:

```php
<!-- View stored in resources/views/hello.php -->
<html>
	<body>
		<p> Hello <?php echo $name ?> </p>
	</body>
</html>
```

The call of this view looks like this:

```php
Route::get('/', function()
{
	return View::make('hello', array('name','Youssef'));
});
```

### Creating a view

To create a view in Vinala, two ways, manualy and by Lumos.

For Lumos please check the [Lumos Creating Views](https://gitlab.com/lighty/Docs/blob/3.3/src/lumos.md#creating-views) part.

### Calling a view

In Vinala we calling the views using the method `View::make()` :

```php
return View::make('view-name');
```

In this example, we passed a parameter contains the file name of the view stored in views folder.

you can also use the `view()` helper.

```php
return view('view-name');
```

If the view you are calling is in a directory inside `resources/views`, The method call must be preceded by the directory name, separated by a point with the name of the view like this:

Here is the view that we will call, notice that the view is stored in the `resources/views/home`.

```php
<!-- View stored in resources/views/home/hello.php -->
<html>
	<body>
		<p> Hello Visitor </p>
	</body>
</html>
```

So the calling of this view must be like this:

```php
return View::make('home.hello');
```

### Pass values to a view

To pass values to a view you must pass in the second parameter of the method an array of data contains values and their names:

```php
View::make('home.hello',array('firstName' => 'Youssef','lastName' => 'Had'));
```

or you can use `with()` function passing array of data or two params the first is the name and the second is the value of the property:

```php
return view('home.hello')->with(['firstName' => 'Youssef','lastName' => 'Had']);
```
or 
```php
return view('home.hello')
	->with('firstName', 'Youssef')
	->with('lastName', 'Had');
```

Here is the view:

```php
<!-- View stored in resources/views/home/hello.php -->
<html>
	<body>
		<p> Hello <?php echo $firstName.' '.$lastName ?> </p> <!-- result : Hello Youssef Had -->
	</body>
</html>
```

### Storing a view (depracated)

For storing a view in a variable, use the method `View::get()`:

```php
$view = View::get('hello', array('name','Youssef'));
echo $view;
```

## Smarty Templating

Vinala uses Smarty.

Smarty is a web template system written in PHP. Smarty is primarily promoted as a tool for separation of concerns.[2] Smarty is intended to simplify compartmentalization, allowing the front-end of a web page to change separately from its back-end. Ideally, this lowers costs and minimizes the efforts associated with software maintenance. **(Source : Wikipedia)**

All views stored in `resources\views` and uses Smarty should have `.tpl.php` extension.

For more information on Smarty visit the official [website](http://www.smarty.net/) of Smarty.
