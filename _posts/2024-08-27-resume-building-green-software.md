---
id: 1634
title: "Notes de lecture sur le livre « Building Green Software »"
date: 2024-08-27T00:00:00+00:00
author: Raphaël Lemaire
layout: post
guid: http://raphael-lemaire.com/blog/?p=1634
permalink: /2024/05/30/resume-building-green-software/
categories:
- GreenIT
---
J’ai lu la semaine dernière le livre de Anne Curie, Sarah Hsu et Sara bergman intitulé [« Building Green Software - A sustainable approach to software development and operations »](https://www.oreilly.com/library/view/building-green-software/9781098150617/). Voici un partage de mes notes et impressions.

[<img loading="lazy"  class="alignright" src="/wp-content/uploads/2024/buildinggw.jpg" alt="" srcset="/wp-content/uploads/2024/buildinggw.jpg" />](https://www.oreilly.com/library/view/building-green-software/9781098150617/)

Au niveau de la forme, le livre est bien écrit, plutôt agréable, bien organisé, avec des graphiques et un peu d’humour (« Bruce Banner, green scientist », je ne sais pas si j’aurais osé 😅).

Sur le contenu, ce n’est pas très opérationnel, l’ouvrage se place plutôt au niveau de l’explication des concepts, des définitions, des pointeurs. Il y a des anecdotes issues de quelques projets, un peu d’actualité et aussi des reprises de promesses de différents acteurs. Par moment, il est même plutôt spéculatif.

L’ouvrage est focalisé sur le côté back des applications : opérations, architecture, réseau, observabilité, hébergement, avec une dimension cloud très développée. On y retrouve de nombreux liens vers les produits, les actions et les promesses des trois grands fournisseurs, Google, Amazon et Microsoft.

Cette lecture m’a permis d’avoir quelques liens intéressants à utiliser ou à creuser et m’a donné quelques idées alternatives de présentation pour certaines choses.

J’y ai aussi découvert l’existence de [la certification « Green Software Practitioner »](https://training.linuxfoundation.org/training/green-software-for-practitioners-lfc131/) de la Linux Foundation, que [j’ai donc passé dans la foulée](https://www.credly.com/badges/f6bcdded-2a39-4102-8f5a-2fd95b1e1b7a/public_url).

Au niveau des points négatifs, dès le départ, le livre tombe dans le travers malheureusement courant de se focaliser uniquement sur l’impact carbone, 
au détriment des autres facteurs d’impacts environnementaux. Même l’eau, pourtant utilisée massivement par les centres 
informatiques, est à peine mentionnée. Dans les définitions, le terme carbone est même défini comme un raccourci pour 
parler des gaz à effet de serre en général, alors que l’acronyme GHG (Greenhouse Gases) n’est pas plus long à lire ou 
à écrire. Dans le même ordre d’idées, il y a des oxymores comme « Carbon Free electricity ».

Les auteures sont des technophiles et sont fascinées par les innovations. Il est par exemple question de serveurs faits 
avec des super conducteurs, qui seraient déployés dans l'espace pour être refroidis, il y a un passage sur 
Starlink (voir plus bas), les machines Graviton (sur l'architecture ARM) sont citées plusieurs fois, il est aussi question 
de l'espoir de pouvoir compter sur les appareils clients pour équilibrer la grille électrique avec leurs batteries.

La sobriété numérique, énergétique, et plus globalement matérielle, n'est pas assez mise en avant à mon goût et se limite à des 
optimisations techniques et fonctionnelles, sans interrogation sur les usages. 

Ces points maintenant écartés, voyons les messages que fait passer le livre :

**Sur l'efficacité des logiciels (_code efficiency_) :**
* Travailler sur les performances des logiciels est important et peut amener des gros gains d’efficience. Il faut cependant tenir compte des contraintes systémiques et économiques en termes de productivité des développeurs. Des exemples d’amélioration de l'efficacité sont donnés avec entres autres les efforts de Microsoft pour Teams lors de la pandémie de Covid-19.
* Utiliser une architecture microservices est potentiellement bénéfique, potentiellement dangereux.
* Les services mesh sont plutôt lents et gourmands.
* Le code le plus efficace est celui qui n’est pas écrit : donc faire à attention à supprimer les fonctionnalités peu ou pas utilisées.
* Le paradoxe de Jevons (effet rebond) est bien mentionné ici.

**Sur l'efficacité des opérations (_Operational efficiency_) :**
* Il faut maximiser l’utilisation des machines avec les pratiques opérationnelles classiques : bien dimensionner les composants (VM, conteneurs), pratiquer l’autoscalling, ce qui est en conflit avec le confort de provisionner plus par sécurité, nécessite une grande maturité (IaC, GitOps, utilisation de Kubernetes, possibilité d’éteindre et de démarrer rapidement et de façon fiable…) et n’est pas très intéressant pour les petites charges applicatives. Il y a un triangle « cloud native greenops » qui est intéressant avec ces différentes pratiques.
* Elles défendent les instances _spot_ (ou préemptibles) qui permettent en théorie de remplir les vides chez le fournisseur, ce qui est plus rentable pour lui. Il y a même un cas d’exemple avec Skyscanner qui a basé toute son architecture sur des instances de ce type et du chaos engineering. De même, pour elles, le serverless est intéressant pour les mêmes raisons.
* L’importance de la localisation de l’hébergement est mentionnée : mieux vaut être dans une région où l'électricité est moins impactante.

**Réactivité à l’intensité carbone (_Carbon awareness_)**
* Il est possible de déplacer la charge applicative en fonction de l’intensité carbone de l’électricité (_demand shifting_).
* Le traitement peut être déplacé dans le temps (_time shifting_) ou dans l’espace (_location shifting_). Il est également possible de réduire la charge (demand shifting) de façon dynamique. Par exemple en réduisant la résolution vidéo pour un outil de visioconférence.
* Au niveau des exemples, cette approche est utilisée par Google et Microsoft donc les mises à jour de Windows ou des X-Box sont carbon aware.
* Les API (comme _electricity maps_) et outils (_carbon aware SDK_) nécessaires sont mentionnés.
* Les impacts environnementaux des énergies renouvelables en dehors de l’impact carbone ne sont pas mentionnés, ni l’impact potentiel sur l’équilibre de la grille électrique dans des endroits comme l’Irlande où il y a beaucoup de centres informatiques.
  

**Sur le matériel (_Hardware efficiency_)**
* La longévité trop courte des appareils clients est mentionnée, mais le livre bascule rapidement côté serveur.
* L’utilisation des machines Graviton permet apparemment une économie d’énergie de jusqu’à 60%.
* Pour les exploitants de centres informatiques, sans surprise les conseils sont de faire durer les machines et de les éteindre autant que possible. Il est aussi question de jouer sur le voltage, ce qui me paraît dangereux, mais je ne suis pas expert. L’utilisation de matériels spécialisés (ie pour le machine learning par exemple) est possible mais nécessite des compétences et il faut être sûr que cela soit rentable à long terme.
* Il y a ensuite beaucoup de liens sur les DEEE et une énumération des programmes environnementaux déclarés par les constructeurs.

**Au niveau réseau :**
* L’efficience des différentes options (4, 5 et 6G, WiFi)  est mentionnée.
* Il y a une section sur Starlink où on sent que l’auteur aime le projet mais où elle échoue à lui trouver des côtés positifs. En effet, d’après le texte, les mini satellites nécessitent de l’énergie, augmentent la pollution spatiale et atmosphérique, dégradent les images des télescopes et l’avantage de connecter les zones blanches n’est pas très utile sans programme contre l'illettrisme et les autres limites sociales à l’accès à l’éducation.
* Il y a une spéculation sur la possibilité de rendre le protocole BGP carbon aware pour répartir la charge spatialement qui se conclut négativement, BGP étant critique et déjà trop complexe.
* Les auteurs défendent les CDN  qui réduisent le trafic avec leurs caches et se mettent à jour quand le réseau est peu utilisé.


**Pour le machine learning, l’IA et les LLM**
* Elles parlent de la large croissance des modèles et de leurs usages et préconisent, pour en réduire l’impact, en plus des pratiques déjà mentionnées dans les chapitres précédents, d’en diminuer les dimensions dès la conception, d’utiliser des modèles et jeux de données sur l’étagère, de s'appuyer sur des appareils spécialisés ou encore de solliciter les appareils des utilisateurs pour l'entraînement.
* Il existe une technique appelée _quantization_ qui consiste à utiliser des types de données plus petits, comme des entiers de 8 bits par exemple, pour réduire la consommation de ressources.

**Au niveau de la mesure de l’empreinte carbone :**
* Le chapitre parle beaucoup du bilan carbone (GHG protocol), des standards, de la méthodologie. Des termes comme _offsets_, _PPA_ ou _net-zero_ sont définis.
* Les outils  mentionnés sont Cloud Carbon Footprint, les consoles des fournisseurs de cloud (avec une comparaison de leurs périmètres), Greenspector, ML CO2 impact, les profiler d’Android Studio et de X Code et Kepler. Il n’y a pas d’exemple d’utilisation. Une page de Green The Web listant d'autres outils est fournie en lien.
* Elles défendent bien les métriques proxy (indicateurs techniques et coût de l'hébergement) pour guider les actions sans nécessairement avoir une observation parfaite de l’impact carbone.

A la fin du livre, il y a un chapitre sur les **bénéfices à attendre de la mise en place de la démarche** :
* Réduction des coûts. Elles citent Pini Reznik de re:cinq pour qui il est possible de réduire les coûts jusqu’à 50%. Mais il n’y a malheureusement pas de lien associé à cette citation.
* L’amélioration des performances et de la résilience.
* L’amélioration de la sécurité par la réduction de la surface d’attaque.
* Il y a un passage sur les DDoS où la mise en place d’actions de type limitation du trafic contre ce type d’attaque est encouragée.

Enfin l’avant-dernier chapitre définit une **matrice de maturité** (_green software maturity matrix_) déclinée de la matrice CMMI qui est plutôt bien faite.

**Quelques pépites que je retiens :**
* Un exemple intéressant pour expliquer la différence entre performance, efficience et responsabilité environnementale : le _high frequency trading_. Il s’agit de logiciels très performants, mais au prix de l’utilisation de beaucoup de ressources, donc peu efficients, et dont l’utilité peut-être discutée.
* RPC est 20 fois plus rapide que REST, c’est peut-être intéressant dans certains cas.
* Le _« cloud native greenops triangle »_ est intéressant.
* Une anecdote : netflix envoie les films aux CDN par camion !
* En Espagne, le prix de l’électricité varie selon son intensité carbone et cette politique pourrait se répandre dans d’autres pays.
* La matrice de maturité.