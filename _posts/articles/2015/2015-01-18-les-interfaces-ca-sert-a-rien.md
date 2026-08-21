---
id: 1112
title: Les interfaces ça sert à rien
date: 2015-01-18T19:17:26+00:00
author: Raphaël Lemaire
layout: post
guid: http://raphael-lemaire.com/blog/?p=1112
permalink: /2015/01/18/les-interfaces-ca-sert-a-rien/
categories:
  - Technique
---
Enfin quasiment toujours, les interfaces dans les projets java moyens ne servent à rien.

Pourquoi toujours ajouter une interface, pour tous les services, repositories, raton-laveurs ? C'est beaucoup plus une
 habitude qu'une nécessité.

Ca ne devrait pas être un sujet, mais mission après mission je vois des centaines de classes, avec à chaque fois une 
interface associée, qui ne sert à rien.

## Rappel : c'est quoi une interface ?

La notion d'interface en java est un _contrat_. Une interface définit un ensemble de méthodes, et les classes 
implémentant l'interface sont tenues d'implémenter ces méthodes.

Par exemple l'interface [Comparable](http://docs.oracle.com/javase/8/docs/api/java/lang/Comparable.html) définit une 
méthode `compareTo`, et toutes les classes implémentant [Comparable](http://docs.oracle.com/javase/8/docs/api/java/lang/Comparable.html) peuvent être utilisées pour des traitements impliquant des comparaisons, comme être ajoutées dans un [SortedSet](http://docs.oracle.com/javase/8/docs/api/java/util/SortedSet.html). Les interfaces permettent un polymorphisme plus riche que ce qu'on aurait avec l'héritage linéaire en java et permettent la réutilisation de code (eg : le [SortedSet](http://docs.oracle.com/javase/8/docs/api/java/util/SortedSet.html) sus mentionné).

## Un service java typique

Après ce bref rappel, prenons notre service Java typique :


```java
public interface BiduleService {
    void save(Bidule bidule)
    
    void computeComplexeLogic(Bidule bidule1, BiduleInfos infos);
}
```

```java
@Service
public class BiduleServiceImpl implements BiduleService {
    @Override
    public void save(Bidule bidule) {
        // implem
    }
    
    @Override
    public void computeComplexeLogic(Bidule bidule1, BiduleInfos infos) {
        // implem
    }
    
    // ...
}
```

Là je suis à 99,99% sur qu'il n'y aura absolument jamais d'autre implémentation de l'interface `BiduleService`. 
Ce service est hyper spécifique à mon application. Il s'agit d'un sac de procédures (oui quand on fait des services 
on ne fait pas de la POO&#8230;) liées à mon métier, pas d'un concept pouvant avoir un contrat comme `Comparable` ou `Serializable`.

Au niveau Java, cette interface n'a pas de raison d'être. Elle est là parce qu'on a toujours mis des interfaces pour 
ce genre de classe, et que c'est comme ça dans le reste du projet.

## Pourquoi a-t-on a pris l'habitude de mettre des interfaces partout ?

Cela date en fait d'un temps que je n'ai pas pu connaitre, mais à l'origine les interfaces (dans ce cas précis) 
servaient à créer des proxys JDK pour les EJB 2.

Par proxy JDK j'entends des proxys dynamiques, (comme dans le design pattern proxy) créés à partir
 de l'[API éponyme](http://docs.oracle.com/javase/8/docs/api/java/lang/reflect/Proxy.html) de Java (note : il s'agit
  d'une fonctionnalité de Java SE, Standard Edition, même pas Java EE, et encore moins d'une dépendance). 
  Les proxys dynamiques permettent d'ajouter du comportement aux classes, comme les transactions, ou de l'AOP.

L'API proxy de Java SE impose à la classe proxifiée d'avoir une interface que le proxy peut implémenter, afin de 
pouvoir être interchangé avec la classe.

Les EJB 2 imposaient donc ces interfaces.

Cela permettait également de créer plus facilement des mocks pour les tests.

Donc plutôt intéressant en effet.

_Sauf qu'il est depuis longtemps possible de faire tout cela sans interfaces._

Spring peut par exemple utiliser cglib plutôt que les proxys JDK pour créer ses proxys, il y a de petites différences 
mais en gros ça se comporte de la même façon. Pour les mocks, `Easy mock class extension` existe depuis longtemps, 
sans parler de `Mockito` (et bien d'autres) qui a toujours supporté le mocking de classes. Et même les EJB, depuis 
la version 3.1 n'imposent plus l'utilisation d'interfaces.

## Depuis quand ça ne sert plus à rien ?

_Spring_ : [Depuis la 1.0.0, en novembre 2003.](http://stackoverflow.com/questions/28012219/since-when-can-spring-use-cglib-for-proxy-creation/)

_EJB 3.1_ : Sortie officielle en décembre 2009.

_Easy mock class extension_ : la plus ancienne version dont j'ai trouvé la date, la 2.2, date d'avril 2006.

_Mockito_ : la plus ancienne version dont j'ai trouvé la date, la 1.3, date d'avril 2008.

## En résumé

Depuis une bientôt une décennie, on garde une habitude héritée des EJB 2, qui double presque le nombre de fichiers des
 projets, sans aucune raison (en général).

Donc avant de créer une interface pour une classe dont les instances seront gérées par le conteneur, assurez vous 
d'avoir vraiment une contrainte qui l'implique.