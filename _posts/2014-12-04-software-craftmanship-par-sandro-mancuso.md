---
id: 1031
title: Software craftsmanship par Sandro Mancuso
date: 2014-12-04T18:06:55+00:00
author: Raphaël Lemaire
layout: post
guid: http://raphael-lemaire.com/blog/?p=1031
permalink: /2014/12/04/software-craftmanship-par-sandro-mancuso/
categories:
  - Craftsmanship
  - favorite
---
[<img loading="lazy"  class="alignright size-medium wp-image-1032" src="/wp-content/uploads/2014/12/Capture-d’écran-2014-12-03-à-18.18.15-234x300.png" alt="" width="234" height="300" srcset="/wp-content/uploads/2014/12/Capture-d’écran-2014-12-03-à-18.18.15-234x300.png 234w, /wp-content/uploads/2014/12/Capture-d’écran-2014-12-03-à-18.18.15-798x1024.png 798w, /wp-content/uploads/2014/12/Capture-d’écran-2014-12-03-à-18.18.15.png 1050w" sizes="(max-width: 234px) 100vw, 234px" />](/wp-content/uploads/2014/12/Capture-d’écran-2014-12-03-à-18.18.15.png)

Tolkien dit des hobbits qu'ils aiment les livres contenant ce qu'ils savent déjà, bien écrit noir sur blanc avec de belles illustrations.

J'ai pensé plusieurs fois à cela en lisant le livre de Sandro Mancuso. Il a fait un très bon travail de compilation des pratiques, valeurs et connaissances actuelles, ainsi que de son expérience personnelle. Tout professionnel expérimenté s'y retrouvera.

Le livre n'est maintenant plus disponible en eBook, car les droits ont été cédés pour une version print qui sera disponible le 19 décembre : <https://leanpub.com/socra>.

Quand je lis un livre technique ou conceptuel, j'aime bien faire un résumé, afin de pouvoir « réviser » le contenu de l'ouvrage quand j'en ressens le besoin sans avoir à tout relire. Bien entendu un tel résumé est tout à fait subjectif.

Pour la première fois sur ce blog, je vais rédiger un de ces résumés et le partager. Ce faisant je vais concurrencer Xébia qui s'est [attaqué au même travail pour le même ouvrage](http://blog.xebia.fr/2014/09/24/chaque-semaine-decouvrez-un-chapitre-du-livre-de-sandro-sur-le-craftsmanship/).

Notez que l'auteur a donné un talk reprenant une partie des idées et des anecdotes du livres à Devoxx FR 2014 et que celui-ci est [disponible sur Parleys](https://www.parleys.com/play/536770f0e4b04bb59f502713/chapter0/about).

## Software Craftsmanship par Sandro Mancuso

### L'agilité ne suffit pas

> The number of colourful Post-Its on a white board became their true measure of Agility

Sur beaucoup de projet on constate une gueule de bois agile (_agile hangover_), avec des gros problèmes de qualité.

Le fait est que _l'agilité ne suffit pas_.

Les méthodes agiles, scrum en particulier, se focalisent sur le processus, sur l'adéquation du logiciel au besoin et la réponse au changement, mais ne traitent pas de qualité.

L'auteur fait beaucoup de publicité pour [eXtreme Programming](http://fr.wikipedia.org/wiki/Extreme_programming) et ses différentes pratiques, XP étant une méthode agile focalisée sur la qualité.

### **Software craftsmanship : définition**

L'auteur fait une tentative de définition de l'artisanat logiciel :

> Software Craftsmanship is about professionalism in software development

