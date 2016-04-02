- [Routing](#routing)
	- [Routing GET](#routing-get)
		- [Routing GET Basic](#routing-get-basic)
		- [Routing GET with static parameters](#routing-get-with-static-parameters)
		- [Routing GET with dynamic parameters](#routing-g-with-dynamic-parameters)
- [Filters](#filters)
- [Routes of Controller](#routes-of-controller)

## Routing

All routes of the application are defined in the file `app/http/Routes.php`, the call of a route should be consist of URL and the function to execute if users request this URL.

### Routing GET

#### Routing GET Basic

A simple route declaration might look like this:

```php
Route::get('/', function()
{
	echo 'Hello World';
});
```
This route for HTTP Get method for empty HTTP request like this `www.exemple.com/`.

You can also use the Scope function  `get()`.

```php
get('/', function()
{
	echo 'Hello World';
});

#### Routing GET with static parameters

If we want to go to this URL `www.exemple.com/world/home` we take the request after the first slash 'world/home'.

```php
Route::get('world/home', function()
{
	echo 'Hello this is world and home';
});
```

#### Routing GET with dynamic parameters

Usually when you want to pass data in the url you use URLs like this `www.exemple.com/?fname=youssef&lname=had`.
In Fiesta you can use more simple way to pass data and get data from URL.

```php
Route::get('user/{fname}/{lname}', function($fname,$lname)
{
	echo "Hello $fname $lname"; <!-- result : Hello Youssef Had -->
});
```

You may define as many route parameters as required by your route:

```php
Route::get('post/{postID}/comment/{commentID}', function($postID,$commentID)
{
	//
});
```
## Filters

All filters of the application are defined in the file `app/http/Filters.php`.

filters are simply methods that run before the route request to check a condition. if the filter return true, then the route runs normally.

Here's a filter to allow website visitors to see the content only in Saturdays.

```php
Route::filter("just_saturday", function()
{
	if(date("D") != "Sat"){
	return false;
}
	else else true;
});
```
implementation of this filter is like that

```php
Route::get('/', array("just_saturday",function()
{
	echo "Hi! this is saturday";
}));
```

## Routes of Controller


