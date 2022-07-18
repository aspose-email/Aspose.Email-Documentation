---
title: Working with Messages from Server
type: docs
weight: 40
url: /python-net/working-with-messages-from-server/
---

## **Getting Mailbox Information**
We can get information about the mailbox such as the number of messages and the mailbox size using the GetMailBoxSize() and GetMailBoxInfo() methods.

- The GetMailBoxSize() method returns the size of the mailbox in bytes.
- The GetMailBoxInfo() method returns an object of type Pop3MailBoxInfo.

It is also possible to get the number of messages using the MessageCount property and the size using the OccupiedSize property. The following sample code shows how to get information about the mailbox. It shows how to:

1. Create a [Pop3Client](https://reference.aspose.com/email/net/aspose.email.clients.pop3/pop3client).
1. Connect to a POP3 server.
1. Get the size of the mailbox.
1. Get mailbox info.
1. Get the number of messages in the mailbox.
1. Get the occupied size.



{{< gist "aspose-email" "356f0e128b9d45a7ee779fc813eb87e5" "Examples-POP3-GettingMailboxInfo-GettingMailboxInfo.py" >}}
## **Getting email count in the mailbox**
The following code snippet shows you how to count the email messages in a mailbox.



{{< gist "aspose-email" "356f0e128b9d45a7ee779fc813eb87e5" "Examples-POP3-GetEmailCountInMailbox-GetEmailCountInMailbox.py" >}}



Aspose.Email lets developers work with emails in many different ways. For example, they can retrieve header information before deciding whether to download an email. Or they can retrieve emails from a server and save them without parsing them (quicker) or after parsing them (slower). This article shows how to retrieve and convert emails.
## **Retrieving Email Headers Information**
Email headers can give us information about an email message that we can use to decide whether or not to retrieve the whole email message. Typically, the header information contains sender, subject, received date etc. (Email headers are described in detail in Customizing Email Headers. That topic is specifically about sending email with SMTP, but the email header content information remains valid for POP3 emails). The following examples show how to retrieve email headers from a POP3 server by the message's sequence number.



{{< gist "aspose-email" "356f0e128b9d45a7ee779fc813eb87e5" "Examples-POP3-RetrievingEmailHeaders-RetrievingEmailHeaders.py" >}}
## **Retrieving Email Messages**
The Aspose.Email.Pop3 class component provides the capability to retrieve email messages from the POP3 server, and parse them into an MailMessage instance with the help of MailMessage components. The MailMessage class contains several properties and methods for manipulating email content. By using the the Pop3Client class FetchMessage function, you can get a MailMessage instance directly from the POP3 server. The following code snippet shows you how to retrieves a complete email message from the POP3 server.



{{< gist "aspose-email" "356f0e128b9d45a7ee779fc813eb87e5" "Examples-POP3-RetrievingEmailMessages-RetrievingEmailMessages.py" >}}
## **Retrieving Message Summary Information using Unique Id**
The POP3 Client of the API can retrieve message summary information from the server using the unique id of the message. This provides quick access to the message’s short information without first retrieving the complete message from the server. The following code snippet shows you how to retrieving message summary information.



{{< gist "aspose-email" "356f0e128b9d45a7ee779fc813eb87e5" "Examples-POP3-RetrieveMessageSummaryInformationUsingUniqueId-RetrieveMessageSummaryInformationUsingUniqueId.py" >}}
## **Fetching Messages from Server and saving to Disc**
### **Save Message to Disk without Parsing**
If you want to download email messages from the POP3 server without parsing them, use the Pop3Client class SaveMessage function. The SaveMessage function does not parse the email message so it is faster than the FetchMessage function. The following code snippet shows how to saves a message by its sequence number, in this case number 1. The SaveMessagemethod saves the message in the original EML format without parsing it.



{{< gist "aspose-email" "356f0e128b9d45a7ee779fc813eb87e5" "Examples-POP3-SaveToDiscWithoutParsing-SaveToDiscWithoutParsing.py" >}}
### **Filtering Messages on Sender, Recipient or Date**
The Pop3Client class, described in Connecting to a POP3 Server, provides the list_messages() method which gets all the messages from a mailbox. To get only messages which match some condition, use the overloaded ListMessages() method which takes MailQuery as an argument. The MailQuery class provides various properties for specifying the query conditions, for example, date, subject, sender, recipient and so on. The MailQueryBuilder class is used to build the search expression. First, all the conditions and constraints are set and then MailQuery is filled with the query developed by MailQueryBuilder. The MailQuery class object is used by Pop3Client to extract the filtered information from the server. This article shows how to filter email messages from a mailbox. The first example illustrates how to filter messages based on date and subject. We also show how to filter on other criteria and how to build more complex queries. It also shows the application of Date and Time filter to retrieve the specific emails from the mailbox. In addition, it also shows how to apply case-sensitive filtering.
### **Filtering Messages from Mailbox**
To filter messages from a mailbox:

1. Connect and log in to a POP3 server.
1. Create an instance of MailQuery and set the desired properties.
1. Call the Pop3Client.list_messages(MailQuery query) method and pass the MailQuery in parameters to get the filtered messages only.

The following code snippet shows you how to connect to a POP3 mailbox and get messages that arrived to day and have the word "newsletter" in the subject.



{{< gist "aspose-email" "356f0e128b9d45a7ee779fc813eb87e5" "Examples-POP3-FilterMessagesFromMailbox-FilterMessagesFromMailbox.py" >}}
