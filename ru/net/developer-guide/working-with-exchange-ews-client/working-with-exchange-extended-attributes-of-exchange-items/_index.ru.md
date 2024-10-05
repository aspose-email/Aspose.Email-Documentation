---
title: "Работа с расширенными атрибутами Exchange предметов"
url: /ru/net/working-with-exchange-extended-attributes-of-exchange-items/
weight: 140
type: docs
---


API Aspose.Email позволяет создавать, извлекать и обновлять Расширенные свойства сообщений с помощью EWS клиента API. Следующий пример кода иллюстрирует это, создавая расширенный атрибут, добавляя его к сообщению на сервере и извлекая сообщение как [MapiMessage](https://reference.aspose.com/email/net/aspose.email.mapi/mapimessage/) из сервера Exchange с использованием клиента [FetchItem](https://reference.aspose.com/email/net/aspose.email.clients.exchange.webservice/iewsclient/fetchitem/).

```csharp
// Определите расширенное свойство PidTagBodyContentId
var extendedProperty = KnownPropertyList.BodyContentId;

// Создайте сообщение и установите значение расширенного свойства
var msg = new MapiMessage("from@from.com", "to@to.com", "Тестовое сообщение", "Это тестовое сообщение");
msg.SetProperty(extendedProperty, "03454432-6230-4e4b-887f-a498ea223599");

// Добавьте сообщение
var uri = ewsClient.AppendMessage(ewsClient.MailboxInfo.InboxUri, msg, true);

// Извлеките добавленный элемент. Передайте дескриптор расширенного свойства в качестве параметра метода.
var fetchedMsg = ewsClient.FetchItem(uri, new PropertyDescriptor[] { extendedProperty });

// Выведите значение расширенного свойства
Console.WriteLine(fetchedMsg.Properties[extendedProperty].GetString());
```