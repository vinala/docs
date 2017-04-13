# Routing

[![alt return](https://gitlab.com/lighty/Art/raw/master/Resources/signs.png) Main Menu](https://gitlab.com/lighty/Docs/tree/3.3/#index)

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
<?php
Route::get('/', function()
{
	echo 'Hello World';
});
```
This route for HTTP Get method for empty HTTP request like this `www.exemple.com/`.

You can also use the Scope function  `get()`.

```php 
<?php
get('/', function()
{
	echo 'Hello World';
});
```

> **Note**: Routes in Vinala doesn't starts with '/' unless if it's empty route

#### Routing GET with static parameters

If we want to go to this URL `www.exemple.com/world/home` we take the request after the first slash 'world/home'.

```php 
<?php
Route::get('world/home', function()
{
	echo 'Hello this is world and home';
});
```

#### Routing GET with dynamic parameters

Usually when you want to pass data in the url you use URLs like this `www.exemple.com/?fname=youssef&lname=had`.
In Lighty you can use more simple way to pass data and get data from URL.

```php 
<?php
Route::get('user/{fname}/{lname}', function($fname,$lname)
{
	echo "Hello $fname $lname"; <!-- result : Hello Youssef Had -->
});
```

You may define as many route parameters as required by your route:

```php 
<?php
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
<?php
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
<?php
Route::get('/', array("just_saturday",function()
{
	echo "Hi! this is saturday";
}));
```

## Routes of Controller

You can determine a set of routes to the static methods of a controller (index - show - add - ...)

In this example, we create a client controller calls clientCntrl, to access this controller we use the client route:

```php 
<?php
Route::resource('client', 'clientCntrl');
```

or 

```php 
<?php
resource('client', 'clientCntrl');
```

so if users request `www.exemple.com/index` the framework will run `clientCntrl::index()`.

<style type="text/css">
.tg  {border-collapse:collapse;border-spacing:0;}
.tg td{font-family:Arial, sans-serif;font-size:14px;padding:10px 5px;border-style:solid;border-width:1px;overflow:hidden;word-break:normal;}
.tg th{font-family:Arial, sans-serif;font-size:14px;font-weight:normal;padding:10px 5px;border-style:solid;border-width:1px;overflow:hidden;word-break:normal;}
.tg .tg-9hbo{font-weight:bold;vertical-align:top}
.tg .tg-yw4l{vertical-align:top}
</style>
<table class="tg" style="undefined;table-layout: fixed; width: 900px">
<colgroup>
<col style="width: 111px">
<col style="width: 223px">
<col style="width: 332px">
<col style="width: 234px">
</colgroup>
  <tr>
    <th class="tg-9hbo">Verb</th>
    <th class="tg-9hbo">URI</th>
    <th class="tg-9hbo">Method</th>
    <th class="tg-9hbo">Route</th>
  </tr>
  <tr>
    <td class="tg-yw4l">GET</td>
    <td class="tg-yw4l">/phones</td>
    <td class="tg-yw4l">index</td>
    <td class="tg-yw4l">phones/index</td>
  </tr>
  <tr>
    <td class="tg-yw4l">GET</td>
    <td class="tg-yw4l">/phones/show/{phone}</td>
    <td class="tg-yw4l">show</td>
    <td class="tg-yw4l">phones/show/{phone}</td>
  </tr>
  <tr>
    <td class="tg-yw4l">GET</td>
    <td class="tg-yw4l">/phones/add</td>
    <td class="tg-yw4l">add</td>
    <td class="tg-yw4l">phones/add</td>
  </tr>
  <tr>
    <td class="tg-yw4l">POST</td>
    <td class="tg-yw4l">/phones/insert</td>
    <td class="tg-yw4l">insert</td>
    <td class="tg-yw4l">phones/insert</td>
  </tr>
  <tr>
    <td class="tg-yw4l">GET</td>
    <td class="tg-yw4l">/phones/edit/{phone}</td>
    <td class="tg-yw4l">edit</td>
    <td class="tg-yw4l">phones/edit/{phone}</td>
  </tr>
  <tr>
    <td class="tg-yw4l">POST</td>
    <td class="tg-yw4l">/phones/update</td>
    <td class="tg-yw4l">update</td>
    <td class="tg-yw4l">phones/update</td>
  </tr>
  <tr>
    <td class="tg-yw4l">GET</td>
    <td class="tg-yw4l">/phones/delete/{phone}</td>
    <td class="tg-yw4l">remove</td>
    <td class="tg-yw4l">phones/delete/{phone}</td>
  </tr>
</table>


