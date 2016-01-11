- [Routing](#routing)
- [Routes de Controller](#routes-de-controller)

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

## Filters

Tous les filtres de l'application sont définie dans le fichier `app/http/Filters.php`

les filtres sont des méthodes que s'exécute avant la requête de route pour vérifier une condition. si le filtre est `true` alors le route s'exécute normalement

Voici un filtre pour que les visiteurs de site peuvent voire le contenu de site seulement dans les jours de samedi :

	Route::filter("just_samedi", function()
	{
		if(date("D") != "Sat"){
		return false;
	}
		else else true;
	});

l'implémentation de ce filtre est comme ça

	Route::get('/', array("just_samedi",function()
	{
		echo "Salut! c'est samedi";
	}));

## Routes de Controller

Vous pouvez déterminer un ensemble de routes vers les methodes statiques d'un Contrôler (index - show - add - ...)

Cet exemple on a créé un contrôleur client, le route de ce contrôleur est comme ça

	Route::resource('client', 'clientCntrl');
