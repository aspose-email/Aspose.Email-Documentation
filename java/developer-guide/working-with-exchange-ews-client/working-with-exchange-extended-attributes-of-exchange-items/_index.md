---
title: Working with Exchange Extended Attributes of Exchange Items
type: docs
weight: 140
url: /java/working-with-exchange-extended-attributes-of-exchange-items/
---


Aspose.Email API lets you create, retrieve and Update Extended Attributes of messages using the EWS client of API. The following code sample illustrates this by creating an extended attribute, adding it to the message on the server and retrieve the message as [MapiMessage](https://reference.aspose.com/email/java/com.aspose.email/mapimessage) from Exchange server using the client's [fetchMapiMessage](https://reference.aspose.com/email/java/com.aspose.email/IEWSClient#fetchMapiMessages\(java.lang.Iterable,%20java.lang.Iterable\)).

~~~Java
// Create a new Property
PidNamePropertyDescriptor pd = new PidNamePropertyDescriptor("MyTestProp", PropertyDataType.String, UUID.fromString("00020329-0000-0000-C000-000000000046"));
String value = "MyTestPropValue";

// Create a message
MapiMessage message = new MapiMessage("from@domain.com", "to@domain.com", "Subject - " + UUID.randomUUID().toString(),
        "Body: Support for create, retrieve and update Extended Attributes for Emails");

// Set property on the message
message.setProperty(pd, value);

// append the message to server
String uri = client.appendMessage(message);

// Fetch the message from server
MapiMessage[] mapiMessage = client.fetchMapiMessages(Arrays.asList(new String[] { uri }), Arrays.asList(new PropertyDescriptor[] { pd }));

// Retrieve the property from the message
String fetchedValue = mapiMessage[0].getNamedProperties().get_Item(pd).getString();
~~~