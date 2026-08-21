---
id: 1612
title: 'Pourquoi il faut supporter IE (en vrai)'
date: 2019-12-16T00:00:00+00:00
author: Raphaël Lemaire
layout: post
guid: http://raphael-lemaire.com/blog/?p=1612
permalink: /2019/12/16/pourquoi-supporter-ie/
categories:
  - GreenIT
---
> Résumé : on devrait toujours supporter IE (ou autre navigateur en retard 
> du futur), même avec une part de marché faible, au nom de la fracture 
> numérique et pour ne pas pousser à l’obsolescence des terminaux. Quitte 
> à s’habituer à rester quelque années derrière les innovations du Web. 

Le support de la plus ancienne version du navigateur de Microsoft est un serpent de mer du développement web : quelle que soit l’équipe, le projet, l’année (en tout cas depuis que j’ai commencé à faire du web), la question se pose.

Souvent les développements commencent sans en tenir compte, en utilisant des avancées récentes de CSS ou HTML 5 (CSS grid aujourd’hui, flexbox il y a quelques années, …) et le site est tout cassé sur IE. Et puis plein de gens plus ou moins techniques poussent pour qu’on le répare et le travail finit par être refait, avec une grosse part de réécriture du layout.

Dans les deux cas, beaucoup de temps perdu, mais aussi beaucoup de frustration de tous côtés : des développeurs qui doivent refaire leur travail en utilisant des techniques « anciennes », des clients et utilisateurs qui ont un site tout cassé sur certains terminaux.

[<img loading="lazy"  src="/wp-content/uploads/2019/12/browser_market_share_bar.png"  alt="Part de marché des navigateurs en France en 2019" width="800"  />](/wp-content/uploads/2019/12/browser_market_share_bar.png)


## Pourquoi ne pas ou mal prendre en compte internet explorer ?

Il y a quelques arguments valables, qui tournent autour de l’idée de pousser les utilisateurs à mettre à jour vers Edge, Chrome ou Firefox :
-	Les problèmes de sécurité que peut poser une ancienne version. 
-	Favoriser la propagation de technologies web modernes, ce qui facilite le développement des solutions et est bon pour l’innovation.

En vrai, on a aussi d’autres choses qui jouent beaucoup, et sans doute plus que ces arguments : 
-	En supportant IE, on ne peut pas utiliser les propriétés CSS les plus récentes et les plus pratiques. 
-	Cela réclame plus de travail : on doit tester sur plus de navigateurs, faire plus attention aux éventuels problèmes de présentation.
-	Il faut garder au moins une machine sous Windows ou une VM pour pouvoir tester sur ce navigateur alors qu’il est plus agréable de travailler sur linux ou mac.

Soyons honnête, cette relative complexité technique joue beaucoup au quotidien.


## Pourquoi est-ce qu’on finit toujours par supporter IE dans ce cas ?

Les arguments sont en général business :
-	La part de marché d’IE est faible, mais pas encore négligeable. On n’a pas envie de perdre ce marché. De plus les utilisateurs d’anciens navigateurs sont parfois bien placés dans l’organigramme de l’entreprise.
-	Il existe des parcs de machines qui sont bloqués sur une version de navigateur, et où les utilisateurs n’ont pas la possibilité d’administrer leur poste.
-	Si la part de marché d’IE est faible en France, elle l’est moins dans d’autres pays, comme en Europe de l’Est, en Asie, En Afrique, etc… Qui peuvent être des marchés cibles de l’entreprise.


## Pourquoi moi je trouve qu’on devrait supporter IE.

J’y ajouterais d’autres arguments, orientés numérique responsable, qui me font dire que le support doit être présent : 
-	En ne supportant pas IE, **on contribue à pousser à l’obsolescence des terminaux parfaitement fonctionnels physiquement**, mais qui ont le simple défaut d’être « vieux », ou du moins de ne pas avoir la toute dernière version de chaque logiciel.  Et des terminaux obsolètes sont renouvelés, ce qui implique une grosse dépense de ressources (énergie, eau et surtout ressources abiotiques pour leur fabrication). Vous me direz qu’on peut installer un navigateur moderne sur la plupart des ordinateurs, mais tout le monde ne le fait pas, pour diverses raisons, ce qui m’amène à un autre argument : 
-	**La fracture numérique** : les gens peu à l’aise avec le numérique ne vont typiquement pas mettre à jour leurs navigateurs, et encore moins expérimenter en en installant un différent. Ils garderont leur appareil avec sa configuration d’origine partant du principe que tout doit continuer à fonctionner sans intervention, comme le ferait une cafetière ou un radioréveil.

Alors oui, supporter IE 11 implique qu’on ne peut pas utiliser les dernières propriétés CSS ou les dernières options des élément HTML 5. Mais doit-on toujours être sur le fil des sorties des spécifications W3C ? Ne peut-on attendre quelques années ans avant de les utiliser ? 

A une époque, celle d’IE 6 et 7, ce qu’on peut faire aujourd’hui avec IE 11 était un rêve lointain. Peut-être devrions nous apaiser notre digestion des nouveautés, par respect pour nos utilisateurs et pour nos ressources.
