---
title: Working with Contacts on Exchange Server using WebDav
type: docs
weight: 50
url: /net/working-with-contacts-on-exchange-server-using-webdav/
---


{{% alert color="primary" %}} 

Exchange Server accounts hold more than just email messages. As well as [fetching](/email/net/working-with-exchange-mailbox-and-messages-using-webdav/#fetch-messages-from-an-exchange-server-mailbox), [moving](/email/net/working-with-exchange-mailbox-and-messages-using-webdav/#moving-messages), [sending](/email/net/working-with-exchange-mailbox-and-messages-using-webdav/#sending-email-messages) and [deleting email messages](/email/net/working-with-exchange-mailbox-and-messages-using-webdav/#deleting-messages) from Exchange Servers, Aspose.Email allows you to work with contacts. This article explains how to retrieve contact information from an Exchange Server directly. This article also shows how you can list contacts from the Contacts folder.

{{% /alert %}} 
## **Getting Contacts from an Exchange Server**
The [ExchangeClient](https://reference.aspose.com/email/net/aspose.email.clients.exchange.dav/exchangeclient) class’ [ListContacts()](https://reference.aspose.com/email/net/aspose.email.clients.exchange.dav/exchangeclient/methods/listcontacts) method can be used to get contact information from an Exchange Server. [ListContacts()](https://reference.aspose.com/email/net/aspose.email.clients.exchange.dav/exchangeclient/methods/listcontacts) method requires the URI of the Contacts folder, which can be easily got with the [ExchangeMailboxInfo.ContactsUri](https://reference.aspose.com/email/net/aspose.email.clients.exchange/exchangemailboxinfo/properties/contactsuri) property.

To get contacts from an Exchange Server:

1. Initialize the [ExchangeClient](https://reference.aspose.com/email/net/aspose.email.clients.exchange.dav/exchangeclient) class with address and credentials.
1. Get the Contacts folder's URI with the [ExchangeClient.MailboxInfo.ContactsUri](https://reference.aspose.com/email/net/aspose.email.clients.exchange/exchangemailboxinfo/properties/contactsuri) property.
1. Call the [ListContacts()](https://reference.aspose.com/email/net/aspose.email.clients.exchange.dav/exchangeclient/methods/listcontacts) method. It returns an array of [MapiContact](https://reference.aspose.com/email/net/aspose.email.mapi/mapicontact).
1. Do a foreach loop on the [MapiContact](https://reference.aspose.com/email/net/aspose.email.mapi/mapicontact) array to read the contact information.

The following code snippet shows you how to use [ExchangeClient](https://reference.aspose.com/email/net/aspose.email.clients.exchange.dav/exchangeclient) class to read all contacts from an Exchange Server.



{{< gist "aspose-com-gists" "6e5185a63aec6fd70d83098e82b06a32" "Examples-CSharp-Exchange_WebDav-GettingContactsFromAnExchangeServer-GettingContactsFromAnExchangeServer.cs" >}}
