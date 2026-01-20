---
title: Search and Filter IMAP Emails in Python Using Aspose.Email
ArticleTitle: Search and Filter IMAP Emails in Python 
type: docs
weight: 30
url: /python-net/filter-messages-from-server-using-imap-client/
---


To retrieve all messages from a mailbox Aspose.Email provides the 'list_messages' method of the [ImapClient](https://reference.aspose.com/email/python-net/aspose.email.clients.imap/imapclient/) class. For fetching only those messages that satisfy specific conditions, you can use the overloaded 'list_messages' method that accepts a [MailQuery](https://reference.aspose.com/email/python-net/aspose.email.tools.search/mailquery/) as an argument. The [MailQuery](https://reference.aspose.com/email/python-net/aspose.email.tools.search/mailquery/) class offers various properties to define these conditions, such as date, subject, sender, and recipient. 

The first code sample demonstrates how to filter messages based on both date and subject. Additional examples showcase filtering by other criteria and constructing more complex queries. Moreover, the API supports case-sensitive search criteria for precise filtering and allows you to specify the encoding of the search string when filtering messages from the mailbox.

## **Filter and Fetch Messages from IMAP Server**

### **Build a Simple IMAP Query**

Use the following code snippet to connect to an IMAP mailbox and get messages that arrived today and have the word "newsletter" in the subject.

1. Connect to the IMAP server using port 993 with the username and password.
2. Select the "Inbox" folder to work with incoming emails.
3. Create an instance of [ImapQueryBuilder](https://reference.aspose.com/email/python-net/aspose.email.clients.imap/imapquerybuilder/) to construct a search query.
4. Specify search criteria, for example, that the subject of emails should contain "Newsletter" and that the internal date should match today's date.
5. Generate the search query by retrieving it from the builder.
6. Use the query to list messages that meet the criteria.
7. Print the total number of messages that match the search criteria.


{{< gist "aspose-email" "356f0e128b9d45a7ee779fc813eb87e5" "Examples-IMAP-FilteringMessagesFromIMAPMailbox-FetchEmailMessageFromServer.py" >}}

### **Build Complex Search Criteria**

Aspose.Email also makes it possible to build complex search criteria for querying and filtering email messages such as delivery date, within a range, specific sender, specific domain, or specific recipient. For this purpose, use the [MailQueryBuilder](https://reference.aspose.com/email/python-net/aspose.email.tools.search/mailquerybuilder/#mailquerybuilder-class) class and its properties. The code samples below will show you how to fetch messages by specific criteria. 

#### **Filter Emails by Today's Date**

To fetch messages by a delivery date, use the 'internal_date' property of the [MailQueryBuilder](https://reference.aspose.com/email/python-net/aspose.email.tools.search/mailquerybuilder/#mailquerybuilder-class) class as shown in the code sample below:

```py
import aspose.email as ae
from datetime import datetime

builder = ae.tools.search.MailQueryBuilder()
builder.internal_date.on(datetime.now())
```

#### **Filter Emails by Date Range**

To fetch messages within a date range, use the same 'internal_date' property specifying the date range as shown in the code sample below:

```py
import aspose.email as ae
from datetime import datetime, timedelta

builder = ae.tools.search.MailQueryBuilder()
# Emails that arrived in last 7 days
builder.internal_date.before(datetime.now())
builder.internal_date.since(datetime.today() - timedelta(days=7))
```

#### **Filter Emails by Specific Sender**

To fetch messages from a specific sender, use the 'from_address' property of the [MailQueryBuilder](https://reference.aspose.com/email/python-net/aspose.email.tools.search/mailquerybuilder/#mailquerybuilder-class) class as shown in the code sample below:

```py
import aspose.email as ae

builder = ae.tools.search.MailQueryBuilder()
builder.from_address.contains("saqib.razzaq@127.0.0.1")
```

#### **Filter Emails by Specific Domain**

To fetch messages from a specific domain, use the 'from_address' property as shown in the code sample below:

```py
import aspose.email as ae

builder = ae.tools.search.MailQueryBuilder()
builder.from_address.contains("SpecificHost.com")
```

#### **Filter Emails by Specific recipient**

To fetch messages to a specific recipient, use the 'to' property as shown in the code sample below:

```py
import aspose.email as ae

builder = ae.tools.search.MailQueryBuilder()
builder.to.contains("recipient")
```

#### **Filter Messages by Internal Date**

Build a query on the specified conditions such as "internal date" and "subject contains". The "internal date" refers to the date and time when an email message was received or added to the email server and can be set using the 'internal_date' property of the [ImapQueryBuilder](https://reference.aspose.com/email/python-net/aspose.email.clients.imap/imapquerybuilder/#imapquerybuilder-class) class. The code sample below demonstrates how to fetch specific emails from an inbox based on subject and date criteria:


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


#### **Filter Messages by Custom Keyword Flags**

Create a query to search an IMAP mailbox for emails containing custom keyword flags, specifically "custom1" and "custom2". To construct a query, use the [ImapQueryBuilder](https://reference.aspose.com/email/python-net/aspose.email.clients.imap/imapquerybuilder/#imapquerybuilder-class) class which filters emails when retrieving them from an IMAP server. 

To begin, create an instance of the query builder. Using the [has_flags](https://reference.aspose.com/email/python-net/aspose.email.clients.imap/imapquerybuilder/#methods) method, add conditions to include only those emails that carry the specified IMAP keyword flags. Custom keywords in IMAP, also referred to as user-defined flags, allow users to tag or categorize emails for various purposes, such as marking their status.

The following code snippet illustrates how to create a query to retrieve emails based on custom keyword flags:  

```py

builder = ae.clients.imap.ImapQueryBuilder()
builder.has_flags(ae.clients.imap.ImapMessageFlags.keyword("custom1"))
builder.has_flags(ae.clients.imap.ImapMessageFlags.keyword("custom2"))
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

builder.either(builder.subject.contains("test"), builder.from_address.contains("noreply@host.com"))
```

#### **Applying Case Sensitive Filters**

The API also provides the capability to filter emails from the mailbox based on a case sensitive criteria. The following methods of the [StringComparisonField](https://reference.aspose.com/email/python-net/aspose.email.tools.search/stringcomparisonfield/#stringcomparisonfield-class) class provide the capability to search emails specifying case sensitive flags.  

- **StringComparisonField.contains(value, ignore_case)**
- **StringComparisonField.equals(value, ignore_case)**
- **StringComparisonField.not_contains(value, ignore_case)**
- **StringComparisonField.not_equals(value, ignore_case)**

The following code snippet shows you how to implement this capability into your project:

```py

builder = ae.tools.search.MailQueryBuilder()
builder.from_address.contains("noreply@host.com", True)
```

### **Perform Custom Search Queries**

Create a search query for an IMAP mailbox that filters emails based on a custom Gmail search criterion — specifically, emails that have attachments.

Start by creating an instance of [ImapQueryBuilder](https://reference.aspose.com/email/python-net/aspose.email.clients.imap/imapquerybuilder/#imapquerybuilder-class), which helps build complex IMAP search queries. Use the [custom_search](https://reference.aspose.com/email/python-net/aspose.email.clients.imap/imapquerybuilder/#methods) method to add a Gmail-specific search string to the query builder.

The search string X-GM-RAW "has:attachment" leverages Gmail extended IMAP attribute X-GM-RAW, enabling the use of Gmail powerful webmail search syntax within IMAP queries. Here, the has:attachment operator returns all emails containing attachments.

The following code snippet demonstrates how to filter emails to get all messages with attachments:


```py

builder = ae.clients.imap.ImapQueryBuilder()
builder.custom_search("X-GM-RAW \"has:attachment\"")

mailQuery = builder.get_query()
```

This method enables advanced Gmail-specific filtering to fetch targeted emails.