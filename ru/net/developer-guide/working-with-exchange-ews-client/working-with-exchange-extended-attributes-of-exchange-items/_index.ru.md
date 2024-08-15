---
title: "Работа с расширенными атрибутами товаров Exchange"
url: /ru/net/working-with-exchange-extended-attributes-of-exchange-items/
weight: 140
type: docs
---


Aspose.Email API позволяет создавать, извлекать и обновлять расширенные свойства сообщений с помощью клиента API EWS. Следующий пример кода иллюстрирует это, создавая расширенный атрибут, добавляя его к сообщению на сервере и получая сообщение в виде [MapiMessage](https://reference.aspose.com/email/net/aspose.email.mapi/mapimessage/) с сервера Exchange с помощью клиента [FetchItem](https://reference.aspose.com/email/net/aspose.email.clients.exchange.webservice/iewsclient/fetchitem/).

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