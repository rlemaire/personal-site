---
id: 1614
title: 'Comment intégrer le numérique responsable dans mon projet agile ?'
date: 2020-05-22T00:00:00+00:00
author: Raphaël Lemaire
layout: post
guid: http://raphael-lemaire.com/blog/?p=1615
permalink: /2020/05/22/agilite-greenit/
categories:
  - GreenIT
---
Comment agilité et numérique responsable peuvent-ils se combiner ? Est-ce que ces deux aspects du développement de 
logiciel sont en phase ou en conflit ? Peut-on éco-concevoir itérativement ?

Étant à la fois un promoteur de l’agilité et du numérique responsable j’ai rassemblé quelques réflexions rapides sur ce sujet.

Déjà on peut remarquer qu’il y a un **prérequis : il faut que l’équipe ait connaissance du sujet**, et qu’elle ait envie de 
mesurer l’impact écologique et social du logiciel et de l’optimiser.

Partons du principe que nous avons une équipe agile un peu idéale et qui a bien cette idée en tête.

## Simplicité : pas de fonctionnalités inutiles, pas de complexité technique inutile.

Dès le départ tout le monde se dit que ça va bien se passer : les méthodes dites agiles, comme comme 
[Scrum](https://fr.wikipedia.org/wiki/Scrum_(d%C3%A9veloppement)), [Kanban](https://fr.wikipedia.org/wiki/Kanban_(d%C3%A9veloppement)) 
ou [XP](https://fr.wikipedia.org/wiki/Extreme_programming), encouragent la **simplicité**. 


XP stipule que _« la solution la plus simple sera toujours celle qui sera retenue »_, ce qui va dans ce sens : on évite 
toute complexité inutile. Cela se traduit en autres par l’acronyme bien connu [YAGNI](https://fr.wikipedia.org/wiki/YAGNI).

En théorie, on ne construit que le logiciel nécessaire pour répondre au besoin de l’utilisateur, en commençant 
par ce qui a le plus de valeur business ([optimum de Pareto](https://fr.wikipedia.org/wiki/Principe_de_Pareto)). 
En utilisant un backlog priorisé, en livrant souvent et en s’arrêtant d’ajouter des choses quand les utilisateurs sont 
satisfaits, on doit avoir un logiciel qui n’a pas plus de fonctionnalités que nécessaire, ce qui aide à **éviter l’obésité logicielle**.

Le principe d’avoir des petites équipes permet aussi de freiner l’implémentation en parrallèle d’un catalogue trop vaste de fonctionnalités 
et impose leur priorisation. 

Du coup il est possible de **conserver le logiciel simple et léger, et donc sobre**.


## Les valeurs : respect des humains, des écosystèmes et des ressources
	
Voilà c’est le début du projet, le premier planning. Tout le monde a bien en tête les valeurs de l’agilité.

Scrum en a cinq : _courage_, _focus_, _engagement_, _respect_, _ouverture_. XP en en également cinq : _simplicité_, 
_communication_, _courage_, _feedback_, _respect_.

On trouve dans les deux cas le respect : on doit respecter ses collègues dans le cadre du projet (c’est le message), 
mais on peut extrapoler au respect des _utilisateurs_, en leur offrant un produit de qualité qu’ils pourront utiliser quelles 
que soit leurs contraintes (réseau 2G, vieux terminaux), et au respect des _éco systèmes_, des _ressources_ et les _humains 
futurs_, que notre comportement impacte chaque jour.



## Focus sur l’utilisateur : pour une UX simple et efficace

Bien sûr on a un **client sur site** qui utilise l’application dans des conditions réelles.

L’UX du produit est donc de qualité, puisque tout ce qui va dans le mauvais sens est immédiatement repéré comme une 
gêne par le client, et critiqué à chaque fin d’itération (courte).

Comme la bonne qualité de l’UX permet de limiter les interactions client/serveur, et aussi qu’une bonne UX a plus de 
chance d’être simple, basée sur un design sobre et épuré, on est encore bien en phase avec le numérique responsable.

Gros bonus si ces utilisateurs réels ont des terminaux anciens ou faibles, voire ont un handicap permettant de vérifier
l’accessibilité du produit.


## Amélioration continue 

L’agilité place les cycles courts et l’amélioration continue au centre des préoccupations de l’équipe.

Prendre en compte les retours et les problèmes à chaque fin d’itération, typiquement toutes les deux semaines, **augmente 
les chances que d’éventuels sujets de performance ou de portabilité de l’application sur des terminaux faibles soient 
pris en compte** (pour ne pas encourager leur obsolescence). Les améliorations peuvent être ajoutées à tout moment dans 
le prochain sprint.


## La responsabilisation des équipes encourage la qualité
	
L’équipe est petite, motivée, engagée. Le produit est le sien, chaque individu a un désir profond de faire du bon 
travail, se sent pleinement responsables de tous les aspects du projet, dont la qualité, la sécurité, l’ergonomie mais 
aussi la consommation de ressources, la pression au renouvellement des terminaux.

A chaque planning, ils réfléchissent sur la façon de faire au plus simple, au plus performant. Étant des professionnels, 
ils challengent régulièrement les propositions des UX et PO pour les améliorer, voire l’opportunité même d’ajouter 
telle ou telle fonctionnalité.

Dans un autre contexte, ces mêmes personnes pourraient se sentir être de petits rouages dans une grande machine et avoir
 plutôt tendance à penser, plus ou moins de façon consciente, que quelqu’un d’autre quelque part s’occupe du problème 
 qu’ils ont remarqué, là où dans une équipe réduite ils peuvent bien voir que c’est à eux de le gérer.


## La responsabilisation et la confiance dans les individus favorise l'émergence et la difusion des bonnes idées

Corolaire du point précédent : les collaborateurs brillants soumettront leurs bonnes idées à toute l’équipe, et ces 
idées ont toutes les chances de voir le jour. C’est avec plus de cerveaux actifs et écoutés qu’on a des chances de voir 
implémentées des idées d’**écoconception radicale**, comme remplacer la consultation d’un site par un envoi de mail ou de
 SMS (_suppression du produit !_), à l’exemple de ce rapporte [ce livre blanc de green-concept](http://www.greenconcept-innovation.fr/wp-content/uploads/2020/02/greenconcept_21022020.pdf) (p37). 


## Un danger : ne pas assez tenir compte du long terme.
	
A chaque itération, on doit sortir quelque chose à temps pour la démo. L’équipe se pose toutes les questions nécessaires 
en prenant bien en compte la qualité logicielle, mais pas forcément les questions de long terme.
 
 Si quelqu’un dit des choses du type : _« Quelle est la durée de vie de cette donnée ? Puis-je la supprimer après 3 ans ? »_ 
 ou encore _« Avec X utilisateurs, cette solution est-elle encore valide ? »_, on risque de lui répondre « on verra après,
  là, on n’a pas le temps ».
 
 On risque de perdre quelques questions de conception si le cycle court courant est le seul horizon que l’équipe a en tête.
 
 De plus comme souvent, si une idée d’amélioration, d’efficience dans le cas présent, apparait tardivement, elle coutera 
 plus cher et aura moins de chances d’être adoptée.


## Et les tests de charges ?

Typiquement longs à implémenter, à exécuter et analyser, les tests de charges sont souvent désynchronisés des itérations 
d’ajout de fonctionnalités : il faut alors améliorer un existant déjà livré pour le rendre plus performant une fois les 
résultats connus, et il est plus difficile de modifier l’implémentation, et surtout l’ergonomie de l’application pour 
aller vers quelque de différent et de plus efficace. 


## Une limite : comment intégrer une ACV ?
	
Mesurer l’impact écologique d’un service numérique doit se faire idéalement avec une [ACV](https://fr.wikipedia.org/wiki/Analyse_du_cycle_de_vie). 

L’ACV est une démarche itérative, comme l’implémentation de logiciel dans une démarche agile : on commence par se forger une vision globale, puis on 
affine les points les plus intéressants, par ordre de priorité.

La première intuition de l’équipe est que deux approches itératives devraient bien se combiner. 

Mais l’ACV est pensée pour l’analyse d’un système (ici un service numérique) qui ne change pas. Or **un logiciel est 
toujours en évolution**, avec des mises à jour à chaque itération, qui peuvent faire varier le résultat.

C’est une des difficulté des ACV de services numériques, [identifiée d’ailleurs par greenspector](https://greenspector.com/wp-content/uploads/2020/01/GREENSPECTOR_Guide_Methodologique_ACV_des_Logiciels.pdf) :
 étudier un système  qui change en permanence.

## Un gros danger : un projet sans fin, qui grossit toujours.
	
Le projet dure depuis des mois, le backlog est toujours bien rempli, avec de quoi faire deux ou trois itérations déjà 
prêt et rédigé. Il ne semble pas avoir de fin. 

A chaque sprint, le produit est un peu plus riche, on peut faire plus de choses, le faire un peu différemment. On commence 
à voir des fonctionnalités qui se ressemblent, d’autres qui sont peu utilisées, voir presque pas. On voit apparaitre des
outils de tracking pour glaner des informations sur les utilisateurs, avec leur coût en ressources client, des synergies
avec d’autres canaux, des choses ajoutées pour faire plaisir à un sponsor…

Un projet agile n’a pas de date de fin définie. Par design, le périmètre n’est pas fixé dès le départ. 

Cela fait partie des points positifs : on peut prendre en compte les changements de contexte : mises à jour des OS (iOS, Android, avec 
leurs guidelines graphiques), des demandes des utilisateurs, des opportunités et contraintes des équipes et outils 
partenaires, etc… 

Mais c’est aussi un danger, puisqu’on peut faire grossir à l’infini le logiciel, au **risque de le rendre lourd, 
lent et peu ergonomique**, c’est-à-dire atteint d’**obésité logicielle**, qui pousse les appareils à l’obsolescence.

Un projet dont le périmètre est négocié et contractualisé au départ a, en théorie au moins, une fin : on arrête d’ajouter 
des choses quand l’objectif est atteint.


## Conclusion

Les promesses d’une agilité bien implémentée ; simplicité, pragmatisme, détection et correction rapide des problèmes 
(donc entre autres de portabilité, de performance et d’efficience) ou encore prise compte rapide des retours d’utilisateurs 
réels, sont plutôt en phase avec la construction de logiciels sobres, qui consommeront peu de ressources, client ou serveur, 
et répondront au besoin de façon efficace.  **A condition que l’équipe ait en tête parmi toutes ses préoccupations, 
la question des impacts écologiques** de ce qu’elle construit.

Les itérations courtes et le manque éventuel de planification du long terme peuvent cependant amener des lacunes en 
termes de performance, surtout coté serveur (données conservées à l’infini, résultats de tests de charges décalés, …) et le fait qu’un projet 
peut ne pas avoir de limite définie en périmètre peut aussi l’amener à grossir excessivement.
