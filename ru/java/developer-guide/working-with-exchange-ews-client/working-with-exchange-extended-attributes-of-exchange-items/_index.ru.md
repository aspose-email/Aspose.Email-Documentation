---
title: "Работа с расширенными атрибутами Exchange элементов Exchange"
url: /ru/java/working-with-exchange-extended-attributes-of-exchange-items/
weight: 140
type: docs
---


Aspose.Email API позволяет создавать, извлекать и обновлять расширенные свойства сообщений с помощью клиента EWS API. Следующий образец кода иллюстрирует это, создавая расширенный атрибут, добавляя его к сообщению на сервере и извлекая сообщение как [MapiMessage](https://apireference.aspose.com/email/java/com.aspose.email/mapimessage) с сервера Exchange, используя метод клиента [fetchItem](https://reference.aspose.com/email/java/com.aspose.email/IEWSClient#fetchItem\(java.lang.String,%20java.lang.Iterable\)).

~~~Java
// Определение расширенного свойства PidTagBodyContentId
PropertyDescriptor extendedProperty = KnownPropertyList.BODY_CONTENT_ID;

// Создание сообщения и установка значения расширенного свойства
MapiMessage msg = new MapiMessage("from@from.com", "to@to.com",
        "Тестовое сообщение", "Это тестовое сообщение");
msg.setProperty(extendedProperty, "03454432-6230-4e4b-887f-a498ea223599");

// Добавление сообщения
String uri = ewsClient.appendMessage(ewsClient.getMailboxInfo().getInboxUri(), msg, true);

// Извлечение добавленного элемента. Передайте дескриптор расширенного свойства как параметр метода.
MapiMessage fetchedMsg = ewsClient.fetchItem(uri, Arrays.asList(new PropertyDescriptor[] { extendedProperty }));

// Печать значения расширенного свойства
System.out.println(fetchedMsg.getProperties().get_Item(extendedProperty).getString());
~~~