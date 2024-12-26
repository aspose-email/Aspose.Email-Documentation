---
title: Managing Conversation Items
ArticleTitle: Managing Conversation Items
type: docs
weight: 40
url: /cpp/managing-conversation-items/
---

Aspose.Email can be used to manage the conversation items on Exchange Server with the [EWSClient](https://apireference.aspose.com/email/cpp/class/aspose.email.clients.exchange.web_service.e_w_s_client) class. This class uses Exchange Web Services, which are only available in Exchange Server 2007 and later releases. This article shows how to find, copy, move and delete conversation items on Exchange Server 2010. Microsoft Exchange Server 2010 Service Pack 1 is required for all the features included in this section.
##  **Finding Conversations**
To get the conversation information from a specific folder on the Exchange Server:

1. Connect to the Exchange Server using the [IEWSClient](https://apireference.aspose.com/email/cpp/class/aspose.email.clients.exchange.web_service.i_e_w_s_client) class.
1. Call the [FindConversations()](https://apireference.aspose.com/email/cpp/class/aspose.email.clients.exchange.web_service.i_e_w_s_client) method to find all the conversation items in a folder.
1. Display the conversation item properties like ID, conversation topic and flag status.

The following code snippet shows you how to find conversations.



{{< gist "aspose-com-gists" "525dd06c8783ebb18fb75cfc4b31d1ef" "Examples-Cpp-source-Exchange_EWS-FindConversationsOnExchangeServer-FindConversationsOnExchangeServer.cpp" >}}
##  **Copying Conversations**
To copy conversations from one folder to another:

1. Connect to the Exchange Server using the [IEWSClient](https://apireference.aspose.com/email/cpp/class/aspose.email.clients.exchange.web_service.i_e_w_s_client) class.
1. Call the [CopyConversationItems()](https://apireference.aspose.com/email/cpp/class/aspose.email.clients.exchange.web_service.i_e_w_s_client) method to copy the conversation item from the source folder to the destination folder.

The following code snippet shows you how to copy conversations.



{{< gist "aspose-com-gists" "525dd06c8783ebb18fb75cfc4b31d1ef" "Examples-Cpp-source-Exchange_EWS-CopyConversations-CopyConversations.cpp" >}}
##  **Moving Conversations**
To move conversations from one folder to another:

1. Connect to the Exchange Server using the [IEWSClient](https://apireference.aspose.com/email/cpp/class/aspose.email.clients.exchange.web_service.i_e_w_s_client) class.
1. Call the [MoveConversationItems()](https://apireference.aspose.com/email/cpp/class/aspose.email.clients.exchange.web_service.i_e_w_s_client) method to move a conversation from the source folder to the destination folder.

The following code snippet shows you how to move conversations.



{{< gist "aspose-com-gists" "525dd06c8783ebb18fb75cfc4b31d1ef" "Examples-Cpp-source-Exchange_EWS-MoveConversations-MoveConversations.cpp" >}}
##  **Deleting Conversations**
To delete conversations from a folder:

1. Connect to the Exchange Server using the [IEWSClient](https://apireference.aspose.com/email/cpp/class/aspose.email.clients.exchange.web_service.i_e_w_s_client) class.
1. Call the [DeleteConversationItems()](https://apireference.aspose.com/email/cpp/class/aspose.email.clients.exchange.web_service.i_e_w_s_client) method to delete the conversation item from the source folder.

The following code snippet shows you how to delete conversations.



{{< gist "aspose-com-gists" "525dd06c8783ebb18fb75cfc4b31d1ef" "Examples-Cpp-source-Exchange_EWS-DeleteConversations-DeleteConversations.cpp" >}}
