---
id: 956
title: Attitude et éthique du développeur.
date: 2014-11-18T16:08:15+00:00
author: Raphaël Lemaire
layout: post
guid: http://raphael-lemaire.com/blog/?p=956
permalink: /2014/11/18/attitude-et-ethique-du-developpeur/
categories:
  - Craftsmanship
  - favorite
---
Après pas mal d’années dans le service, pour différents clients, différents projets et dans différents contextes, après maintes lectures de livres et d’articles, je me suis forgé intérieurement une idée de l'attitude à avoir dans le métier, et l'envie m'est venue mettre cela par écrit et de partager.

Je me reconnais beaucoup dans l'idée derrière le[ software craftsmanship](http://fr.wikipedia.org/wiki/Software_craftsmanship) que nous sommes des artisans, taillant avec nos mains de beaux produits, responsables de leurs qualité, réfléchissant sur notre travail.

J'ai aussi beaucoup d'atomes crochus avec l'agilité.  En XP en particulier, on liste [cinq valeurs](http://fr.wikipedia.org/wiki/Extreme_programming#Valeurs) : communication, feedback, simplicité, courage, respect. On verra qu'on peut les retrouver dans la suite de l'article .

### **Produire du logiciel**

#### _Se focaliser sur le projet_

Le but d’un professionnel devrait d’abord être le bien de son projet. C’est pour faire avancer leurs projets que nos clients nous appellent, que nous nous levons tôt et faisons trois quart d’heure de trajet en métro tous les matins.

_Il faut s'intéresser au projet_ : pourquoi a-t-il été lancé, pour quel besoin ? Quel est le planning ? Est-on dans les temps ? Dans quel état de qualité est-il ? Comment peut-on améliorer les choses ? Comment les tâches sont-elles gérées ? Est-ce efficace ?

Ca peut paraître évident mais j'ai vu souvent des gens s'intéresser assez peu à ces questions, le pensant sans soute géré par d'autres. Pour moi il est difficile de faire du bon travail en regardant que des détails épars (le ticket du moment par exemple) .

#### _Etre productif_

> Good enginners ship
  
> &#8212; Tracy Kidder

Produire, cela signifie en premier lieu être productif : il faut implémenter des fonctionnalités, corriger des problèmes, fermer des tickets, des stories, déplacer des post-it (avec une qualité raisonnable bien sur, j’y reviendrais).

Beaucoup de développeurs sont contents quand ils ont passé du temps à intégrer un nouvel outil ou qu’ils ont réalisé quelque chose de compliqué ou tape à l’œil. De mon coté, _ma satisfaction est corrélée au nombre de tâches que j’ai terminées_. A la valeur produite pour le client. J'ai toujours une _todo list_ et une _done list_.

