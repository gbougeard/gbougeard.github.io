---
layout: post
title: "Documenter une API REST grace a RAML"
date: 2014-03-14 21:36
comments: true
categories: [REST, api]
keywords: REST, api
tags : [REST]
---

Avoir une API REST c'est cool, avoir une API REST documentée c'est encore mieux!

### Quelques exemples de documentation d'API REST

- [Expedia](http://developer.ean.com/docs/hotel-list/) : plain text, pas super pratique
- [Twitter](https://dev.twitter.com/docs/api/1.1) : c'est déjà mieux
- [Marvel](http://developer.marvel.com/docs) : waouh!

A mon humble avis la doc la plus lisible et mieux organisée est celle de l'API de Marvel.

Elle a été générée grâce à [Swagger](https://helloreverb.com/developers/swagger).
Swagger permet pour une application Java et plus particulièrement une application JAX-RS, de générer cette documentation
et ceci grâce à des annotations ( [exemple](https://github.com/kongchen/swagger-maven-example/blob/master/src/main/java/com/foo/bar/api/car/CarResourceV1.java) ).
Il existe aussi un [module Swagger pour Play2](https://github.com/wordnik/swagger-core/tree/master/modules/swagger-play2) qui utilise lui aussi des annotations.

C'est bien sympa tout ca, ca génère tout tout seul mais c'est tout de même super intrusif et ca "pollue" quelque peu notre code.
Il y a presque plus d'annotations Swagger que de code...

## RAML

[RAML](http://www.raml.org) ou RESTful API Modeling Language, est une initiative de [Mulesoft](http://www.mulesoft.com) mais pas [que](http://raml.org/about.html#six).
L'idée de RAML ce n'est pas de générer de la doc à partir de code existant mais de définir un language de description d'APIs REST.
Il se base sur [YAML](http://www.yaml.org) et a donc sa propre [specification](http://raml.org/spec.html).

RAML.org fournit différents [outils](http://raml.org/projects.html) open source :

### API Designer
Un editeur développé en AngularJS permettant de créer des fichiers RAML. L'éditeur a la coloration syntaxique, l'auto-complétion ainsi que la vérification de la syntaxe RAML.
En attenant un plugin équivalent pour votre IDE préféré, cela reste le meilleur outil pour éditer un fichier RAML.
Il utilise lui même l'API Console pour faire la prévisualisation des fichiers édités.
Pour l'utiliser localement, il suffit de cloner le [repo github](https://github.com/mulesoft/api-designer) puis de lancer l'application grâce à grunt.
Personnellement je préfère utiliser [l'éditeur en ligne](http://api-portal.anypoint.mulesoft.com/raml/api-designer) car en local je n'ai pas trouvé comment persister les fichiers :)
### API Console
Une directive AngularJS permettant de faire un rendu web d'un fichier RAML donné.
### JAX-RS Codegen
Un générateur d'application JAX-RS a partir d'un fichier RAML.


### Un exemple concret
Afin de se rendre bien compte de la syntaxe et des possibilités offertes par RAML, voilà un exemple concret de [doc générée pour l'API de Github](http://api-portal.anypoint.mulesoft.com/github/api/github-api-v3/docs/raml) et le [fichier RAML source](http://api-portal.anypoint.mulesoft.com/github/api/github-api-v3/github-api-v3.raml).

RAML permet de définir des traits, des type de resources (dans l'exemple de l'API Github il y a par exemple le resourceType *item* pour les URI vers une ressource unique et *collection* pour les listes)
ce qui permet d'éviter de se répéter mais aussi de bien catégoriser et organiser ses ressources.

Pour les réponses, on peut spécifier directement dans le fichier RAML la structure d'un objet json au format json-schema dans le cadre d'une réponse de type application/json mais on peut aussi
inclure (gradce à la syntaxe !include:myfile ) un fichier json ou une xsd (pour une réponse de type application/xml). La même chose est possible pour les exemples de réponses.
Ce qu'il faut savoir avec les exemples, c'est qu'ils vont être les valeurs par défaut dans l'onglet *Try it*.

On pourrait alors imaginer, dans le cas où l'ont veut documenter une application existante (je rappelle que l'idée de base de RAML c'est de décrire d'abord l'API puis de générer le code à partir de cette spec),
pour une application Play2 Scala, un plugin SBT permettant de générer des fichiers json décrivant au format json-schema tous les Readers/Writers définis dans l'application.
Ca serait toujours plus pratique que devoir les écrire "à la main".

## Conclusion
REST API Designer est un métier d'avenir. Bien construire une API REST n'est pas forcément évident (cf [ce thread](https://groups.google.com/forum/#!topic/lescastcodeurs/Fjk7L9P3Jsg)).
Des outils comme ceux que proposent RAML (en particulier l'API Designer et l'API Console) me semblent plus qu'adaptés pour tous ceux qui doivent créer une API REST ou documenter une existante.




