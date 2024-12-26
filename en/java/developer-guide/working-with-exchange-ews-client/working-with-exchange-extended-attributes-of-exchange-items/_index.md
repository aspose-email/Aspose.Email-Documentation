---
title: Working with Exchange Extended Attributes of Exchange Items
ArticleTitle: Working with Exchange Extended Attributes of Exchange Items
type: docs
weight: 140
url: /java/working-with-exchange-extended-attributes-of-exchange-items/
---


Aspose.Email API lets you create, retrieve and update Extended properties of messages using the EWS client of API. The following code sample illustrates this by creating an extended attribute, adding it to the message on the server and retrieve the message as [MapiMessage](https://apireference.aspose.com/email/java/com.aspose.email/mapimessage) from Exchange server using the client's [fetchItem](https://reference.aspose.com/email/java/com.aspose.email/IEWSClient#fetchItem\(java.lang.String,%20java.lang.Iterable\)).

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
