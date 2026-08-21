---
id: 499
title: 'CSS : Une API peu intuitive'
date: 2012-06-25T22:46:41+00:00
author: Raphaël Lemaire
layout: post
guid: http://raphael-lemaire.com/blog/?p=499
permalink: /2012/06/25/css-une-api-peu-intuitive/
categories:
  - Technique
---
Avec CSS je suis passé par trois périodes.

D'abord, comme tout le monde, je me disais que c'était compliqué, pas fiable et bien relou de devoir vérifier tous les
 navigateurs, d'autant plus que j'ai commencé à l'époque où IE6 était encore incontournable.

Ensuite, à force d'en faire, après avoir lu un petit bouquin et pas mal d'articles, je me suis dis « bon, il faut 
connaitre, mais ça marche bien »

Maintenant je pense que cela a été en partie mal pensé.

**Disclaimer** : J'aime le web! J'aime développer des sites et des interfaces web, et globalement je prends du plaisir 
à écrire des feuilles du style, surtout dans l'ambiance actuelle où cela bouge beaucoup. Mais &#8230;

J'ai lu il y a déjà quelque temps un livre que je conseille vivement : **The design of everyday things**.

<img loading="lazy"  title="The Design of everyday things" src="http://ecx.images-amazon.com/images/I/418eiOV-FSL._BO2,204,203,200_PIsitb-sticker-arrow-click,TopRight,35,-76_AA300_SH20_OU08_.jpg" alt="" width="300" height="300" />

Depuis, quand je n'arrive pas à me servir de quelque chose du premier coup, produit manufacturé, logiciel, site, etc&#8230;
 je blâme les concepteurs qui n'ont pas fait assez attention à l'ergonomie et aux [affordances](http://fr.wikipedia.org/wiki/Affordance). 
 C'est un grand soulagement dans la vie de tous les jours de ne pas se culpabiliser parce qu'on ne trouve pas un menu 
 dans office, qu'on arrive pas à ouvrir son lot de tranches de saumon fumé, ou qu'on tire une porte au lieu de la 
 pousser. Mais ce livre est aussi et surtout une source de réflexion dans mon métier de créateur de logiciels.

Plus récemment je me suis fait la réflexion que les APIs devraient suggérer leur propre utilisation, de la même manière
 que les belles interfaces Apple. Ce qui me conduit à penser qu'à ce point de vue CSS est un échec : ce n'est pas intuitif.

Il y a des choses très bien, comme les sélecteurs, des manques un peu étranges, comme _l'absence de constantes pour les couleurs_ 
(mais pourquoi ?!), mais le positionnement des éléments, le comportement des marges, etc, &#8230; pour moi c'est mal pensé.

Les notions de flux, de flottants, et autres **ne correspondent pas à la manière dont les humains imaginent les objets dans l'espace**, 
ou sur un plan. Je crois que les gens, pas forcément consciemment, pensent en lignes, en colonnes, en « au dessus », 
« en dessous », « à coté », « en haut » et « en bas »&#8230; D'ailleurs la plupart des logiciels que nous utilisons 
au quotidien, type `word` ou `excel` sont conçus sur ce modèle (et le renforcent, du coup).

C'est pour ça que les tableaux de présentations, malgré leurs défauts, ont eu un succès aussi triomphant et durable : 
parce que c'est intuitif. Les éléments sont les uns à coté des autres ? C'est un ligne ! Au dessus ? Une colonne ! 
En en imbriquant et rusant un peu on peut faire beaucoup de choses.

CSS n'a pas cette intuitivité. La plupart des designs, qui viennent naturellement aux graphistes, sont pénibles à 
réaliser. Pénibles au sens où il faut pas mal d'instructions changeant le comportement d'éléments simples, souvent avec
 des astuces obscures, pour avoir trois colonnes qui prennent toute la hauteur dans une page, des onglets dont le bas 
 est collé à l'élément en dessous, des inputs alignés verticalement dans un formulaire, ou un footer qui est en bas même 
 quand il n'a pas beaucoup de contenu dans la page. Il n'y a qu'à voir le nombre d'exemples de designs en lignes : 
 clairement, il y a un manque.

A l'opposé, je trouve les layout managers de swing beaucoup plus intuitifs : border layout, flow layout, grid layout&#8230;
 Parfait! On lit une fois la définition, on sait ce que cela fait, et où et comment s'en servir.

<img loading="lazy"  class="alignleft" title="Border layouit" src="http://docs.oracle.com/javase/7/docs/api/java/awt/doc-files/BorderLayout-1.gif" alt="" width="200" height="200" />

Regardez ce border layout : cela ne rappelle-t-il pas la structure d'à peu près toutes les pages de toutes les applis web,
 au moins en partie ? Header, footer, side bars, &#8230; Ce serait formidable quelque chose comme ça en CSS.

```css
#applet { layout : border; }

#applet #header { layout-position : north; }

#applet #content { layout-position : center; }
```

Et pourquoi pas des composants standards, comme des onglets ou des menus, à l'image des inputs email ou téléphone de html 5 ?

C'est vrai que l'on commence a avoir des choses comme `display : table`, et surtout plein d'outils du genre [LESS](http://lesscss.org/ "Less"), 
mais j'aime la simplicité, et pouvoir faire des choses sans dépendances, sans setup additionnel.