---
title: Managing Conversation Items
type: docs
weight: 40
url: /net/managing-conversation-items/
---


Aspose.Email for .NET can be used to manage the conversation items on Exchange Server with the [EWSClient](https://reference.aspose.com/email/net/aspose.email.clients.exchange.webservice/ewsclient) class. This class uses Exchange Web Services, which are only available in Exchange Server 2007 and later releases. This article shows how to [find](#finding-conversations), [copy](#copying-conversations), [move](#moving-conversations) and [delete](#deleting-conversations) conversation items on Exchange Server 2010. Microsoft Exchange Server 2010 Service Pack 1 is required for all the features included in this section.
## **Finding Conversations**
To get the conversation information from a specific folder on the Exchange Server:

1. Connect to the Exchange Server using the [IEWSClient](https://reference.aspose.com/email/net/aspose.email.clients.exchange.webservice/iewsclient) class.
1. Call the [IEWSClient.FindConversations()](https://reference.aspose.com/email/net/aspose.email.clients.exchange.webservice/iewsclient/methods/findconversations) method to find all the conversation items from a folder.
1. Display the conversation item properties like ID, conversation topic and flag status.

The following code snippet shows you how to find conversations.



{{< gist "aspose-com-gists" "6e5185a63aec6fd70d83098e82b06a32" "Examples-CSharp-Exchange_EWS-FindConversationsOnExchangeServer-FindConversationsOnExchangeServer.cs" >}}
## **Copying Conversations**
To copy conversations from one folder to another:

1. Connect to the Exchange Server using the [IEWSClient](https://reference.aspose.com/email/net/aspose.email.clients.exchange.webservice/iewsclient) class.
1. Call the [IEWSClient.CopyConversationItems()](https://reference.aspose.com/email/net/aspose.email.clients.exchange.webservice/iewsclient/methods/copyconversationitems) method to copy the conversation item from source folder to destination folder.

The following code snippet shows you how to copying conversations.



{{< gist "aspose-com-gists" "6e5185a63aec6fd70d83098e82b06a32" "Examples-CSharp-Exchange_EWS-CopyConversations-CopyConversations.cs" >}}
## **Moving Conversations**
To move conversations from one folder to another:

1. Connect to the Exchange Server using the [IEWSClient](https://reference.aspose.com/email/net/aspose.email.clients.exchange.webservice/iewsclient) class.
1. Call the [IEWSClient.MoveConversationItems()](https://reference.aspose.com/email/net/aspose.email.clients.exchange.webservice/iewsclient/methods/moveconversationitems) method to move a conversation from the source folder to the destination folder.

The following code snippet shows you how to moving conversations.



{{< gist "aspose-com-gists" "6e5185a63aec6fd70d83098e82b06a32" "Examples-CSharp-Exchange_EWS-MoveConversations-MoveConversations.cs" >}}
## **Deleting Conversations**
To delete conversations from a folder:

1. Connect to the Exchange Server using the [IEWSClient](https://reference.aspose.com/email/net/aspose.email.clients.exchange.webservice/iewsclient) class.
1. Call the [IEWSClient.DeleteConversationItems()](https://reference.aspose.com/email/net/aspose.email.clients.exchange.webservice/iewsclient/methods/deleteconversationitems) method to delete the conversation item from the source folder.

The following code snippet shows you how to delete conversations.



{{< gist "aspose-com-gists" "6e5185a63aec6fd70d83098e82b06a32" "Examples-CSharp-Exchange_EWS-DeleteConversations-DeleteConversations.cs" >}}
