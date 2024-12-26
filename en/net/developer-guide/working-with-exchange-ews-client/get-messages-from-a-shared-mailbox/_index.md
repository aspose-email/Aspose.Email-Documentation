---
title: Retrieve Emails from a Shared Mailbox Using C# and EWS API
ArticleTitle: Access and List Emails from a Shared Mailbox with Exchange Web Services (EWS) 
type: docs
weight: 140
url: /net/retrieve-email-messages-from-shared-mailbox-using-ews-api/
---


Aspose.Email supports accessing messages from the shared mailbox. To achieve this, you connect to your primary mailbox by using the [EWSClient](https://reference.aspose.com/email/net/aspose.email.clients.exchange.webservice/ewsclient/) class. To access messages from the shared mailbox, you pass the shared mailbox as a string parameter to the [ListMessages](https://reference.aspose.com/email/net/aspose.email.clients.exchange.webservice/iewsclient/listmessages/) or [ListItems](https://reference.aspose.com/email/net/aspose.email.clients.exchange.webservice/iewsclient/listitems/) method.

The following code sample shows how to access messages from the shared mailbox using the [ListItems](https://reference.aspose.com/email/net/aspose.email.clients.exchange.webservice/iewsclient/listitems/) method.

{{< gist "aspose-com-gists" "522d47278b8ca448dc1d7eb97193322c" "Examples-CSharp-Exchange_EWS-GetMessagesFromSharedMailbox-1.cs" >}}
