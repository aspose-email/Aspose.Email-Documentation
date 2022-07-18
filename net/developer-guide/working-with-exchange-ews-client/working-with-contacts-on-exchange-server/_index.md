---
title: Working with Contacts on Exchange Server
type: docs
weight: 60
url: /net/working-with-contacts-on-exchange-server/
---


{{% alert color="primary" %}} Exchange Server accounts hold more than just email messages. As well as [fetching](/email/net/working-with-exchange-mailbox-and-messages/#fetch-messages-from-an-exchange-server-mailbox), [moving](/email/net/working-with-exchange-mailbox-and-messages/#moving-messages), [sending](/email/net/working-with-exchange-mailbox-and-messages/#sending-email-messages) and [deleting email messages](/email/net/working-with-exchange-mailbox-and-messages/#deleting-messages) from Exchange Servers, Aspose.Email allows you to work with contacts. This article explains how to retrieve contact information using Exchange Web Services. This article also shows how you can list contacts from the Contacts folder or resolve contacts based on contact name. {{% /alert %}} 
## **Getting Contacts with EWS**
Aspose.Email provides the [EWSClient](https://reference.aspose.com/email/net/aspose.email.clients.exchange.webservice/ewsclient) class to connect to Microsoft Exchange Server using Exchange Web Services. The code snippets that follow use Exchange Web Services to read all the contacts. The following code snippet shows you how to get Contacts with EWS.



{{< gist "aspose-email" "9e8fbeb51a8cbc4129dc71ca8cd55f0b" "Examples-CSharp-Exchange_EWS-GettingContactsUsingEWS-GettingContactsUsingEWS.cs" >}}
## **Resolve Contacts using Contact Name**
The following code snippet shows you how to use get contacts with EWS



{{< gist "aspose-email" "9e8fbeb51a8cbc4129dc71ca8cd55f0b" "Examples-CSharp-Exchange_EWS-ResolveContactsUsingContactName-ResolveContactsUsingContactName.cs" >}}
## **Determining Contact Notes Format**
The Aspose.Email.Mail.Contact.NotesFormat specifies the contacts' notes text format type defined by Aspose.Email.TextFormat enumerator.
## **Fetch Contact using Id**
A particular contact can be retrieved from the server using its contact id as shown in the following code sample.



{{< gist "aspose-email" "9e8fbeb51a8cbc4129dc71ca8cd55f0b" "Examples-CSharp-Exchange_EWS-FetchContactUsingId-FetchContactUsingId.cs" >}}
## **Adding Contacts**
The EWSClient class CreateContact() method can be used to add Contact information to an Exchange Server. The CreateContact() method takes a Contact object as an input parameter.

To add contacts to an Exchange Server:

1. Initialize the EWSClient with address and credentials.
1. Initialize the Contact object with the desired properties.
1. Call the CreateContact method to add the contact to the Exchange Server.

Aspose.Email provides the [EWSClient](https://reference.aspose.com/email/net/aspose.email.clients.exchange.webservice/ewsclient) class to connect to Microsoft Exchange Server using Exchange Web Services. The code snippets shows you how to follow use Exchange Web Services to add contacts to an Exchange Server.



{{< gist "aspose-email" "9e8fbeb51a8cbc4129dc71ca8cd55f0b" "Examples-CSharp-Exchange_EWS-AddContactsToExchangeServerUsingEWS-AddContactsToExchangeServerUsingEWS.cs" >}}
## **Updating Contacts**
Contact information can be updated using Microsoft Outlook. Aspose.Email can also update contact information on Exchange Server using the Exchange Web Service (EWS). The IEWSClient's UpdateContact method can update contact information on Exchange Server.



{{< gist "aspose-email" "9e8fbeb51a8cbc4129dc71ca8cd55f0b" "Examples-CSharp-Exchange_EWS-UpdateContactInformationUsingEWS-UpdateContactInformationUsingEWS.cs" >}}
## **Deleting Contacts**
The [EWSClient](https://reference.aspose.com/email/net/aspose.email.clients.exchange.webservice/ewsclient) class provides the DeleteContact to access and delete contacts from an Exchange Server's contacts folder. This method takes the contact ID or MapiContact as an input parameter.

To delete contacts from an Exchange Server:

1. Initialize the ExchangeWebServiceClient with address and credentials.
1. Delete a contact using its ID.
1. Delete a contact by calling the DeleteContact method with MapiContact as input parameter.

The following code snippets shows you how to deleting contacts from an exchange server using exchange web service.



{{< gist "aspose-email" "9e8fbeb51a8cbc4129dc71ca8cd55f0b" "Examples-CSharp-Exchange_EWS-DeleteContactsFromExchangeServerUsingEWS-DeleteContactsFromExchangeServerUsingEWS.cs" >}}
## **Working with Extended Properties of Contacts on Exchange Server**


``` cs

 IEWSClient client = EWSClient.GetEWSClient("https://outlook.office365.com/ews/exchange.asmx", "testUser", "pwd", "domain");

//The required extended properties must be added in order to create or read them from the Exchange Server

string[] extraFields = new string[] {{ "User Field 1", "User Field 2", "User Field 3", "User Field 4" }};

foreach (string extraField in extraFields)

    client.ContactExtendedPropertiesDefinition.Add(extraField);

//Create a test contact on the Exchange Server

Contact contact = new Contact();

contact.DisplayName = "EMAILNET-38433 - " + Guid.NewGuid().ToString();

foreach (string extraField in extraFields)

    contact.ExtendedProperties.Add(extraField, extraField);

string contactId = client.CreateContact(contact);

//retrieve the contact back from the server after some time

Thread.Sleep(5000);

contact = client.GetContact(contactId);

//Parse the extended properties of contact

foreach (string extraField in extraFields)

    if (contact.ExtendedProperties.ContainsKey(extraField))

        Console.WriteLine(contact.ExtendedProperties[extraField].ToString());

```
