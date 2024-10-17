---
title: "Trabajando con los Atributos Extendidos de Exchange de los Elementos de Exchange"
url: /es/java/working-with-exchange-extended-attributes-of-exchange-items/
weight: 140
type: docs
---

La API Aspose.Email te permite crear, recuperar y actualizar propiedades extendidas de mensajes utilizando el cliente EWS de la API. El siguiente ejemplo de código ilustra esto creando un atributo extendido, añadiéndolo al mensaje en el servidor y recuperando el mensaje como [MapiMessage](https://apireference.aspose.com/email/java/com.aspose.email/mapimessage) del servidor de Exchange utilizando el método [fetchItem](https://reference.aspose.com/email/java/com.aspose.email/IEWSClient#fetchItem\(java.lang.String,%20java.lang.Iterable\)) del cliente.

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