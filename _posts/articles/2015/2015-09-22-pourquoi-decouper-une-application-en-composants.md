---
id: 1174
title: Pourquoi découper une application en microservices / composants ?
date: 2015-09-22T22:10:21+00:00
author: Raphaël Lemaire
layout: post
guid: http://raphael-lemaire.com/blog/?p=1174
permalink: /2015/09/22/pourquoi-decouper-une-application-en-composants/
categories:
  - Technique
  - favorite 
---
On parle pas mal de micro-services en ce moment, même si le buzz word commence à prendre du plomb dans l’aile et à avoir une image négative (comme SAO en son temps). Sans rentrer dans le débat de savoir si cela correspond bien à la définition de micro service ou pas, il peut être intéressant de découper une application en composant pour tout un tas de raisons.

Disclaimer : on parle ici de découpage en plusieurs composants _déployés_. On peut déjà ranger une base de code avec des paquetages ou des modules. On peut aussi utiliser la même base de code, le même livrable (genre un war) et l’exploiter de plusieurs façon, comme serveur web, comme batch, comme client de queue, etc&#8230;

Donc pourquoi briser le kiss et créer des modules séparés ?

Voici une liste (non exhaustive et peu détaillée) de raisons.

### Séparation par responsabilité fonctionnelle

C’est la de raison découper qui vient en premier à l’esprit. Séparer par responsabilité est intuitif, et souvent fait dès le début des projets. Ce n’est pas vital en soi, mais c’est la voie permettant d’obtenir les autres avantages que je vais décrire plus loin.

La séparation fonctionnelle doit être le centre de l’interrogation sur la division : _est-ce que ça a un sens fonctionnel ?_

### Pour utiliser un langage ou une technologie adaptée

Certains langages et certaines technologies sont plus adaptés à certains usages. Par exemple pour manipuler du json il sera plus confortable d’utiliser javascript et node que Java. Pour un métier complexe avec du calcul distribué ou du machine learning on aura envie d’accéder à des outils comme Akka ou Spark dans leur langage natif, etc…

Avoir un découpage technique ou fonctionnel de l’application permet l’exploitation de ces différences, là où tout regrouper impose l’usage d’une stack de technologies unique et donc des compromis.

### Pour confier la réalisation à des équipes différentes

Corollaire au point précédent : tout le monde n’a pas les même compétences, les même spécialités. Une entreprise qui a une partie de son équipe compétente en Ruby et une autre compétente en .NET devra utiliser ces compétences sur des composants différents.

Cela permet également d’exploiter des profils spécialisés, par exemple des data scientists, qui pourront se focaliser sur leurs sujets, sans être perturbés par les autres aspects du produit.

### Maintenabilité

Des unités plus petites sont plus facilement maintenables, voire remplaçables, qu’un seul gros logiciel. C’est vrai pour une méthode, pour une classe, c’est aussi vrai pour un composant.

### Scalabilité ciblée

Toutes les parties d’une application ne sont pas autant sollicitées. Un découpage permet d’optimiser les ressources en scalant uniquement les composants qui prennent le plus de charge, alors qu’avoir un seul module impose de multiplier le nombre de serveurs et leur taille.

Un cas typique : le producteur / consommateur : on a souvent plus de lectures que d'écritures de données, il peut être intéressant de séparer les deux pour déployer plus de consommateurs.

### Isoler les parties critiques

Tous les aspects d'une application n'ont pas la même criticité. Certains sont critiques pour le business, d'autres 
accessoires. Il peut être intéressant d'isoler les parties critiques afin qu'elles ne soient pas perturbées par 
d'autres aspects du produit qui sont moins importantes.

Imaginez un site permettant de suivre les actualités financières, ainsi que d’échanger des titres. Le site prend une commission sur l’échange de titres, ceux-ci sont donc un élément essentiel, car source de revenu. De même pour les utilisateurs, si pour une raison ou une autre il n’y avait plus de rafraîchissement de l’actualité, il en résulterait une certaine frustration, mais beaucoup moins que s’ils ne pouvaient pas vendre l’action dont le cours baisse à temps. L’échange de titre est donc critique alors que l’actualité ne l’est pas. Séparer permet d’isoler cette fonctionnalité, de telle sorte qu’un dysfonctionnement d’un autre système ne l’impacte pas.

### Optionalité

Isoler une fonctionnalité dans une brique à part permet de l’activer ou de la désactiver plus facilement, sans que le code associé alourdisse le composant principal. Cela facilite aussi l’A/B testing.

### Composant proxy / couche de médiation

Un composant peut être un simple proxy d’adaptation, permettant à un client d’utiliser un service.

Une RIA Javascript ne saura que faire d’un service SOAP par exemple, on peut donc créer un service traduisant le SOAP et l’XML en REST et Json. Ou encore cacher une fonction mainframe un peu exotique derrière une interface plus moderne.

### Sécurité / confidentialité

Il peut arriver que l’on ne souhaite pas qu’une ressource soit accessible par toutes les équipes. Par exemple pour tout ce qui est facturation, ou encore les informations personnelles des utilisateurs. On peut alors séparer la partie sensible dans un composant dédié à l’accès plus limité.

### Isolation de code « legacy »

Si l’on ne veut plus travailler avec une application dont les technologies datent ou dont la dette technique est trop importante, il est possible de toujours l’exploiter tout en la complétant par d’autres briques intégrant les nouvelles fonctionnalités et/ou remplaçant progressivement les anciennes.

_Bien sur tous ces aspects sont complémentaires._

&nbsp;

### A garder en tête quand on découpe :

On parle ici d’abord de séparation au déploiement.

La base de code doit autant que possible rester regroupée dans un seul projet, sur le même repository. Les éléments partagés doivent rester accessibles avec un seul ctrl+clic. Sinon on risque de faciliter l’apparition de duplications, par paresse ou méconnaissance des éléments disponibles dans les autres applications.

De plus garder les éléments groupés permet d’avoir un historique plus consistant : un incrément de fonctionnalité impliquant plusieurs briques déployées reste accessible dans le même commit, sans besoin de naviguer entre les repositories.

Si on choisit d’utiliser des langages différents il faut bien s’assurer qu’il n’y ait pas de fonctionnel commun avec une ou d’autres briques, sinon on risque d’implémenter la même chose deux fois.

De manière générale, il vaut mieux se méfier des séparations qui n’ont qu’un sens technique, ce qui peut être artificiel, et de toujours se demander si la séparation a bien un sens fonctionnel .