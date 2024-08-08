---
title: Working with Gmail Contacts
type: docs
weight: 30
url: /net/working-with-gmail-contacts/
---


Aspose.Email supports working with Gmail contacts. Using the [IGmailClient](https://reference.aspose.com/email/net/aspose.email.clients.google/igmailclient/) interface, users can retrieve contacts from a Gmail account, create new contacts, and update as well as delete existing contacts. Gmail allows developers to perform all these using its public developer's API. The following user information is required for working with Gmail contacts:
User name, email address, password, client ID, client secret refresh token.
This article shows how to:

- [Access Gmail contacts](/email/net/working-with-gmail-contacts/).
- [Create new Gmail contacts](/email/net/working-with-gmail-contacts/).
- [Update existing contacts](/email/net/working-with-gmail-contacts/).
- [Delete a contact](/email/net/working-with-gmail-contacts/).
- [Save contact](/email/net/working-with-gmail-contacts/).
  
## **Access Gmail Contacts**

The following is a sample application which can be used to access the detail of contacts in all the groups.

{{< gist "aspose-email" "9e8fbeb51a8cbc4129dc71ca8cd55f0b" "Examples-CSharp-Gmail-AccessGmailContacts-AccessGmailContacts.cs" >}}

## **Creating Contact**

The following code snippet shows you how to create a contact.

{{< gist "aspose-email" "9e8fbeb51a8cbc4129dc71ca8cd55f0b" "Examples-CSharp-Gmail-CreateGmailContact-CreateGmailContact.cs" >}}

## **Updating Contact**

Once a contact is retrieved, its attributes can be updated and the contact can be saved back to the Gmail account. The following code snippet shows you how to retrieve contacts from a Gmail account and then modify one of these which is then saved back.

{{< gist "aspose-email" "9e8fbeb51a8cbc4129dc71ca8cd55f0b" "Examples-CSharp-Gmail-UpdateGmailContact-UpdateGmailContact.cs" >}}

## **Deleting Contact**

In order to delete a Gmail contact, the Gmail client [DeleteContact](https://reference.aspose.com/email/net/aspose.email.clients.google/igmailclient/deletecontact/#igmailclientdeletecontact-method) method is used as shown in the following sample snippet.

{{< gist "aspose-email" "9e8fbeb51a8cbc4129dc71ca8cd55f0b" "Examples-CSharp-Gmail-DeleteGmailContact-DeleteGmailContact.cs" >}}

## **Saving Contact**

Aspose.Email allows saving contacts to various output formats such as MSG and VCF. The [Save](https://reference.aspose.com/email/net/aspose.email.personalinfo/contact/save/) method provides the capability to achieve this. The following code snippet shows you how to save a contact.

{{< gist "aspose-email" "9e8fbeb51a8cbc4129dc71ca8cd55f0b" "Examples-CSharp-Gmail-SavingContact-SavingContact.cs" >}}
