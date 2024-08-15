---
title: "Работа с расширенными атрибутами товаров Exchange"
url: /ru/java/working-with-exchange-extended-attributes-of-exchange-items/
weight: 140
type: docs
---


Aspose.Email API позволяет создавать, извлекать и обновлять расширенные свойства сообщений с помощью клиента API EWS. Следующий пример кода иллюстрирует это, создавая расширенный атрибут, добавляя его к сообщению на сервере и получая сообщение в виде [MapiMessage](https://apireference.aspose.com/email/java/com.aspose.email/mapimessage) с сервера Exchange с использованием клиента [fetchItem](https://reference.aspose.com/email/java/com.aspose.email/IEWSClient#fetchItem\(java.lang.String,%20java.lang.Iterable\)).

~~~Java
// Define a PidTagBodyContentId extended property
PropertyDescriptor extendedProperty = KnownPropertyList.BODY_CONTENT_ID;

// Create a message and set an extended property value
MapiMessage msg = new MapiMessage("from@from.com", "to@to.com",
        "Test message", "This is a test message");
msg.setProperty(extendedProperty, "03454432-6230-4e4b-887f-a498ea223599");

// Append message
String uri = ewsClient.appendMessage(ewsClient.getMailboxInfo().getInboxUri(), msg, true);

// Fetch appended item. Pass the extended property descriptor as method parameter.
MapiMessage fetchedMsg = ewsClient.fetchItem(uri, Arrays.asList(new PropertyDescriptor[] { extendedProperty }));

// Print the extended property value
System.out.println(fetchedMsg.getProperties().get_Item(extendedProperty).getString());
~~~