---
title: Manage Contacts in Exchange Server Using EWS 
ArticleTitle: Retrieve, Manage, and Update Contacts in Exchange Server Using EWS
type: docs
weight: 60
url: /net/manage-contacts-on-exchange-server-using-ews/
---


{{% alert color="primary" %}} Exchange Server accounts hold more than just email messages. As well as [fetching](https://docs.aspose.com/email/net/working-with-exchange-mailbox-and-messages/#fetch-messages-from-an-exchange-server-mailbox), [moving](https://docs.aspose.com/email/net/working-with-exchange-mailbox-and-messages/#moving-messages), [sending](https://docs.aspose.com/email/net/working-with-exchange-mailbox-and-messages/#sending-email-messages) and [deleting email messages](https://docs.aspose.com/email/net/working-with-exchange-mailbox-and-messages/#deleting-messages) from Exchange Servers, Aspose.Email allows you to work with contacts. This article explains how to retrieve contact information using Exchange Web Services. This article also shows how you can list contacts from the Contacts folder or resolve contacts based on contact name. {{% /alert %}} 

## **Get Contacts with EWS**

Aspose.Email provides the [EWSClient](https://reference.aspose.com/email/net/aspose.email.clients.exchange.webservice/ewsclient/) class to connect to Microsoft Exchange Server using Exchange Web Services. The code snippets that follow use Exchange Web Services to read all the contacts. The following code snippet shows you how to get Contacts with EWS.

{{< gist "aspose-email" "9e8fbeb51a8cbc4129dc71ca8cd55f0b" "Examples-CSharp-Exchange_EWS-GettingContactsUsingEWS-GettingContactsUsingEWS.cs" >}}

## **Resolve Contacts by Name**

The following code snippet shows you how to use get contacts with EWS

{{< gist "aspose-email" "9e8fbeb51a8cbc4129dc71ca8cd55f0b" "Examples-CSharp-Exchange_EWS-ResolveContactsUsingContactName-ResolveContactsUsingContactName.cs" >}}

## **Determine Contact Notes Format**

The Aspose.Email.Mail.Contact.NotesFormat specifies the contacts notes text format type defined by Aspose.Email.TextFormat enumerator.

## **Fetch Contacts by ID**

A particular contact can be retrieved from the server using its contact id as shown in the following code sample.

{{< gist "aspose-email" "9e8fbeb51a8cbc4129dc71ca8cd55f0b" "Examples-CSharp-Exchange_EWS-FetchContactUsingId-FetchContactUsingId.cs" >}}

## **Adding Contacts**

The [EWSClient](https://reference.aspose.com/email/net/aspose.email.clients.exchange.webservice/ewsclient/#ewsclient-class) class [CreateContact()](https://reference.aspose.com/email/net/aspose.email.clients.exchange.webservice/iewsclient/createcontact/) method can be used to add Contact information to an Exchange Server. The [CreateContact()](https://reference.aspose.com/email/net/aspose.email.clients.exchange.webservice/iewsclient/createcontact/) method takes a Contact object as an input parameter.

To add contacts to an Exchange Server:

1. Initialize the EWSClient with address and credentials.
1. Initialize the Contact object with the desired properties.
1. Call the CreateContact method to add the contact to the Exchange Server.

Aspose.Email provides the [EWSClient](https://reference.aspose.com/email/net/aspose.email.clients.exchange.webservice/ewsclient/#ewsclient-class) class to connect to Microsoft Exchange Server using Exchange Web Services. The code snippets show you how to use Exchange Web Services to add contacts to an Exchange Server.

{{< gist "aspose-email" "9e8fbeb51a8cbc4129dc71ca8cd55f0b" "Examples-CSharp-Exchange_EWS-AddContactsToExchangeServerUsingEWS-AddContactsToExchangeServerUsingEWS.cs" >}}

## **Updating Contacts**

Contact information can be updated using Microsoft Outlook. Aspose.Email can also update contact information on Exchange Server using the Exchange Web Service (EWS). The IEWSClient [UpdateContact](https://reference.aspose.com/email/net/aspose.email.clients.exchange.webservice/iewsclient/updatecontact/) method can update contact information on Exchange Server.

{{< gist "aspose-email" "9e8fbeb51a8cbc4129dc71ca8cd55f0b" "Examples-CSharp-Exchange_EWS-UpdateContactInformationUsingEWS-UpdateContactInformationUsingEWS.cs" >}}

## **Deleting Contacts**

The [EWSClient](https://reference.aspose.com/email/net/aspose.email.clients.exchange.webservice/ewsclient/) class allows the DeleteContact to access and delete contacts from an Exchange Server contacts folder. This method takes the contact ID or MapiContact as an input parameter.

To delete contacts from an Exchange Server:

1. Initialize the ExchangeWebServiceClient with address and credentials.
1. Delete a contact using its ID.
1. Delete a contact by calling the [DeleteContact](https://reference.aspose.com/email/net/aspose.email.clients.exchange.dav/exchangeclient/deletecontact/) method with [MapiContact](https://reference.aspose.com/email/net/aspose.email.mapi/mapicontact/mapicontact/) as input parameter.

The following code snippets show you how to delete contacts from an exchange server using exchange web service.

{{< gist "aspose-email" "9e8fbeb51a8cbc4129dc71ca8cd55f0b" "Examples-CSharp-Exchange_EWS-DeleteContactsFromExchangeServerUsingEWS-DeleteContactsFromExchangeServerUsingEWS.cs" >}}

## **Working with Extended Contact Properties**

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
