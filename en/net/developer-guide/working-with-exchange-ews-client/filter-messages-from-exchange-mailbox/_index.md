---
title: Filter and Sort Messages in Exchange Server Mailbox Using EWS
ArticleTitle: Filter and Sort Messages in Exchange Server Mailbox Using EWS
type: docs
weight: 30
url: /net/filter-messages-from-exchange-mailbox/
---


{{% alert color="primary" %}}

Aspose.Email for .NET provides the capability to filter messages from Exchange Mailbox using the EWSClient and ExchangeQueryBuilder. Messages can be filtered via different criteria such as by date, domain, message-id, and by Mail Delivery Notifications. This article shows how to filter messages from Exchange Server using different Criteria.

{{% /alert %}} 

## **Filter and Sort Messages using EWS**

The [IEWSClient](https://reference.aspose.com/email/net/aspose.email.clients.exchange.webservice/iewsclient/) interface provides the [ListMessages()](https://reference.aspose.com/email/net/aspose.email.clients.exchange.webservice/iewsclient/listmessages/#listmessages) method which gets all messages from a mailbox. To get only messages which match some condition, use the overloaded [ListMessages()](https://reference.aspose.com/email/net/aspose.email.clients.exchange.webservice/iewsclient/listmessages/#listmessages) method which takes the [MailQuery](https://reference.aspose.com/email/net/aspose.email.tools.search/mailquery/) class as an argument. The [MailQuery](https://reference.aspose.com/email/net/aspose.email.tools.search/mailquery/) class provides various properties for specifying conditions, for example, date, subject, sender and recipient. In addition, the API also allows applying case-sensitivity filters for retrieving emails from the mailbox.

### **Filter Messages by Criteria**

To get filtered messages from a mailbox:

1. Connect to the Exchange server.
1. Create an instance of [MailQuery](https://reference.aspose.com/email/net/aspose.email.tools.search/mailquery/) and set the desired properties.
1. Call the [IEWSClient.ListMessages()](https://reference.aspose.com/email/net/aspose.email.clients.exchange.webservice/iewsclient/listmessages/#listmessages) method and pass the [MailQuery](https://reference.aspose.com/email/net/aspose.email.tools.search/mailquery/) in the parameters to get the filtered messages only.

The following code snippet shows you how to connect to an IMAP mailbox and get messages that have the string "Newsletter" in the subject and were sent today.

{{< gist "aspose-com-gists" "6e5185a63aec6fd70d83098e82b06a32" "Examples-CSharp-Exchange_EWS-FilterMessagesUsingEWS-FilterMessagesUsingEWS.cs" >}}

#### **By Today's Date**

The following code snippet shows you how to filter all emails on the basis of today's date.

{{< gist "aspose-com-gists" "6e5185a63aec6fd70d83098e82b06a32" "Examples-CSharp-Exchange_EWS-FilterMessagesOnCriteriaUsingEWS-GetEmailsWithTodayDate.cs" >}}

#### **By Date Range**

The following code snippet shows you how to filter all emails on the basis of the date range.

{{< gist "aspose-com-gists" "6e5185a63aec6fd70d83098e82b06a32" "Examples-CSharp-Exchange_EWS-FilterMessagesOnCriteriaUsingEWS-GetEmailsOverDateRange.cs" >}}

#### **By Sender**

The following code snippet shows you how to filter all emails on the basis of a specific sender.

{{< gist "aspose-com-gists" "6e5185a63aec6fd70d83098e82b06a32" "Examples-CSharp-Exchange_EWS-FilterMessagesOnCriteriaUsingEWS-GetSpecificSenderEmails.cs" >}}

#### **By Domain**

The following code snippet shows you how to filter all emails on the basis of a specific domain.

{{< gist "aspose-com-gists" "6e5185a63aec6fd70d83098e82b06a32" "Examples-CSharp-Exchange_EWS-FilterMessagesOnCriteriaUsingEWS-GetSpecificDomainEmails.cs" >}}

#### **By Recipient**

The following code snippet shows you how to filter all emails on the basis of a specific recipient.

{{< gist "aspose-com-gists" "6e5185a63aec6fd70d83098e82b06a32" "Examples-CSharp-Exchange_EWS-FilterMessagesOnCriteriaUsingEWS-GetSpecificRecipientEmails.cs" >}}

#### **By MessageID**

The following code snippet shows you how to filter all emails on the basis of MessageID.

{{< gist "aspose-com-gists" "6e5185a63aec6fd70d83098e82b06a32" "Examples-CSharp-Exchange_EWS-FilterMessagesOnCriteriaUsingEWS-GetSpecificMessageIdEmail.cs" >}}

#### **By Mail Delivery Notifications**

The following code snippet shows you how to filter all emails on the basis of all mail delivery notifications.

{{< gist "aspose-com-gists" "6e5185a63aec6fd70d83098e82b06a32" "Examples-CSharp-Exchange_EWS-FilterMessagesOnCriteriaUsingEWS-GetMailDeliveryNotifications.cs" >}}

#### **By Message Size**

{{< gist "aspose-com-gists" "6e5185a63aec6fd70d83098e82b06a32" "Examples-CSharp-Exchange_EWS-FilterMessagesOnCriteriaUsingEWS-FilterMessagesByMessageSize.cs" >}}


### **Building Complex Queries**

If different [MailQueryBuilder](https://reference.aspose.com/email/net/aspose.email.tools.search/mailquerybuilder/) properties are set in a separate statement, all the conditions are matched. For example, to get a message in a particular date range and from a specific host, write three statements:

#### **Combining Queries with AND**

The following code snippet shows you how to Combine Queries with AND.

{{< gist "aspose-com-gists" "6e5185a63aec6fd70d83098e82b06a32" "Examples-CSharp-Exchange_EWS-FilterWithComplexQueriesUsingEWS-CombineQueriesWithAND.cs" >}}

#### **Combining Queries with OR**

[MailQueryBuilder](https://reference.aspose.com/email/net/aspose.email.tools.search/mailquerybuilder/) provides the [Or()](https://reference.aspose.com/email/net/aspose.email.tools.search/mailquerybuilder/or/#or) method which takes two [MailQuery](https://reference.aspose.com/email/net/aspose.email.tools.search/mailquery/) instances as parameters. It gets messages that match any of the two conditions specified. The example below filters messages that either have the word “test” in the subject or “noreply@host.com” as the sender. The following code snippet shows you how to combine queries with OR.

{{< gist "aspose-com-gists" "6e5185a63aec6fd70d83098e82b06a32" "Examples-CSharp-Exchange_EWS-FilterWithComplexQueriesUsingEWS-CombiningQueriesWithOR.cs" >}}

#### **Case-Sensitive Email Filtering**

Emails can be filtered based on case-sensitivity by specifying the IgnoreCase flag in the filter criteria as shown in the following code snippet.

{{< gist "aspose-com-gists" "6e5185a63aec6fd70d83098e82b06a32" "Examples-CSharp-Exchange_EWS-CaseSensitiveEmailsFilteringUsingEWS-CaseSensitiveEmailsFiltering.cs" >}}

### **Filter Messages with Paging Support**

{{< gist "aspose-com-gists" "6e5185a63aec6fd70d83098e82b06a32" "Examples-CSharp-Exchange_EWS-FilterMessagesOnCriteriaUsingEWS-FilterMessagesWithPagingSupport.cs" >}}

### **Sort Filtered messages in Ascending/Descending Order**

Email filtering can be supported with sorting of messages in ascending/descending order. In this case, [OrderBy](https://reference.aspose.com/email/net/aspose.email.tools.search/comparisonfield/orderby/) method is used to specify the order in which the results of an email search are sorted using the MailQueryBuilder class. This method allows you to define sorting criteria for a search query, specifying whether the results should be sorted in ascending or descending order based on a particular property.

The method accepts the ascending parameter, which specifies the sort order for the specified property. If the ascending parameter is true, it means that the search results should be sorted in ascending order. Conversely, if the ascending parameter is false, it means that the search results should be sorted in descending order.

```cs
MailQueryBuilder builder = new MailQueryBuilder();
builder.Subject.Contains("Report");
builder.InternalDate.Since(new DateTime(2020, 1, 1));
builder.Subject.OrderBy(true); // sort the subject ascending
builder.InternalDate.OrderBy(false); // sort the date descending

MailQuery query = builder.GetQuery();

// Get list of messages
ExchangeMessageInfoCollection messages = client.ListMessages(client.MailboxInfo.InboxUri, query, false);
```

In the above code snippet, the OrderBy method is applied twice, once for the subject and once for the date of the emails. As a result of executing the ListMessages method with the passed request, we will get a list of messages with the subject containing the word "Report" which were received on the specified date or later. At the same time, the results will be sorted by subject in ascending order. This means that the messages will be sorted alphabetically from A to Z, depending on their subject. Also, the results will be sorted by date in descending order. This means that posts will be ordered from newest to oldest.

### **Filter Messages Using AQS**

With Aspose.Email for .NET, users can leverage the powerful capabilities of Advanced Query Syntax (AQS) to filter messages directly from an Exchange mailbox. AQS provides a robust and intuitive means of constructing queries that can precisely target emails based on specific criteria such as date, sender, and subject. For more detailed insights on its itegration into your email filtering processes and comprehensive code samples on implementing message filtering using AQS with Aspose.Email for .NET, please refer to the [Filter Messages With AQS From Exchange Mailbox](https://docs.aspose.com/email/net/filter-messages-with-aqs-from-exchange-mailbox/) article.
