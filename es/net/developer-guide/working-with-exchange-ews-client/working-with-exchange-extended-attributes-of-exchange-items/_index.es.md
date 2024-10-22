---
title: "Trabajando con Atributos Extendidos de Exchange de Elementos de Exchange"
url: /es/net/working-with-exchange-extended-attributes-of-exchange-items/
weight: 140
type: docs
---


La API Aspose.Email te permite crear, recuperar y actualizar propiedades extendidas de mensajes utilizando el cliente EWS de la API. El siguiente ejemplo de código ilustra esto creando un atributo extendido, añadiéndolo al mensaje en el servidor y recuperando el mensaje como [MapiMessage](https://reference.aspose.com/email/net/aspose.email.mapi/mapimessage/) desde el servidor de Exchange usando el cliente [FetchItem](https://reference.aspose.com/email/net/aspose.email.clients.exchange.webservice/iewsclient/fetchitem/).

```csharp
// Define una propiedad extendida PidTagBodyContentId
var extendedProperty = KnownPropertyList.BodyContentId;

// Crea un mensaje y establece un valor de propiedad extendida
var msg = new MapiMessage("from@from.com", "to@to.com", "Mensaje de prueba", "Este es un mensaje de prueba");
msg.SetProperty(extendedProperty, "03454432-6230-4e4b-887f-a498ea223599");

// Añadir mensaje
var uri = ewsClient.AppendMessage(ewsClient.MailboxInfo.InboxUri, msg, true);

// Recuperar elemento añadido. Pasa el descriptor de propiedad extendida como parámetro del método.
var fetchedMsg = ewsClient.FetchItem(uri, new PropertyDescriptor[] { extendedProperty });

// Imprimir el valor de la propiedad extendida
Console.WriteLine(fetchedMsg.Properties[extendedProperty].GetString());
```