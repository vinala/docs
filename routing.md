## Routing

Toutes les routes de l'application sont définie dans le fichier `app/http/Routes.php`, l'appelle d'une route doivent être consisté d'URL et la function de callback

### Routing GET Basique

	Route::get('/', function()
	{
		echo 'Hello World';
	});

### Routing POST Basique

Ce routes pour verifier si il y a des $_POST

	Route::post('/', function()
	{
		echo 'Hello World';
	});