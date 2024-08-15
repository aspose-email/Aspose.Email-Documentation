---
title: Filter Messages from Server using IMAP Client
type: docs
weight: 40
url: /net/filter-messages-from-server-using-imap-client/
---


The [ImapClient](https://reference.aspose.com/email/net/aspose.email.clients.imap/imapclient/) class provides the [ListMessages()](https://reference.aspose.com/email/net/aspose.email.clients.imap/imapclient/listmessages/#listmessages) method which gets all the messages from a mailbox. To get only messages which match some condition, use the overloaded [ListMessages()](https://reference.aspose.com/email/net/aspose.email.clients.imap/imapclient/listmessages/#listmessages) method which takes [MailQuery](https://reference.aspose.com/email/net/aspose.email.tools.search/mailquery/) as an argument. The [MailQuery](https://reference.aspose.com/email/net/aspose.email.tools.search/mailquery/) class provides various properties for specifying the conditions, for example, date, subject, sender, recipient and so on. The first example illustrates how to filter messages based on date and subject. We also show how to filter on other criteria and how to build more complex queries. The API also provides the capability to apply case-sensitive searching criteria to match exact filtering criteria. The API also allows specifying the search string encoding for filtering messages from the mailbox.

## **Filtering Messages from Mailbox**

1. [Connect and log in to an IMAP server](https://docs.aspose.com/email/net/connecting-to-imap-server/#connecting-with-imap-server)
2. Create an instance of the [MailQuery](https://reference.aspose.com/email/net/aspose.email.tools.search/mailquery/) and set the properties
3. Call the [`ImapClient.ListMessages(MailQuery query)`](https://reference.aspose.com/email/net/aspose.email.clients.imap/imapclient/listmessages/#listmessages_14) method and pass the [`MailQuery`](https://reference.aspose.com/email/net/aspose.email.tools.search/mailquery/) with the parameters to get filtered messages only.

The following code snippet shows you how to connect to an IMAP mailbox and get messages that arrived today and have the word "newsletter" in the subject.

{{< gist "aspose-com-gists" "6e5185a63aec6fd70d83098e82b06a32" "Examples-CSharp-IMAP-FilteringMessagesFromIMAPMailbox-FilteringMessagesFromIMAPMailbox.cs" >}}

## **Get Messages that Meet Specific Criteria**

[The code samples above](#filtering-messages-from-mailbox) filters messages based on the email subject and date. We can use other properties to set other supported conditions as well. Below are some examples of setting the conditions using [MailQuery](https://reference.aspose.com/email/net/aspose.email.tools.search/mailquery/). The code snippets that follow show how to filter emails on:

1. Today's date.
1. A date range.
1. From a specific sender.
1. From a specific domain.
1. From a specific recipient.

### **Today's Date**

The following code snippet shows you how to filter emails on Today's Date.

{{< gist "aspose-com-gists" "6e5185a63aec6fd70d83098e82b06a32" "Examples-CSharp-IMAP-GetMessagesWithSpecificCriteria-GetEmailsWithTodayDate.cs" >}}

### **Date Range**

The following code snippet shows you how to filter emails on the date range.

{{< gist "aspose-com-gists" "6e5185a63aec6fd70d83098e82b06a32" "Examples-CSharp-IMAP-GetMessagesWithSpecificCriteria-GetEmailsOverDateRange.cs" >}}

### **Specific Sender**

The following code snippet shows you how to filter emails on a specific sender.

{{< gist "aspose-com-gists" "6e5185a63aec6fd70d83098e82b06a32" "Examples-CSharp-IMAP-GetMessagesWithSpecificCriteria-GetSpecificSenderEmails.cs" >}}

### **Specific Domain**

The following code snippet shows you how to filter emails on a specific domain.

{{< gist "aspose-com-gists" "6e5185a63aec6fd70d83098e82b06a32" "Examples-CSharp-IMAP-GetMessagesWithSpecificCriteria-GetSpecificDomainEmails.cs" >}}

### **Specific Recipient**

The following code snippet shows you how to filter emails on a specific recipient.

{{< gist "aspose-com-gists" "6e5185a63aec6fd70d83098e82b06a32" "Examples-CSharp-IMAP-GetMessagesWithSpecificCriteria-GetSpecificRecipientEmails.cs" >}}

## **Building Complex Queries**

If different [MailQueryBuilder](https://reference.aspose.com/email/net/aspose.email.tools.search/mailquerybuilder/) properties are set in separate statements, then all the conditions would be matched. For example, if we want to get messages between a date range and from a specific host, we need to write three statements.

### **Combining Queries with AND**

The following code snippet shows you how to combine queries with AND.

{{< gist "aspose-com-gists" "6e5185a63aec6fd70d83098e82b06a32" "Examples-CSharp-IMAP-BuildingComplexQueries-CombineQueriesWithAND.cs" >}}

### **Combining Queries with OR**

[MailQueryBuilder](https://reference.aspose.com/email/net/aspose.email.tools.search/mailquerybuilder/) provides the [Or()](https://reference.aspose.com/email/net/aspose.email.tools.search/mailquerybuilder/or/#or) method which takes two [MailQuery](https://reference.aspose.com/email/net/aspose.email.tools.search/mailquery/) instances as parameters. It gets the messages that match any of the two conditions specified. The following code snippet shows how to filter messages that either have “test” in the subject or “noreply@host.com” as the sender. The following code snippet shows you how to combine queries with OR.

{{< gist "aspose-com-gists" "6e5185a63aec6fd70d83098e82b06a32" "Examples-CSharp-IMAP-BuildingComplexQueries-CombiningQueriesWithOR.cs" >}}

## **Filtration on InternalDate**

Messages can be extracted from the server based upon the InternalDate however sometimes the server does not return all messages as visible in the inbox. Its reason can be the server timezone because it may not be UTC for all the servers like [Gmail](https://www.google.com.ua/search?client=opera&q=timezone+gmail&sourceid=opera&ie=utf-8&oe=utf-8&channel=suggest#channel=suggest&q=gmail+server+timezone++). Aspose sends commands like 008 SEARCH ON 4-May-2014 as per the [IMAP protocol](https://www.rfc-editor.org/rfc/rfc1730) however result can differ due to server timezone settings. A new member is added in [ImapMessageInfo](https://reference.aspose.com/email/net/aspose.email.clients.imap/imapmessageinfo/) as [InternalDate](https://reference.aspose.com/email/net/aspose.email.clients.imap/imapmessageinfo/internaldate/) which further helps in filtering the messages. The following code snippet shows the use of [InternalDate](https://reference.aspose.com/email/net/aspose.email.clients.imap/imapmessageinfo/internaldate/) to filter messages.

{{< gist "aspose-com-gists" "6e5185a63aec6fd70d83098e82b06a32" "Examples-CSharp-IMAP-InternalDateFilter-InternalDateFilter.cs" >}}

### **Case-Sensitive Emails Filtering**

The following code snippet shows you how to use case-sensitive emails filtering.

{{< gist "aspose-com-gists" "6e5185a63aec6fd70d83098e82b06a32" "Examples-CSharp-IMAP-CaseSensitiveEmailsFiltering-CaseSensitiveEmailsFiltering.cs" >}}

### **Specify Encoding for Query Builder**

The API's [ImapQueryBuilder](https://reference.aspose.com/email/net/aspose.email.clients.imap/imapquerybuilder/) constructor can be used to specify the Encoding for the search string. This can also be set using the [DefaultEncoding](https://reference.aspose.com/email/net/aspose.email.tools.search/mailquerybuilder/defaultencoding/) property of the MailQueryBuilder. The following code snippet shows you how to specify the encoding for query builder.

{{< gist "aspose-com-gists" "6e5185a63aec6fd70d83098e82b06a32" "Examples-CSharp-IMAP-SpecifyEncodingForQueryBuilder-SpecifyEncodingForQueryBuilder.cs" >}}

### **Filter Messages with Paging Support**

The [ImapClient](https://reference.aspose.com/email/net/aspose.email.clients.imap/imapclient/) provides the capability to search for messages from the mailbox and list them with paging support. The following code snippet shows you how to filter messages with paging support.

{{< gist "aspose-com-gists" "6e5185a63aec6fd70d83098e82b06a32" "Examples-CSharp-IMAP-SearchWithPagingSupport-SearchWithPagingSupport.cs" >}}

## **Filter Messages with Custom Flag**

{{< gist "aspose-com-gists" "6e5185a63aec6fd70d83098e82b06a32" "Examples-CSharp-IMAP-GetMessagesWithSpecificCriteria-GetMessagesWithCustomFlags.cs" >}}

## **Filter Messages using Custom Search**

For example, RFC 3501 standard does not allow a message search based on the existence of attachments in messages. But **Gmail** provides [IMAP Extensions](https://developers.google.com/gmail/imap/imap-extensions?hl=ru) that allow performing such a search. The next code snippet shows how to make a corresponding query.

```csharp
ImapQueryBuilder queryBuilder = new ImapQueryBuilder();
queryBuilder.CustomSearch("X-GM-RAW \"has:attachment\"");

MailQuery mailQuery = queryBuilder.GetQuery();
ImapMessageInfoCollection messageInfoCollection = imapClient.ListMessages(mailQuery);
```
