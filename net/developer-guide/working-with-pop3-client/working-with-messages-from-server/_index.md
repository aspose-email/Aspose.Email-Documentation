---
title: Working with Messages from Server
type: docs
weight: 50
url: /net/working-with-messages-from-server/
---


## **Getting Mailbox Information**
We can get information about the mailbox such as the number of messages and the mailbox size using the [GetMailBoxSize](https://apireference.aspose.com/net/email/aspose.email.clients.pop3/pop3client/methods/getmailboxsize/index) and [GetMailBoxInfo](https://apireference.aspose.com/net/email/aspose.email.clients.pop3/pop3client/methods/getmailboxinfo/index) methods of the [Pop3Client](https://apireference.aspose.com/net/email/aspose.email.clients.pop3/pop3client) class.

- The [GetMailBoxSize](https://apireference.aspose.com/net/email/aspose.email.clients.pop3/pop3client/methods/getmailboxsize/index) method returns the size of the mailbox in bytes.
- The [GetMailBoxInfo](https://apireference.aspose.com/net/email/aspose.email.clients.pop3/pop3client/methods/getmailboxinfo/index) method returns an object of type [Pop3MailBoxInfo](https://apireference.aspose.com/net/email/aspose.email.clients.pop3/pop3mailboxinfo).

It is also possible to get the number of messages using the [MessageCount](https://apireference.aspose.com/net/email/aspose.email.clients.pop3/pop3mailboxinfo/properties/messagecount) property and the size using the [OccupiedSize](https://apireference.aspose.com/net/email/aspose.email.clients.pop3/pop3mailboxinfo/properties/occupiedsize) property of the [Pop3MailBoxInfo](https://apireference.aspose.com/net/email/aspose.email.clients.pop3/pop3mailboxinfo) class. The following sample code shows how to get information about the mailbox. It shows how to:

1. Create a [Pop3Client](https://apireference.aspose.com/net/email/aspose.email.clients.pop3/pop3client).
1. Connect to a POP3 server.
1. Get the size of the mailbox.
1. Get mailbox info.
1. Get the number of messages in the mailbox.
1. Get the occupied size.



{{< gist "aspose-com-gists" "6e5185a63aec6fd70d83098e82b06a32" "Examples-CSharp-POP3-GettingMailboxInfo-GettingMailboxInfo.cs" >}}
## **Getting email count in the mailbox**
The following code snippet shows you how to count the email messages in a mailbox.



{{< gist "aspose-com-gists" "6e5185a63aec6fd70d83098e82b06a32" "Examples-CSharp-POP3-GetEmailCountIntheMailbox-GetEmailCountIntheMailbox.cs" >}}



Aspose.Email lets developers work with emails in many different ways. For example, they can retrieve header information before deciding whether to download an email. Or they can retrieve emails from a server and save them without parsing them (quicker) or after parsing them (slower). This article shows how to retrieve and convert emails.
## **Retrieving Email Headers Information**
Email headers can give us information about an email message that we can use to decide whether or not to retrieve the whole email message. Typically, the header information contains sender, subject, received date, etc. (Email headers are described in detail in [Customizing Email Headers](/email/net/creating-and-setting-contents-of-emails/#set-email-headers). That topic is specifically about sending an email with SMTP, but the email header content information remains valid for POP3 emails). The following examples show how to retrieve email headers from a POP3 server by the message's sequence number.



{{< gist "aspose-com-gists" "6e5185a63aec6fd70d83098e82b06a32" "Examples-CSharp-POP3-RetrievingEmailHeaders-RetrievingEmailHeaders.cs" >}}
## **Retrieving Email Messages**
The [Pop3Client](https://apireference.aspose.com/net/email/aspose.email.clients.pop3/pop3client) class component provides the capability to retrieve email messages from the POP3 server, and parse them into a [MailMessage](https://apireference.aspose.com/net/email/aspose.email/mailmessage) instance with the help of [MailMessage](https://apireference.aspose.com/net/email/aspose.email/mailmessage) components. The [MailMessage](https://apireference.aspose.com/net/email/aspose.email/mailmessage) class contains several properties and methods for manipulating email content. By using [FetchMessage](https://apireference.aspose.com/net/email/aspose.email.clients.pop3/pop3client/methods/fetchmessage/index) method of the [Pop3Client](https://apireference.aspose.com/net/email/aspose.email.clients.pop3/pop3client) class, you can get a [MailMessage](https://apireference.aspose.com/net/email/aspose.email/mailmessage) instance directly from the POP3 server. The following code snippet shows you how to retrieves a complete email message from the POP3 server.



{{< gist "aspose-com-gists" "6e5185a63aec6fd70d83098e82b06a32" "Examples-CSharp-POP3-RetrievingEmailMessages-RetrievingEmailMessages.cs" >}}
## **Retrieving Message Summary Information using Unique Id**
The POP3 Client of the API can retrieve message summary information from the server using the unique id of the message. This provides quick access to the message’s short information without first retrieving the complete message from the server. The following code snippet shows you how to retrieve message summary information.



{{< gist "aspose-com-gists" "6e5185a63aec6fd70d83098e82b06a32" "Examples-CSharp-POP3-RetrieveMessageSummaryInformationUsingUniqueId-RetrieveMessageSummaryInformationUsingUniqueId.cs" >}}
## **Listing Messages with MultiConnection**
[Pop3Client](https://apireference.aspose.com/net/email/aspose.email.clients.pop3/pop3client) provides a [UseMultiConnection](https://apireference.aspose.com/net/email/aspose.email.clients/emailclient/properties/usemulticonnection) property which can be used to create multiple connections for heavy operations. You may also set the number of connections to be used during multiconnection mode by using [Pop3Client.ConnectionsQuantity](https://apireference.aspose.com/net/email/aspose.email.clients/emailclient/properties/connectionsquantity). The following code snippet demonstrates the use of the multiconnection mode for listing messages and compares its performance with single connection mode.



{{< gist "aspose-com-gists" "522d47278b8ca448dc1d7eb97193322c" "Examples-CSharp-POP3-Pop3ListMessagesWithMultiConnection-1.cs" >}}

{{% alert color="primary" %}} 

Please note that the usage of multiconnection mode does not guarantee performance increase.

{{% /alert %}} 
## **Fetching Messages from Server and saving to Disc**
### **Save Message to Disk without Parsing**
If you want to download email messages from the POP3 server without parsing them, use the [Pop3Client](https://apireference.aspose.com/net/email/aspose.email.clients.pop3/pop3client) class [SaveMessage](https://apireference.aspose.com/net/email/aspose.email.clients.pop3/pop3client/methods/savemessage/index) function. The [SaveMessage](https://apireference.aspose.com/net/email/aspose.email.clients.pop3/pop3client/methods/savemessage/index) function does not parse the email message so it is faster than the [FetchMessage](https://apireference.aspose.com/net/email/aspose.email.clients.pop3/pop3client/methods/fetchmessage/index) function. The following code snippet shows how to saves a message by its sequence number, in this case, number 1. The [SaveMessage](https://apireference.aspose.com/net/email/aspose.email.clients.pop3/pop3client/methods/savemessage/index) method saves the message in the original EML format without parsing it.



{{< gist "aspose-com-gists" "6e5185a63aec6fd70d83098e82b06a32" "Examples-CSharp-POP3-SaveToDiskWithoutParsing-SaveToDiskWithoutParsing.cs" >}}
### **Parse Message Before Saving**
The following code snippet uses the [Pop3Client](https://apireference.aspose.com/net/email/aspose.email.clients.pop3/pop3client) [FetchMessage](https://apireference.aspose.com/net/email/aspose.email.clients.pop3/pop3client/methods/fetchmessage/index) method to retrieve a message from a POP3 server by its sequence number, then save the message to disk using the subject as the file name.



{{< gist "aspose-com-gists" "6e5185a63aec6fd70d83098e82b06a32" "Examples-CSharp-POP3-ParseMessageAndSave-ParseMessageAndSave.cs" >}}
## **Group Fetch Messages**
[Pop3Client](https://apireference.aspose.com/net/email/aspose.email.clients.pop3/pop3client) provides a [FetchMessages](https://apireference.aspose.com/net/email/aspose.email.clients.pop3/pop3client/methods/fetchmessages/index) method which accepts iterable of Sequence Numbers or Unique ID and returns a list of [MailMessage](https://apireference.aspose.com/net/email/aspose.email/mailmessage). The following code snippet demonstrates the use of the [FetchMessages](https://apireference.aspose.com/net/email/aspose.email.clients.pop3/pop3client/methods/fetchmessages/index) method to fetch messages by Sequence Numbers and Unique ID.



{{< gist "aspose-com-gists" "522d47278b8ca448dc1d7eb97193322c" "Examples-CSharp-POP3-Pop3FetchGroupMessages-1.cs" >}}
## **Filtering Messages on Sender, Recipient or Date**
The [Pop3Client](https://apireference.aspose.com/net/email/aspose.email.clients.pop3/pop3client) class, described in [Connecting to a POP3 Server](/email/net/connect-to-pop3-server/#connecting-to-pop3-server), provides the [ListMessages()](https://apireference.aspose.com/net/email/aspose.email.clients.pop3/pop3client/methods/listmessages/index) method which gets all the messages from a mailbox. To get only messages which match some condition, use the overloaded [ListMessages()](https://apireference.aspose.com/net/email/aspose.email.clients.pop3/pop3client/methods/listmessages/index) method which takes [MailQuery](https://apireference.aspose.com/net/email/aspose.email.tools.search/mailquery) as an argument. The [MailQuery](https://apireference.aspose.com/net/email/aspose.email.tools.search/mailquery) class provides various properties for specifying the query conditions, for example, date, subject, sender, recipient and so on. The [MailQueryBuilder](https://apireference.aspose.com/net/email/aspose.email.tools.search/mailquerybuilder) class is used to build the search expression. First, all the conditions and constraints are set and then [MailQuery](https://apireference.aspose.com/net/email/aspose.email.tools.search/mailquery) is filled with the query developed by [MailQueryBuilder](https://apireference.aspose.com/net/email/aspose.email.tools.search/mailquerybuilder). The [MailQuery](https://apireference.aspose.com/net/email/aspose.email.tools.search/mailquery) class object is used by [Pop3Client](https://apireference.aspose.com/net/email/aspose.email.clients.pop3/pop3client) to extract the filtered information from the server. This article shows how to filter email messages from a mailbox. The first example illustrates how to filter messages based on date and subject. We also show how to filter on other criteria and how to build more complex queries. It also shows the application of Date and Time filter to retrieve the specific emails from the mailbox. In addition, it also shows how to apply case-sensitive filtering.
### **Filtering Messages from Mailbox**
To filter messages from a mailbox:

1. [Connect and log in to a POP3 server](/email/net/connect-to-pop3-server#connecting-to-pop3-server).
1. Create an instance of [MailQuery](https://apireference.aspose.com/net/email/aspose.email.tools.search/mailquery) and set the desired properties.
1. Call the [Pop3Client.ListMessages(MailQuery query)](https://apireference.aspose.com/net/email/aspose.email.clients.pop3.pop3client/listmessages/methods/8) method and pass the [MailQuery](https://apireference.aspose.com/net/email/aspose.email.tools.search/mailquery) in parameters to get the filtered messages only.

The following code snippet shows you how to connect to a POP3 mailbox and get messages that arrived today and have the word "newsletter" in the subject.



{{< gist "aspose-com-gists" "6e5185a63aec6fd70d83098e82b06a32" "Examples-CSharp-POP3-FilterMessagesFromPOP3Mailbox-FilterMessagesFromPOP3Mailbox.cs" >}}
### **Getting Messages that Meet Specific Criteria**
[The code samples above](/email/net/working-with-messages-from-server/#filtering-messages-from-mailbox) filter messages based on the email subject and date. We can use other properties to set other supported conditions as well. Below are some examples of setting the conditions using [MailQuery](https://apireference.aspose.com/net/email/aspose.email.tools.search/mailquery).

The code snippets that follow show how to filter emails on other criteria:

- Find emails delivered today.
- Find emails received within a range.
- Find emails from a specific sender.
- Find emails sent from a specific domain.
- Find emails sent to a specific recipient.
#### **Today's Date**
The following code snippet shows you how to find emails delivered today.



{{< gist "aspose-com-gists" "6e5185a63aec6fd70d83098e82b06a32" "Examples-CSharp-POP3-GetMessagesUsingSpecificCriteria-GetEmailsWithTodayDate.cs" >}}
#### **Date Range**
The following code snippet shows you how to find emails received within a range.



{{< gist "aspose-com-gists" "6e5185a63aec6fd70d83098e82b06a32" "Examples-CSharp-POP3-GetMessagesUsingSpecificCriteria-GetEmailsOverDateRange.cs" >}}
#### **Specific Sender**
The following code snippet shows you how to find emails from a specific sender.



{{< gist "aspose-com-gists" "6e5185a63aec6fd70d83098e82b06a32" "Examples-CSharp-POP3-GetMessagesUsingSpecificCriteria-GetSpecificSenderEmails.cs" >}}
#### **Specific Domain**
The following code snippet shows you how to find emails sent from a specific domain.



{{< gist "aspose-com-gists" "6e5185a63aec6fd70d83098e82b06a32" "Examples-CSharp-POP3-GetMessagesUsingSpecificCriteria-GetSpecificDomainEmails.cs" >}}
#### **Specific Recipient**
The following code snippet shows you how to find emails sent to a specific recipient.



{{< gist "aspose-com-gists" "6e5185a63aec6fd70d83098e82b06a32" "Examples-CSharp-POP3-GetMessagesUsingSpecificCriteria-GetSpecificRecipientEmails.cs" >}}
### **Building Complex Queries**
If different [MailQueryBuilder](https://apireference.aspose.com/net/email/aspose.email.tools.search/mailquerybuilder) properties are set in separate statements, then all the conditions would be matched. For example, if we want to get messages between a date range and from a specific host, we need to write three statements.
#### **Combining Queries with AND**
The following code snippet shows you how to combine queries with AND.



{{< gist "aspose-com-gists" "6e5185a63aec6fd70d83098e82b06a32" "Examples-CSharp-POP3-BuildComplexQueries-CombineQueriesWithAND.cs" >}}
#### **Combining Queries with OR**
[MailQueryBuilder](https://apireference.aspose.com/net/email/aspose.email.tools.search/mailquerybuilder) provides the [Or()](https://apireference.aspose.com/net/email/aspose.email.tools.search/mailquerybuilder/methods/or) method which takes two [MailQuery](https://apireference.aspose.com/net/email/aspose.email.tools.search/mailquery) instances as parameters. It gets the messages that match any of the two conditions specified. The following code snippet shows how to filter messages that either have “test” in the subject or “noreply@host.com” as the sender. The following code snippet shows you how to combine queries with OR.



{{< gist "aspose-com-gists" "6e5185a63aec6fd70d83098e82b06a32" "Examples-CSharp-POP3-BuildComplexQueries-CombiningQueriesWithOR.cs" >}}
#### **Applying Case Sensitive Filters**
The API also provides the capability to filter emails from the mailbox based on a case sensitive criteria. The following methods provide the capability to search emails specifying case sensitive flag.

- Method Aspose.Email.StringComparisonField.Contains(string value, bool ignoreCase)
- Method Aspose.Email.StringComparisonField.Equals(string value, bool ignoreCase)
- Method Aspose.Email.StringComparisonField.NotContains(string value, bool ignoreCase)
- Method Aspose.Email.StringComparisonField.NotEquals(string value, bool ignoreCase)



{{< gist "aspose-com-gists" "6e5185a63aec6fd70d83098e82b06a32" "Examples-CSharp-POP3-ApplyCaseSensitiveFilters-ApplyCaseSensitiveFilters.cs" >}}
