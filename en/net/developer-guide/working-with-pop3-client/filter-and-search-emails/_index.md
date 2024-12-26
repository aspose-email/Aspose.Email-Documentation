---
title: Filter Emails from Mail Server
ArticleTitle: Filter Emails from Mail Server
type: docs
weight: 50
url: /net/filter-emails-from-mail-server/
---


## **Filter Messages by Sender, Recipient or Date**

The [Pop3Client](https://reference.aspose.com/email/net/aspose.email.clients.pop3/pop3client/) class, described in [Connect to POP3 Server](https://docs.aspose.com/email/net/connect-to-pop3-server/), provides the [ListMessages()](https://reference.aspose.com/email/net/aspose.email.clients.pop3/pop3client/listmessages/#listmessages/) method which gets all the messages from a mailbox. To get only messages which match some condition, use the overloaded [ListMessages()](https://reference.aspose.com/email/net/aspose.email.clients.pop3/pop3client/listmessages/#listmessages/) method which takes [MailQuery](https://reference.aspose.com/email/net/aspose.email.tools.search/mailquery/) as an argument. The [MailQuery](https://reference.aspose.com/email/net/aspose.email.tools.search/mailquery/) class provides various properties for specifying the query conditions, for example, date, subject, sender, recipient and so on. The [MailQueryBuilder](https://reference.aspose.com/email/net/aspose.email.tools.search/mailquerybuilder/) class is used to build the search expression. First, all the conditions and constraints are set and then [MailQuery](https://reference.aspose.com/email/net/aspose.email.tools.search/mailquery/) is filled with the query developed by [MailQueryBuilder](https://reference.aspose.com/email/net/aspose.email.tools.search/mailquerybuilder/). The [MailQuery](https://reference.aspose.com/email/net/aspose.email.tools.search/mailquery/) class object is used by [Pop3Client](https://reference.aspose.com/email/net/aspose.email.clients.pop3/pop3client/) to extract the filtered information from the server. This article shows how to filter email messages from a mailbox. The first example illustrates how to filter messages based on date and subject. We also show how to filter on other criteria and how to build more complex queries. It also shows the application of Date and Time filter to retrieve the specific emails from the mailbox. In addition, it also shows how to apply case-sensitive filtering.

## **Filter Messages from Mailbox**

To filter messages from a mailbox:

1. [Connect to POP3 server](https://docs.aspose.com/email/net/connect-to-pop3-server/#connect-to-pop3-server).
2. Create an instance of [MailQuery](https://reference.aspose.com/email/net/aspose.email.tools.search/mailquery/) and set the desired properties.
3. Call the [Pop3Client.ListMessages(MailQuery query)](https://reference.aspose.com/email/net/aspose.email.clients.pop3/pop3client/listmessages/#listmessages_8) method and pass the [MailQuery](https://reference.aspose.com/email/net/aspose.email.tools.search/mailquery/) in parameters to get the filtered messages only.

The following code snippet shows you how to connect to a POP3 mailbox and get messages that arrived today and have the word "newsletter" in the subject.

{{< gist "aspose-com-gists" "6e5185a63aec6fd70d83098e82b06a32" "Examples-CSharp-POP3-FilterMessagesFromPOP3Mailbox-FilterMessagesFromPOP3Mailbox.cs" >}}

## **Retrieve Messages by Specific Criteria**

[The code samples above](https://docs.aspose.com/email/net/filter-emails-from-mail-server/#filter-messages-from-mailbox) shows how you can filter messages based on the email subject and date. We can use other properties to set other supported conditions as well. Below are some examples of setting the conditions using [MailQuery](https://reference.aspose.com/email/net/aspose.email.tools.search/mailquery/).

The code snippets that follow show how to filter emails on other criteria:

- Find emails delivered today.
- Find emails received within a range.
- Find emails from a specific sender.
- Find emails sent from a specific domain.
- Find emails sent to a specific recipient.
  
### **Today's Date**

The following code snippet shows you how to find emails delivered today.

{{< gist "aspose-com-gists" "6e5185a63aec6fd70d83098e82b06a32" "Examples-CSharp-POP3-GetMessagesUsingSpecificCriteria-GetEmailsWithTodayDate.cs" >}}

### **Date Range**

The following code snippet shows you how to find emails received within a range.

{{< gist "aspose-com-gists" "6e5185a63aec6fd70d83098e82b06a32" "Examples-CSharp-POP3-GetMessagesUsingSpecificCriteria-GetEmailsOverDateRange.cs" >}}

### **Specific Sender**

The following code snippet shows you how to find emails from a specific sender.

{{< gist "aspose-com-gists" "6e5185a63aec6fd70d83098e82b06a32" "Examples-CSharp-POP3-GetMessagesUsingSpecificCriteria-GetSpecificSenderEmails.cs" >}}

### **Specific Domain**

The following code snippet shows you how to find emails sent from a specific domain.

{{< gist "aspose-com-gists" "6e5185a63aec6fd70d83098e82b06a32" "Examples-CSharp-POP3-GetMessagesUsingSpecificCriteria-GetSpecificDomainEmails.cs" >}}

### **Specific Recipient**

The following code snippet shows you how to find emails sent to a specific recipient.

{{< gist "aspose-com-gists" "6e5185a63aec6fd70d83098e82b06a32" "Examples-CSharp-POP3-GetMessagesUsingSpecificCriteria-GetSpecificRecipientEmails.cs" >}}

## **Build Complex Queries**

If different [MailQueryBuilder](https://reference.aspose.com/email/net/aspose.email.tools.search/mailquerybuilder/) properties are set in separate statements, then all the conditions would be matched. For example, if we want to get messages between a date range and from a specific host, we need to write three statements.

### **Combine Queries with AND**

The following code snippet shows you how to combine queries with AND.

{{< gist "aspose-com-gists" "6e5185a63aec6fd70d83098e82b06a32" "Examples-CSharp-POP3-BuildComplexQueries-CombineQueriesWithAND.cs" >}}

### **Combine Queries with OR**

[MailQueryBuilder](https://reference.aspose.com/email/net/aspose.email.tools.search/mailquerybuilder/) provides the [Or()](https://reference.aspose.com/email/net/aspose.email.tools.search/mailquerybuilder/or/#or) method which takes two [MailQuery](https://reference.aspose.com/email/net/aspose.email.tools.search/mailquery/) instances as parameters. It gets the messages that match any of the two conditions specified. The following code snippet shows how to filter messages that either have “test” in the subject or "noreply@host.com" as the sender. The following code snippet shows you how to combine queries with OR.

{{< gist "aspose-com-gists" "6e5185a63aec6fd70d83098e82b06a32" "Examples-CSharp-POP3-BuildComplexQueries-CombiningQueriesWithOR.cs" >}}

### **Case Sensitive Filters**

The API also provides the capability to filter emails from the mailbox based on a case sensitive criteria. The following methods provide the capability to search emails specifying case sensitive flag.

- Method Aspose.Email.StringComparisonField.Contains(string value, bool ignoreCase)
- Method Aspose.Email.StringComparisonField.Equals(string value, bool ignoreCase)
- Method Aspose.Email.StringComparisonField.NotContains(string value, bool ignoreCase)
- Method Aspose.Email.StringComparisonField.NotEquals(string value, bool ignoreCase)

{{< gist "aspose-com-gists" "6e5185a63aec6fd70d83098e82b06a32" "Examples-CSharp-POP3-ApplyCaseSensitiveFilters-ApplyCaseSensitiveFilters.cs" >}}
