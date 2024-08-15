---
title: "Administración de los elementos de conversación"
url: /es/java/managing-conversation-items/
weight: 40
type: docs
---


Aspose.Email para Java se puede usar para administrar los elementos de conversación en Exchange Server con [EWSClient](https://apireference.aspose.com/email/java/com.aspose.email/ewsclient) clase. Esta clase usa los servicios web de Exchange, que solo están disponibles en Exchange Server 2007 y versiones posteriores. En este artículo se muestra cómo [find](#finding-conversations), [copy](#copying-conversations), [move](#moving-conversations) and [delete](#deleting-conversations) elementos de conversación en Exchange Server 2010. Todas las funciones incluidas en esta sección requieren el Service Pack 1 de Microsoft Exchange Server 2010.
## **Búsqueda de conversaciones**
Para obtener la información de la conversación de una carpeta específica del servidor Exchange:

1. Conéctese al servidor Exchange mediante la clase IEWSClient.
1. Llame al método iewsClient.findConversations () para buscar todos los elementos de conversación de una carpeta.
1. Muestra las propiedades del elemento de conversación, como el identificador, el tema de la conversación y el estado de la marca.

El siguiente fragmento de código muestra cómo buscar conversaciones.



~~~Java
IEWSClient client = EWSClient.getEWSClient(mailboxUri, credentials);
System.out.println("Connected to Exchange 2010");

// Find Conversation Items in the Inbox folder
ExchangeConversation[] conversations = client.findConversations(client.getMailboxInfo().getInboxUri());
// Show all conversations
for (ExchangeConversation conversation : conversations) {
    // Display conversation properties like Id and Topic
    System.out.println("Topic: " + conversation.getConversationTopic());
    System.out.println("Flag Status: " + conversation.getFlagStatus());
    System.out.println();
}
~~~
## **Copiar conversaciones**
Para copiar conversaciones de una carpeta a otra:

1. Conéctese al servidor Exchange mediante la clase IEWSClient.
1. Llame al método iewsClient.copyConversationItems () para copiar el elemento de conversación de la carpeta de origen a la carpeta de destino.

El siguiente fragmento de código muestra cómo copiar conversaciones.



~~~Java
IEWSClient client = EWSClient.getEWSClient(mailboxUri, credentials);
System.out.println("Connected to Exchange 2010");

// Find those Conversation Items in the Inbox folder which we want to copy
ExchangeConversation[] conversations = client.findConversations(client.getMailboxInfo().getInboxUri());
for (ExchangeConversation conversation : conversations) {
    System.out.println("Topic: " + conversation.getConversationTopic());
    // Copy the conversation item based on some condition
    if (conversation.getConversationTopic().contains("test email")) {
        client.copyConversationItems(conversation.getConversationId(), client.getMailboxInfo().getDeletedItemsUri());
        System.out.println("Copied the conversation item to another folder");
    }
}
~~~
## **Conversaciones conmovedoras**
Para mover conversaciones de una carpeta a otra:

1. Conéctese al servidor Exchange mediante la clase IEWSClient.
1. Llame al método iewsClient.moveConversationItems () para mover una conversación de la carpeta de origen a la carpeta de destino.

En el siguiente fragmento de código, se muestra cómo mover las conversaciones.



~~~Java
IEWSClient client = EWSClient.getEWSClient(mailboxUri, credentials);
System.out.println("Connected to Exchange 2010");

// Find those Conversation Items in the Inbox folder which we want to move
ExchangeConversation[] conversations = client.findConversations(client.getMailboxInfo().getInboxUri());

for (ExchangeConversation conversation : conversations) {
    System.out.println("Topic: " + conversation.getConversationTopic());
    // Move the conversation item based on some condition
    if (conversation.getConversationTopic().contains("test email") == true) {
        client.moveConversationItems(conversation.getConversationId(), client.getMailboxInfo().getDeletedItemsUri());
        System.out.println("Moved the conversation item to another folder");
    }
}
~~~
## **Eliminar conversaciones**
Para eliminar conversaciones de una carpeta:

1. Conéctese al servidor Exchange mediante la clase IEWSClient.
1. Llame al método IewsClient.deleteConversationItems () para eliminar el elemento de conversación de la carpeta de origen.

En el siguiente fragmento de código, se muestra cómo eliminar conversaciones.



~~~Java
IEWSClient client = EWSClient.getEWSClient(mailboxUri, credentials);
System.out.println("Connected to Exchange 2010");

// Find those Conversation Items in the Inbox folder which we want to delete
ExchangeConversation[] conversations = client.findConversations(client.getMailboxInfo().getInboxUri());
for (ExchangeConversation conversation : conversations) {
    System.out.println("Topic: " + conversation.getConversationTopic());
    // Delete the conversation item based on some condition
    if (conversation.getConversationTopic().contains("test email") == true) {
        client.deleteConversationItems(conversation.getConversationId());
        System.out.println("Deleted the conversation item");
    }
}
~~~