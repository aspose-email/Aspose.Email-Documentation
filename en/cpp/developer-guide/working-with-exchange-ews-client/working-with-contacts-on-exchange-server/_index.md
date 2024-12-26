---
title: Working with Contacts on Exchange Server
ArticleTitle: Working with Contacts on Exchange Server
type: docs
weight: 60
url: /cpp/working-with-contacts-on-exchange-server/
---

{{% alert color="primary" %}} Exchange Server accounts hold more than just email messages. As well as fetching, moving, sending and deleting email messages from Exchange Servers, Aspose.Email allows you to work with contacts. This article explains how to retrieve contact information using Exchange Web Services. This article also shows how you can list contacts from the Contacts folder or resolve contacts based on the contact name. {{% /alert %}} 
## **Getting Contacts with EWS**
Aspose.Email provides the [EWSClient](https://apireference.aspose.com/email/cpp/class/aspose.email.clients.exchange.web_service.e_w_s_client) class to connect to Microsoft Exchange Server using Exchange Web Services. The code snippets that follow use Exchange Web Services to read all the contacts. The following code snippet shows you how to get Contacts with EWS.



{{< gist "aspose-com-gists" "525dd06c8783ebb18fb75cfc4b31d1ef" "Examples-Cpp-source-Exchange_EWS-GettingContactsUsingEWS-GettingContactsUsingEWS.cpp" >}}
## **Resolve Contacts using Contact Name**
The following code snippet shows you how to get contacts using the contact name.



{{< gist "aspose-com-gists" "525dd06c8783ebb18fb75cfc4b31d1ef" "Examples-Cpp-source-Exchange_EWS-ResolveContactsUsingContactName-ResolveContactsUsingContactName.cpp" >}}
## **Determining Contact Notes Format**
The [Contact->get_NotesFormat](https://apireference.aspose.com/email/cpp/class/aspose.email.personal_info.contact) specifies the contacts' notes text format type defined by [TextFormat](https://apireference.aspose.com/email/cpp/namespace/aspose.email.personal_info) enumerator.
## **Fetch Contact using Id**
A particular contact can be retrieved from the server using its contact id as shown in the following code sample.



{{< gist "aspose-com-gists" "525dd06c8783ebb18fb75cfc4b31d1ef" "Examples-Cpp-source-Exchange_EWS-FetchContactUsingId-FetchContactUsingId.cpp" >}}
## **Adding Contacts**
The [CreateContact()](https://apireference.aspose.com/email/cpp/class/aspose.email.clients.exchange.web_service.i_e_w_s_client) method of the [IEWSClient](https://apireference.aspose.com/email/cpp/class/aspose.email.clients.exchange.web_service.i_e_w_s_client) class can be used to add Contact information to an Exchange Server. The [CreateContact()](https://apireference.aspose.com/email/cpp/class/aspose.email.clients.exchange.web_service.i_e_w_s_client) method takes a [Contact](https://apireference.aspose.com/email/cpp/class/aspose.email.personal_info.contact) object as an input parameter.

To add contacts to an Exchange Server:

1. Initialize the [IEWSClient](https://apireference.aspose.com/email/cpp/class/aspose.email.clients.exchange.web_service.i_e_w_s_client) with address and credentials.
1. Initialize the [Contact](https://apireference.aspose.com/email/cpp/class/aspose.email.personal_info.contact) object with the desired properties.
1. Call the [CreateContact()](https://apireference.aspose.com/email/cpp/class/aspose.email.clients.exchange.web_service.i_e_w_s_client) method and pass the contact to add to the Exchange Server.

The following code snippet demonstrates adding contacts to the Exchange Server.



{{< gist "aspose-com-gists" "525dd06c8783ebb18fb75cfc4b31d1ef" "Examples-Cpp-source-Exchange_EWS-AddContactsToExchangeServerUsingEWS-1.cpp" >}}
## **Updating Contacts**
Contact information can be updated using Microsoft Outlook. Aspose.Email can also update contact information on Exchange Server using the Exchange Web Service (EWS). The [IEWSClient->UpdateContact](https://apireference.aspose.com/email/cpp/class/aspose.email.clients.exchange.web_service.i_e_w_s_client) method can update contact information on Exchange Server.



{{< gist "aspose-com-gists" "525dd06c8783ebb18fb75cfc4b31d1ef" "Examples-Cpp-source-Exchange_EWS-UpdateContactInformationUsingEWS-UpdateContactInformationUsingEWS.cpp" >}}
## **Deleting Contacts**
The [IEWSClient](https://apireference.aspose.com/email/cpp/class/aspose.email.clients.exchange.web_service.i_e_w_s_client) class provides the [DeleteContact](https://apireference.aspose.com/email/cpp/class/aspose.email.clients.exchange.web_service.i_e_w_s_client) to access and delete contacts from an Exchange Server's contacts folder. This method takes the contact ID or [Contact](https://apireference.aspose.com/email/cpp/class/aspose.email.personal_info.contact) as an input parameter.

To delete contacts from an Exchange Server:

1. Initialize the [IEWSClient](https://apireference.aspose.com/email/cpp/class/aspose.email.clients.exchange.web_service.i_e_w_s_client) with address and credentials.
1. Delete a contact using its ID.
1. Delete a contact by calling the [DeleteContact](https://apireference.aspose.com/email/cpp/class/aspose.email.clients.exchange.web_service.i_e_w_s_client) method with [Contact](https://apireference.aspose.com/email/cpp/class/aspose.email.personal_info.contact) as an input parameter.

The following code snippet shows you how to delete contacts from an exchange server using [IEWSClient->DeleteContact](https://apireference.aspose.com/email/cpp/class/aspose.email.clients.exchange.web_service.i_e_w_s_client).



{{< gist "aspose-com-gists" "525dd06c8783ebb18fb75cfc4b31d1ef" "Examples-Cpp-source-Exchange_EWS-DeleteContactsFromExchangeServerUsingEWS-DeleteContactsFromExchangeServerUsingEWS.cpp" >}}
