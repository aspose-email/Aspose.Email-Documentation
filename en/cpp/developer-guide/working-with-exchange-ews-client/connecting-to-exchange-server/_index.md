---
title: Connecting to Microsoft Exchange via EWS in C++
ArticleTitle: Connecting to Microsoft Exchange via EWS
type: docs
weight: 10
url: /cpp/connect-to-exchange-ews-client
description: Learn how to connect to Exchange servers and MS 365 using EWSClient in Aspose.Email for C++ and create an IEWSClient instance.
---

In order to connect to Exchange servers and MS 365 using Exchange Web Service, Aspose.Email provides the [EWSClient](https://apireference.aspose.com/email/cpp/class/aspose.email.clients.exchange.web_service.e_w_s_client) class. The [GetEWSClient](https://apireference.aspose.com/email/cpp/class/aspose.email.clients.exchange.web_service.e_w_s_client#a1cba1af5a0bae889dedf76b9890ecb40) method instantiates and returns an [IEWSClient](https://apireference.aspose.com/email/cpp/class/aspose.email.clients.exchange.web_service.i_e_w_s_client) object that is further used to perform operations related to an Exchange mailbox and other folders. This article shows how to instantiate objects of [IEWSClient](https://apireference.aspose.com/email/cpp/class/aspose.email.clients.exchange.web_service.i_e_w_s_client).

The following code sample demonstrates how to connect to an Exchange Server using Exchange Web Services (EWS) by configuring connection parameters and authenticating with network credentials using Aspose.Email for C++. It shows the process of setting up the Exchange server URI, domain, username, and password, then creating a network credential object and establishing a connection to the Exchange server through the EWS client.



{{< gist "aspose-com-gists" "525dd06c8783ebb18fb75cfc4b31d1ef" "Examples-Cpp-source-Exchange_EWS-ConnectingToExchangeServerUsingEWS-ConnectingToExchangeServerUsingEWS.cpp" >}}
