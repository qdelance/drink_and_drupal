D8
===

Création de type de contenu classique, lien vers taxonomie.
Création d'une vue page de listing
Création d'une vue bloc "best rated"
TODO : faire une commande Drush qui importe les films à partir du CSV...
TODO : tester thème bootstrap ?

Note : outils de dev D8 : http://seth.fischer.nz/drupal-8-development-tools.html

Symfony
=======

Création du projet avec Symfony
-------------------------------

symfony new <projet>

Framework complet : 
 * Layout de projet avec Bundles, dossier de config, bin/src/var/web
 * Routing, Event dispatcher
 * Forms
 * Twig (templating)
 * Doctrine
 * Monolog
 * Console
 * Webprofiler
 * Guard (accès et autorisations)
 * Environnements (prod/test/dev), caches et logs par environnements

SF3 (SF 2.8 avec le deprecated en moins)
----------------------------------------

Annotations pour le routing et plus YML
1 seul AppBundle
Installer Symfony
 * parameter.yml déjà généré (mais on retrouve les questions avec composer install)
 * remplace le composer require => va beaucoup plus vite


Silex
=====

Création du projet avec Silex
-----------------------------

composer require silex/silex

=> un dossier vendor et c'est tout !
Besoin de se faire une arbo (dossier "web", un .htaccess, un gitignore qui évite les commits de /vendor/, ajout du psr-0 dans composer.json pour pouvoir structurer son code plus tard en dehors du docroot)
Pas de logs, pas de cache, pas d'environnement
Pas de Twig, ni de Doctrine
Routing + Event Dispatcher + Injection de dépendance (Pimple)
Pas même de gestion élémentaire des erreurs autre que les Exceptions PHP (errors PHP non traitées)

Twig
----

composer require...
Activation du provider Twig (besoin du bridge, sinon pas de path(), ni URL()), OK pour Flash cependant via SessionProvider
asset() à remplacer par {{ app.request.basepath }}
Besoin d'activer un provider pour {{ render() }}
Pas de cache par défaut dans l'exemple de la doc

Form
----

Oblige à charger de nombreux composants Symfony (reload, error, composer require, reload, error...)

Doctrine
--------

Il y a un provider, mais qui ne fait que DBAL et pas intégration ORM : http://silex.sensiolabs.org/doc/providers/doctrine.html
Possible d'en chercher 1 third party : 
 * https://github.com/silexphp/Silex/wiki/Third-Party-ServiceProviders
 * https://packagist.org/packages/dflydev/doctrine-orm-service-provider
Pas de scafolding via console...
Utilisation pénible de fonctions bas niveau (lecture d'une date => chaîne à convertir soit même)

En contrepartie, vendor SF = 51 Mo versus vendor Silex = 4,6 Mo ... à l'init car à la fin on tombe à 32 Mo
Dans l'ensemble, le code des 2 projets Github (Symfony et Silex) reste proche, peu d'adaptation sur les templates Twig et le code des controllers
