---
id: 925
title: Anglais ou Franglais?
date: 2014-07-15T21:51:01+00:00
author: Raphaël Lemaire
layout: post
guid: http://raphael-lemaire.com/blog/?p=925
permalink: /2014/07/15/anglais-ou-franglais/
categories:
  - Craftsmanship
---

Il y a un dilemme qui revient fréquemment : est-ce qu’il faut utiliser le français ou l’anglais pour le code métier ?

**Avantages de l’anglais**

  * C’est plus concis que le français.
  * Cela ne fait pas bizarre avec les conventions java bean. On a pas de `isParticulier()`, `getPrenom()` et autres mélanges.
  * C’est plus consistant avec les diverses API, frameworks, outils, etc… que l’on peut utiliser.

**Mais :**

  * On traduit souvent mal les termes anglais. Combien de fois a-t-on vu « code postal » traduit en « zip code » alors que zip est spécifique aux US ?
  * Il y a des traductions discutables, par exemple « département » en « department ». Il n’y a pas de département dans les pays anglophones, c’est une division administrative française qui date de Napoléon. Department a plus le sens d’une division d’une entreprise.
  * Il y a des choses complètement intraduisibles. Par exemple SIREN est un acronyme utilisable uniquement dans l’administration française.

**Traduire est un métier**


Il s’agit là des cas les plus simples. La plupart du temps, on construit une application qui répond à un besoin métier, 
et la plupart des métiers ont leur jargon. Pensez à la finance, au commerce (rien que la nuance entre soldes et 
promotions, c’est traduisible ça ?) ou encore au juridique. Là traduire c’est compliqué, trouver la bonne nuance, le bon
 terme qui est vraiment l’équivalent du terme français… C’est un métier en soi.


**On s’éloigne du vocabulaire métier**


Enfin traduire implique que l’_on utilise plus le même langage que le métier_. Cela oblige à avoir un mapping mental 
en permanence entre le vocabulaire de nos partenaires et l’implémentation de leurs besoins.

**Et l’i18n ?**

Alors me direz-vous, il y a des applications déployées à l’international, sur plusieurs pays ? Mais là typiquement, il y 
a déjà une traduction faite par des gens dont c’est le métier. Donc la question ne se pose pas, ou alors à un niveau plus global.

**Problème des diacritiques.**

On pourrait faire une autre objection à l’utilisation du français : les diacritiques. En français l’accent est porteur 
de sens. Sans lui on mange des biscuits au beurre _sale_ ou encore on ne peut pas différencier relève et relevé.


Mais généralement ce n’est pas un problème, le contexte permet de distinguer les différentes valeurs possible pour un mot,
 mon exemple de beurre sale ayant peu de chance de se retrouver dans un projet réel, et même si c'était le cas tout le 
 monde comprendrait bien salé (et on aurait quelques blagues).

Note : Il se trouve qu’en java, ça, ça compile :

```java
public void beurreSalé() {}
```

Après j’avoue je n’ai pas encore utilisé d’identifiant non ascii sur un projet . Mais ça vaudrait le coup d’essayer : 
les problèmes d’encodage dans les sources sont plutôt rares.


**Conclusion**

Pour moi, pour un projet fait en France pour un client français, sans déploiement vraiment prévu à l’international, 
le mieux est de coder en français, quitte à avoir des noms plus longs et des noms en franglais pour suivre les 
conventions Javabeans.
