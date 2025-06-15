---
id: 451
title: 'P#|@#%* de Validations !'
date: 2012-05-21T22:20:27+00:00
author: Raphaël Lemaire
layout: post
guid: http://raphael-lemaire.com/blog/?p=451
permalink: /2012/05/21/p-de-validations/
categories:
  - Craftsmanship
  - Technique
---
Dans nos applications web et back office du monde Java EE, l’un des problèmes récurrents les plus difficiles est la 
validation des données. Même les données « simples », genre nom, prénom, email posent en fait pas mal de problèmes.

### Nom, prénom ?

_Imaginons un développeur, Bertrand, qui développe un formulaire d’inscription à une newsletter pour un site. Dans les 
spécifications, il y a écrit :_

_« Les noms et prénoms sont constitués uniquement de caractères alphabétiques »_

_Bertrand, dont c’est le premier formulaire (et qui n’a pas d’accent dans son nom), utilise donc une regex du type 
`[a-zA-Z]` pour les deux champs. Et là, le lendemain, l’aMOA qui recette le site lui dit :_

_« Je n’arrive pas à utiliser le formulaire, il me dit que mon prénom est invalide »_

_« Mélanie ? Ah oui je suis bête je n’ai pas autorisé les accents. »_

_Mélanie saisit donc « Melanie » (Meuhlanie), et ça passe. Bertrand se creuse la tête et ajoute à sa regex tous les
 accents qu’il a déjà vu dans un prénom ou un nom. Au test suivant l’aMOA est satisfaite, et time to market oblige, 
 on envoie ça en prod._

_Et là, bim, les utilisateurs appellent, ils ne peuvent pas s’inscrire. Eh oui, impossible quand on s’appelle 
Jacques-Henri de la Roche Meunière. Les espaces et les tirets sont interdits._

_Bertrand et Mélanie s’en veulent d’avoir laissé passer cela. On implémente le fix et en 15 minutes, la nouvelle 
regex (du style `[a-zA-Zéèêëàù -]`) est 
en place._

_Quelques semaines plus tard, un nouvel ingénieur arrive dans la société. Un américain. Bertrand lui demande comment il s’appelle :_

_« James E. Smith Jr. »_

Je ne sais pas vous, mais moi ça m’énerve beaucoup quand un site m’empêche de saisir le **ë** dans mon prénom, parce `
que sans diacritique, ça ne se prononce pas pareil, ce n’est plus mon prénom, c’est [autre chose](http://fr.wikipedia.org/wiki/Dassault_Rafale).

Il y a des gens qui pensent qu’il ne faut pas valider les données de type nom/prénom. Mais dans ce cas on laisse passer
 des gens qui s’appellent `#h$nr| t@t@&lt. C’est un choix… Pour moi valider est important, mais comme le montre
 l’histoire ci-dessus, ce n’est pas forcément garanti d’arriver du premier coup  à la bonne version.

Confronté au problème, comme tous les deux mois, j’ai créé en décembre de 2011 [cette regex](https://twitter.com/#!/rlemaire/status/150140156517687296) : 
`[a-zA-ZÀ-ÖØ-öø-ÿ -]`, en me basant sur la table des caractères unicode, et en essayant d’inclure tous les caractères 
avec diacritiques.

En fait cette version ne comprend pas les points pour notre ami américain avec son E. qui est juste là pour faire classe, mais je les ai ajoutés ensuite.

Et bien sur elle ne reconnaît que l’alphabet latin et ne convient pas pour des utilisateurs russes ou chinois. Pour valider владимир, ça n’ira pas.

La bonne réponse, comme toujours dépend du contexte. Si on s’adresse à un public anglophone, on peut refuser tous les diacritiques et rester sur l’ascii (encore que), pour des occidentaux on peut utiliser la regex ci-dessus, pour une cible mondiale, …

### Email

Ah mais l’adresse email par contre c’est facile me direz-vous, c’est standard, il y a des RFC, etc, …

Ok, quelle est la bonne regex pour valider une adresse mail ?

La plupart des temps les développeurs valident quelque chose du style `[a-zA-Z0-9-_\.]+@[a-zA-Z0-9.-_ \.]+\.[a-zA-Z]{2,4}` : des alphanumérique et quelques caractères spéciaux, un @, et un nom de domaine assez libre, qui finit par `.truc`. Eh bien c’est faux.

Si on regarde sur [Wikipédia ](http://en.wikipedia.org/wiki/Email_address#Valid_email_addresses):

  * `0@a` est une adresse valide. Il n’y a pas forcément de `.truc` à la fin d’un nom de domaine.
  * `!#$%&amp;'*+-/=?^_{}|~@example.org` est une adresse valide.
  * `" une 4dresse biz@rre £"."@&amp;#"@test.com` est valide aussi. En fait on peut mettre ce qu’on veut tant que c’est entre guillemets.
  * Et même `user@[IPv6:2001:db8:1ff::a0b:dbd0]` est valide.

En plus la regex naïve ci dessus laisse passer des cas qui ne devraient pas être autorisés, comme `ab..ab..a@test..com` : on ne peut pas avoir deux points d’affilée (et word reconnaît cela comme une adresse mail et ajoute le lien, funny).

Donc, on doit pouvoir saisir `test@test`. Mais dans 99,99% des cas, **un utilisateur qui saisit une adresse comme celle-ci (valide) se plante.**

Il saisit par exemple `fleurymichou@hotmail` ou `abc123@yahoo`, sans terminer le nom de domaine, et d’un point de vue ergonomique, il est plus raisonnable de ne pas lui valider son mail. Sauf que ce serait faux, et que la personne qui a de bonne foi un email qui ne finit pas par `.truc` est rejetée.

Ici on peut mettre en place un warning, en javascript par exemple, du type :

« êtes vous sur que cette adresse est bonne ? ».

### Epilogue

_Le chef de projet de Bertrand et Mélanie arrive et dit :_

_« Bon, maintenant on va aussi enregistrer l’adresse postale. »_

PS : Pour moi [bean validation](http://jcp.org/en/jsr/detail?id=303) [jsr 303] est une des meilleures idées d'API de ces dernières années : quelque chose de relativement simple, bien intégré dans les outils, qui traite un problème récurrent et peut vraiment faciliter la vie.