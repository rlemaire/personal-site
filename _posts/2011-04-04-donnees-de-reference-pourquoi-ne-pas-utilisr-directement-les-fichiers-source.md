---
id: 51
title: Données de référence, pourquoi ne pas utiliser directement les fichiers source ?
date: 2011-04-04T10:15:20+00:00
author: Raphaël Lemaire
layout: post
guid: http://random-arguments.fr/?p=51
permalink: /2011/04/04/donnees-de-reference-pourquoi-ne-pas-utilisr-directement-les-fichiers-source/
categories:
  - Technique
---
Il arrive régulièrement d'intégrer dans nos systèmes d'information des fichiers produits par des services extérieurs ou des humains, du type Xml, CSV, ou Excel (xls). En général, le réflexe est de parser ces fichiers pour les traduire dans un modèle objet, que l'on stocke ensuite dans une base de données relationnelle comme « Données de référence ».

Au sein du programme, ces données sont ensuite chargées à partir de la base, en général traduites via un ORM en graphe d'objet, très certainement similaire ou identique à celui utilisé après le parsing des fichiers bruts.

[<img loading="lazy"  class="aligncenter size-full wp-image-342" title="with_db-300x151" src="/wp-content/uploads/2011/04/with_db-300x1511.png" alt="" width="300" height="151" />](/wp-content/uploads/2011/04/with_db-300x1511.png)

Pour simplifier le code, pourquoi ne pas utiliser directement les fichiers sources ?

[<img loading="lazy"  class="aligncenter size-full wp-image-343" title="without_db-300x68" src="/wp-content/uploads/2011/04/without_db-300x681.png" alt="" width="300" height="68" />](/wp-content/uploads/2011/04/without_db-300x681.png)

### Comment ?

#### Sur le système de fichiers

Le plus simple et le plus évident est de stocker ces fichiers sur le **même système de fichier** que l’application. Cette solution convient dans beaucoup de cas. On peut placer les fichiers dans un répertoire partagé ou créer un accès FTP pour faciliter leur mise à jour par des fonctionnels sans exhiber toute l’architecture de production. Attention tout de même à ne pas trop [complexifier les livraisons](http://raphael-lemaire.com/blog/2011/03/23/simplicite-des-mises-en-production-pourquoi-les-warear/) en multipliant les fichiers à livrer et leurs locations. On peut imaginer un bundle parallèle avec les fichiers de données.

#### Dans le classpath

On peut également stocker ces fichiers directement dans le **classpath**, ou dans l’application elle même, si le rythme de mise à jour des fichiers et inférieur au rythme de mise à jour de l’application, ou si la mise en production de l’application juste pour mettre à jour le fichier est acceptable. Cette solution présente les avantages de la précédente (simplicité, performance, …), sans l’inconvénient de multiplier les livrables.

#### Sur un serveur distant

Sur un **serveur distant**, avec accès par FTP, HTTP ou autre. Là encore, on est proche du système de fichier. L’avantage ici est, du point de vue architecture serveur, de séparer l’application de ses données. L’inconvénient étant le temps de téléchargement via le réseau.

#### En mémoire.

Niveau performance on ne pourra pas faire mieux. Il faudra tout de même prévoir un mécanisme de mise à jour du cache mémoire par un utilisateur lambda (ou un admin lambda), ce qui est relativement simple.

#### Via un (web) service indépendant.

Dans l’esprit SOA, un service indépendant est chargé de lire les données de référence et les fournir à l’application. L’architecture est légèrement complexifiée, les performance impactée, mais le tout et plus modulaire et peut évoluer en parallèle.

#### Dans un blob ou un clob.

C’est un peu la solution « Je n’ai pas pu décider ». L’avantage c’est qu’on regroupe (toujours) toutes les données au même  endroit. Les données peuvent être mises à jour par requête si elles sont sous la forme de texte de taille raisonnable (eg : petit xml).

### Pourquoi ?

#### Utiliser ces fichiers, c'est facile, et de toute façon il faut le faire.

Parser du CSV est trivial. C'est un exercice de programmation pour les tout bébés programmeurs, à leur quatrième cours de Pascal [remplacer par votre langage d’apprentissage préféré : Ada, Basic, C (warrior !), Java, …], intitulé : « les fichiers ». Il existe des bibliothèques décentes pour parser du XLS, et de toute façon ce format peut en général être traduit en CSV. Quand au XML, on ne compte plus les manières de l'utiliser.

Mais de toute façon, pour stocker vos données de références, il faudra les lire, ces fichiers. Pas question pour un programmeur d'écrire ses inserts à la main ! Ce code là est inévitable.

#### L'impact sur les performances serait peu significatif.

Pour des fichiers relativement petits (jusqu'à quelques dizaines de mégas octets), si le fichier est sur la même machine que le programme, voir dans le classpath, le parsing est instantané. Le temps d’exécution dépend surtout de la quantité de données à charger. La différence avec une requête en base (pas forcément bien construite) n'est sans doute pas énorme, d'autant que la base est, elle, en général sur une autre machine. Et les fichiers contenant ces fameuses données de références sont, effectivement, typiquement très petits.

#### Cache

Ce type de données est très souvent mis en cache, avec une longue durée de vie (par exemple 24h), les mises à jour étant très rares. Si ces données sont mises à jour une fois par trimestre ou même toutes les 24h, un temps de latence d'une demi seconde pour mettre à jour le cache est tout à fait acceptable pour une application de de gestion. Si les données sont à 99% lues à partir du cache, peu importe que celui-ci soit alimenté par une base relationnelle ou directement un fichier brut.

#### Simplicité, moins de code à maintenir, travail redondant évité.

Lire les fichiers, traduire le résultat en graphe d'objets et stocker ces objets en base, puis à la demande, recharger ces objets depuis la base, dans le même graphe d'objet.

Ce travail est redondant : on écrit deux mappings : un du fichier source vers le code utilisé, puis un second de la base vers ce même code. Même si le second est rapide à écrire avec les ORMs modernes type JPA, pourquoi s'en encombrer ? Préservons nos jours/hommes pour du travail à valeur ajoutée fonctionnelle ou l'amélioration de la qualité du projet (écriture de tests par exemple). D'autant que cela simplifie la base de données cible et les interactions : moins de tables, moins de requêtes, moins de transactions.

Vous me direz, on peut générer ce code en quelque commandes avec Seam, Grails ou [insérez votre techno préférée]. Ok. Mais pourquoi créer du code, même automatiquement, qui sera potentiellement buggé, soumis à évolution ou à correction, bref, à maintenir, si on peut l'éviter ?

#### Les mises à jour sont faciles.

La mise à jour d'un fichier de référence est aussi facile et rapide qu'une mise à jour en base, et est moins technique et plus intuitive pour un fonctionnel/moa/admin. Plus besoin de générer de back-office avec x-MDA ou Seam. Un glisser/déposer via un client FTP ou un répertoire partagé, ou un post sur un bête formulaire statique avec une Servlet basique derrière et le tour est joué.