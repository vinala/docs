- [Views](#views)
	- [L'appel d'une view](#lappel-dune-view)
	- [Passer des valeurs à une view](#passer-des-valeurs-à-une-view)
	- [Stockage d'une view](#stockage-dune-view)
- [Smarty Templating](#smarty-templating)


## Views

Views constitués par HTML de votre application et le PHP dans une manière élégante qui manipule les contrôleurs de votre application, Les Vue sont stocker dans le répertoire `app/views`

Une vue simple pourrait ressembler à ceci :

	<!-- View stocké in app/views/hello.php -->
	<html>
		<body>
			<p> Hello <?php echo $nom ?> </p>
		</body>
	</html>

L'apelle de cette view ressembler à ceci :

	Route::get('/', function()
	{
		return View::make('hello', array('nom','Youssef'));
	});

### L'appel d'une view

En Fiesta nous appelant vue à l'aide de la methode `View::make()` La méthode qu'elle accepte un paramètre :

	View::make('le-nom-de-view');

vous pouvez également utiliser la Scoop fonction `view()`.

	view('le-nom-de-view');

Si la view que vous appeler est dans en répertoire sous le répertoire `app/views` L'appel de méthode doit être précédé par le nom de répertoire séparant par un point avec le nom du view comme ceci :

Voici la view qu'on va appeler, remarquer que la view est stockée dans le répertoire `app/views/home`

	<!-- View stocké in app/views/home/hello.php -->
	<html>
		<body>
			<p> Hello Visitor </p>
		</body>
	</html>

Alors l'appel de cette view doit être comme ça :

	View::make('home.hello');

### Passer des valeurs à une view

Pour passer des valeurs à une vue vous devez passer un `array()` de données contiennent les valeurs et leurs noms :

	View::make('home.hello',array('nom' => 'youssef'));

Voici la view :

	<!-- View stocké in app/views/home/hello.php -->
	<html>
		<body>
			<p> Hello <?php echo $nom ?> </p> <!-- Produit : Hello Youssef -->
		</body>
	</html>

### Stockage d'une view

Pour stocker une view dans un variable en utilisant la methode `View::get()`

	$view = View::get('hello', array('nom','Youssef'));
	echo $view;

## Smarty Templating

Fiesta Utilise Smarty.

Smarty est un moteur de template pour le langage PHP. Il est rapide et permet la gestion des caches.Il facilite la séparation entre la logique applicative et la présentation **(Source : Wikipedia)**

Tous les Fichier de Smarty doivent utiliser l'extention `.tpl.php`.

Pour plus des infos sur Smarty visiter le [site Web](http://www.smarty.net/) officiel de Smarty