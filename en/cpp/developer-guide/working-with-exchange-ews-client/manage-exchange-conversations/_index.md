---
title: Manage Exchange Conversations via EWS in C++
ArticleTitle: Manage Exchange Conversations via EWS 
type: docs
weight: 40
url: /cpp/manage-exchange-conversations-ews/
description: Learn how to find, copy, move, and delete conversation items on Exchange Server using Aspose.Email with Exchange Web Services (EWS) for efficient mailbox management.
---

Aspose.Email allows you to manage conversation items on Microsoft Exchange Server using the [EWSClient](https://apireference.aspose.com/email/cpp/class/aspose.email.clients.exchange.web_service.e_w_s_client) class. This functionality relies on Exchange Web Services (EWS), available in Exchange Server 2007 and later.
The examples in this guide demonstrate how to **find, copy, move**, and **delete conversation items** on **Exchange Server 2010 SP1** or later.



##  **Find Conversations**

To retrieve conversation information from a specific Exchange folder, follow the steps below:

1. Connect to the Exchange Server using [IEWSClient](https://apireference.aspose.com/email/cpp/class/aspose.email.clients.exchange.web_service.i_e_w_s_client).
2. Call [FindConversations()](https://apireference.aspose.com/email/cpp/class/aspose.email.clients.exchange.web_service.i_e_w_s_client) method to list conversations in the target folder.
3. Read properties such as conversation ID, topic, and flag status.

The following code sample demonstrates how to find and display conversation items from an Exchange Server inbox.


{{< gist "aspose-com-gists" "525dd06c8783ebb18fb75cfc4b31d1ef" "Examples-Cpp-source-Exchange_EWS-FindConversationsOnExchangeServer-FindConversationsOnExchangeServer.cpp" >}}


##  **Copy Conversations**

To copy conversation items to another folder:

1. Connect to the Exchange Server using [IEWSClient](https://apireference.aspose.com/email/cpp/class/aspose.email.clients.exchange.web_service.i_e_w_s_client).
2. Retrieve conversations with the [FindConversations()](https://apireference.aspose.com/email/cpp/class/aspose.email.clients.exchange.web_service.i_e_w_s_client) method.
3. Use [CopyConversationItems()](https://apireference.aspose.com/email/cpp/class/aspose.email.clients.exchange.web_service.i_e_w_s_client) to copy matching conversations.


The following code sample demonstrates how to find and copy specific conversation items from an Exchange Server inbox to the Deleted Items folder based on the specified condition.


{{< gist "aspose-com-gists" "525dd06c8783ebb18fb75cfc4b31d1ef" "Examples-Cpp-source-Exchange_EWS-CopyConversations-CopyConversations.cpp" >}}

##  **Move Conversations**

You can move conversations between folders. The following code sample demonstrates how to find and move specific conversation items from an Exchange Server inbox to another folder.

1. Connect to the Exchange Server using [IEWSClient](https://apireference.aspose.com/email/cpp/class/aspose.email.clients.exchange.web_service.i_e_w_s_client).
2. Identify the conversations to move.
3. Call the [MoveConversationItems()](https://apireference.aspose.com/email/cpp/class/aspose.email.clients.exchange.web_service.i_e_w_s_client) method with the destination folder URI.



{{< gist "aspose-com-gists" "525dd06c8783ebb18fb75cfc4b31d1ef" "Examples-Cpp-source-Exchange_EWS-MoveConversations-MoveConversations.cpp" >}}


##  **Delete Conversations**

To delete conversation threads from a folder:

1. Connect to the Exchange Server using [IEWSClient](https://apireference.aspose.com/email/cpp/class/aspose.email.clients.exchange.web_service.i_e_w_s_client).
2. Use [FindConversations()](https://apireference.aspose.com/email/cpp/class/aspose.email.clients.exchange.web_service.i_e_w_s_client) to locate the target conversations.
3. Call the [DeleteConversationItems()](https://apireference.aspose.com/email/cpp/class/aspose.email.clients.exchange.web_service.i_e_w_s_client) method to remove them.


The following code sample demonstrates how to find and delete specific conversation items from an Exchange Server inbox.


{{< gist "aspose-com-gists" "525dd06c8783ebb18fb75cfc4b31d1ef" "Examples-Cpp-source-Exchange_EWS-DeleteConversations-DeleteConversations.cpp" >}}
