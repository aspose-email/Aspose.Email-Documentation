---
title: Utility Features
type: docs
weight: 120
url: /net/utility-features/
---


## **Sending a Message with Voting Option**
Microsoft Outlook allows users to create a poll when composed a new message. This is done by including voting options such as Yes, No, Maybe, etc. The FollowUpOptions class offered by Aspose.Email, provides the VotingButtons property that can be used to set or get the value of the voting options. This article provides a detailed example of creating a MapiMessage with voting options for creating a poll and then sending the message using Exchange Web Service (EWS) client.
### **Creating and Sending a Message with Voting Options**
The following code snippet shows you how to create a new message and then send it with voting options.



{{< gist "aspose-email" "9e8fbeb51a8cbc4129dc71ca8cd55f0b" "Examples-CSharp-Exchange_EWS-CreateAndSendingMessageWithVotingOptions-CreateAndSendingMessageWithVotingOptions.cs" >}}
### **Sample Methods Used in Examples**
The following code snippet shows you how to use methods used in above example.



{{< gist "aspose-email" "9e8fbeb51a8cbc4129dc71ca8cd55f0b" "Examples-CSharp-Exchange_EWS-CreateAndSendingMessageWithVotingOptions-CreateTestMessage.cs" >}}
## **Ignore or Bypass Invalid or Expired SSL Certificate**
Aspose.Email can handle SSL certificates on Exchange Server using both the [ExchangeClient](https://reference.aspose.com/email/net/aspose.email.clients.exchange.dav/exchangeclient) and [EWSClient](https://reference.aspose.com/email/net/aspose.email.clients.exchange.webservice/ewsclient) classes. If the SSL certificate has expired or become invalid, Aspose.Email throws an exception due to invalid SSL certificate. Avoid such SSL certificate errors by ignoring them using the method used in the code below. Register the callback handler in your main() or init() method and add the method below as the member of the class.



{{< gist "aspose-email" "9e8fbeb51a8cbc4129dc71ca8cd55f0b" "Examples-CSharp-Exchange_EWS-IgnoringInvalidSSLCertificates-IgnoringInvalidSSLCertificates.cs" >}}
## **Creating RE and FW messages from MSG files**
IEWSClient lets developers create RE (Reply/Reply All) and FW (Forward) messages from a source message. The source message is identified by selecting a particular ExchangeMessageInfo from ExchangeMessageInfoCollection obtained by IEWSClient.ListMessages(). The other argument is the actual MailMessage to be sent as RE or FW message. The following code snippet shows you how to create a sample account is used to send a message and then the Reply and Forward message features are demonstrated against that sample message. To perform this task:

1. Initialize the IEWSClient object by providing valid credentials.
1. Send a few sample messages.
1. Call the IEWSClient.Reply(), IEWSClient.ReplyAll() and IEWSClient.Forward() functions to send messages.



{{< gist "aspose-email" "9e8fbeb51a8cbc4129dc71ca8cd55f0b" "Examples-CSharp-Exchange_EWS-CreateREAndFWMessages-CreateREAndFWMessages.cs" >}}
## **Support for Email Tracking**
Aspose.Email API provides support of email tracking using Message Disposition Notification (MDN). This is achieved by requesting the read receipts and creating the required information. The MailMessage class’s ReadReceiptTo property gets or sets the set read receipt address. The CreateReadReceipt and ReadReceiptRequested methods are used for creating and retrieving the information whether read receipts are requested. The following code snippet shows you how to email track using Aspose.Email API.



{{< gist "aspose-email" "9e8fbeb51a8cbc4129dc71ca8cd55f0b" "Examples-CSharp-Exchange-EmailTracking-EmailTracking.cs" >}}
## **Support for Logging in Exchange Clients**
Aspose.Email API provides the capability to provide logging facility of Exchange Web Service client. This can be achieved by configuring the App.config file.
### **Logging for EWS Client**


{{< gist "aspose-email" "9e8fbeb51a8cbc4129dc71ca8cd55f0b" "LoggingForEWSClient.xml" >}}
## **Adding Headers in EWS Requests**
Aspose.Email API allows adding headers to Exchange requests. This can be used to add headers to the EWS requests for different headers that can be used for different purposes. Once such example could be adding the X-AnchorMailbox header that is used to manage the throttling issues on Exchange server. The AddHeader method of the IEWSClient is used to add headers to the EWS requests as shown in the following code snippet.



{{< gist "aspose-email" "9e8fbeb51a8cbc4129dc71ca8cd55f0b" "Examples-CSharp-Exchange_EWS-AddingHeadersToEWSRequests-AddingHeadersToEWSRequests.cs" >}}
## **Working with Unified Messaging**
Aspose.Email can retrieve unified messaging information from Exchange Server 2010. Unified messaging such as getting configuration information, initiating an outbound call, retrieving phone call information by call ID and disconnecting a phone call by ID is supported at present. The following code sample shows how to retrieve unified messaging configuration information from Microsoft Exchange Server 2010.



{{< gist "aspose-email" "9e8fbeb51a8cbc4129dc71ca8cd55f0b" "Examples-CSharp-Exchange_EWS-GettingUnifiedMessagingConfigurationInformation-GettingUnifiedMessagingConfigurationInformation.cs" >}}
## **Getting Mail Tips**
Microsoft Exchange Server added several new features with Exchange Server 2010 and 2013. One of them lets users get mail tips when composing an email message. These tips are very useful as they provide information before the email is sent. For example, if an email address is wrong in the recipient’s list, a tip is displayed to let the you know that the email address is invalid. Mail tips also lets you see out of office replies before sending an email: Exchange Server (2010 & 2013) sends the mail tip when the email is being composed if one or more of the recipients have set out of office replies. Microsoft Exchange Server 2010 Service Pack 1 is required for all the features demonstrated in this article. The following code snippet shows you how to uses the [EWSClient](https://reference.aspose.com/email/net/aspose.email.clients.exchange.webservice/ewsclient) class which uses Exchange Web Services, available in Microsoft Exchange Server 2007 and later versions.



{{< gist "aspose-email" "9e8fbeb51a8cbc4129dc71ca8cd55f0b" "Examples-CSharp-Exchange_EWS-GetMailTips-GetMailTips.cs" >}}
## **Exchange Impersonation**
Exchange impersonation allows someone to impersonate another account and perform tasks and operations using the impersonated account's permissions instead of their own. Where delegation lets users act on behalf of other users, Impersonation allows them to act as other users. Aspose.Email supports Exchange Impersonation. The [EWSClient](https://reference.aspose.com/email/net/aspose.email.clients.exchange.webservice/ewsclient) class provides the ImpersonateUser and ResetImpersonation methods to facilitate this feature.

To perform this task:

1. Initialize the ExchangeWebServiceClient for user 1.
1. Initialize the ExchangeWebServiceClient for user 2.
1. Append test messages to the accounts.
1. Enable Impersonation.
1. Reset Impersonation.

The following code snippet shows you how to use the [EWSClient](https://reference.aspose.com/email/net/aspose.email.clients.exchange.webservice/ewsclient) class to implement the Impersonation feature.



{{< gist "aspose-email" "9e8fbeb51a8cbc4129dc71ca8cd55f0b" "Examples-CSharp-Exchange_EWS-ExchangeImpersonationUsingEWS-ExchangeImpersonationUsingEWS.cs" >}}
## **Auto Discover Feature using EWS**
Aspose.Email API lets you discover about the Exchange Server settings using the EWS Client. 

{{< gist "aspose-email" "9e8fbeb51a8cbc4129dc71ca8cd55f0b" "Examples-CSharp-Exchange_EWS-AutoDiscoverUsingEWS-AutoDiscoverUsingEWS.cs" >}}
## **Abort PST Restore to Exchange Server Operation**
Aspose.Email API lets you restore a PST file to Exchange Server. However, if the operation is taking long due to large size PST file, it may be required to specify criterion for aborting the operation. This can be achieved using the API as shown in the following sample code.

**Note:** The example needs the following class to be added as well.

``` cs

 public class CustomAbortRestoreException : Exception { }

```

{{< gist "aspose-email" "9e8fbeb51a8cbc4129dc71ca8cd55f0b" "Examples-CSharp-Exchange_EWS-AbortPSTToExchangeServerOperation-AbortPSTToExchangeServerOperation.cs" >}}
