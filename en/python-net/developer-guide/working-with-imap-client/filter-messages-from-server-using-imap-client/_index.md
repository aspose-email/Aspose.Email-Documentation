---
title: Filter Messages from Server using IMAP Client
ArticleTitle: Filter Messages from Server using IMAP Client
type: docs
weight: 30
url: /python-net/filter-messages-from-server-using-imap-client/
---


The ImapClient class provides the ListMessages() method which gets all the messages from a mailbox. To get only messages which match some condition, use the overloaded ListMessages() method which takes MailQuery as an argument. The MailQuery class provides various properties for specifying the conditions, for example, date, subject, sender, recipient and so on. The first example illustrates how to filter messages based on date and subject. We also show how to filter on other criteria and how to build more complex queries. The API also provides the capability to apply case-sensitive searching criteria to match exact filtering criteria. The API also allows to specify the search string encoding for filtering messages from the mailbox.
## **Filtering Messages from Mailbox**
1. Connect and log in to an IMAP server
1. Create an instance of the MailQuery and set the properties
1. Call the ImapClient.ListMessages(MailQuery query) method and pass the MailQuery with the parameters to get filtered messages only.

The following code snippet shows you how to connect to an IMAP mailbox and get messages that arrived to day and have the word "newsletter" in the subject.



{{< gist "aspose-email" "356f0e128b9d45a7ee779fc813eb87e5" "Examples-IMAP-FilteringMessagesFromIMAPMailbox-FetchEmailMessageFromServer.py" >}}

## **Getting Messages that Meet Specific Criteria**

Aspose.Email also makes it possible to build complex search criteria for querying and filtering email messages. For this purpose use the [MailQueryBuilder](https://reference.aspose.com/email/python-net/aspose.email.tools.search/mailquerybuilder/#mailquerybuilder-class) class and its properties. The criteria for fetching are as follows:

- Fetch messages by delivery date.
- Fetch messages within a range.
- Fetch messages from a specific sender.
- Fetch messages from a specific domain.
- Fetch messages to a specific recipient.

### **Today's date**

To fetch messages by a delivery date, use the 'internal_date' property as shown in the code sample below:

```py
import aspose.email as ae
from datetime import datetime

builder = ae.tools.search.MailQueryBuilder()
builder.internal_date.on(datetime.now())
```
### **Date range**

To fetch messages within a date range, use the same 'internal_date' property specifying the date range as shown in the code sample below:

```py
import aspose.email as ae
from datetime import datetime, timedelta

builder = ae.tools.search.MailQueryBuilder()
# Emails that arrived in last 7 days
builder.internal_date.before(datetime.now())
builder.internal_date.since(datetime.today() - timedelta(days=7))
```
### **Specific Sender**

To fetch messages from a specific sender, use the 'from_address' property as shown in the code sample below:

```py
import aspose.email as ae

builder = ae.tools.search.MailQueryBuilder()
builder.from_address.contains("saqib.razzaq@127.0.0.1")
```
### **Specific domain**

To fetch messages from a specific domain, use the 'from_address' property as shown in the code sample below:

```py
import aspose.email as ae

builder = ae.tools.search.MailQueryBuilder()
builder.from_address.contains("SpecificHost.com")
```
### **Specific recipient**

To fetch messages to a specific recipient, use the 'to' property as shown in the code sample below:

```py
import aspose.email as ae

builder = ae.tools.search.MailQueryBuilder()
builder.to.contains("recipient")
```

## **Building Complex Queries**

Sometimes it is necessary to satisfy more than one query. Aspose.Email makes it possible by combining queries in several statements. Create a [MailQueryBuilder](https://reference.aspose.com/email/python-net/aspose.email.tools.search/mailquerybuilder/#mailquerybuilder-class) object and use its properties to build specific queries.

### **Combining Queries with AND**

The following code snippet shows you how to combine queries with AND.

```py
import aspose.email as ae
from datetime import datetime, timedelta

builder = ae.tools.search.MailQueryBuilder()
builder.internal_date.before(datetime.now())
builder.internal_date.since(datetime.today() - timedelta(days=7))
builder.from_address.contains("SpecificHost.com")
```
### **Combining Queries with OR**

The following code snippet shows you how to combine queries with OR.

```py
import aspose.email as ae

builder = ae.tools.search.MailQueryBuilder()
builder.either(builder.subject.contains("test"), builder.from_address.contains("noreply@host.com"))
```
## **Filtration on InternalDate**

The API provides the capability to retrieve a list of messages from the server that meet the specified conditions. The code sample below shows how to build a query on the "internal date" and "subject contains" conditions. The "internal date" refers to the date and time when an email message was received or added to the email server and can be set using the 'internal_date' property of the [ImapQueryBuilder](https://reference.aspose.com/email/python-net/aspose.email.clients.imap/imapquerybuilder/#imapquerybuilder-class) class. 


```py
import aspose.email as ae
from datetime import datetime

client = ae.clients.imap.ImapClient("imap.domain.com", 993, "user@domain.com", "pwd")
client.select_folder("Inbox")

# Set conditions, Subject contains "Newsletter", Emails that arrived today
builder = ae.clients.imap.ImapQueryBuilder()
builder.subject.contains("Newsletter")
builder.internal_date.on(datetime.now())

# Build the query and Get list of messages
query = builder.get_query()
messages = client.list_messages(query)
for info in messages:
    print(f"Internal Date: {info.internal_date}")
```
The code prints out the internal date of each message that meets the specified conditions.

## **Filter Messages by Custom Keyword Flags**

The Aspose.Email library allows for creating a query to search an IMAP mailbox for emails that contain custom keyword flags. In the example below, the custom keywords used are "custom1" and "custom2". Use the [ImapQueryBuilder](https://reference.aspose.com/email/python-net/aspose.email.clients.imap/imapquerybuilder/#imapquerybuilder-class) class which is a tool that allows you to build search queries that can be used to filter emails when retrieving them from an IMAP server. Create a query builder. Using the 'has_flags' method of the builder, add conditions to the query to only include emails that have the IMAP flags keywords. Custom keywords in IMAP are also known as user-defined flags that can be used to tag or mark emails in the mailbox for various purposes, including categorization, status, and more. The following code snippet demonstrates how to create a query to retrieve specific emails by custom keyword flags:  

```py
import aspose.email as ae

builder = ae.clients.imap.ImapQueryBuilder()
builder.has_flags(ae.clients.imap.ImapMessageFlags.keyword("custom1"))
builder.has_flags(ae.clients.imap.ImapMessageFlags.keyword("custom2"))
```
## **Filter Messages using Custom Search**

The Python library can be used to create a search query for an IMAP mailbox that filters emails based on a custom Gmail search criterion, specifically emails that have attachments. Create an instance of [ImapQueryBuilder](https://reference.aspose.com/email/python-net/aspose.email.clients.imap/imapquerybuilder/#imapquerybuilder-class), which allows you to build complex IMAP search queries that can be used to filter emails from an IMAP server. By calling the 'custom_search' method, add a custom search string to the query builder. The string X-GM-RAW "has:attachment" is a Gmail-specific search term that uses the X-GM-RAW attribute. Gmail allows for the use of their webmail search syntax in IMAP searches through this attribute. The term "has:attachment" is a Gmail search operator that finds all emails containing an attachment. The following code snippet demonstrates how to filter emails according to the criteria defined (in this case, all emails with an attachment):

```py
import aspose.email as ae

builder = ae.clients.imap.ImapQueryBuilder()
builder.custom_search("X-GM-RAW \"has:attachment\"")

mailQuery = builder.get_query()
```

### **Applying Case Sensitive Filters**

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
