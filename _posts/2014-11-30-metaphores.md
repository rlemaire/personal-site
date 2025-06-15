---
id: 1003
title: Métaphores
date: 2014-11-30T19:08:58+00:00
author: Raphaël Lemaire
layout: post
guid: http://raphael-lemaire.com/blog/?p=1003
permalink: /2014/11/30/metaphores/
categories:
  - Craftsmanship
---
Un petit tour des métaphores utilisées pour la construction de logiciels.

#### _Recette de cuisine_

Une bonne métaphore pour expliquer la programmation impérative. Une recette de cuisine est une suite d'instructions, plus ou moins abstraites, avec un jargon (« faites revenir les oignons », « montez les blancs, … »), qui permet à la fin d'obtenir un résultat. Le cuisinier jouant ici le rôle de la machine exécutant le programme.

Cette métaphore explique plus ce qu'est un programme que ce que c'est de programmer. Elle ne représente aussi qu'un seul paradigme : la programmation impérative, pas la programmation fonctionnelle ou logique.

#### _Construction_

Cette métaphore a été très utilisée, comme le montre les titres d'architecte, MOE et MOA que nous utilisons encore.

Elle a aussi fait beaucoup de mal, parce qu'assez peu pertinente au final.

Pour un bâtiment, disons un pont, on dessine des plans. Une fois les plans dessinés, et surtout les travaux commencés, le projet est figé, il est impossible de changer quoi que ce soir sans tout casser. Modifier le pont équivaut à démolir un pont et à en reconstruire un autre, coût qui est en général inacceptable.

Les logiciels n'ont pas cette contrainte, il s'agit de texte, le coût du changement est proportionnel au changement demandé.

De plus dans le cas d'un bâtiment, le client choisit un projet à partir d'un beau dessin ou d'une maquette, puis fait confiance à l'entrepreneur. La maquette est tout à fait suffisante pour imaginer le résultat final, et peu d'ajustements sont possibles. Dans le cas d'un logiciel, on sait depuis longtemps que le besoin initial est quasi toujours flou et qu'on a besoin du feedback du client tout au long du projet.

On peut comprendre que pour les premiers projets d'envergure, les protagonistes ait cherché à s'accrocher à des méthodes d'organisation existantes dans d'autres corps de métiers. Comme on connait de mieux en mieux maintenant les spécificités du notre, le vocabulaire devrait se renouveler.

#### _Jardin_

On compare le produit logiciel à un jardin (plutôt un potager ou un verger) dont il faut s'occuper. Si on n'arrache pas les mauvaises herbes, qu'on ne chasse pas les parasites, le jardin va se détériorer et deviendra moins productif.

Cette comparaison est assez mignonne, et explique pas trop mal pourquoi on passe tant de temps à « ranger », renommer des trucs, rassembler ou découper des fichiers, etc&#8230;

Un défaut cependant : c'est le code source qu'il faut entretenir pour éviter qu'il se ne détériore, et c'est le logiciel déployé qui produit de la valeur. Un snapshot pas trop beugué peut produire de la valeur pendant des années sans que personne ne change quoi que soit au code source.

#### _Artisanat_

On logiciel est comparé à un produit de l'artisanat, comme un violon sculpté à la main.

Au niveau de la création du produit, celle-ci a presque les même défaut que la métaphore du bâtiment : nécessité d'avoir une bonne idée du produit final au départ et impossibilité de modifier le résultat final.

C'est pour la vision du métier que cette comparaison est intéressante : on parle d'un professionnel qualifié et respecté par son commanditaire qui façonne une quasi-oeuvre d'art.

#### _Livre ou symphonie_

On compare l'écriture d'un logiciel à l'écriture d'un roman ou d'une symphonie.

Cette comparaison rend bien le coté créatif de la programmation, ainsi que le coût du changement : celui-ci est toujours possible, et son coût est directement proportionnel à son importance. Il est possible de changer rapidement des choses peu importantes, il est plus long de faire des gros changement, comme modifier la personnalité d'un personnage, mais ça reste possible.

En revanche le romancier ou le compositeur (même pour les histoires sur commande ou les musiques de film) a moins de contraintes, techniques, fonctionnelles, contextuelles.  Et il travaille en général seul, pas au sein d'une équipe potentiellement très hétérogène.

#### _Dette technique_

On compare le coût du manque de qualité du code source à une dette financière.

On a deux types de dette technique : une dette délibérée, où on a choisi de ne pas implémenter comme il faut pour livrer plus vite, ou une dette issue d'un manque de discipline. [Fowler en parle mieux que moi](http://martinfowler.com/bliki/TechnicalDebtQuadrant.html).

Le gros problème de cette comparaison, c'est que la dette financière n'a aucun impact sur la productivité d'une entreprise. Si une entreprise empreinte un million d'euros, cela ne change rien au quotidien de ses employés, cela n'affecte pas leur travail. Et même comme souvent les entreprises s'endettent pour acquérir des outils de production, celle-ci a plutôt un impact positif. Amazon par exemple n'a jamais été bénéficiaire et est très endetté, personne ne dira pourtant que cette entreprise est en mauvaise santé.

La dette technique en revanche modifie la vélocité : on doit comprendre le code illisible et non testé pour le modifier, le corriger ou tourner autour.

&nbsp;