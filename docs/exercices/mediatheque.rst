Gestion de médiathèque
======================

Présentation du thème
---------------------
Les exércices suivants ont pour thème la gestion de médiathèque étendu à la
gestion de médiacenter. Ces exercices proposent un fil directeur pour aborder les
différents aspects proposés en formation.

Le package `draft` contient un package `media` qui vous propose un ensemble de modules que vous
pouvez prendre comme le squelette de composants.

Le package `training.projects.mediamanager` propose une implémentation complète de cet exercice.

Une série est modélisée par le concept de *série* (`tvshow`)  ayant comme caractéristiques le nom
de la série. Chaque série contient des *saisons* (`seasons`) dont la caractéristiques est le numéro
de saison (int). Enfin, chaque saison contient une collection d'épisodes (`episode`) caractérisés
par leur numéro dans la saison et leur titre.

Modélisation objet
------------------

Dans un module dédié, écrivez la classe **Episode** permétant de gérer un épisode.

Ajoutez la classe **Season** permétant de gérer une saison. Le numéro de la saison est défini par
un attribut **number**. La classe doit avoir une méthode permétant d'ajouter un épisode et une
méthode **episodes()** retournant la liste des épisodes de la saison.

Ajoutez la classe **TvShow** qui possède un attribut **name**. La classe doit avoir une méthode
**add_episode(episode, season_number)** qui permet d'ajouter un épisode pour une saison et une
méthode **seasons()** qui retourne la liste des saisons.

Pour la suite, le module `mediamodel` propose une structure de base de ce modèle objet.

Exceptions : contrôle d'intégrité
---------------------------------

Il ne doit pas être possible d'ajouter une saison ou un épisode si un élément avec le même numéro
exite déjà. Ce cas doit être géré à l'aide des exceptions afin d'informer l'appelant de cette
situation.

Ajoutez la levée d'exceptions lorsque cela est pertinent.

Pour tester le mécanisme des esceptions, vous disposez du module
**training.poo.mediamanager.mediacli**. Recopiez ce module dans votre projet et ajoutez la capture
des exceptions afin que l'utilisateur ne voit pas de stack trace.

Regex : chargement des données
------------------------------

Les fichiers suivants correspondent au pattern reconnu par le médiacenter Plex ::

    Silicon_Valley-s01e01-Minimum_Viable_Product.avi
    Silicon_Valley-s01e02-The_Cap_Table.avi
    Silicon_Valley-s01e03-Articles_Of_Incorporation.avi
    Mr_Robot-s02e07-H4ndshake.mp4
    Mr_Robot-s02e09-Init5.mp4
    Breaking_Bad-s04e05-Shotgun.avi
    Breaking_Bad-s04e08-Hermanos.avi
    Supergirl-s01e01-Pilot.mkv

#. Ecrivez un script qui permet d'extraire le numéro de la saison et le numéro de l'épisode d'une
   séquence de ce type.
#. Améliorez ce code en extrayant les noms de séries, numéro de saison, numéro d'épisode dans la
   saison, titre de l'épisode et type de fichier (extension).
#. Placez ce code dans une fonction qui prend en paramètre une chaine de caractères qui doit
   correspondre à une des lignes précédentes et retourne une liste des éléments (titre série, numéro
   saison, numéro épisode, titre épisode et extension de fichier).

Base de données : Stockage des données
--------------------------------------

Pour le stockage et l'accès aux données, nous allons maintenant utiliser une base de données. Le
module media_db propose un objet qui va créer une base contenant une table qui stock les épisodes
et propose une méthode permétant de sauvegarder les épisodes.

#. Testez l'ajout d'épisodes par le shell interractif.
#. Ajoutez une méthode pour charger les épisodes et les afficher (la requête est écrite dans le
   module).
#. Ajoutez de quoi ne charger les données que d'une saison.

Le module `mediacli_db` est destiné à permettre une interraction avec l'utilisateur et des données
stockées en base.

#. Complétez ce module pour ajouter un épisode à l'aide du terminal et afficher la liste des
   épisodes dans le terminal.

TkInter : Interface homme-machine
---------------------------------

L'exercice consiste à créer une interface qui permet d'ajouter au système un épisode (titre et
numéro), d'afficher les détails d'un épisode et de supprimer un épisode.

#. Créez un formulaire permétant la saisie d'une chaine de caractères (le titre) et d'un nombre (le
   numéro de l'épisode).
#. Assurez-vous du bon fonctionnement en affichant la saisie dans le terminal lors de la valdation.
#. Les épisodes sont gérés dans une liste. À chaque ajout, afficher le contenu de la liste.
#. Assurez-vous qu'à chaque ajout, la liste soit ordonnée (par le numéro de l'épisode).
#. Ajoutez une ListBox qui contiendra la liste des épisodes.
#. Lorsque vous ajoutez un épisode, son titre doit apparaitre dans la ListBox.
#. Assurez-vous que lorsque vous ajoutez un épisode à la ListBox, l'ordre soit préservé.
#. Ajoutez un bouton qui permet d'afficher dans le formulaire les détails de l'épisode.
#. Ajoutez un bouton qui permet de supprimer un épisode.