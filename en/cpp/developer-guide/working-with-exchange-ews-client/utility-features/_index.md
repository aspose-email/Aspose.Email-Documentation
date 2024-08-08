---
title: Utility Features
type: docs
weight: 120
url: /cpp/utility-features/
---

## **Sending a Message with Voting Option**
Microsoft Outlook allows users to create a poll when composing a new message. This is done by including voting options such as Yes, No, Maybe, etc. The *FollowUpOptions* class offered by Aspose.Email provides the *VotingButtons* property that can be used to set or get the value of the voting options. This article provides a detailed example of creating a *MapiMessage* with voting options for creating a poll and then sending the message using Exchange Web Service (EWS) client.
### **Creating and Sending a Message with Voting Options**
The following code snippet shows you how to create a new message and then send it with voting options.



{{< gist "aspose-com-gists" "525dd06c8783ebb18fb75cfc4b31d1ef" "Examples-Cpp-source-Exchange_EWS-CreateAndSendingMessageWithVotingOptions-CreateAndSendingMessageWithVotingOptions.cpp" >}}


The following code snippet shows the definition of the *CreateTestMessage* method used in the above example.



{{< gist "aspose-com-gists" "525dd06c8783ebb18fb75cfc4b31d1ef" "Examples-Cpp-source-Exchange_EWS-CreateAndSendingMessageWithVotingOptions-CreateTestMessage.cpp" >}}
## **Ignore or Bypass Invalid or Expired SSL Certificate**
Aspose.Email can handle SSL certificates on Exchange Server by using the [EWSClient](https://apireference.aspose.com/email/cpp/class/aspose.email.clients.exchange.web_service.e_w_s_client) class. If the SSL certificate has expired or become invalid, Aspose.Email throws an exception due to invalid SSL certificate. Avoid such SSL certificate errors by ignoring them using the method used in the code below. Register the callback handler in your main() or init() method and add the method below as the member of the class.



{{< gist "aspose-com-gists" "525dd06c8783ebb18fb75cfc4b31d1ef" "Examples-Cpp-source-Exchange_EWS-IgnoringInvalidSSLCertificates-IgnoringInvalidSSLCertificates.cpp" >}}
## **Creating RE and FW messages from MSG files**
[IEWSClient](https://apireference.aspose.com/email/cpp/class/aspose.email.clients.exchange.web_service.i_e_w_s_client) lets developers create RE (Reply/Reply All) and FW (Forward) messages from a source message. The source message is identified by selecting a particular [ExchangeMessageInfo](https://apireference.aspose.com/email/cpp/class/aspose.email.clients.exchange.exchange_message_info) from [ExchangeMessageInfoCollection](https://apireference.aspose.com/email/cpp/class/aspose.email.clients.exchange.exchange_message_info_collection) obtained by [ListMessages()](https://apireference.aspose.com/email/cpp/class/aspose.email.clients.exchange.web_service.i_e_w_s_client#aad8420247acd17cb1d73303ed1982d1e). The other argument is the actual [MailMessage](https://apireference.aspose.com/email/cpp/class/aspose.email.mail_message) to be sent as RE or FW message. The following code snippet shows you how to send a message and then reply to that message and Forward that message. To perform this task:

1. Initialize the [IEWSClient](https://apireference.aspose.com/email/cpp/class/aspose.email.clients.exchange.web_service.i_e_w_s_client) object by providing valid credentials.
1. Send a few sample messages.
1. Call the [Reply()](https://apireference.aspose.com/email/cpp/class/aspose.email.clients.exchange.web_service.i_e_w_s_client#a2d925824adc83ffdebeb7d135bd99099), [ReplyAll()](https://apireference.aspose.com/email/cpp/class/aspose.email.clients.exchange.web_service.i_e_w_s_client#ac08b12a3db4f1e20eaaa0d5f99c27c41) and [Forward()](https://apireference.aspose.com/email/cpp/class/aspose.email.clients.exchange.web_service.i_e_w_s_client#a1040eb913667b6702b0253e48a48ec27) methods to send messages.



{{< gist "aspose-com-gists" "525dd06c8783ebb18fb75cfc4b31d1ef" "Examples-Cpp-source-Exchange_EWS-CreateREAndFWMessages-CreateREAndFWMessages.cpp" >}}
## **Adding Headers in EWS Requests**
Aspose.Email API allows adding headers to Exchange requests. This can be used to add headers to the EWS requests for different headers that can be used for different purposes. One such example could be adding the X-AnchorMailbox header that is used to manage the throttling issues on the Exchange server. The [AddHeader](https://apireference.aspose.com/email/cpp/class/aspose.email.clients.exchange.web_service.i_e_w_s_client#a93b0dd8364564686a15e720d8e5a4e9f) method of the [IEWSClient](https://apireference.aspose.com/email/cpp/class/aspose.email.clients.exchange.web_service.i_e_w_s_client) is used to add headers to the EWS requests as shown in the following code snippet.



{{< gist "aspose-com-gists" "525dd06c8783ebb18fb75cfc4b31d1ef" "Examples-Cpp-source-Exchange_EWS-AddingHeadersToEWSRequests-AddingHeadersToEWSRequests.cpp" >}}
## **Working with Unified Messaging**
Aspose.Email can retrieve unified messaging information from Exchange Server 2010. Unified messaging such as getting configuration information, initiating an outbound call, retrieving phone call information by call ID and disconnecting a phone call by ID is supported at present. The following code sample shows how to retrieve unified messaging configuration information from Microsoft Exchange Server 2010.



{{< gist "aspose-com-gists" "525dd06c8783ebb18fb75cfc4b31d1ef" "Examples-Cpp-source-Exchange_EWS-GettingUnifiedMessagingConfigurationInformation-GettingUnifiedMessagingConfigurationInformation.cpp" >}}
## **Getting Mail Tips**
Microsoft Exchange Server added several new features with Exchange Server 2010 and 2013. One of them lets users get mail tips when composing an email message. These tips are very useful as they provide information before the email is sent. For example, if an email address is wrong in the recipient’s list, a tip is displayed to let you know that the email address is invalid. Mail tips also let you see out of office replies before sending an email: Exchange Server (2010 & 2013) sends the mail tip when the email is being composed if one or more of the recipients have set out of office replies. Microsoft Exchange Server 2010 Service Pack 1 is required for all the features demonstrated in this article. The following code snippet shows you how to uses the [EWSClient](https://apireference.aspose.com/email/cpp/class/aspose.email.clients.exchange.web_service.e_w_s_client) class which uses Exchange Web Services, available in Microsoft Exchange Server 2007 and later versions.



{{< gist "aspose-com-gists" "525dd06c8783ebb18fb75cfc4b31d1ef" "Examples-Cpp-source-Exchange_EWS-GetMailTips-GetMailTips.cpp" >}}
