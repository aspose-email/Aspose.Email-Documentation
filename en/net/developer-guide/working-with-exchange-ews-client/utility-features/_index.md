---
title: Advanced Email Management for .NET Applications
ArticleTitle: Utility Features in Aspose.Email for .NET
type: docs
weight: 170
url: /net/utility-features/
---


## **Working with Unified Messaging**

Aspose.Email can retrieve unified messaging information from Exchange Server 2010. Unified messaging such as getting configuration information, initiating an outbound call, retrieving phone call information by call ID and disconnecting a phone call by ID is supported at present. The following code sample shows how to retrieve unified messaging configuration information from Microsoft Exchange Server 2010.

{{< gist "aspose-email" "9e8fbeb51a8cbc4129dc71ca8cd55f0b" "Examples-CSharp-Exchange_EWS-GettingUnifiedMessagingConfigurationInformation-GettingUnifiedMessagingConfigurationInformation.cs" >}}

## **Getting Mail Tips**

Microsoft Exchange Server added several new features with Exchange Server 2010 and 2013. One of them lets users get mail tips when composing an email message. These tips are very useful as they provide information before the email is sent. For example, if an email address is wrong in the recipient list, a tip is displayed to let you know that the email address is invalid. Mail tips also let you see out of office replies before sending an email: Exchange Server (2010 & 2013) sends the mail tip when the email is being composed if one or more of the recipients have set out of office replies. Microsoft Exchange Server 2010 Service Pack 1 is required for all the features demonstrated in this article. The following code snippet shows you how to use the [EWSClient](https://reference.aspose.com/email/net/aspose.email.clients.exchange.webservice/ewsclient/) class which uses Exchange Web Services, available in Microsoft Exchange Server 2007 and later versions.

{{< gist "aspose-email" "9e8fbeb51a8cbc4129dc71ca8cd55f0b" "Examples-CSharp-Exchange_EWS-GetMailTips-GetMailTips.cs" >}}

## **Exchange Impersonation**

Exchange impersonation allows someone to impersonate another account and perform tasks and operations using the impersonated account permissions instead of their own. Where delegation lets users act on behalf of other users, Impersonation allows them to act as other users. Aspose.Email supports Exchange Impersonation. The [EWSClient](https://reference.aspose.com/email/net/aspose.email.clients.exchange.webservice/ewsclient/) class provides the [ImpersonateUser](https://reference.aspose.com/email/net/aspose.email.clients.exchange.webservice/iewsclient/impersonateuser/) and [ResetImpersonation](https://reference.aspose.com/email/net/aspose.email.clients.exchange.webservice/iewsclient/resetimpersonation/) methods to facilitate this feature.

To perform this task:

1. Initialize the ExchangeWebServiceClient for user 1.
1. Initialize the ExchangeWebServiceClient for user 2.
1. Append test messages to the accounts.
1. Enable Impersonation.
1. Reset Impersonation.

The following code snippet shows you how to use the [EWSClient](https://reference.aspose.com/email/net/aspose.email.clients.exchange.webservice/ewsclient/) class to implement the Impersonation feature.

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
