---
id: 880
title: 'Apache 2 : modes worker et prefork'
date: 2014-04-23T22:06:46+00:00
author: Raphaël Lemaire
layout: post
guid: http://raphael-lemaire.com/blog/?p=880
permalink: /2014/04/23/apache-2-modes-worker-et-prefork/
categories:
  - Technique
---
Il y a deux <del>tribus</del>, modes pour apache 2 : [prefork et worker](http://fr.wikipedia.org/wiki/Apache_HTTP_Server#Les_modes_Prefork.2C_Worker_et_Event), affectés au moment de la compilation.

Quelles différences ?

En mode **prefork**, les requêtes sont traitées par des processus lourds. Le premier processus lancé écoute sur le port 80 (et/ou 443, ou autre), puis dispatche les requêtes sur des processus fils <small>(le nom prefork venant de la méthode C fork qui permet de créer de nouveaux processus sous unix)</small>.

Pour traiter 250 connexions simultanées, il faudra donc 251 processus : le processus parent qui écoute et les 250 fils qui traitent.

Dans la configuration, le paramètre _ServerLimit_ limite le nombre de processus pouvant être lancés au maximum. Le paramètre _MaxClients_ limite le nombre de clients pouvant se connecter. Il doit être inférieur ou égal à _ServerLimit_, l'égalité étant plus logique.

Exemple de configuration :

```
<IfModule mpm_prefork_module>
    ServerLimit         500
    MaxClients          500
    MaxRequestsPerChild   0
</IfModule>
```

En mode **worker**, les requêtes sont traitées par des threads, eux même regroupés dans des processus. On a par exemple 25 thread par processus, et 10 processus. Pour traiter 250 requêtes il faudra 11 processus, et 250 threads. Le _MaxClients_ correspond au nombre de threads total. Il faudra aussi configurer le nombre de processus et le nombre de thread par processus. Le _MaxClients_ peut inférieur au nombre de processus (_ServerLimit_) multiplié par le nombre de thread (_ThreadsPerChild_), mais pas supérieur.

Exemple de configuration :

```
<IfModule mpm_worker_module>
    [...]
    ServerLimit         20
    MaxClients          500
    [...]
    ThreadsPerChild      25
</IfModule>
```

**Lequel utiliser ?**

Le mode worker utilisant des processus léger, il est plus performant pour traiter un grand nombre d’utilisateurs : moins de mémoire occupée, context switching plus léger&#8230; Or par défaut, apache est installé en mode prefork. Pourquoi ? Pour éviter [les problèmes avec certaines librairies PHP qui ne sont pas thread safe](http://serverfault.com/questions/45042/which-to-install-apache-worker-or-prefork-what-are-the-dis-advantages-of-eac).