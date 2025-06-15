---
id: 1626
title: "Revue de presse - janvier 2024"
date: 2024-01-31T00:00:00+00:00
author: Raphaël Lemaire
layout: post
guid: http://raphael-lemaire.com/blog/?p=1626
permalink: /2024/01/31/revue-de-presse/
categories:
- GreenIT
- Liens du mois
---
Bonjour,

Voici une sélection parmi mes lectures de janvier :-)

GreenIT : 
* La fin de la prise en charge de Windows 10 [pourrait transformer 240 millions de PC en déchets électroniques](https://windows.developpez.com/actu/352229/La-fin-de-la-prise-en-charge-de-Windows-10-pourrait-transformer-240-millions-de-PC-en-dechets-electroniques-en-raison-de-l-incompatibilite-avec-le-systeme-d-exploitation-Windows-11-d-apres-Canalys/).
* Sur le même sujet : GreenIT.fr [se penche sur l’impact environnemental de la décision de Microsoft de ne plus supporter Windows 10](https://www.greenit.fr/2024/01/16/fin-de-windows-10-37-276-687-millions-de-tonnes-eq-co2-evitables/), ce qui va pousser à l’obsolescence un grand nombre de machines : l’équivalent de 4,7 millions de tours du monde ou 10 % des émissions annuelles de GES de la France, ou encore 14 milliards de tonnes de terre excavées.
* [Un « malus écologique » est à l’étude pour les appareils les moins réparables](https://www.lemonde.fr/pixels/article/2024/01/15/un-malus-ecologique-a-l-etude-pour-les-appareils-les-moins-reparables_6210840_4408996.html).
* J'ai beaucoup aimé [cette excellente présentation (en)](https://hollycummins.com/cloud-zombies-qcon-london/) de Holly Cummins sur les serveurs zombies sur le Cloud. On y apprend entres autres que les ressources serveurs sur provisionnées et allumées pour rien ont généré 26.6 milliards de dollars de dépenses en 2021, que 44% des dépenses Cloud sont pour des environnements hors production, que 40% des instances sont surdimensionnés ou encore que 35% des dépenses de stockages sont pour des volumes détachés.
* En creusant cette présentation, je suis tombé sur [ce papier sur la dépense d’énergie des Fonctions as a Service (en)](https://cgi.luddy.indiana.edu/~prateeks/papers/hotcarbon22.pdf). Il indique que les FaaS sont par construction inefficientes à cause de l’overhead du à la virtualisation et aux conteneurs ainsi qu’au *control plane* qui les orchestre chez le fournisseur. Il y est stipulé qu’une fonction peut utiliser jusqu’à 15 fois plus d’énergie qu’un service web « normal ». Les auteurs parlent tout de même d’opportunités comme le déplacement du traitement dans une zone ou à une heure où l’énergie est moins impactante ou le lissage la charge au niveau du serveur et/ou du cluster pour limiter les dépenses d’énergies. J’ajouterais que les FaaS sont pour moi intéressantes si l’opération est peu souvent utilisée et qu’on peut se passer d’une infrastructure toujours up. Sinon, autant avoir un ou plusieurs serveurs/conteneurs déployé(s).
* [Une tribune d’Agnes Crepet et Adrien Montagut dans le monde](https://www.lemonde.fr/idees/article/2024/01/07/smartphone-quand-l-europe-peine-a-trouver-un-consensus-autour-des-definitions-de-durabilite-et-de-facilite-de-reparation_6209517_3232.html) déplore la stratégie européenne sur l’indice de durabilité.
* Le Monde a fait [un article sur son bilan carbone](https://www.lemonde.fr/le-monde-et-vous/article/2024/01/17/le-groupe-le-monde-publie-son-bilan-carbone_6211363_6065879.html), en incluant le scope 3, donc entre autres la phase d’utilisation des appareils numériques des utilisateurs pour lire le journal, qui représente 38 % de l’empreinte carbone totale du groupe. Le numérique pèse plus que le papier en valeur absolue, mais moins par lecteur.
* Boavizta sort [une étude](https://boavizta.org/blog/numerique-responsable-convaincre-hierarchie) pour « Construire un argumentaire en faveur de la mise en place d’une démarche de mesure de l’impact environnemental du numérique et plus largement de sobriété », avec [des arguments que je donnais déjà en 2021](https://blog.zenika.com/2021/03/25/les-avantages-de-lecoconception-et-du-greenit/).
* [Microsoft limite l'espace de stockage cloud dans le secteur de l'éducation](https://microsoft.developpez.com/actu/353202/Microsoft-limite-l-espace-de-stockage-cloud-dans-le-secteur-de-l-education-pour-des-raisons-environnementales-mais-des-observateurs-estiment-que-l-entreprise-cherche-plutot-a-faire-des-economies/) officiellement pour limiter l'impact environnemental et améliorer la sécurité. Il est probable que cela soit aussi pour faire des économies, mais les deux vont bien ensemble. C'est plutôt positif de voir que les grands opérateurs travaillent sur leur offre et leur activité et ne se contentent plus d'acheter des crédits de compensation carbone et de l'énergie renouvelable.


Anecdotes :
* Une histoire intéressante racontée dans Le Monde : au début des années 80, [un collectif de connaisseurs appelé le CLODO (ça ne s’invente pas) sabote et brûle des ordinateurs](https://www.lemonde.fr/pixels/visuel/2023/12/22/l-histoire-oubliee-du-clodo-le-comite-liquidant-ou-detournant-les-ordinateurs_6207257_4408996.html) pour « dénoncer les dangers et les dérives de l’informatique, mais aussi *« lutter contre toutes les dominations »*. ».
* [Un adolescent américain vient à bout du jeu vidéo « Tetris » pour la première fois sur NES](https://www.lemonde.fr/pixels/article/2024/01/04/un-adolescent-americain-vient-a-bout-du-jeu-video-tetris-pour-la-premiere-fois_6208995_4408996.html). Le jeu se fige à ce stade. Jusqu’ici seule des programmes avaient réussi.
* Un serveur [physiquement perdu pendant 4 ans retrouvé derrière un mur (en)](https://www.theregister.com/2001/04/12/missing_novell_server_discovered_after/) (2001).
* Une histoire d’IoT : un ingénieur plonge dans les appareils installés chez lui : [C'est quoi cet écran tactile ? (en)](https://laplab.me/posts/whats-that-touchscreen-in-my-room/)

Technique :
* Cet article (avec des benchmarks) défend l'idée [qu'il est toujours intéressant de rassembler les fichiers (CSS, JS), même avec HTTP 2 ou 3 (en)](https://csswizardry.com/2023/10/the-three-c-concatenate-compress-cache/).
* ZOMBIE (encore! Braaaiinns 🧟), [un moyen mnémotechnique pour identifier les choses à tester](https://craftacademy.substack.com/p/-toujours-savoir-quel-test-ecrire) : Zéro, One, More, Boundary, Interface definition, Exceptional behavior.
* [Une étude de Microsoft](https://azure.microsoft.com/en-us/blog/quantifying-the-impact-of-developer-experience/) menée par Nicole Forsgren (d'Accelerate) trouve que la productivité ressentie des développeurs est corrélée à une charge cognitive faible (haut de degré de compréhension de la base de code), à la présence de boucles de feedback rapides (en particulier lors des code-reviews) et à la réservation de temps dédié pour du « travail profond » (_deep work_) permettant une concentration optimale (_flow state_).

Autres :
* [OpenAI a silencieusement retiré l'inclusion des usages militaires pour chatGPT (en)](https://theintercept.com/2024/01/12/open-ai-military-ban-chatgpt/). Sarah Connor ?
* [Tristan Nitot revient sur le décès récent de Niklaus Wirth](https://www.standblog.org/blog/post/2024/01/05/Deces-de-Niklaus-Wirth), inventeur de Pascal (langage qui m’a fait aimer la programmation et choisir cette carrière), détenteur du prix Turing et auteur de la loi de Wirth « le logiciel ralentit plus vite que le matériel n’accélère ».
* L’état met à jour son [référentiel de rémunération des métiers du numérique](https://www.numerique.gouv.fr/publications/referentiel-de-remuneration-des-55-metiers-de-la-filiere-numerique/) avec des fourchettes de salaire en fonction de l’expérience. Les rémunérations indiquées paraissent étrangement assez hautes.
* [Un bout de code Javascript pour inverser les couleurs d’un site](https://glaforge.dev/posts/2024/01/18/light-mode-bookmarlet/) (pour passer d’un mode sombre à un clair par exemple), avec une version que l’on peut ajouter sous forme de marque page d'un navigateur.
* Nouvelle vidéo de Science Etonnante sur [une généralisation du jeu de la vie](https://www.youtube.com/watch?v=PlzV4aJ7iMI) de Conway permettant de créer des créatures virtuelles encore plus intéressantes avec des règles très simples.




