---
id: 114
title: Bonnes pratiques pour les resources bundles
date: 2011-04-23T10:00:43+00:00
author: Raphaël Lemaire
layout: post
guid: http://random-arguments.fr/?p=114
permalink: /2011/04/23/resources-bundles/
categories:
  - Technique
---
Dans une application internationalisée, tous les messages doivent pouvoir être modifiés en fonction de la langue. En java, et dans les technologies dérivées, on utilise pour cela des _resources bundles_, qui sont des fichiers clef/valeurs, la clef permettant de retrouver le message, et la valeur étant le message lui même, le bon resource bundle étant choisi en fonction de la locale.

Exemple :

```properties
messages_fr_FR.properties :
menu.home = Acceuil
menu.catalog = Découvrez nos produits
menu.cart = Votre panier
menu.contact = Nous contacter

messages_en_US.properties :
menu.home = Home
menu.catalog = Our products
menu.cart = Cart
menu.contact = Contact Us
```

A chaque développement de page, ajout de message de validation ou autre, le développeur doit donc ajouter une clef parmi la liste de bundles pour son nouveau message. Comme souvent en programmation, cela peut paraitre simple, mais n'est pas triviale à réaliser correctement.

En effet, pour être convenablement maintenable, les bundles doivent :

– **Laisser la possibilité du partage de labels**. Des textes identiques répétés sur différentes pages devraient être mutualisés pour éviter les duplications. Pourtant certains labels au départ identiques peuvent évoluer differement : il faut les identifier dès le départ et ne pas regrouper ce qui ne devrait pas l'être.
  
– **Assurer une relative indépendance de la clef et du contenu**. De même que des classes css comme _red_ ou _paddingBottom3_ sont plutôt problématiques, des clef comme _our.products_ ou _contact.us_ deviendrons ridicules quand le lien vers les produits deviendra « consultez notre catalogue merveilleux ».
  
– **Être compréhensible sans le message pour quelqu'un familier avec le site**. Dans l'idéal, la clef devrait suffire pour quelqu'un connaissant le site/l'application pour identifier le contenu du message. Le mieux est d'avoir un document associant les clefs à leur emplacement dans des captures d'écrans du site pour les localisations.

On le voit, comme pour la plupart des taches de développement, **la connaissance globale du site**, de sa carte, de son story board et de ses évolutions possible est **importante**.

L'élaboration des clef peut suivre une politique mimant la fameuse « urbanisation » de SOA. Par exemple _section.page.subtitle_, avec autant de niveaux que nécessaire, selon la taille de l'application (celle-ci pouvant évoluer).

Les clefs servant aux messages partagés devraient être aisément identifiables, eg, _form.emailFormatError_. Si la clef ne suffit pas, cela peut-être une bonne idée d'ajouter un commentaire dans le resource bundle signalant que le couple est partagé.

**Casser les messages est une mauvaise idée**

J'ai vu des développeurs casser les messages en petit morceaux, parce qu’ils devraient être sur plusieurs paragraphes (avec des message1, message2, &#8230;), contenait un morceau dynamique ou des balises html (un lien par exemple).

C'est une très mauvaise idée.

D'abord parce que ce n'est pas vraiment utile. Il existe un mécanisme permettant d'insérer des variables dans les messages (avec Message.format au final). Eg :

```
Votre recherche : {0} résultats
```

ou encore :

```allez sur &lt;a href="{1}"&gt;Votre espace client&lt;/a&gt; pour ...```

Ensuite cela complique la page et le fichier de ressources, rendant l'ensemble plus difficile à comprendre et à maintenir.

De plus il est peu probable que la cassure choisie soit judicieuse toutes les langues. Selon la traduction, la deuxième partie du message peut se retrouver avant. Par exemple « Votre recherche : 12 résultats » en français et « Results found : 12 for your search » en anglais.

Enfin je ne vois pas d'objection à introduire une dose raisonnable de HTML dans les resources bundle, tant qu'il s'agit effectivement de contenu et que l'on respecte les règles de séparation avec la présentation (le style). Les balises paragraphes, strong, em, voire les liens, sont ok. Par contre, hors de question d'y mettre un tableau ou un menu, évidemment.

Exemple de bundle complexe :

```properties
catalog.main.explanation = &lt;p&gt;&lt;strong&gt;N'hésitez plus {1} {2} !
&lt;/strong&gt; et craquez pour nos &lt;a href="{0}"&gt;&lt;em&gt;
super promotions&lt;/em&gt;&lt;/a&gt;!&lt;p&gt;&lt;p&gt;Dans la limite des
 stocks disponibles&lt;/p&gt;\
```