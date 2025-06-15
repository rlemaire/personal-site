---
id: 168
title: Ne jamais faire en dev ce qu’on ne veut pas voir en prod
date: 2011-05-06T10:00:11+00:00
author: Raphaël Lemaire
layout: post
guid: http://random-arguments.fr/?p=168
permalink: /2011/05/06/ne-jamais-faire-en-dev-ce-quon-ne-veut-pas-voir-en-prod/
categories:
  - Craftsmanship
---
La plupart du temps (et c’est d’heureux), les développeurs d’applications, de sites, travaillent sur un environnement de développement, le plus souvent leur propre machine. Ce qu’ils y font n’est visible que d’eux même et de quelques privilégiés de la même équipe.

Comme le travail d’ingénieur peut être ennuyeux et que les développeurs ne sont pas dénués de sens de l’humour (même s’il peut être [particulier](http://xkcd.com/)), la tentation d’ajouter dans l’application en cours de développement ou dans ses ressources une petite blague peut se présenter. Cela peut prendre la forme d’une image ou d’un message amusant (pour celui qui l’ajoute du moins), en encore d’un [easter egg](http://fr.wikipedia.org/wiki/Easter_egg).

Il peut également arriver que le travail soit frustrant ou énervant. Et là on a des commentaires désobligeant pour son boss, le navigateur, l’équipe MOA, …

On a par exemple la gaffe récente d’un développeur travaillant pour TF1 traitant de « Couillons » les internautes cliquant sur les publicités ou encore les commentaires HTML insultants IE6 dans les commentaires HTML d’une page.

L’auteur n’a cependant certainement aucune envie de voir ce genre d’exploits en production, alors comment cela arrive-t-il ?

D’abord, la séparation est parfois mince entre ce qui est visible par l’utilisateur et ce qui ne l’est pas.

Prenons par exemple la différence entre les commentaires JSP et les commentaires HTML :

```html
<%– Tableau de présentation à cause de ce #@$§! d’IE6–%> Commentaire JSP, **non visible** dans le HTML final
  
<!– Tableau de présentation à cause de ce #@$§! d’IE6–>Commentaire HTML, **visible** dans le HTML final
```

A deux caractères près, on a des grossièretés visibles par tout le monde.

On peut aussi avoir des problèmes avec la configuration des environnements :

```properties
service-externe1.url = http://prod.service.com/service1
service-externe2.url = http://test.service.com/service2
service-externe3.url = http://prod.service.com/service3
```

Une URL de test est restée dans le fichier de propriétés de l’environnement de production. Cela peut prendre du temps à être vu si le service ne sert pas souvent.

On a aussi, comme dans le cas de TF1, la possibilité que d’autres informaticiens s'intéressent à l'application et décompilent le code, par exemple flash, ou les fichiers .class s’ils y ont accès.

La conclusion est implacable : **Ne jamais faire en DEV ce qu’on ne voudrait pas voir en production**.