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

1. Create a [Pop3Client](https://apireference.aspose.com/email/net/aspose.email.clients.pop3/pop3client).
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
## **Listing Messages with MultiConnection**

For heavy-loaded operations Aspose.Email offers the 'use_multi_connection' property of the [Pop3Client](https://reference.aspose.com/email/python-net/aspose.email.clients.pop3/pop3client/#pop3client-class) class to use multiple connections while retrieving emails. However, using this mode does not necessarily have to lead to the increase in performance. The following code snippet shows you how to establish a connection to a POP3 server, configure the client to allow up to 5 concurrent connections and enable multi-connection mode to retrieve information about the messages present on the server:

```py
import aspose.email as ae

client = ae.clients.pop3.Pop3Client("host", 995, "username", "password", ae.clients.SecurityOptions.AUTO)

client.connections_quantity = 5
client.use_multi_connection = ae.clients.MultiConnectionMode.ENABLE
message_info_coll = client.list_messages()
```

## **Fetching Messages from Server and saving to Disc**
### **Save Message to Disk without Parsing**
If you want to download email messages from the POP3 server without parsing them, use the Pop3Client class SaveMessage function. The SaveMessage function does not parse the email message so it is faster than the FetchMessage function. The following code snippet shows how to saves a message by its sequence number, in this case number 1. The SaveMessagemethod saves the message in the original EML format without parsing it.



{{< gist "aspose-email" "356f0e128b9d45a7ee779fc813eb87e5" "Examples-POP3-SaveToDiscWithoutParsing-SaveToDiscWithoutParsing.py" >}}

### **Parse Message Before Saving**

Use the 'fetch_message' method of the client object created using [Pop3Client](https://reference.aspose.com/email/python-net/aspose.email.clients.pop3/pop3client/#pop3client-class) class to retrieve the message with a specific sequence number. The code sample below demonstrates how to retrieve a specific message and save it using its subject as the file name by calling the 'save' method on the msg object:

```py
import aspose.email as ae

client = ae.clients.pop3.Pop3Client("host", 995, "username", "password", ae.clients.SecurityOptions.AUTO)

# Fetch the message by its sequence number and Save the message using its subject as the file name
msg = client.fetch_message(1)
msg.save("first-message_out.eml", ae.SaveOptions.default_eml)
```
### **Filtering Messages on Sender, Recipient or Date**
The Pop3Client class, described in Connecting to a POP3 Server, provides the list_messages() method which gets all the messages from a mailbox. To get only messages which match some condition, use the overloaded ListMessages() method which takes MailQuery as an argument. The MailQuery class provides various properties for specifying the query conditions, for example, date, subject, sender, recipient and so on. The MailQueryBuilder class is used to build the search expression. First, all the conditions and constraints are set and then MailQuery is filled with the query developed by MailQueryBuilder. The MailQuery class object is used by Pop3Client to extract the filtered information from the server. This article shows how to filter email messages from a mailbox. The first example illustrates how to filter messages based on date and subject. We also show how to filter on other criteria and how to build more complex queries. It also shows the application of Date and Time filter to retrieve the specific emails from the mailbox. In addition, it also shows how to apply case-sensitive filtering.
### **Filtering Messages from Mailbox**
To filter messages from a mailbox:

1. Connect and log in to a POP3 server.
1. Create an instance of MailQuery and set the desired properties.
1. Call the Pop3Client.list_messages(MailQuery query) method and pass the MailQuery in parameters to get the filtered messages only.

The following code snippet shows you how to connect to a POP3 mailbox and get messages that arrived to day and have the word "newsletter" in the subject.



{{< gist "aspose-email" "356f0e128b9d45a7ee779fc813eb87e5" "Examples-POP3-FilterMessagesFromMailbox-FilterMessagesFromMailbox.py" >}}

### **Getting Messages that Meet Specific Criteria**

Aspose.Email also makes it possible to build complex search criteria for querying and filtering email messages. For this purpose use the [MailQueryBuilder](https://reference.aspose.com/email/python-net/aspose.email.tools.search/mailquerybuilder/#mailquerybuilder-class) class and its properties. The criteria for fetching are as follows:

- Fetch messages by delivery date.
- Fetch messages within a range.
- Fetch messages from a specific sender.
- Fetch messages from a specific domain.
- Fetch messages to a specific recipient.

#### **Today's date**

To fetch messages by a delivery date, use the 'internal_date' property as shown in the code sample below:

```py
import aspose.email as ae
from datetime import datetime

builder = ae.tools.search.MailQueryBuilder()
builder.internal_date.on(datetime.now())
```
#### **Date range**

To fetch messages within a date range, use the same 'internal_date' property specifying the date range as shown in the code sample below:

```py
import aspose.email as ae
from datetime import datetime, timedelta

builder = ae.tools.search.MailQueryBuilder()
# Emails that arrived in last 7 days
builder.internal_date.before(datetime.now())
builder.internal_date.since(datetime.today() - timedelta(days=7))
```
#### **Specific Sender**

To fetch messages from a specific sender, use the 'from_address' property as shown in the code sample below:

```py
import aspose.email as ae

builder = ae.tools.search.MailQueryBuilder()
builder.from_address.contains("saqib.razzaq@127.0.0.1")
```
#### **Specific domain**

To fetch messages from a specific domain, use the 'from_address' property as shown in the code sample below:

```py
import aspose.email as ae

builder = ae.tools.search.MailQueryBuilder()
builder.from_address.contains("SpecificHost.com")
```
#### **Specific recipient**

To fetch messages to a specific recipient, use the 'to' property as shown in the code sample below:

```py
import aspose.email as ae

builder = ae.tools.search.MailQueryBuilder()
builder.to.contains("recipient")
```
### **Building Complex Queries**

Sometimes it is necessary to satisfy more than one query. Aspose.Email makes it possible by combining queries in several statements. Create a [MailQueryBuilder](https://reference.aspose.com/email/python-net/aspose.email.tools.search/mailquerybuilder/#mailquerybuilder-class) object and use its properties to build specific queries.

#### **Combining Queries with AND**

The following code snippet shows you how to combine queries with AND.

```py
import aspose.email as ae
from datetime import datetime, timedelta

builder = ae.tools.search.MailQueryBuilder()
builder.internal_date.before(datetime.now())
builder.internal_date.since(datetime.today() - timedelta(days=7))
builder.from_address.contains("SpecificHost.com")
```
#### **Combining Queries with OR**

The following code snippet shows you how to combine queries with OR.

```py
import aspose.email as ae

builder = ae.tools.search.MailQueryBuilder()
builder.either(builder.subject.contains("test"), builder.from_address.contains("noreply@host.com"))
```

#### **Applying Case Sensitive Filters**

The API also provides the capability to filter emails from the mailbox based on a case sensitive criteria. The following methods of the [StringComparisonField](https://reference.aspose.com/email/python-net/aspose.email.tools.search/stringcomparisonfield/#stringcomparisonfield-class) class provide the capability to search emails specifying case sensitive flags.  

Method Aspose.Email.StringComparisonField.contains(value, ignore_case)
Method Aspose.Email.StringComparisonField.equals(value, ignore_case)
Method Aspose.Email.StringComparisonField.not_contains(value, ignore_case)
Method Aspose.Email.StringComparisonField.not_equals(value, ignore_case)

The following code snippet shows you how to implement this capability into your project:

```py
import aspose.email as ae

builder = ae.tools.search.MailQueryBuilder()
builder.from_address.contains("noreply@host.com", True)
```

