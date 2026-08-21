---
id: 149
title: Pourquoi la programmation se fera toujours avec du texte
date: 2011-05-02T10:00:38+00:00
author: Raphaël Lemaire
layout: post
guid: http://random-arguments.fr/?p=149
permalink: /2011/05/02/toujours-utiliser-du-texte/
categories:
  - Craftsmanship
  - Technique
---
<!-- @page { margin: 2cm } P { margin-bottom: 0.21cm } -->Les applications modernes sont en général composées de plusieurs parties, écrites dans des langages différents. On a du java, du xml, du json, d'autres langages encore.

Dans tous les cas le texte prédomine.

Il arrive pourtant parfois que le logiciel s'appuie sur des composants non textuels. J'ai déjà vu la couche présentation programmée en base via une interface graphique ou encore des règles métiers stockées dans des fichiers excel (drools le permet).

On peut aussi imaginer écrire les programmes de manière différente, par exemple en dessinant de l'UML, en décrivant les algorithmes par l'exemple de manière graphique, en faisant des flèches pour les mappings, en imbriquant des boites les unes dans les autres à la manière des paquetages.

Bref utiliser autre chose que du texte.

Mais ce n'est vraiment pas pratique.

Si le texte prédomine dans la programmation, il y a une raison, autre qu'historique : les outils. Tous nos merveilleux outils sont conçus pour fonctionner sur du texte, et font en général des choses formidables avec.

Du texte ça peut se versionner, et surtout se comparer avec des outils permettant de voir les différences entre les versions. On peut aussi y faire des recherches de chaînes, via nos IDE ou la commande grep. On peut lire du texte sur l'importe quelle plateforme, avec des dizaines d'éditeurs différents. Il y a assez peu de problèmes de compatibilité, puisque la source est toujours du texte simple, lisible via vim ou le bloc notes. On peut faire de copier/coller, des remplacements de chaînes, du reformatage. On peut analyser tout ça avec des outils comme PMD. On peut utiliser des compilateurs différents avec le même code source. _Et cetera_.

Comparer des documents office versionnés avec SVN ou Git ne sert à rien (c'est du binaire).

Une recherche de texte ne permettra jamais de trouver le code métier qui apparaît dans la stack, parce qu'il est planqué dans le fichier excel de règles.

Pour ces raisons, aucune autre manière de programmer que par le texte ne s'est popularisée ni ne se popularisera.