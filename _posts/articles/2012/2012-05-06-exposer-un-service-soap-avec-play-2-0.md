---
id: 414
title: Exposer un service SOAP avec Play ! 2.0
date: 2012-05-06T17:09:24+00:00
author: Raphaël Lemaire
layout: post
guid: http://raphael-lemaire.com/blog/?p=414
permalink: /2012/05/06/exposer-un-service-soap-avec-play-2-0/
categories:
  - Technique
---
Ok SOAP n’est plus trop à la mode et Play est fait pour du REST, mais il peut arriver que le client demande un service de ce type, et dans ce cas il faut bien en créer un.

Depuis Java 6, les services SOAP peuvent être écrit en annotant simplement une classe avec @WebService, avec éventuellement des @WebMethod et @WebParam pour préciser l'interface.

Pour l'exposer, en [Java SE](http://blog.excilys.com/2009/12/10/creation-et-utilisation-de-webservice-avec-java-6/) on peut faire un appel à Endpoint.publish(), mais on ne peut le faire ici, en tout cas pas sur le même port que pour le reste de l’application.

En Java EE, il suffit que la classe portant l’annotation @WebService soit déclarée dans le conteneur (par exemple dans le fichier web.xml) pour que le service soit déployé, mais il n’y a pas de tel mécanisme dans Play.

Mais bon, comme les appels SOAP se font via http, implémenter les réponses aux appels que le client peut effectuer suffit.

J’ai trouvé un [exemple en Play 1](https://github.com/marcuspocus/soap-examples), dont je me suis inspiré pour créer un service d'exemple en Play 2. L’idée est d’avoir une classe Controller, avec deux handlers, un pour retourner la wsdl et un  pour répondre aux requêtes.

Voici donc le tutoriel complet.

## Création du service.

Commençons par créer le WebService :

```java
package ws;

import javax.jws.WebService;
import javax.xml.ws.Endpoint;

@WebService
public class TheWS {

    public String hello(String message) {
        return "hello " + message;
    }
}
```

Cette classe ne sera pas utilisée pour le service final en Play, mais on peut ainsi générer la wsdl et des exemples de requêtes et de réponses en xml, avec un outil type SOAP UI.

```java
public static void main(String[] args) {
    // Publishing the service (to have the wsdl)
    Endpoint.publish("http://localhost:8081/TheWS", new TheWS());
}
```


Notez que le schéma est dans un fichier externe à la wsdl. Pour simplifier, je modifie la wsdl pour avoir le schéma inclu directement, sans dépendance.

Vous pouvez aussi télécharger le schéma (à l’adresse <http://localhost:8081/TheWS?xsd=1> donc) et l’exposer avec la wsdl dans le controller Play.

Dans tous les cas, le schéma est obligatoire pour que le client puisse être généré.

## Le controller play.

Enregistrez la wsdl avec un suffixe en .scala.xml afin qu'elle soit détectée comme vue et puisse être utilisée.

On peut ensuite écrire le controller suivant :

```java
public class WSController extends Controller {

    @BodyParser.Of(play.mvc.BodyParser.Xml.class)
    public static Result wsdl(String wsdlParam) {
        return ok(TheWSwsdl.render());
    }
    // ...
}
```

Et la route associée :

```
GET /services/TheWS controllers.WSController.wsdl(wsdl)
```

## Répondre aux requêtes

Il faut maintenant répondre aux requêtes. Nous recevons et renvoyons directement du xml brut.

On peut utiliser n'importe quelle API xml pour parser la requête (dom, xpath, &#8230;).

Pour la réponse, le plus simple est de créer, comme pour la wsdl, un template en .scala.xml à partir de la réponse générée par SOAP UI, que l'on remplit comme une page web.

La méthode du controller :

```java
@BodyParser.Of(play.mvc.BodyParser.Xml.class)
public static Result router() {
    try {
        // Récupération de la requpete xml.
        Document dom = request().body().asXml();
        Logger.info(dom.toString());
        return ok(helloResponse.render("Salut"));
    } catch (Exception e) {
        Logger.error(e.toString(), e);
        return internalServerError(e.toString());
    }
}
```

Le template de réponse :

```html
@(message: String)

@message
```

Et les routes :

```
GET /services/TheWS controllers.WSController.wsdl(wsdl)
POST /services/TheWS controllers.WSController.router
```

## Création du client et test.

On peut maintenant générer le client :

```
wsimport -keep http://localhost:9000/services/TheWS?wsdl
```

Et vérifier le bon comportement du système :

```java
package client;

import java.net.MalformedURLException;

import ws.TheWS;
import ws.TheWSService;

public class MainClient {

    public static void main(String[] args) throws MalformedURLException {
        TheWS service = new TheWSService().getTheWSPort();
        System.out.println(service.hello("test"));
    }
}
```

J'ai ajouté cet exemple sur Github : https://github.com/rlemaire/play2-soap-ws-example
  