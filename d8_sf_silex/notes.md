D8
===

TODO

Symfony
=======

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

Annotations pour le routing et plus YML
1 seul AppBundle
Installer Symfony
 * parameter.yml déjà généré (mais on retrouve les questions avec composer install)
 * remplace le composer require => va beaucoup plus vite


Silex
=====

composer require silex/silex

=> un dossier vendor et c'est tout !
Besoin de se faire une arbo (dossier "web", un gitignore qui évite les commits de /vendor/)
Pas de logs, pas de cache, pas d'environnement
Pas de Twig, ni de Doctrine
Routing + Event Dispatcher + Injection de dépendance (Pimple)
Pas même de gestion élémentaire des erreurs

En contrepartie, vendor SF = 60 Mo versus vendor Silex = 6 Mo
