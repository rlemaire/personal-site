---
id: 696
title: 'FIXME & TODOs'
date: 2012-12-25T23:28:19+00:00
author: Raphaël Lemaire
layout: post
guid: http://raphael-lemaire.com/blog/?p=696
permalink: /2012/12/25/1-fixme-todos/
categories:
  - Craftsmanship
---
Nos IDEs reconnaissent des tags TODO, FIXME et XXX, etc&#8230;, permettant de spécifier que quelque chose est à faire, ou pourrait être à faire, dans le code d'un projet. Je n'en écris plus, et je n'aime pas en voir dans du code sur lequel je travaille. Voici mes arguments contre :

### Definition of Done

> « Do or do not, &#8230; »

On ne devrait pas laisser de morceaux inachevés quand on réalise une tâche. Or commiter du code avec un commentaire de ce type signifie quelque part que l'implémentation n'est pas terminée.

On a deux cas :

  * Soit le point relevé dans le `TODO` est à faire dans le cadre de la tâche, et dans ce cas la tâche n'est terminée que quand celui-ci est fait.
  * Soit il n'est pas indispensable, au moins pour le moment et dans ce cas (KISS, YAGNI, tout ça, &#8230;) il n'est pas à faire, du moins pour le moment.

Dans le second cas, on peut laisser un commentaire expliquant ce qui pourrait être amélioré si le besoin se fait sentir (exemples : optimisation des performances, gestion plus fine des différents cas, &#8230;), mais sans laisser de flag, ainsi on a l'avantage d'offrir de l'information au développeur suivant, sans marquer le projet comme inachevé. Un `TODO` c'est de la dette, un commentaire c'est de la doc.

### Effet tâche cachée

Autre point gênant : Les `TODO` sont en quelque sortes des tâches « cachées » dans le code : à moins d'afficher la vue adequate dans l'IDE, ce que peu de gens font (y compris parmi ceux qui en écrivent) on ne les voit pas. Ils resteront donc intouchés et non implémentés pendant une bonne partie de la vie du projet; ce qui peut amener à avoir l'équivalent de jours, voire de semaines de travail en `TODO` et `FIXME`.

Et en fait, il y a d'autres outils pour gérer les tâches :

Pour la plupart des projets, on utilise un bug tracker. Donc si quelque chose ne peut pas être réalisé à un certain moment, parce qu'il manque un pré requis par exemple, ou que cela représente trop de charge pour l'itération en cours, cela devrait apparaitre dans le bug tracker plutôt que dans le code, afin d'éviter cet effet de tâche cachée.

Autre avantage de passer par le tracker : comme bien souvent beaucoup de collaborateurs, notamment des responsables et des fonctionnels y ont accès cela permet aussi de filtrer les todos en se posant les questions « Est-ce vraiment nécessaire ? », et surtout : « Ne devrais-je pas le faire tout de suite en fait ? »

### Conclusion

Il ne devrait pas y avoir de `TODO` dans le code : soit il faut le faire tout de suite, soit ce n'est pas vraiment utile.

### Bonus : Et si on en écrit un quand même ?

Si malgré cela on en écrit tout de même, il faut se souvenir que peut-être quelque d'autre s'en occupera, peut-être un an plus tard, et donc laisser assez d'information pour que le point puisse être corrigé.

Exemple d'informations insuffisantes :

`// TODO Erreur`

Est-ce qu'on devrait remonter une erreur ? Est-ce qu'une erreur se produit parfois ? Laquelle ? Pourquoi ?

&nbsp;