---
id: 888
title: \@author is irrelevant
date: 2014-06-12T22:58:40+00:00
author: Raphaël Lemaire
layout: post
guid: http://raphael-lemaire.com/blog/?p=888
permalink: /2014/06/12/author-is-irrelevant/
categories:
  - Craftsmanship
---
Sur une équipe de plus que 1, laisser l'IDE ajouter le tag `@author` sur chaque classe n'a aucun sens.

Forcément à un moment ou un autre le code sera touché par quelqu'un d'autre et la mention de l'auteur ne sera plus vraie. 
Dans beaucoup de cas ce sera même la seule ligne que l'auteur d'origine aura toujours vraiment à son actif.

C'est l'historique SCM donne vraiment la bonne information. Qui a modifié quoi, quand, pourquoi&#8230;

```
a0455d09 Lovegood   2013-07-23       @Override
a0455d09 Granger    2013-07-23       public final <span style="text-decoration: underline;"> Stream<span style="text-decoration: underline;"> mapToObj(IntFunction&lt;? extends U&gt; mapper) {
a0455d09 Granger    2013-07-23           Objects.requireNonNull(mapper);
1e78cee4 Granger    2013-09-28           return new ReferencePipeline.StatelessOp&lt;Integer, U&gt;;(this, StreamShape.INT_VALUE,
aada68b5 Granger    2013-11-08                                                                StreamOpFlag.NOT_SORTED | StreamOpFlag.NOT_DISTINCT) {
1e78cee4 Brown      2013-09-28               @Override
1e78cee4 Brown      2013-09-28               Sink opWrapSink(int flags, SinkU&gt; sink) {
1e78cee4 Brown      2013-09-28                   return new Sink.ChainedInt&lt;U&gt;(sink) {
1e78cee4 Granger    2013-09-28                       @Override
1e78cee4 Granger    2013-09-28                       public void accept(int t) {
1e78cee4 Longbottom 2013-09-28                           downstream.accept(mapper.apply(t));
1e78cee4 Longbottom 2013-09-28                       }
aada68b5 Granger    2013-11-08                   };
aada68b5 Granger    2013-11-08               }
aada68b5 Lovegood   2013-11-08           };
1e78cee4 Lovegood   2013-09-28       }
1e78cee4 Granger    2013-09-28
```

Alors ok en tant que craftsman, on doit signer son travail, pour montrer qu'on en est fier. Mais pour moi cela se fait
 tout naturellement via l'historique du SCM.

En fait, en plus d'être inexact et donc inintéressant, la mention de l'auteur décourage l'appartenance collective, 
encourageant l'auteur d'origine à considérer la classe comme chasse gardée et les contributeurs futurs à faire des 
changements a minima (même si c'est juste un tout petit peu, même si c'est inconsciement).

D'ailleurs sur ce sujet l'équipe de _pragmatic programmer tips_ [est d'accord avec moi](http://pragmatictips.com/70).
De même apparement apache [impose la suppression des tages @author](http://www.theinquirer.net/inquirer/news/1037207/apache-enforces-the-removal-of-author-tags).