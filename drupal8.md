
Drupal 8
========


Historique
----------

* Janvier 2007 = sortie de Drupal 7
* Plusieurs mois de retard
* Volonté d''améliorer le respect du planning pour Drupal 8
* Sélection d''en ensemble de priorités "les initiatives"


Les initiatives
---------------

* http://groups.drupal.org/drupal-initiatives
* http://drupal.org/community-initiatives/drupal-core
* Mettre en valeur le fait que des points initialement pas vraiment dans les priorités se sont ajoutés (Views in core/VDC, la reorg de modules, content authoring ?)
* TODO: A quel moment on parle de Spark = expérimentation pré D8 ?

Configuration Management Initiative/CMI
---------------------------------------

* Problème : Séparation nécessaire de la configuration et du contenu
* Introduction de ConfigEntities au niveau de l''API
* Sauvegardes YAML files dans <DRUPAL_ROOT>/sites/default/files/config_*
* Exemple
	$ cat <DRUPAL_ROOT>/sites/default/files/config_*/active/system.site.yml
	name: drupal8.corp.capgemini.com
	mail: quentin.delance@gmail.com
	slogan: ''
	page:
	  403: ''
	  404: ''
	  front: node
	admin_compact_mode: '0'
	weight_select_max: '100'
* Suppression de la table variables
* Ecran rudimentaire d''import
* TODO: Nom du dossier de conf, dossier active VS staging, vérifier fin purge table variables, prep démo ou on copie entre instances ?

Multilingual/D8MI
-----------------

* Problème : Internationaliser un site nécessite un grand nombre de modules, 2 approches sur Drupal 8 (node level VS field level)
* http://hojtsy.hu/was-d8mi 
* Schema archi avec les X modules remplacés D7 vs D8
* Choix possible de la langue durant l''installation
* TODO: Trouver le schéma de la réorg des modules (source ?) demo ! (jamais testé, vérifier au passage si on peut traduire le title ! ;)

WSCCI/whiskey
-------------

* Problème : Amélioration de la plateforme de développement sans réinventer la roue
* Intégration de Symfony 2 (routing, librairie HTTP, Twig)
* REST server (exit module Services ?)
* TODO: Comment faire une démo ?

SCOTCH
------

* Problème : Amélioration du système de mise en page, de la gestion des blocs, faire un panels dans le core et en mieux
* Plugins Symfony appliqués aux blocs (démo/impact sur admin des blocs ? )
* Modules Breakpoints (core) et Layout (pas core)
* Layout builder (sera sans doute sorti, jamais testé, démo possible, lié à un nouveau thème ? )

Mobile
------

* Problème : Traffic mobile a dépassé le traffic desktop, Drupal doit s''adapter
* Intégration HTML 5 (thème, composants de formulaires)
* Support du Responsive Web Design (barre d''outils, formulaires de contribution, administration par exemple dans Views)
* TODO: Screenshots

Views in Drupal Core/VDC
------------------------

* Problème : Intégrer un module utilisé par la plupart des installation Drupal, convertir aux normes core, sortir Drupal 8 avec un Views prêt
* Conversion de la home /node en vue
* Conversion future des interface d''admin (contenu, utilisateurs) ?
* Suppression de CTools
* Ajout d''une version simplifiée de Views Bulk Operations (VBO)
* Ajout de composants
* TODO: lister les composants + démo

Autres améliorations
--------------------

* Reorganisation de modules (suppressions Forum/Blog et ajouts Date/EntityRef/Views/Morceau VBO/CKEditor/i18n like)
* Adoption de Twig (statut ?)
* Nouveau theme (je ne sais pas ou cela en est)
* Content authoring update :

    CKEditor intégré (à la place de Aloha)
    Inline Editing
    Légères amélioration ergonomiques (sidebar (dé)pliante, bouton par défaut mis en valeur, dropdown save/publish)

Statut et conclusion
----------

* http://buytaert.net/code-freeze-and-thresholds => Tout n''est pas prêt pour Drupal 8
* Statut, ce qui devrait être OK ou pas (Layout ?)
* hooks Drupal vs API Symfony (plus loin en D9 ?)
* FileEntity dans core (?) mais toujours pas de media (arg)
* Impact sur le portage des modules (REX Simon ?), prérequis PHP, nvelle version Drush
* Modules déjà dispo pour D8 ?

Sources
-------

* http://fr.slideshare.net/swentel/the-state-of-drupal-8-drupalcamp-gent
* http://fr.slideshare.net/chipway/conference-drupagoradrupal8-20121109