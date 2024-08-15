---
title: "Управление элементами беседы"
url: /ru/java/managing-conversation-items/
weight: 40
type: docs
---


Aspose.Email для Java можно использовать для управления элементами беседы на сервере Exchange с помощью [EWSClient](https://apireference.aspose.com/email/java/com.aspose.email/ewsclient) класс. В этом классе используются веб-службы Exchange, доступные только в Exchange Server 2007 и более поздних версиях. В этой статье показано, как [find](#finding-conversations), [copy](#copying-conversations), [move](#moving-conversations) and [delete](#deleting-conversations) элементы беседы на сервере Exchange 2010. Для всех функций, описанных в этом разделе, требуется пакет обновления 1 для Microsoft Exchange Server 2010.
## **Поиск разговоров**
Чтобы получить информацию о разговоре из определенной папки на сервере Exchange, выполните следующие действия:

1. Подключитесь к серверу Exchange с помощью класса IEWSClient.
1. Вызовите метод IEWSclient.findConversations (), чтобы найти все элементы беседы в папке.
1. Отобразите свойства элемента беседы, такие как идентификатор, тема разговора и статус флага.

В следующем фрагменте кода показано, как найти разговоры.



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
## **Копирование разговоров**
Чтобы скопировать разговоры из одной папки в другую, выполните следующие действия:

1. Подключитесь к серверу Exchange с помощью класса IEWSClient.
1. Вызовите метод IEWSClient.copyConversationItems (), чтобы скопировать элемент беседы из исходной папки в папку назначения.

В следующем фрагменте кода показано, как копировать разговоры.



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
## **Трогательные разговоры**
Чтобы перенести беседы из одной папки в другую, выполните следующие действия:

1. Подключитесь к серверу Exchange с помощью класса IEWSClient.
1. Вызовите метод IEWSClient.moveConversationItems (), чтобы переместить беседу из исходной папки в папку назначения.

В следующем фрагменте кода показано, как перемещать разговоры.



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
## **Удаление разговоров**
Чтобы удалить разговоры из папки, выполните следующие действия:

1. Подключитесь к серверу Exchange с помощью класса IEWSClient.
1. Вызовите метод IEWSClient.deleteConversationItems (), чтобы удалить элемент беседы из исходной папки.

В следующем фрагменте кода показано, как удалять разговоры.



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