La référence en matière de productivité est le livre [Getting things done](http://fr.wikipedia.org/wiki/Getting_Things_Done) que je conseille à tout le monde, quel que soit sa fiche de poste.

#### _Simplicité : être pragmatique_

> La simplicité est la sophistication ultime.
  
> &#8212; Léonard de Vinci

Mettre en avant la production de valeur pour le client plutôt que l’accomplissement technique amène à éviter certaines dérives courantes comme l’over engineering.  On aura aussi moins tendance à se perdre des heures ou des jours dans une tâche technique. Le pragmatisme et la simplicité sont depuis longtemps des principes encouragés (voir par exemple les [YAGNI](http://fr.wikipedia.org/wiki/YAGNI) et [KISS](http://fr.wikipedia.org/wiki/Principe_KISS))  mais pas toujours bien assimilés ni appliqués.

[<img loading="lazy"  class="aligncenter size-medium wp-image-977" src="/wp-content/uploads/2014/11/the_general_problem-300x125.png" alt="the_general_problem" width="300" height="125" srcset="/wp-content/uploads/2014/11/the_general_problem-300x125.png 300w, /wp-content/uploads/2014/11/the_general_problem.png 550w" sizes="(max-width: 300px) 100vw, 300px" />](/wp-content/uploads/2014/11/the_general_problem.png)

Un exemple de manque de pragmatisme : j’ai déjà vu sur un projet, les intégrateurs faire toute l’intégration d’un site avec [flexbox](https://developer.mozilla.org/en-US/docs/Web/Guide/CSS/Flexible_boxes), puis passer des jours à tout refaire dans une autre feuille de style pour IE, alors qu’il était établi dès le départ que IE8 était dans la cible. Ils avaient envie d'utiliser flexbox, ce qui est compréhensible, mais dans ce contexte c’était une perte de temps pour tout le monde. La bonne technique aurait du être de faire une version correcte sur IE8, avec les techniques utilisables ([ça ne manque pas](http://blog.goetter.fr/articles/les-grilles-en-css/)), et d’ajouter ensuite les beaux dégradés, ombres, etc… que permet CSS3.

_CV Driven Development_: ce n’est pas un but dans un projet d’avoir le plus d’outils possible. La taille du `package.json` ou du `pom.xml` ne rend pas le projet plus intéressant. Chaque dépendance ajoute de la complexité, et doit être bien réfléchie.

#### _Respect : il y a toujours un contexte, une histoire, des contraintes_

Il y a toujours ou presque un contexte dans lequel on travaille. D’autres systèmes avec lesquels interagir, pas forcément pratiques (« quoi du SOAP ? »), parfois vraiment anciens (« ce vieux système mainframe est vraiment bizarre est limité »). Il faut faire avec. Dans un SI de taille significative, il est impossible que tout soit toujours flambant neuf, implémenté avec la dernière technologie à la mode. Un DSI ne va pas refaire en Scala ou en Java 8 son mainframe qui est le cœur du business de la boite et qui a pris des années à être implémenté. Ce serait couteux, dangereux et peu utile.

La bonne attitude n’est pas de râler ou de troller mais de réfléchir et de proposer des solutions, par exemple une couche de médiation pour transformer du SOAP mal formaté en JSON mignon.

#### _Respect : Respecter la productivité des autres_

[<img loading="lazy"  class="alignright size-medium wp-image-975" src="/wp-content/uploads/2014/11/interrupt-300x203.png" alt="interrupt" width="300" height="203" srcset="/wp-content/uploads/2014/11/interrupt-300x203.png 300w, /wp-content/uploads/2014/11/interrupt-1024x693.png 1024w, /wp-content/uploads/2014/11/interrupt.png 1346w" sizes="(max-width: 300px) 100vw, 300px" />](/wp-content/uploads/2014/11/interrupt.png)

Vous trouvez ça pénible quand quelqu’un vous interromps en pleine réflexion pour poser une question ou ajouter une petite tâche ? Ne le faites pas subir aux autres.

S’il n’y pas d’urgence, pas de raison d’interrompre la personne en lui parlant ou en lui téléphonant ; soyez asynchrone : envoyez un mail ou un message chat (Skype, ou autre, si votre équipe l’utilise). Groupez aussi les questions, attendez d’en avoir plusieurs c’est plus efficace pour tout le monde.

De même, _déléguer prend du temps_ : il faut expliquer la tâche et vérifier son exécution. Si la tâche ne prend que quelques minutes il est contre productif de la déléguer. J’ai eu une fois un manager qui m’a à plusieurs reprise demandé d’éditer une page wiki (à l’oral, donc en coupant ma tâche en cours), alors qu’il aurait pu faire modifications lui même en quelques dizaines de secondes.

#### _Courage : être présent en cas de crise_

[Les problèmes, ça arrive](http://fr.wikipedia.org/wiki/Loi_de_Murphy). Découvrir un bug bloquant en prod, voir passer un commit qui casse tout la veille d’une démo importante, … Il peut y avoir plein de situations d’urgence, de crise, et dans ces cas là il faut être prêt à offrir son aide, à réparer ce qui est cassé, que cela soit de notre faute, ou non.

### **Le produire bien**

En tant que professionnel, on doit non seulement produire un logiciel, mais aussi un logiciel de qualité.

#### _Respect : être lisible_

Un code ou une architecture très complexe demande une certaine forme d’intelligence pour être mis en place, mais la personne qui vous relire et essayer de vous comprendre va vous hair. Vous lui ferez perdre son temps, et par conséquent le temps et l’argent du client. Comme le relève [Sandro Mancuso](https://twitter.com/sandromancuso), écrire quelque chose de cryptique est un manque de respect pour les personnes qui vous relit.

Exemple : que fait ce code ?

```javascript
var total = (Math.max(0, Math.min(base, 11991) - 6011)) * 0.055
+ (Math.max(0, Math.min(base, 26631) - 11991)) * 0.14
+ (Math.max(0, Math.min(base, 71397) - 26631)) * 0.3
+ (Math.max(0, Math.min(base, 151200) - 71397)) * 0.41
+ Math.max(0, base - 151200) * 0.45;
```


Pas évident hein ? La version ci dessous est plus verbeuse mais plus claire (peut-être perfectible mais ce n'est pas le sujet) :

```javascript
function calculImpotSurLeRevenu(revenu) {
    var tranches = [
        { "seuil" : 0, "plafond" : 6011, "taux" : 0.0 },
        { "seuil" : 6011, "plafond" : 11991, "taux" : 0.055 },
        { "seuil" : 11991, "plafond" : 26631, "taux" : 0.14 },
        { "seuil" : 26631, "plafond" : 71397, "taux" : 0.3 },
        { "seuil" : 71397, "plafond" : 151200, "taux" : 0.41 },
        { "seuil" : 151200, "plafond" : null, "taux" : 0.45 }
    ];
    
    var impotSurLeRevenu = tranches
        .map(impotParTranche)
        .reduce(function (tranche1, tranche2) { return tranche1 + tranche2}, 0);
    
    return impotSurLeRevenu;
}
    
function impotParTranche(tranche) {
    if (revenu < tranche.seuil) {
        return 0;
    }
    var borneMax = revenu;
    if (tranche.plafond !== null) {
        borneMax = Math.min(revenu, tranche.plafond);
    }
    var imposablePourLaTranche = borneMax - tranche.seuil;
    return imposablePourLaTranche * tranche.taux;
}
```

#### _Simplicité (humilité) : tester, tester, tester !_

> In God we trust, Everything else we test. – <a class="twitter-atreply pretty-link" dir="ltr" href="https://twitter.com/Ly_Jia"><s>@</s><b>Ly_Jia</b></a>

Je ne m'attarde pas c'est la base : écrire des tests automatique et toujours tester en vrai avant commiter. C'est la seule façon d'être confiant que ça marche.

#### _Courage et humilité : accueillir le feedback, même négatif_

(et paf trois valeurs dans le même sous titre!)

Analyse statique, code review, recette, dialogue avec le métier, démos ratées, remarques des autres collaborateurs&#8230; Il y a plein de sources de feedback sur notre travail, qui souvent lèvent des problèmes et amènent des corrections et améliorations possibles; donc du travail. C'est positif! C'est bon pour le projet! Accueillons le avec plaisir et améliorons notre produit.

#### _Courage : il n'y pas de fatalité sur la qualité_

> We are what we repeatedly do. Excellence, then, is not an act, but a habit.
  
> &#8212; Aristotle

Quel que soit le niveau de qualité d'un logiciel, il n'y a pas de fatalité, on peut toujours améliorer les choses, petit à petit. La [règle du boy scout](http://programmer.97things.oreilly.com/wiki/index.php/The_Boy_Scout_Rule) est emblématique à ce niveau : toujours laisser les choses plus propre qu'on les a trouvées, rendre le monde meilleur. C'est aussi une marque de respect pour les suivants :-).

### Relations avec les collaborateurs

#### _Communication : être pédagogue et empathique avec les collaborateurs peu techniques_

[<img loading="lazy"  class="alignright size-medium wp-image-972" src="/wp-content/uploads/2014/11/users-300x262.jpg" alt="users" width="300" height="262" srcset="/wp-content/uploads/2014/11/users-300x262.jpg 300w, /wp-content/uploads/2014/11/users.jpg 381w" sizes="(max-width: 300px) 100vw, 300px" />](/wp-content/uploads/2014/11/users.jpg)

Tout le monde ne connait pas les difficultés de CSS, les niveaux d'isolation des transactions ou la différence entre SOAP et JSON. Il faut savoir se placer à un plus haut niveau, et comprendre les questions et problématiques des collaborateurs, au delà de leurs implications techniques (en général, qu'est-ce qui est faisable, à quel coût). S'il y a vraiment besoin, on peut recourir à des métaphores pour expliquer certains problèmes.  Ne parler que technique, même avec des gens dont ce n'est pas le métier et que cela intéresse peu laisse une image de geek perdu dans son monde, qui s'intéresse peu à la finalité du projet ou de l'entreprise.

#### _Respect : pas de bashing des autres pour leur niveau ou leur poste_

Tout le monde n'a pas le même niveau, la même motivation à apprendre, à faire de la veille. On peut aussi oublier des choses si on n'y a pas été confronté depuis longtemps. La bonne attitude : répondre aux questions, expliquer, encourager la curiosité et l'apprentissage.

#### _Respect : pas de troll sur les technologies_

Chaque technologie a sa philosophie, ses points forts, ses points faibles. Cela implique des choix techniques (ex : je travaille surtout en Java et Javascript et pourtant j'utilise wordpress, donc PHP) à faire.

Il n'y a par contre aucun intérêt à troller des heures sur la verbosité de Java ou la lenteur de Ruby. Cela peut susciter des séparations inutiles entre des équipes et des gens qui par ailleurs pourraient très bien s'entendre.