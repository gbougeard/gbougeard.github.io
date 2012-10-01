---

layout: post
title: Drag and Drop avec Primefaces
info : DnD JSF2 Primefaces
tags : [jsf, primefaces, tutorial]
published: true
---

{% include JB/setup %}

##ou comment créer un éditeur de formation de football

Depuis début 2011 je me suis mis à JSF2, si décrié par certain, et j'ai découvert [Primefaces](http://www.primefaces.org).
J'ai rapidement accroché car tout simplement je l'ai trouvé plus joli que les cadors du marchés (RichFaces, IceFaces, ..)
et puis aussi parce que les exemples du [showcase de Primefaces](http://www.primefaces.org/showcase-labs/ui/) m'ont beaucoup
interessé puisqu'ils sont souvent basés sur des données liées au  joueurs du FC Barcelone. Et vu que mon projet est lié au foot,
j'ai de suite eu des idées sur comment mettre en oeuvre

J'utilise la version de développement de Primefaces (3.0-RC1-SNAPSHOT à ce jour) et la version finale (3.0) est prévue pour très bientôt.
Mon environnement de développement est très standard : Netbeans 7, Glassfish 3.1.1, le tout sous linux. Coté base de données, après 
avoir tetsé du Derby j'utilise aussi MySql.

Rentrons dans le vif du sujet : le but est de créer un composant (bien que ce ne va pas être un composant JSF à proprement parler)
qui permettra de définir la position de joueurs afin de définir un schéma de jeu (les fameux 4-4-2, 4-3-3 que connaissent les footeux).

Pour cela j'ai défini 2 entités que l'on va persister (je ne vais pas m'attarder sur la partie JPA2-EJB3 dans cette article) :
La première; Formation, représente une formation (ou schéma tactique) :

<script src="https://gist.github.com/2568180.js"> </script>

La deuxième entité, FormationItem, représentera les différents postes d'une formation :

<script src="https://gist.github.com/2568203.js"> </script>

Passons aux choses sérieuses coté JSF. L'idée va être de positionner les différentes FormationItem selon une grille, c'est à ça
que sert la propriété FamFormation.coord, à représenter la case de la grille sur laquelle le FormationItem.numItem es positionné.

On ne va pas persister cette grille mais par contre on va avoir besoin d'un petit JSF Bean pour nous aider à faire cette représentation :

<script src="https://gist.github.com/2568216.js"> </script>

Ce bean va représenter chaque case de la grille que l'on va créer. Chaque case à un index et potentiellement un FormationItem.

Il ne reste plus qu'à créer un Controller et une page JSF.

Dans le controller on va avoir besoin de :

<script src="https://gist.github.com/2568226.js"> </script>

Coté JSF, on va utiliser le composant DataGrid de PrimeFaces. Il permet d'afficher les données d'une ArrayList sur différentes colonnes,
de paginer ou pas cette ArrayList, ... bref, il va nous permettre d'afficher notre grille.
Personnellement j'ai choisi une grille de 5*6 soit 30 cases. Mais on pourrait très bien affiner le positionnement des FormationItem
en augmentant le nombre de cases.
A l'affichage de notre page, il faut donc avoir construit une ArrayList de 30 CanvasFormationItem.

<script src="https://gist.github.com/2568230.js"> </script>

Basculons coté Web :
On va avoir besoin d'une petite fonction javascript (toute petite et c'est la seule).

<script src="https://gist.github.com/2568236.js"> </script>

D'abord un petit formulaire pour la Formation

<script src="https://gist.github.com/2568243.js"> </script>

et maintenant la fameuse DataGrid :

<script src="https://gist.github.com/2568253.js"> </script>

On a rajouté un listener sur l'action onDrop, il faut donc le coder dans le Controller. 
On va gérer les modifications de coords sur les FormationItem dans ce listener.
Puis en rafraichissant la DataGrid, ca sera automatiquement pris en compte.

<script src="https://gist.github.com/2568258.js"> </script>

Et voilà!
![une petite capture d'écran du résultat](http://gbougeard.github.com/images/formation.png)

