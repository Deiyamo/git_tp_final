# Partiel de Cloud

**https://app-pokedex-partiel.herokuapp.com**

## Instructions de fonctionnement

Pour faire fonctionner un application php sur Heroku, il faut simplement un fichier index.php ainsi qu'un fichier composer.json dans lequel on ne va mettre que les caractères suivant `{}`. C'est le minimum à mettre dans le fichier composer.json.
On peut bien évidemment mettre plsu de chose comme des require ainsi que la librairie  à utiliser mais, ici, notre fichier composer.json n'est composé que de ces accolades `{}`.



## Nos différents addons

### Heroku Postgres

* Insérer les credentials Heroku dans notre fichier de configuration `includes/config.php`, pour que la connection entre notre site et notre addon Postgres se fasse.

```
function connectDb(){

	try{
		$connect = new PDO('pgsql:host=ec2-99-81-238-134.eu-west-1.compute.amazonaws.com;dbname=db85kg3nu3e2ls;port=5432', 'wplhxaowzkcqlh', '1ea3908eb8c9aa9e9c907f147e2a699bfbf70e4acaa69b56e75ef27b1608cf78');
	}catch(Exception $e){
		die("Erreur SQL".$e->getMessage());
	}
	return $connect;
}
```
> visuel de notre fichier config.php

* Création de la base de données adéquate pour notre site.

on a dans un premier temps voulu utilisé DataGrip, mais on a eu qlq soucis avec la création de table (ca ne fonctionnait pas), donc on a opté pour la ligne de commande CLI pour créer une table et voir si elle s'affichait dans DataGrip :

```
$heroku pg:psql nom_de_la_bdd --app nom_de_l'app
CREATE TABLE test (name varchar);
```
>on a d'ailleurs dû installer postgreSQL sur notre pc pour que la commande fonctionne

Ca fonctionne, on a bien notre table test dnas DataGrip et à partir de ça, on peut la modifier comme on le souhaite.


### Librato.

* Installation très simple, choisir l'addon, cliquer sur le lien et on arrive dirrectement sur la plateforme de monitoring.


### Trevor.io

* Une fois installé, on doit choisir sur quelle app on veut le mettre en place et ensuite sur quelle bdd (au cas où on en ait plusieurs), et ensuite l'addon nous propose même un mini tuto pour apprendre à le faire fonctionner.


### Deploy Hooks

* Permet de garder une trace à chaque fois qu'un admin fait un push... on peut l'afficher avec la commande :
```
$heroku logs
```



>Vannier Timoté
