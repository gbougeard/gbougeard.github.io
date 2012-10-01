---

layout: post
title: Devoxxfr et Jenkins User Conference
info : Premières conférences
tags : [jenkins, devoxx, jug]
published: true
---

##et dire qu'il y a deux ans je ne savais pas ce qu'était un JUG...

Avant de rentrer dans le vif du sujet et de faire un long compte-rendu de mes toutes premières conférences, je suis
obligé de parler un peu de mon parcours.   
J'ai fait mes premiers en Java en 1998 à l'IUT info de Montpellier. J'ai mis 10 ans avant d'en refaire.   
Entre temps, j'ai commencé ma vie professionnelle en 2001 à Paris avec du client lourd windows (C++, MFC), des bases Oracle,
puis du PL/SQL. Après 4 ans, retour en province à Toulouse avec une étiquette "développeur PL/SQL" (dur à s'en défaire
quand on est dans une grosse SSII). Après donc 3 ans à ronger mon frein, à découvrir ExtJS, à s'initier au web avec un peu de PHP,
je retrouve enfin Java et plus partculièrement GWT. Il y a maintenant presque 2 ans, je débarque en région PACA, à Aubagne (connue
mondialement pour ses santons, Marcel Pagnol et sa légion).   
Autant dire que je ne croulais pas trop sous le travail et me taper 100 bornes par jour (les SSII sont concentrées du coté d'Aix)
pour rien faire, j'occupe mon temps à faire de la veille. Je découvre alors [les castcodeurs](http://lescastcodeurs.com/), ce qu'est un JUG et qu'en fait
une énorme communauté Java existe. Je plonge dans le livre d'[Antonio](https://twitter.com/#!/agoncal) et tombe amoureux de Java EE 6, délaisse GXT pour JSF2
et en particulier Primefaces.   
On essaye de m'occuper en me demandant pour une avant-vente de me renseigner sur l'intégration continue. Je tombe des nues.
Mais pourquoi on en a jamais fait sur mes anciens projets?! On aurait peut-etre pas consommé le double que prévu!   
Bref, je me rends compte que dans ces fameuses grosses boites, personne ne sait ce qu'est qu'un JUG, ne fait vraiment de veille...
A cela on m'annonce que l'agence veut se focaliser sur Sharepoint et Cobol... je décide de changer d'air.   
Depuis maintenant presqu'un an je suis dans une petite structure (< 50 personnes). A la base "Référent SQL", je suis plutôt
"Integration manager". J'ai fait une migration de CVS vers Git, mis en place Jenkins pour faire de l'intégration continue (plus de 300
jobs créés), ...   
Et je vais régulièrement au MarsJug, je ne loupe quasiment aucune session.

Donc quand j'ai vu les annonces conjuguées de DevoxxFr et de la Jenkins User Conference à Paris, il m'a semblé évident qu'il fallait
que j'y aille. C'était dans la continuité de mon évolution professionnelle commencée il y a maintenant 2 ans.   
Je pense que si j'étais resté dans la grosse boite je n'aurais jamais pu y aller.   

Attaquons donc le vif du sujet et mon compte-rendu des deux premières conférences de ma vie.

## Jenkins User Conference

###Premier jour soft au Mariott.
Pendant que l'équipe de DevoxxFr s'attèle aux derniers préparatifs au rez-de-chaussée, la JUC se tient au sous-sol. Je n'ai pas les chiffres
exacts mais selon Nicolas de Loof il devait y avoir une grosse centaine de participants.
La conf est résolument plus internationale que DevoxxFr puisque, si je ne me trompe, c'est la première JUC européenne. Il y
a donc des partipants venus d'Angletterre, Allemagne, Hollande, ...   
Après une rapide introduction de [Sacha Labourey](https://twitter.com/#!/sachalabourey), [KK](https://twitter.com/#!/kohsukekawa), le créateur de Jenkins, fait une courte keynote retraçant l'histoire de son bébé.   
A partir de là, les sessions auront lieu dans deux salles en parallèle.   
Voilà le résumé de mon programme :
### Better Build Pipeline  : introducing Build-Flow plugin
par [Nicolas de Loof](https://twitter.com/#!/ndeloof) et [Matthieu Ancelin](https://twitter.com/#!/trevorreznik)   
J'ai découvert Nicolas à ma première session au MarsJug. A l'époque il baignait dans GWT et pas encore dans Jenkins.   
J'utilise le Build Pipeline plugin sur mes 3 Jenkins, il me permet de me servir de Jenkins plus comme un ordonnanceur
à la Dollar Universe plus qu'un simple serveur de build. J'ai ainsi un pipeline de mise en production qui permet de suivre
la déploiement sur une vingtaine de serveurs.   
L'idée originale de Nicolas, il me semble, était de fusionner le Join plugin et le Build Pipeline plugin. Au final il
s'est carrément emballé et est allé jusqu'à créer un DSL pour représenter des workflows. Le plugin est prometteur.
Un gros chantier est la représentation graphique (l'interêt principal du Build Pipeline plugin) qui reste à faire. Et
vu le nombre de questions à la fin de la présentation, ce plugin a un bel avenir devant lui!
### Native Package Build Factory Powered by Jenkins
par [Henri Gomez](https://twitter.com/#!/hgomez)   
J'ai aussi découvert Henri au MarsJug. Il m'a donné de précieux conseils pour la mise en place de jenkins.   
Henri a été un peu pris de court, il avait préparé sont talk en français et a du le faire en anglais au dernier moment.   
Henri présente les avantages du packaging natif (c'est son coté Ops). Avec le Matrix Job plugin, il montre comment créer des RPMS par plateforme/architecture.
Dans son talk du lendemain avec les 4 autres mercenaires, tout ceci sera mis en application.
### Advanced Continuous Deployment with Jenkins
par Benoit Moussaud   
Benoit de Xebia Labs présente Deploy-IT, un outil maison qui permet de déployer par drag'n'drop des livrables sur des serveurs.
J'avoue que j'ai été un peu déçu. Pas par l'outil, mais je m''attendais plus à un talk sur des best practices de
continuous deployment qu'à une présentation technico-commerciale d'un produit.
### Tycho, Jenkins & Sonar : the Eclipse Build Dream Team
par Xavier Seignard et Mickael Istria   
Vu que c'était sur l'utilisation de Jenkins lors du développement de plugin Eclipse, ce n'était pas trop pour moi.
### Clearcase UCM plugin
par Jens Brejner   
Alors je n'ai jamais utilisé Clearcase, mais ce talk a eu un franc succès en abordant un sujet interessant : la notion de [pre-tested commit](https://wiki.jenkins-ci.org/display/JENKINS/Designing+pre-tested+commit).
### Jenkins at Nuxeo
par Julien Carsique   
Une présentation 101 pour ceux qui n'utilisent pas encore Jenkins.
### Integrating PHP Projects with Jenkins
par Sebastian Bergmann   
Autant le dire franchement, le pauvre Sebastian n'a pas vraiment eu de public. Dans la grande salle il n'y avait à peine
10 personnes qui étaient intéressées par l'intégration continue de projets PHP.   
Personnellement j'ai une partie PHP à gérer et j'ai essayé, en vain, de faire un job Jenkins qui déclencherait une analyse statique de code
et un reporting dans Sonar. Faut dire que j'ai opté pour une solution proposée dans le wiki du plugin PHP de Sonar :   
créer un projet maven et y mettre les sources PHP.   
Le talk de Sebastian reprend ce qui est dit sur son site jenkins-php et présente les différents outils propres à PHP (PHPUnit, PHPmd, ...).
### Conclusion
Je m'attendais à des talks un peu plus poussés, en même temps mon choix n'était peut-etre pas le bon. J'aurais peut-etre du aller
voir Grégory Boissinot et son talk How to develop a Jenkins plugin, ou les quickies sur Jenkins chez Apache par Olivier Lamy,
la présentation du Template Plugin, ...


