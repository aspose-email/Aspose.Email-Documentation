---
title: Manage Contacts with Exchange Web Services (EWS) in C++
ArticleTitle: Manage Contacts with Exchange Web Services (EWS)
type: docs
weight: 60
url: /cpp/manage-contacts-on-exchange-server/
description: Learn how to retrieve, resolve, add, update, and delete Exchange Server contacts using Aspose.Email EWS client, with clear examples in C++.
---


Aspose.Email lets you work with more than just email messages on Microsoft Exchange Server. Using the [EWSClient](https://apireference.aspose.com/email/cpp/class/aspose.email.clients.exchange.web_service.e_w_s_client) API, you can retrieve, resolve, create, update, and delete contacts stored in an Exchange mailbox. This article explains the key operations for managing contacts with Exchange Web Services (EWS).


## **Get Contacts with EWS**

Aspose.Email provides the [EWSClient](https://apireference.aspose.com/email/cpp/class/aspose.email.clients.exchange.web_service.e_w_s_client) class to connect to Microsoft Exchange via EWS. The example below shows how to **read all contacts** from the Contacts folder:



{{< gist "aspose-com-gists" "525dd06c8783ebb18fb75cfc4b31d1ef" "Examples-Cpp-source-Exchange_EWS-GettingContactsUsingEWS-GettingContactsUsingEWS.cpp" >}}

## **Resolve Contacts by Name**

You can resolve contacts using a display name. The following example fetches matching contacts and their details:


{{< gist "aspose-com-gists" "525dd06c8783ebb18fb75cfc4b31d1ef" "Examples-Cpp-source-Exchange_EWS-ResolveContactsUsingContactName-ResolveContactsUsingContactName.cpp" >}}

## **Determine Contact Notes Format**

The [Contact->get_NotesFormat](https://apireference.aspose.com/email/cpp/class/aspose.email.personal_info.contact) property specifies the format of the notes text according to the [TextFormat](https://apireference.aspose.com/email/cpp/namespace/aspose.email.personal_info) enumerator.


## **Fetch Contact using Id**

You can retrieve a specific contact using its unique contact ID as shown in the code sample below.


{{< gist "aspose-com-gists" "525dd06c8783ebb18fb75cfc4b31d1ef" "Examples-Cpp-source-Exchange_EWS-FetchContactUsingId-FetchContactUsingId.cpp" >}}

## **Add Contacts**

Use the [CreateContact()](https://apireference.aspose.com/email/cpp/class/aspose.email.clients.exchange.web_service.i_e_w_s_client) method to add a new contact to Exchange Server. The following example demonstrates how to populate and save a contact:


{{< gist "aspose-com-gists" "525dd06c8783ebb18fb75cfc4b31d1ef" "Examples-Cpp-source-Exchange_EWS-AddContactsToExchangeServerUsingEWS-1.cpp" >}}

## **Update Contacts**

Contact information can be modified on the server using [IEWSClient->UpdateContact](https://apireference.aspose.com/email/cpp/class/aspose.email.clients.exchange.web_service.i_e_w_s_client). The following code sample demonstrates how to retrieve, display, and update Exchange Server contacts:


{{< gist "aspose-com-gists" "525dd06c8783ebb18fb75cfc4b31d1ef" "Examples-Cpp-source-Exchange_EWS-UpdateContactInformationUsingEWS-UpdateContactInformationUsingEWS.cpp" >}}

## **Deleting Contacts**

The [IEWSClient](https://apireference.aspose.com/email/cpp/class/aspose.email.clients.exchange.web_service.i_e_w_s_client) class provides the [DeleteContact](https://apireference.aspose.com/email/cpp/class/aspose.email.clients.exchange.web_service.i_e_w_s_client) to access and delete contacts from the Exchange Server. This method takes the contact ID or [Contact](https://apireference.aspose.com/email/cpp/class/aspose.email.personal_info.contact) as an input parameter.

The following code snippet shows you how to delete contacts from an exchange server using [IEWSClient->DeleteContact](https://apireference.aspose.com/email/cpp/class/aspose.email.clients.exchange.web_service.i_e_w_s_client).



{{< gist "aspose-com-gists" "525dd06c8783ebb18fb75cfc4b31d1ef" "Examples-Cpp-source-Exchange_EWS-DeleteContactsFromExchangeServerUsingEWS-DeleteContactsFromExchangeServerUsingEWS.cpp" >}}
