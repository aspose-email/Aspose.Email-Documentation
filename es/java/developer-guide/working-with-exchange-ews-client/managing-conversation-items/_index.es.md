---
title: "Gestionando Elementos de Conversación"
url: /es/java/gestionando-elementos-de-conversacion/
weight: 40
type: docs
---


Aspose.Email para Java se puede utilizar para gestionar los elementos de conversación en Exchange Server con la clase [EWSClient](https://apireference.aspose.com/email/java/com.aspose.email/ewsclient). Esta clase utiliza Exchange Web Services, que solo están disponibles en Exchange Server 2007 y versiones posteriores. Este artículo muestra cómo [encontrar](#finding-conversations), [copiar](#copying-conversations), [mover](#moving-conversations) y [eliminar](#deleting-conversations) elementos de conversación en Exchange Server 2010. Se requiere Microsoft Exchange Server 2010 Service Pack 1 para todas las características incluidas en esta sección.
## **Encontrando Conversaciones**
Para obtener la información de conversación de una carpeta específica en el Exchange Server:

1. Conéctese al Exchange Server utilizando la clase IEWSClient.
1. Llame al método IEWSClient.findConversations() para encontrar todos los elementos de conversación de una carpeta.
1. Muestre las propiedades del elemento de conversación como ID, tema de conversación y estado de la bandera.

El siguiente fragmento de código muestra cómo encontrar conversaciones.



~~~Java
IEWSClient client = EWSClient.getEWSClient(mailboxUri, credentials);
System.out.println("Conectado a Exchange 2010");

// Encontrar elementos de conversación en la carpeta de la Bandeja de entrada
ExchangeConversation[] conversations = client.findConversations(client.getMailboxInfo().getInboxUri());
// Mostrar todas las conversaciones
for (ExchangeConversation conversation : conversations) {
    // Mostrar propiedades de conversación como Id y Tema
    System.out.println("Tema: " + conversation.getConversationTopic());
    System.out.println("Estado de la Bandera: " + conversation.getFlagStatus());
    System.out.println();
}
~~~
## **Copiando Conversaciones**
Para copiar conversaciones de una carpeta a otra:

1. Conéctese al Exchange Server utilizando la clase IEWSClient.
1. Llame al método IEWSClient.copyConversationItems() para copiar el elemento de conversación de la carpeta de origen a la carpeta de destino.

El siguiente fragmento de código muestra cómo copiar conversaciones.



~~~Java
IEWSClient client = EWSClient.getEWSClient(mailboxUri, credentials);
System.out.println("Conectado a Exchange 2010");

// Encontrar aquellos elementos de conversación en la carpeta de la Bandeja de entrada que queremos copiar
ExchangeConversation[] conversations = client.findConversations(client.getMailboxInfo().getInboxUri());
for (ExchangeConversation conversation : conversations) {
    System.out.println("Tema: " + conversation.getConversationTopic());
    // Copiar el elemento de conversación basado en alguna condición
    if (conversation.getConversationTopic().contains("test email")) {
        client.copyConversationItems(conversation.getConversationId(), client.getMailboxInfo().getDeletedItemsUri());
        System.out.println("Copiado el elemento de conversación a otra carpeta");
    }
}
~~~
## **Moviendo Conversaciones**
Para mover conversaciones de una carpeta a otra:

1. Conéctese al Exchange Server utilizando la clase IEWSClient.
1. Llame al método IEWSClient.moveConversationItems() para mover una conversación de la carpeta de origen a la carpeta de destino.

El siguiente fragmento de código muestra cómo mover conversaciones.



~~~Java
IEWSClient client = EWSClient.getEWSClient(mailboxUri, credentials);
System.out.println("Conectado a Exchange 2010");

// Encontrar aquellos elementos de conversación en la carpeta de la Bandeja de entrada que queremos mover
ExchangeConversation[] conversations = client.findConversations(client.getMailboxInfo().getInboxUri());

for (ExchangeConversation conversation : conversations) {
    System.out.println("Tema: " + conversation.getConversationTopic());
    // Mover el elemento de conversación basado en alguna condición
    if (conversation.getConversationTopic().contains("test email") == true) {
        client.moveConversationItems(conversation.getConversationId(), client.getMailboxInfo().getDeletedItemsUri());
        System.out.println("Movido el elemento de conversación a otra carpeta");
    }
}
~~~
## **Eliminando Conversaciones**
Para eliminar conversaciones de una carpeta:

1. Conéctese al Exchange Server utilizando la clase IEWSClient.
1. Llame al método IEWSClient.deleteConversationItems() para eliminar el elemento de conversación de la carpeta de origen.

El siguiente fragmento de código muestra cómo eliminar conversaciones.



~~~Java
IEWSClient client = EWSClient.getEWSClient(mailboxUri, credentials);
System.out.println("Conectado a Exchange 2010");

// Encontrar aquellos elementos de conversación en la carpeta de la Bandeja de entrada que queremos eliminar
ExchangeConversation[] conversations = client.findConversations(client.getMailboxInfo().getInboxUri());
for (ExchangeConversation conversation : conversations) {
    System.out.println("Tema: " + conversation.getConversationTopic());
    // Eliminar el elemento de conversación basado en alguna condición
    if (conversation.getConversationTopic().contains("test email") == true) {
        client.deleteConversationItems(conversation.getConversationId());
        System.out.println("Eliminado el elemento de conversación");
    }
}
~~~