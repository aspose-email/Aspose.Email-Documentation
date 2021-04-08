---
title: Managing Conversation Items
type: docs
weight: 40
url: /java/managing-conversation-items/
---


Aspose.Email for Java can be used to manage the conversation items on Exchange Server with the [EWSClient](https://apireference.aspose.com/email/java/com.aspose.email/ewsclient) class. This class uses Exchange Web Services, which are only available in Exchange Server 2007 and later releases. This article shows how to [find](#finding-conversations), [copy](#copying-conversations), [move](#moving-conversations) and [delete](#deleting-conversations) conversation items on Exchange Server 2010. Microsoft Exchange Server 2010 Service Pack 1 is required for all the features included in this section.
## **Finding Conversations**
To get the conversation information from a specific folder on the Exchange Server:

1. Connect to the Exchange Server using the IEWSClient class.
1. Call the IEWSClient.findConversations() method to find all the conversation items from a folder.
1. Display the conversation item properties like ID, conversation topic and flag status.

The following code snippet shows you how to find conversations.



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
## **Copying Conversations**
To copy conversations from one folder to another:

1. Connect to the Exchange Server using the IEWSClient class.
1. Call the IEWSClient.copyConversationItems() method to copy the conversation item from source folder to destination folder.

The following code snippet shows you how to copying conversations.



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
## **Moving Conversations**
To move conversations from one folder to another:

1. Connect to the Exchange Server using the IEWSClient class.
1. Call the IEWSClient.moveConversationItems() method to move a conversation from the source folder to the destination folder.

The following code snippet shows you how to moving conversations.



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
## **Deleting Conversations**
To delete conversations from a folder:

1. Connect to the Exchange Server using the IEWSClient class.
1. Call the IEWSClient.deleteConversationItems() method to delete the conversation item from the source folder.

The following code snippet shows you how to delete conversations.



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