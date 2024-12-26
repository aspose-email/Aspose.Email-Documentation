---
title: Working with Contacts on Exchange Server using WebDav
ArticleTitle: Working with Contacts on Exchange Server using WebDav
type: docs
weight: 120
url: /java/working-with-contacts-on-exchange-server-using-webdav/
---


{{% alert color="primary" %}} 

This article explains how to retrieve contact information from an Exchange Server directly. This article also shows how you can list contacts from the Contacts folder.

{{% /alert %}} 
## **Getting Contacts from an Exchange Server**
The [ExchangeClient](https://apireference.aspose.com/email/java/com.aspose.email/ExchangeClient) class’ [listContacts()](https://apireference.aspose.com/email/java/com.aspose.email/ExchangeClient#listContacts\(java.lang.String\)) method can be used to get contact information from an Exchange Server. [listContacts()](https://apireference.aspose.com/email/java/com.aspose.email/ExchangeClient#listContacts\(java.lang.String\)) method requires the URI of the Contacts folder, which can be easily got with the [ExchangeMailboxInfo.ContactsUri](https://apireference.aspose.com/email/java/com.aspose.email/ExchangeMailboxInfo#getContactsUri\(\)) property.

To get contacts from an Exchange Server:

1. Initialize the ExchangeClient class with address and credentials.
1. Get the Contacts folder's URI with the ExchangeClient.getMailboxInfo().getContactsUri() property.
1. Call the listContacts() method. It returns an array of MapiContact.
1. Do a foreach loop on the MapiContact array to read the contact information.

The following code snippet shows you how to use [ExchangeClient](https://apireference.aspose.com/email/java/com.aspose.email/ExchangeClient) class to read all contacts from an Exchange Server.


~~~Java
String mailboxURI = "http://ex2003/exchange/administrator"; // WebDAV
String username = "administrator";
String password = "pwd";
String domain = "domain.local";

// Credentials for connecting to Exchange Server
NetworkCredential credential = new NetworkCredential(username, password, domain);
ExchangeClient client = new ExchangeClient(mailboxURI, credential);

// List all the contacts
MapiContact[] contacts = client.listContacts(client.getMailboxInfo().getContactsUri());
for (MapiContact contact : contacts)
{
    // Display name and email address
    System.out.println("Name: " + contact.getNameInfo().getDisplayName() + ", Email Address: " + contact.getElectronicAddresses().getEmail1());
}
~~~