Il redonne bien sur in extenso le [manifeste](http://manifesto.softwarecraftsmanship.org/) :

  * Not only working software, but also well-crafted software
  * Not only responding to change, but also steadily adding value
  * Not only individuals and interactions, but also a community of professionals
  * Not only customer collaboration, but also productive partnerships

Et détaille sa vision pour chacune des lignes :

  * _Well crafted software_ signifie qualité logicielle. Pas seulement un produit qui fonctionne mais aussi un produit de qualité.
  * _Adding value_ : là il se répète un peu, il reparle de qualité logicielle, [cite la règle du boy-scout](http://programmer.97things.oreilly.com/wiki/index.php/The_Boy_Scout_Rule). Je ne suis pas sur que ce soit la seule façon d'ajouter de la valeur.
  * _Community of professionnals_ : les professionnels passionnés doivent apprendre et partager constamment, via des UG, conférences, blogs, etc&#8230;
  * _Productive partnership_ : le professionnel doit voir ses clients ou patrons comme des partenaires, avec lesquels la collaboration apporte des bénéfices mutuels. Le craftsman n'est pas un ouvrier docile.

Il y a une importante critique contre ce manifeste : à partir du moment où on adhère aux valeurs agiles, il est impossible de ne pas être d'accord avec son contenu. Le manifeste agile au contraire, introduisait un changement de paradigme.

### **L'attitude : bonne volonté et professionnalisme**

> Solving problems is what we are paid for

Il donne l'anecdote d'un projet où il travaillait beaucoup, avec tout le reste de l'équipe, de tôt le matin jusque tard le soir, et ne dormait que quelques heures par nuit, dans sa voiture, se sentant comme un genre de héros&#8230; Pour finalement peu de reconnaissance, le management faisant des horaires normaux.

Avec le recul il critique cette attitude comme peu professionnelle : ils ne se sont pas attaqués aux vrais problèmes.

> We allowed ourselves to be treated as factory workers

Il faut apprendre les leçons des projets précédents, apprendre à dire non, à chercher les vrais problèmes plutôt que de travailler plus fort.

C’est être professionnel de questionner, challenger, critiquer constructivement.

Par contre il ne faut pas dire non sans fournir de solutions ou d'alternatives.

#### _Séniorité_

Dans les années 90, on mesurait la séniorité à la capacité à écrire du code incompréhensible, et tout le monde voulait être architecte. Ecrire du code incompréhensible est irrespectueux et contre productif.

La séniorité est relative, elle dépend du contexte, des personnes à qui on se compare, etc&#8230; et _transiente_, dans le sens où elle ne persiste pas : 5 ans d'expérience en Delphi ne font pas un senior en Scala.

> There is a huge difference between having ten years of experience and having one year of experience repeated ten times

De plus les développeurs modernes ne doivent pas qu’écrire du code : ils doivent parler au client, automatiser les tests et le déploiement, faire des choix techniques, des présentations, des estimations, &#8230; tout cela fait partie de l'expérience et de la séniorité.

#### _Sur le poste d'architecte_

Sandro se moque du travail des architectes et de l'idée de big design up front : comme on ne connait pas encore le système et son évolution on a tendance à ajouter des abstractions et des design patterns partout.

> Today we would call it over engineering and stupidity. Back then we called it architecture and seniority.

Après avoir été architecte quelques mois il décide de redevenir développeur.

### **Working software**

Certes, avoir un beau code n’est pas suffisant pour qu’un projet soit réussi : il peut y avoir une mauvaise stratégie business, des concurrents plus forts, une mauvaise gestion de projet, un mauvais pricing, un time to market trop important, etc&#8230;

Mais tout de même dans un projet logiciel, le plus important c’est quand même le logiciel.

> Working software is not enough : loads of Agile projects are producing bad working software

Les développeurs ont souvent une mauvaise notion du temps, se pensant toujours sous pression, et cherchant toujours à aller vite.

Il faut éviter les réflexions du genre “on verra ça plus tard” : on aura pas plus de temps plus tard. Il n'y a pas une personne hypothétique dans le futur qui a plus de temps. C'est plutôt souvent l'inverse.

Nos clients et employeurs sont intéressés par des logiciels qui correspondent à leurs besoins et peuvent être modifiés presque aussi vite qu'ils changent d'avis.

> The difference between projects in different companies is normally just the size of the mess they are in.

Produire du code de qualité fait partie du travail quotidien, c'est de la routine, pas quelque chose que l'on fait dans un second temps. Ainsi il ne faut pas avoir une tâche « tests », les tests font partie du travail, point. De même la règle du boy-scout doit toujours être appliquée pour du code legacy.

Le code legacy, plutôt que de le voir comme une corvée, on peut le voir comme un puzzle intéressant, qui nous oblige à penser différemment et nous offre une occasion d’améliorer les choses.

_The cost of low morale_

Avoir des gens non motivés, venant travailler comme des zombies et attendant qu’il soit 5h pour partir, est mauvais pour les projets.

Dans un contexte où la plupart des gens sont peu motivés et n’ont pas envie de s’améliorer, il est très difficile pour une seule personne de changer les choses.

Un craftsman, à la différence des autres, est en mission, en mission pour améliorer les choses, et inspirer les gens autour de lui.

### **Carrière**

Le craftsman est en charge de sa propre carrière.

Il doit se garder à jour :

  * en lisant des livres
  * en lisant des blogs
  * en suivant les bonnes personnes sur twitter
  * en pratiquant 
      * faisant des katas,
      * ayant un _pet project_
      * en contribuant à des projets open source.
  * en participant aux users groups

Pour Sandro, il faut avoir un blog, sans trop se préoccuper de ce que vont penser les lecteurs du contenu, le but étant surtout d'écrire pour soi même, car écrire sur un sujet permet de mieux le maitriser.

Il donne des petits trucs pour « créer du temps », c'est à dire libérer du temps pour toutes ces tâches de veille, et pour mieux se concentrer :

  * Moins de TV, d'internet non productif, de réseau sociaux, de jeux.
  * aller à un café avec du wifi plutôt que de travailler chez soi.
  * garder son iPad/Kindle à portée pour lire des trucs dès qu’on a un moment.

Il donne des conseils de gestion de carrière :

> You’ve got to be careful if you don’t know where you’re going because you might not get there.

Pensez à votre carrière comme à un projet sur plusieurs années : une fois qu'on a une bonne vision projet – le but – on prend les besoins les plus importants, on coupe en petites tâches, et on itère, en tenant compte du feedback.

Si on est pas sur de ce qu'on veut faire, on peut ouvrir des portes, créer des situations où les opportunités se présenteront. Par exemple :

  * Etendre notre savoir technique, étudier des choses en dehors de notre zone de confort, des nouveaux langages et nouvelles technologies.
  * Aller à des user groups et des événements techniques
  * Réseauter.
  * Blogger sur ce qu'on apprend et sur ce que l'on fait.
  * Contribuer à des projets open source.
  * Développer des projets personnels et les rendre publics.
  * Aller à des conférences
  * Présenter à des conferences

Ce que souhaite un craftsman dans son travail (à part de l’argent) :  l'autonomie, la maitrise (au sens être un maitre artisan) et avoir un but.

### **Recrutement**

> The first thing to do when hiring a new person is to make sure we are not making our existing problem bigger

Il n’aime pas les fiches de poste, qui ne devraient pas être utilisées selon lui. Il critique par exemple la présence de chiffres absolus, du style « 5 ans d'expérience », ce qui ne veut pas dire grand chose, ou du matching de mots clefs, de listes de technologies, avec une forte probabilité de perdre de bons profils, alors qu’apprendre fait partie du métier.

Il donne tout de même un exemple de fiche de poste correcte selon lui. Très verbeuse, elle insiste sur la motivation du développeur, décrit son role, décrit la société, avec les technologies qu’elle utilise (et non les technologies que l’on souhaite voir maitrisées par le candidat).

Il conseille aux entreprises de recruter dans les user groups (d’après mon expérience les gens ne vont pas aux UG pour recevoir des offres d’emploi,  mais c’est peut-être différent au RU), de recruter des gens qui posent des questions sur l’entreprise et le projet, tirent des leçons de leurs expériences et cherchent à s’améliorer.

Toujours pour les entreprises il conseille d'éviter les questions encyclopédiques ou les QCM : mieux vaut avoir une conversation sur le monde réel, des scénarios, des solutions, etc&#8230; Il plébiscite également le pair programming, éventuellement sur la machine du candidat.

Il n'aime pas les questions du genre « combien on peut mettre de balles de golf dans un avion ? », qui n’ont rien à voir avec les compétences attendues.

Pour les développeurs, qui doivent choisir leurs missions, il donne les trucs suivants :

  * c’est mauvais signe si on est interrogé par des managers et pas des développeurs, cela veut dire qu’ils n’ont pas de pouvoir de décision.
  * un processus de recrutement à plusieurs étapes indique plus de soin dans le recrutement
  * les questions posées renseignent sur ce que l’interviewer valorise le plus, c'est un bon indicateur de la culture de l'entreprise

> A good interview is like a good and informal chat between passionate developers

### **Culture de l'apprentissage**

> Creating a culture of learning is one of the most efficient ways to inject passion into a company

Sandro donne des idées pour créer une culture de l'apprentissage (_culture of learning_) dans une société :

  * Mettre en place un club de lecture de livres techniques
  * Organiser des [BBL](http://www.brownbaglunch.fr/)
  * Organiser des discussions ; lightning talks internes et discussions techniques informelles
  * Changer de projet pour une itération, ou pour quelques heures  : permet de bénéficier du recul d’un regard extérieur et de partager les connaissances
  * Faire des code reviews en groupe
  * Organiser des _hands on_ des _katas_, des communautés de pratique

S'il est impossible d'organiser ces activités pendant les heures de travail, cela peut se faire  tôt le matin, le soir ou pendant les repas.


### **Driving technical changes**

> After a short period of time in a new project or organisation, ideas for improvements start popping into our heads like popcorn in a microwave oven.

Dans ce chapitre, on a droit à un petit guide sur l'introduction d'une nouvelle pratique ou d'un nouvel outil.

Sandro liste les différents profils à convaincre :

  * _Le Non informé_ : ne connait pas la pratique ou l’outil.
  * _Le membre du Troupeau_ : ne se sent pas assez expérimenté pour prendre des décisions, mais suivra facilement.
  * _Le cynique_ : va questionner pour le plaisir de se montrer plus intelligent. « Looking smart is more important than being smart ».
  * _Le désabusé_ : il a essayé (par exemple TDD) mais ça n’a pas bien fonctionné, et est maintenant fermé à l'idée.
  * _Le surbooqué_ : n’a “pas le temps” d’apprendre, et ne voit pas les gains potentiels.
  * _Le boss_ : ne va pas comprendre (mais ce n’est pas son problème en fait).
  * _L’irrationnel_ : changera d’argument à chaque fois que l’un sera réfuté.
  * _L’indifférent_ : n’est pas impliqué. Le problème c’est que l’indifférence peut mener à de mauvaises implémentations de bonnes idées, par exemple de mauvais tests peuvent être pires que pas de tests.
  * _Le persécuté_ : il pense que l’entreprise le traite mal et nuit au projet en attendant sa prime de licenciement.
  * _L’inapte_ : pas forcément non motivé, mais incapable de faire le travail.
  * _L’architecte tour d’ivoire_ : il croit tout savoir et a un pouvoir de décision (au sens responsible mais pas accountable), mais n'a pas touché au code depuis des années.
  * _L’insecure_ : développeur en zone de confort, installé depuis longtemps, qui a peur qu’on se rende compte qu’il n’est pas si bon.
  * _Le fanboy_ : entièrement dévoué à un seul sujet, souvent expert pointu sur le sujet en question, et voulant tout faire avec.

Afin de convaincre il faut bien maitriser son sujet, pouvoir énoncer l’idée avec simplicité, adapter son vocabulaire à l’interlocuteur  (PO, manager, ops, dev). Il faut respecter les gens, ne pas penser qu’ils sont stupides parce qu'ils ne connaissent pas ou ne comprennent pas tout de suite.

Il faut construire la confiance : l’équipe doit reconnaitre le craftsman pour sa compétence, et pour cela il faut produire du logiciel de qualité, mais aussi le faire de manière visible, faire du bon travail en silence dans son bureau n’est pas suffisant

On peut ensuite informer le non informé, influencer le troupeau, désarmer le cynique, le fanboy, le surbooqué et l’architecte avec de bons arguments, comprendre les problèmes qu’a rencontré le désabusé pour le convaincre qu’on peut faire mieux, ignorer l’irrationnel, montrer l’exemple pour l'indifférent et l’inapte.

On ne peut rien faire pour le persécuté, il faut attendre qu’il soit viré

Le boss n’a pas à être convaincu, les pratiques techniques ne sont pas de son ressort, il fait confiance à son équipe pour délivrer du logiciel de qualité, le comment est le problème de l’équipe.

Il est impossible de vouloir changer tout le monde

  * Etre un exemple
  * Se focaliser sur ceux qui sont motivés
  * Ne pas forcer, inviter
  * Choisir ses batailles : on ne peut pas tout faire en même temps, il faut prioriser

## Conclusion

Voilà, désolé si cela parait décousu, c'est fait à partir de notes prises en cours de lecture. Le livre est bien sur beaucoup plus complet, plus développé et contient plus d'anecdotes issues de la carrière de l'auteur.

&nbsp;