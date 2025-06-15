---
id: 1565
title: 'Résumé de livre « Eco-Conception Web : les 115 bonnes pratiques »'
date: 2018-05-22T20:43:06+00:00
author: Raphaël Lemaire
layout: post
guid: http://raphael-lemaire.com/blog/?p=1565
permalink: /2018/05/22/resume-de-livre-eco-conception-web-les-115-bonnes-pratiques/
categories:
  - GreenIT
---
[<img loading="lazy"  class="alignright" src="/wp-content/uploads/2018/05/41FnnOKTVL._SX330_BO1204203200_-200x300.jpg" alt="Couverture du livre « Eco-Conception Web : les 115 bonnes pratiques »" width="200" height="300" srcset="/wp-content/uploads/2018/05/41FnnOKTVL._SX330_BO1204203200_-200x300.jpg 200w, /wp-content/uploads/2018/05/41FnnOKTVL._SX330_BO1204203200_.jpg 332w" sizes="(max-width: 200px) 100vw, 200px" />](/wp-content/uploads/2018/05/41FnnOKTVL._SX330_BO1204203200_.jpg)

J'ai il y a peu fait la lecture du livre « éco-conception Web : les 115 bonnes pratiques ». Je vous en propose donc un résumé.

_Disclaimer : ce résumé est partiel et personnel et ne remplace pas le contenu original. _

## Rappel : l'IT détruit le monde

Le livre commence par des rappels factuels :

 _Chaque opération numérique a un impact sur le monde réel._

L'économie numérique ne remplace pas l'économie traditionnelle, elle s'y ajoute. Toutes ces activités que nous faisons sur nos terminaux électroniques ont un impact réel sur la planète, d'autant plus insidieux qu'il est invisible (contrairement aux sacs plastiques ou aux pots d'échappement).

_Deux gros postes de consommation_

L'IT consomme des ressources pour la fabrication, l'entretien et le démantèlement des terminaux : minéraux précieux, terres rares, etc&#8230; et contribue à l'épuisement des ressources, à l'érosion de la biodiversité, &#8230;

Lors de l’utilisation des terminaux on a surtout de la consommation électrique. Qui semble petite à l'échelle individuelle&#8230; sauf qu'il y en a des milliards.

_Il y a une épidémie d'obésiciel._

C'est à dire de logiciels beaucoup plus couteux en ressources que nécessaire pour le service rendu.

Par exemple une page web faisait 14ko en 1995 et 1600ko en 2015. Pourtant on écrit pas 115 fois plus vite un courriel, on ne commande pas 115 fois plus vite un livre, etc… Les services ne se sont pas améliorés quantitativement avec la puissance utilisée.

Je me fais moi même souvent la réflexion qu'une suite bureautique rame autant sur mon mac de 2013 que sur mon Aptiva de quand j'étais ado, pour le même service rendu.

Les auteurs font une évaluation de la consommation du Web :

  * 1037 twh d'électricité, soit 40 à 50 centrales nucléaires et deux fois la consommation de la France.
  * 608 millions de tonnes équivalent CO2 (87 millions de français)
  * 8,8 milliards de m3 d’eau, 160 million de français.

Et par internaute ça donne :

  * 342 kwh d'électricité (soit l'équivalent 10 ordinateurs portables pendant un an)
  * 203 kg équivalent CO2
  * 3000 litres d’eau.

Un autre chiffre qui fait peur : 90% des courriels sont des spams.

_Obsolescence programmée_

Les services trop coûteux contribuent à l'obsolescence programmée en incitant les gens à changer d’appareils !

De plus ces logiciels gourmands augmentent la fracture numérique : un utilisateur ne peut utiliser les outils dans de bonnes conditions si son terminal est trop vieux, trop lent, &#8230;

Il y a deux cent fois plus de terminaux coté client que coté serveur.

Un ordinateur de bureau dure à peu près aussi longtemps qu’un serveur (4 à 6 ans), par contre un smartphone dure entre dix huit et vingt quatre mois. Ce renouvellement rapide consomme d'autant plus de ressources.

_Efficience vs efficacité_

Les auteurs préconisent l'efficience, c'est à dire utiliser le moins de ressources possibles, et non la performance, c'est à dire aller plus vite, faire plus, plus fort.

En pratique, les actions mises en œuvre se ressemblent pas mal.

## **La démarche**

Comment réduire l'impact environnemental des logiciels ? Augmenter leur efficience ?

Les auteurs listent trois principes fondateurs sur lesquels s’appuient les pratiques :

  * _Simplicité_  : Démarche qualitative : éviter l’usine à gaz.
  * _Frugalité_ : limiter la couverture et la profondeur fonctionnelle au minimum (nombre d’éléments affichés, taux de compression, etc…)
  * _Pertinence_ : une interaction pertinente fait gagner du temps à l'internaute, donc économiser des ressources.

## **Les pratiques.**

Rassurez vous je ne vais pas faire une liste à puce avec cent quinze éléments.

Déjà parce qu'il n'y a pas vraiment cent quinze pratiques dans le livre. Il y a beaucoup de répétition. Par exemple au 
lieu d'écrire « Regrouper, minifier, et compresser les ressources statiques », on a une pratique « Regrouper les fichiers JS », 
une autre « Minifier les fichiers CSS », et ainsi de suite.

