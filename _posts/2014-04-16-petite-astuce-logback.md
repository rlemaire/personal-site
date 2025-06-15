---
id: 853
title: Petite astuce logback
date: 2014-04-16T22:23:28+00:00
author: Raphaël Lemaire
layout: post
guid: http://raphael-lemaire.com/blog/?p=853
permalink: /2014/04/16/petite-astuce-logback/
categories:
  - Technique
---
Petite astuce avec logback : il est possible [d’utiliser des variables dans le fichier de configuration](http://logback.qos.ch/manual/configuration.html#variableSubstitution),
 définies comme variables d’environnement (-D) ou venant d’un fichier de properties paramétré dans le fichier logback.xml. 
 Ce fichier peut même provenir du classpath :

par exemple avec dans mon fichier properties :

```
environment=INT
```

Et la config logback suivante :

```xml
<property resource="monapp-config.properties" />

<appender name="monapp" class="ch.qos.logback.core.rolling.RollingFileAppender">
    <file>/tmp/logs/monapp-${environment}.log</file>
    <rollingPolicy class="ch.qos.logback.core.rolling.TimeBasedRollingPolicy">
        <fileNamePattern>/tmp/logs/monapp-${environment}.%d{yyy-MM-dd}.log</fileNamePattern>
        <maxHistory>30</maxHistory>
    </rollingPolicy>
    
    <encoder>
        <pattern>%-4relative [%thread] %-5level %logger{35} - %msg%n</pattern>
    </encoder>
</appender>
```


Je peux faire varier le nom du fichier en fonction de l'environnement (qui peut lui même être filtré par maven mais c'est une autre histoire).