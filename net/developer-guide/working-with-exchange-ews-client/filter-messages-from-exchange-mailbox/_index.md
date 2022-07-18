---
title: Filter Messages From Exchange Mailbox
type: docs
weight: 30
url: /net/filter-messages-from-exchange-mailbox/
---


{{% alert color="primary" %}} 

Aspose.Email for .NET provides the capability to filter messages from Exchange Mailbox using the EWSClient and ExchangeQueryBuilder. Messages can be filtered via different criteria such as by date, domain, message-id, and by Mail Delivery Notifications. This article shows how to filter messages from Exchange Server using different Criteria.

{{% /alert %}} 
## **Filtering Messages using EWS**
The [IEWSClient](https://reference.aspose.com/email/net/aspose.email.clients.exchange.webservice/iewsclient) class provides the [ListMessages()](https://reference.aspose.com/email/net/aspose.email.clients.exchange.webservice/iewsclient/methods/listmessages) method which gets all messages from a mailbox. To get only messages which match some condition, use the overloaded [ListMessages()](https://reference.aspose.com/email/net/aspose.email.clients.exchange.webservice.iewsclient/listmessages/methods/5) method which takes the [MailQuery](https://reference.aspose.com/email/net/aspose.email.tools.search/mailquery) class as an argument. The [MailQuery](https://reference.aspose.com/email/net/aspose.email.tools.search/mailquery) class provides various properties for specifying conditions, for example, date, subject, sender and recipient. In addition, the API also allows applying case-sensitivity filters for retrieving emails from the mailbox.
### **Filtering Messages**
To get filtered messages from a mailbox:

1. Connect to the Exchange server.
1. Create an instance of [MailQuery](https://reference.aspose.com/email/net/aspose.email.tools.search/mailquery) and set the desired properties.
1. Call the [IEWSClient.ListMessages()](https://reference.aspose.com/email/net/aspose.email.clients.exchange.webservice.iewsclient/listmessages/methods/5) method and pass the [MailQuery](https://reference.aspose.com/email/net/aspose.email.tools.search/mailquery) in the parameters to get the filtered messages only.

The following code snippet shows you how to connect to an IMAP mailbox and get messages that have the string "Newsletter" in the subject and were sent today.

{{< gist "aspose-com-gists" "6e5185a63aec6fd70d83098e82b06a32" "Examples-CSharp-Exchange_EWS-FilterMessagesUsingEWS-FilterMessagesUsingEWS.cs" >}}
### **Filter Messages on Criteria**
The code samples above filters messages based on the email subject and date. We can filter on other properties too. Below are some examples of setting the conditions using [MailQuery](https://reference.aspose.com/email/net/aspose.email.tools.search/mailquery).
#### **Filter Criteria Today's Date**
The following code snippet shows you how to filter all emails on the basis of today's date.

{{< gist "aspose-com-gists" "6e5185a63aec6fd70d83098e82b06a32" "Examples-CSharp-Exchange_EWS-FilterMessagesOnCriteriaUsingEWS-GetEmailsWithTodayDate.cs" >}}
#### **Filter Criteria Date Range**
The following code snippet shows you how to filter all emails on the basis of the date range.



{{< gist "aspose-com-gists" "6e5185a63aec6fd70d83098e82b06a32" "Examples-CSharp-Exchange_EWS-FilterMessagesOnCriteriaUsingEWS-GetEmailsOverDateRange.cs" >}}
#### **Filter Criteria Specific Sender**
The following code snippet shows you how to filter all emails on the basis of a specific sender.

{{< gist "aspose-com-gists" "6e5185a63aec6fd70d83098e82b06a32" "Examples-CSharp-Exchange_EWS-FilterMessagesOnCriteriaUsingEWS-GetSpecificSenderEmails.cs" >}}
#### **Filter Criteria Specific Domain**
The following code snippet shows you how to filter all emails on the basis of a specific domain.

{{< gist "aspose-com-gists" "6e5185a63aec6fd70d83098e82b06a32" "Examples-CSharp-Exchange_EWS-FilterMessagesOnCriteriaUsingEWS-GetSpecificDomainEmails.cs" >}}
#### **Filter Criteria Specific Recipient**
The following code snippet shows you how to filter all emails on the basis of a specific recipient.

{{< gist "aspose-com-gists" "6e5185a63aec6fd70d83098e82b06a32" "Examples-CSharp-Exchange_EWS-FilterMessagesOnCriteriaUsingEWS-GetSpecificRecipientEmails.cs" >}}
#### **Filter Criteria By MessageID**
The following code snippet shows you how to filter all emails on the basis of MessageID.

{{< gist "aspose-com-gists" "6e5185a63aec6fd70d83098e82b06a32" "Examples-CSharp-Exchange_EWS-FilterMessagesOnCriteriaUsingEWS-GetSpecificMessageIdEmail.cs" >}}
#### **Filter Criteria All Mail Delivery Notifications**
The following code snippet shows you how to filter all emails on the basis of all mail delivery notifications.

{{< gist "aspose-com-gists" "6e5185a63aec6fd70d83098e82b06a32" "Examples-CSharp-Exchange_EWS-FilterMessagesOnCriteriaUsingEWS-GetMailDeliveryNotifications.cs" >}}
#### **Filter by Message Size**
{{< gist "aspose-com-gists" "6e5185a63aec6fd70d83098e82b06a32" "Examples-CSharp-Exchange_EWS-FilterMessagesOnCriteriaUsingEWS-FilterMessagesByMessageSize.cs" >}}
### **Building Complex Queries**
If different [MailQueryBuilder](https://reference.aspose.com/email/net/aspose.email.tools.search/mailquerybuilder) properties are set in a separate statement, all the conditions are matched. For example, to get a message in a particular date range and from a specific host, write three statements:
#### **Combining Queries with AND**
The following code snippet shows you how to Combine Queries with AND.

{{< gist "aspose-com-gists" "6e5185a63aec6fd70d83098e82b06a32" "Examples-CSharp-Exchange_EWS-FilterWithComplexQueriesUsingEWS-CombineQueriesWithAND.cs" >}}
#### **Combining Queries with OR**
[MailQueryBuilder](https://reference.aspose.com/email/net/aspose.email.tools.search/mailquerybuilder) provides the [Or()](https://reference.aspose.com/email/net/aspose.email.tools.search/mailquerybuilder/methods/or) method which takes two [MailQuery](https://reference.aspose.com/email/net/aspose.email.tools.search/mailquery) instances as parameters. It gets messages that match any of the two conditions specified. The example below filters messages that either have the word “test” in the subject or “noreply@host.com” as the sender. The following code snippet shows you how to combine queries with OR.

{{< gist "aspose-com-gists" "6e5185a63aec6fd70d83098e82b06a32" "Examples-CSharp-Exchange_EWS-FilterWithComplexQueriesUsingEWS-CombiningQueriesWithOR.cs" >}}
### **Case-Sensitive Email Filtering**
Emails can be filtered based on case-sensitivity by specifying the IgnoreCase flag in the filter criteria as shown in the following code snippet.

{{< gist "aspose-com-gists" "6e5185a63aec6fd70d83098e82b06a32" "Examples-CSharp-Exchange_EWS-CaseSensitiveEmailsFilteringUsingEWS-CaseSensitiveEmailsFiltering.cs" >}}
## **Filtering Messages with Paging Support**
{{< gist "aspose-com-gists" "6e5185a63aec6fd70d83098e82b06a32" "Examples-CSharp-Exchange_EWS-FilterMessagesOnCriteriaUsingEWS-FilterMessagesWithPagingSupport.cs" >}}