Il y a aussi des pratiques très spécifiques à un univers (Drupal, PHP), qui n'intéressent pas tout le monde.

En fait il y en a 115 pour arriver au même chiffre que la multiplication de la taille d'une page Web entre 1995 et 2015 : x115 !

### **Faire un logiciel simple, épuré et efficace**

Les premières pratiques sont assez abstraites mais sans doute les plus pertinentes :

**Éliminer les fonctionnalités non essentielles**

Selon des études (cast software et standish group), 70% des fonctionnalités ne sont jamais ou rarement utilisées. 45% ne sont jamais utilisées.

Ne pas les inclure ou les supprimer réduit le poids du logiciel, donc son cout en ressources.

Cela a aussi pour effet d'en simplifier l'utilisation, puisqu'il y a moins de choses à comprendre.

**Fluidifier l'UX**

Les auteurs ne parlent pas d'UX mais de « processus ».

On comprend quand même quand ils parlent de réduire le nombre d'écrans, le nombre d'étapes, le temps nécessaire pour que l'utilisateur atteigne son objectif qu'il s'agit bien de cela.

Une UX plus efficace n'augmente pas seulement la satisfaction des utilisateurs mais, en réduisant le temps passé sur le site, permet d'en réduire l'impact écologique.

**Favoriser un design simple et épuré**

Ce qui fait moins d’éléments affichés, donc téléchargés, calculés, etc&#8230; C'est aussi plus facile à comprendre pour les utilisateurs.

J'ajoute que c'est totalement à mon gout personnel : j'aime le web blanc et noir, avec du _contenu_ (du texte hein, pas des vidéos), pas les portails clignotants qu'on voit trop souvent.

**Utiliser une approche « mobile first »**

C'est à dire commencer par concevoir le site pour des appareils mobiles, qui ont des petits écrans et sont plus lents que les ordinateurs de bureau.

Cela permet de se focaliser sur l'essentiel au niveau fonctionnalités, et aussi d'être efficient à plein de niveaux : taille des pages, animations, traitements javascript, lisibilité, &#8230;

**Utiliser des traitements asynchrones si possible**

Encourager l'utilisateur à lancer un traitement un arrière plan, puis à aller chercher le résultat plus tard, ce qui limite le temps passé sur le site.

### Les pratiques techniques

On a ensuite beaucoup de pratiques techniques, plus ou moins haut niveau, plus ou moins spécifiques à un univers (drupal, php, etc&#8230;).

Voici une sélection compressée, avec un classement par moi :

**Réduire le nombre de requêtes HTTP et la bande passante utilisée**

  * Regrouper, minifier et compresser les ressources statiques (js, css, &#8230;)
  * Optimiser les images, les fichiers audios et vidéos, les documents PDF, etc&#8230;
  * Utiliser des sprites
  * Préférer des glyphes aux images
  * Utiliser des images vectorielles, optimisées.
  * Mettre en cache tout ce qui peut l’être, et bien utiliser les en têtes Expires, Cache-Control, et les ETags pour que le cache soit le plus efficace possible.
  * Utiliser CSS pour les dégradés ou coins arrondis plutôt que des images
  * Respecter l'historique du navigateur (ne pas forcer de refresh avec les boutons précédent / suivant)
  * Utiliser des polices standards (pour ne pas avoir à télécharger de police)

**Éviter les calculs cotés clients**

  * Envoyer des fichiers CSS, JS et HTML valides
  * Ne pas faire redimensionner les images par le navigateur (avec width, height, &#8230;)
  * Utiliser des sélecteurs CSS efficaces (id, classe), regrouper les déclarations similaires, utiliser les notation abrégées (margin plutôt que margin-top, margin-bottom, etc&#8230;)
  * Fournir une CSS print, pour limiter le nombre de pages imprimées
  * Éviter les animations
  * Faire attention à la manipulation du DOM pour éviter les repaint/reflow inutiles (cacher les nœuds pendant leur modification, ne pas modifier de nœud inutilement, &#8230;)

**Éviter les calculs coté serveur**

  * Favoriser les pages statiques
  * Utiliser des caches pour ne pas accéder à des données ou recalculer des données inutilement
  * Optimiser les images les fichiers audios et vidéos, les documents PDF, etc&#8230; lors du développement initial et pas dynamiquement à chaque accès, quand c'est possible.
  * Utiliser des serveurs virtualisés, et mutualisés, pour partager les ressources avec d'autres services
  * Installer uniquement les services (daemon) indispensables, désactiver les logs inutiles (par exemple de MySQL ou d'apache)
  * Utiliser des solutions performantes (serveurs asynchrones type nginx, &#8230;)

## Conclusion

On le voit les pratiques listées dans le livre sont pour la plupart des bonnes pratiques du web pour d'autres raisons : performance, accessibilité, satisfaction client&#8230;

Tour converge !

Réduire l&#8217;empreinte écologique de son site permet d'en améliorer les performances, l'accessibilité, de réduire sa facture électrique, de réduire la fracture numérique, et, si on améliore l'UX, on peut même augmenter son chiffre d'affaire.

Et si on s'y mettait tous ?