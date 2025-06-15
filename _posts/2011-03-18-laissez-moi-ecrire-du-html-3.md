---
id: 15
title: 'Frameworks : Laissez moi écrire du HTML.'
date: 2011-03-18T09:37:48+00:00
author: Raphaël Lemaire
layout: post
guid: http://random-arguments.fr/?p=15
permalink: /2011/03/18/laissez-moi-ecrire-du-html-3/
categories:
  - Technique
---
Certaines technologies permettant de créer des pages webs, comme JSF ou GWT, cachent le code html final généré, le développeur déléguant celui-ci à l’API. A partir de là, certains pensent qu’il n’est pas nécessaire au développeur de connaître les technologies sous-jacentes pour développer les pages. Ce n’est pas mon avis.

D’abord, dans tout les cas, il faut comprendre ce que l’on fait pour faire du bon travail. Pour moi on ne devrait pas écrire des pages webs toute la journée (même pour un intranet), sans avoir des connaissances correctes en html, css, javascript; http. Pour les même raisons, toute formation sérieuse à la programmation inclut des cours d’assembleur et de compilation.

D’ailleurs, comparer le web (html, css & JS) à l’assembleur est intéressant, mais plutôt inapproprié :

  * L’assembleur est figé au moment de sa sortie à quelques dizaines d’instructions. Le html est en constante évolution, et est beaucoup plus riche, ce qui le rend beaucoup plus difficile à générer correctement par des outils.
  * L’assembleur est le langage du processeur. Il s’agit d'instructions pour une machine, difficilement digérables par un humain. Personne ne s’attend, sur les architectures modernes, à que ce que de nombreux développeurs utilisent directement l’assembleur. Ceux qui le font codent des noyaux systèmes et des drivers.  A l’opposé, le html est fait par et pour des humains. Le w3c s’attend à ce que des humains utilisent directement ses standards.
  * Le html n’est pas bas niveau. On ne dit pas au navigateur quels pixels dessiner, quel registre mettre sur la pile. On lui dit qu’on veut un lien, un champ texte, voire maintenant, en html 5, un champ date ou URL, une section, un menu.

Ces outils ne font de toute façon pas toujours correctement les choses. Par exemple, beaucoup de balises standard de JSF utilisent des tableaux de présentation. Il y a aussi des bugs, et des bibliothèques de tags pas forcement bien écrites (j’ai déjà vu un attribut style=”width : 100%” écrit en dur dans le code généré par une balise d'une API JSF).

Par essence, ces outils ne sont pas à jour. Le web ne s’est jamais aussi bien porté, et les innovations d’HTML 5 et CSS 3 sont passionnantes à suivre. Il est impossible pour un outil de génération de code d’inclure convenablement les dernières nouveautés.

De plus, en ne connaissant pas bien le html, on risque de rater une version plus simple et plus élégante de réaliser ce que l’on souhaite (voyez donc ces pages truffées de widgets pour deux menus et un tableau de données, …), et on risque de ne pas prévoir de dégradation élégante de la page (qu’est-ce qui se passe sans Javascript ? Sans CSS ?), de mettre en péril l’accessibilité, &#8230;

Il y a pourtant un bon argument en faveur de ces outils : la compatibilité entre les navigateurs. Il est vrai qu’il y a ne serait-ce que deux ans, c’était un vrai problème, il fallait que le site tourne sur IE 6, voir IE 5.5, et c’était dur, … Mais dans le paysage actuel des navigateurs l'argument est moins valable. De plus JQuery et consorts aident à se défaire de ces problèmes tout en laissant visible le html final.

Enfin ces technologies ne sont pas inaccessibles. Un développeur dont le quotidien est fait de REST, de SOAP et de Scala, qui lit la JSR de JPA avant de se coucher, aurait peur de CSS ?