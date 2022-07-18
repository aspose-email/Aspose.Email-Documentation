---
title: Get Messages from a Shared Mailbox
type: docs
weight: 160
url: /net/get-messages-from-a-shared-mailbox/
---


Aspose.Email supports accessing messages from the shared mailbox. To achieve this, you connect to your primary mailbox by using the [EWSClient](https://reference.aspose.com/email/net/aspose.email.clients.exchange.webservice/ewsclient) class. To access messages from the shared mailbox, you pass the shared mailbox as a string parameter to the [ListMessages](https://reference.aspose.com/email/net/aspose.email.clients.exchange.webservice.iewsclient/listmessages/methods/13) or [ListItems](https://reference.aspose.com/email/net/aspose.email.clients.exchange.webservice.iewsclient/listitems/methods/3) method.

The following code sample shows how to access messages from the shared mailbox using the [ListItems](https://reference.aspose.com/email/net/aspose.email.clients.exchange.webservice.iewsclient/listitems/methods/3) method.

{{< gist "aspose-com-gists" "522d47278b8ca448dc1d7eb97193322c" "Examples-CSharp-Exchange_EWS-GetMessagesFromSharedMailbox-1.cs" >}}
