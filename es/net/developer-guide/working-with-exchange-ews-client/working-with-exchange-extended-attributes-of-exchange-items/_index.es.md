---
title: "Cómo trabajar con los atributos ampliados de Exchange de los artículos de Exchange"
url: /es/net/working-with-exchange-extended-attributes-of-exchange-items/
weight: 140
type: docs
---


La API Aspose.Email le permite crear, recuperar y actualizar las propiedades ampliadas de los mensajes mediante el cliente de la API EWS. El siguiente ejemplo de código ilustra esto creando un atributo extendido, agregándolo al mensaje del servidor y recuperando el mensaje como [MapiMessage](https://reference.aspose.com/email/net/aspose.email.mapi/mapimessage/) desde el servidor Exchange mediante el cliente [FetchItem](https://reference.aspose.com/email/net/aspose.email.clients.exchange.webservice/iewsclient/fetchitem/).

```csharp
// Define a PidTagBodyContentId extended property
var extendedProperty = KnownPropertyList.BodyContentId;

// Create a message and set an extended property value
var msg = new MapiMessage("from@from.com", "to@to.com", "Test message", "This is a test message");
msg.SetProperty(extendedProperty, "03454432-6230-4e4b-887f-a498ea223599");

// Append message
var uri = ewsClient.AppendMessage(ewsClient.MailboxInfo.InboxUri, msg, true);

// Fetch appended item. Pass the extended property descriptor as method parameter.
var fetchedMsg = ewsClient.FetchItem(uri, new PropertyDescriptor[] { extendedProperty });

// Print the extended property value
Console.WriteLine(fetchedMsg.Properties[extendedProperty].GetString());
```