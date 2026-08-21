---
id: 1507
title: Litterate programming 2017
date: 2017-10-15T18:25:03+00:00
author: Raphaël Lemaire
layout: post
guid: http://raphael-lemaire.com/blog/?p=1507
permalink: /2017/10/15/litterate-programming-2017/
categories:
  - Craftsmanship
  - "L'art du logiciel"
  - favorite
---
J’ai récemment lu l’article de [Donald Knuth](https://en.wikipedia.org/wiki/Donald_Knuth) sur la [programmation lettrée](https://en.wikipedia.org/wiki/Literate_programming). C’est un de ces paradigmes un peu oubliés, avec pourtant un potentiel très cool.

_C’est quoi la programmation lettrée ?_

L’idée original de Donald Knuth est d’écrire un programme sous la forme d’un essai en langage naturel, expliquant ce que le programme fait, avec entre les lignes des morceaux de code exécutable.

> Le programme est écrit sous la forme d'un essai en langage naturel, avec du code exécutable entre les lignes.

Il est ainsi possible de générer à partir du même fichier une documentation en langue naturelle (par exemple sous la forme d’un fichier latex, html, etc…) et un programme exécutable par une machine.

_Vous me direz « c’est javadoc » : Eh bien non !_

Les outils de génération auxquels nous sommes habitués permettent de générer une _documentation_ à partir de texte annoté sur la structure du programme. C’est toujours le langage machine qui donne la contrainte de où est placé le texte. On documente une classe ou une fonction.

Avec la programmation lettrée, le texte est au premier plan, et c’est lui qui impose la structure du programme, pas le langage machine.

> Avec la programmation lettrée, le texte est au premier plan.

Personnellement je trouve l’idée assez cool. Pour plein de raisons.

Déjà, on ne raconte pas assez nos vies, ou plutôt la vie du projet dans nos programmes. Il est rare que les gens placent le contexte, le pourquoi fonctionnel, politique, historique de tel ou tel morceau de code. Et souvent on se pose des questions longtemps après, même si le code est clair sur ce qu’il fait, sur pourquoi ça a été fait.

Ensuite, écrire du texte en français (ou en anglais, c’est un autre débat) permet de structurer sa pensée. On peut penser à des choses que l’on aurait oublié (pour moi qui suit un intuitif et un éternel distrait c’est intéressant), mieux comprendre un concept, une fonctionnalité, et donc mieux l’implémenter, etc…

Et aussi, j’aime assez tout ce qui s'écarte de l’habituel et permet de voir la programmation autrement. Avouons que le changement est rafraîchissant.

Comme ce paradigme est un peu oublié, il y a peu d’outils à disposition pour en faire, et pas vraiment d’envie de le voir arriver dans les projets (contrairement à la programmation fonctionnelle, qui a le vent en poupe).

Je me suis demandé ce que cela donnerait si on essayait d’appliquer cette idée dans un langage mainstream actuel. Voici un exemple en Java, tiré d’un programme réel, et un peu retravaillé :

Le code complet :

```java
/**
* Interroge le service infos pour récupérer les informations, et les stocke
* dans redis.
* On ne garde que les infos en cours de validité.
*/
public F.Promise<List> poll() {
    // En avril 2016, la direction des renards a demandé à intégrer les
    // informations aviaires à l'application, afin de [...].
    // On commence par récupérer la liste des contenus auprès du service infos.
    return infosClient.getContentList().flatMap((contentList) -> {
        // On a alors une liste d'objets qui contiennent les ids et date
        // de validité des contenus existants.
        List<F.Promise> promises = contentList.stream()
            // On ne conserve que les publications en cours de validité.
            .filter(InfosService::mustBeDisplayedNow)
            // pour chacun des contenus non filtrés, on va chercher le
            // détail (avec le titre, le texte, etc...) en appelant
            // le service infos avec l'identifiant donné dans la liste,
            // et on traduit le résultat dans notre modèle.
            .map((content) -> infosClient
            .getContent(content.getContentId())
            .map(InfosService::convert))
            .collect(Collectors.toList());

        // Note : on va chercher les détails en parrallèle, pour plus d'efficacité.
        return F.Promise.sequence(promises).map((informations) -> {
            // Une fois les contenus récupérés, on les stocke dans redis
            storeInCache(informations);
            // Par commodité, on renvoie les contenus stockés, ce qui permet
            // pour un poll fait à la main de voir ce qui a été stocké.
            return informations;
        });
    });
}
```

On voit qu’il y a beaucoup de commentaires, qui peuvent parfois paraître un peu redondant avec le code en dessous, mais pas non plus complètement inutiles.

Si on enlève les commentaires qui ne sont pas de la documentation de méthode ça donne :

```java
/**
* Interroge le service infos pour récupérer les informations, et les stocke
* dans redis.
* On ne garde que les infos en cours de validité.
*/
public F.Promise<List> poll() {
    return infosClient.getContentList().flatMap((contentList) -> {
        List<F.Promise> promises = contentList.stream()
            .filter(InfosService::mustBeDisplayedNow)
            .map((content) -&gt; infosClient
            .getContent(content.getContentId())
            .map(InfosService::convert))
            .collect(Collectors.toList());
        return F.Promise.sequence(promises).map((informations) -> {
            storeInCache(informations);
            return informations;
        });
    });
}
```

C’est le genre de chose qu’on est habitué à voir tous les jours. C’est assez lisible, si on est familier avec la syntaxe du langage et les API du framework play!.

Si on garde seulement les commentaires d’explication inséré au milieu du code ça donne :

```
En avril 2016, la direction des renards a demandé à intégrer les informations aviaires à l’application, afin de […].
On commence par récupérer la liste des contenus auprès du service infos.
On a alors une liste d’objets qui contiennent les ids et date de validité des contenus existants. On ne conserve que les publications en cours de validité.
Pour chacun des contenus non filtrés, on va chercher le détail (avec le titre, le texte, etc…) en appelant le service infos avec l’identifiant donné dans la liste, et on traduit le résultat dans notre modèle.
Note : on va chercher les détails en parrallèle, pour plus d’efficacité.
Une fois les contenus récupérés, on les stocke dans redis.
Par commodité, on renvoie les contenus stockés, ce qui permet pour un poll fait à la main de voir ce qui a été stocké.
```

On le voit ce petit texte ne ressemble pas du tout à une description de méthode, et il explique très bien ce que fait le petit bout de programme et pourquoi.

On a donc un essai qui décrit le programme.

Les avantages de cette démarche :

  * Le programme produit est plein d’explications, et donc plus documenté et plus clair.
  * Ecrire le texte permet de penser plus longtemps le programme et aussi un peu différemment, on pense donc à plus de choses, et cela permet d’éviter des oublis, des cas particuliers, etc…
  * Les commentaires ajoutés permettent de donner du contexte, d’expliciter des choses et de justifier des choix techniques, même micros.

Les inconvénients :

  * C’est assez verbeux et un peu redondant.