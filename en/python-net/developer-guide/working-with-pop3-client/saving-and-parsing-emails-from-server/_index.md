---
title: Retrieving Emails from POP3 Server in Python
ArticleTitle: Retrieving Emails from POP3 Server
type: docs
weight: 40
url: /python-net/retrieve-email-from-pop3-server-python/
---

## **Save Emails to Disk without Parsing**

To download email messages from a POP3 server without parsing, you can use the `save_message` method of the Aspose.Email [Pop3Client](https://reference.aspose.com/email/python-net/aspose.email.clients.pop3/pop3client/#pop3client-class) class. The following code snippet illustrates how to save a message using its sequence number, in this case, number 1. The `save_message` method preserves the original EML format without parsing:


{{< gist "aspose-email" "356f0e128b9d45a7ee779fc813eb87e5" "Examples-POP3-SaveToDiscWithoutParsing-SaveToDiscWithoutParsing.py" >}}

## **Parse Messages Before Saving**

You can retrieve a specific email message by using the `fetch_message` method of the [Pop3Client](https://reference.aspose.com/email/python-net/aspose.email.clients.pop3/pop3client/#pop3client-class) class, specifying the desired sequence number for the client object. The following code sample shows how to fetch a particular message and then save it using its subject as the filename by calling the `save` method on the msg object:   

```py
import aspose.email as ae

client = ae.clients.pop3.Pop3Client("host", 995, "username", "password", ae.clients.SecurityOptions.AUTO)

# Fetch the message by its sequence number and Save the message using its subject as the file name
msg = client.fetch_message(1)
msg.save("first-message_out.eml", ae.SaveOptions.default_eml)
```

## **Filter Emails from Server by Criteria**

The Aspose.Email [Pop3Client](https://reference.aspose.com/email/python-net/aspose.email.clients.pop3/pop3client/#pop3client-class) class provides the `list_messages()` method which gets all the messages from a mailbox. To get only messages which match some condition, use the overloaded `list_messages(query)` method which takes [MailQuery](https://reference.aspose.com/email/python-net/aspose.email.tools.search/mailquery/) as an argument. The [MailQuery](https://reference.aspose.com/email/python-net/aspose.email.tools.search/mailquery/) class provides various properties for specifying the query conditions, for example, date, subject, sender, recipient and so on. 

To build the search expression, use the [MailQueryBuilder](https://reference.aspose.com/email/python-net/aspose.email.tools.search/mailquerybuilder/) class. First, define all the necessary conditions and constraints, and then populate the MailQuery object with the query created by the [MailQueryBuilder](https://reference.aspose.com/email/python-net/aspose.email.tools.search/mailquerybuilder/). Pop3Client utilizes this MailQuery object to fetch filtered information from the server.

The following code sample demonstrates how to filter and retrieve emails from a Gmail account based on various criteria including subject, internal date, sender, and recipient. It also shows case-sensitive filtering and demonstrates how to build complex queries efficiently.

1. Establish a connection to the Gmail POP3 server using the [Pop3Client](https://reference.aspose.com/email/python-net/aspose.email.clients.pop3/pop3client/#pop3client-class) class with the specified server address, port, username, and password. Security options are set to AUTO for secure connection.
2. Create an instance of the [MailQueryBuilder](https://reference.aspose.com/email/python-net/aspose.email.tools.search/mailquerybuilder/) to construct the search criteria for filtering emails.
3. Filtering by **Subject**: 
   - Emails containing "Newsletter" in the subject line are specified as a filter condition.
4. Filtering by **Internal Date**:
   - A filter is set for emails received on the current date.
   - An additional filter is added to retrieve emails received within the last week.
5. Filtering by **Sender**:
   - Filters are applied to look for emails from a specific email address (saqib.razzaq@127.0.0.1) and to include emails from a particular domain (SpecificHost.com).
6. Filtering by **Recipient**: 
   - A filter is specified to find emails sent to a specific recipient.
7. **Combine queries** using the OR operator to search for emails that either match a given subject or are sent from a specific address.
8. **Case-Sensitive Filtering**: 
   - A case-sensitive filter for the subject containing "Newsletter" is specified (indicated by the True parameter).
9. Listing Messages: 
   - The list_messages() method is called with the constructed query to retrieve the filtered messages from the mailbox.
10. Finally, print the count of the filtered messages.


{{< gist "aspose-email" "356f0e128b9d45a7ee779fc813eb87e5" "Examples-POP3-FilterMessagesFromMailbox-FilterMessagesFromMailbox.py" >}}


### **Filter Emails by Date**

To fetch messages by a delivery date, use the `internal_date` property as shown in the code sample below:

```py
import aspose.email as ae
from datetime import datetime

builder = ae.tools.search.MailQueryBuilder()
builder.internal_date.on(datetime.now())
```

### **Filter Emails by Date Range**

To fetch messages within a date range, use the same `internal_date` property specifying the date range as shown in the code sample below:

```py
import aspose.email as ae
from datetime import datetime, timedelta

builder = ae.tools.search.MailQueryBuilder()
# Emails that arrived in last 7 days
builder.internal_date.before(datetime.now())
builder.internal_date.since(datetime.today() - timedelta(days=7))
```

### **Filter Emails by Sender**

To fetch messages from a specific sender, use the `from_address` property as shown in the code sample below:

```py
import aspose.email as ae

builder = ae.tools.search.MailQueryBuilder()
builder.from_address.contains("saqib.razzaq@127.0.0.1")
```

### **Filter Emails by Domain**

To fetch messages from a specific domain, use the `from_address` property as shown in the code sample below:

```py
import aspose.email as ae

builder = ae.tools.search.MailQueryBuilder()
builder.from_address.contains("SpecificHost.com")
```

### **Filter Emails by Recipient**

To fetch messages to a specific recipient, use the `to` property as shown in the code sample below:

```py
import aspose.email as ae

builder = ae.tools.search.MailQueryBuilder()
builder.to.contains("recipient")
```

### **Build Complex Search Queries**

Sometimes it is necessary to satisfy more than one query. Aspose.Email makes it possible to combine queries in several statements. Create a [MailQueryBuilder](https://reference.aspose.com/email/python-net/aspose.email.tools.search/mailquerybuilder/#mailquerybuilder-class) object and use its properties to build specific queries.

#### **Combine Queries with AND**

The following code snippet shows you how to combine queries with AND operator:

```py
import aspose.email as ae
from datetime import datetime, timedelta

builder = ae.tools.search.MailQueryBuilder()
builder.internal_date.before(datetime.now())
builder.internal_date.since(datetime.today() - timedelta(days=7))
builder.from_address.contains("SpecificHost.com")
```

#### **Combine Queries with OR**

The following code snippet shows you how to combine queries with OR operator:

```py
import aspose.email as ae

builder = ae.tools.search.MailQueryBuilder()
builder.either(builder.subject.contains("test"), builder.from_address.contains("noreply@host.com"))
```

#### **Apply Case-Sensitive Filters**

The API also provides the capability to filter emails from the mailbox based on a case sensitive criteria. The following methods of the [StringComparisonField](https://reference.aspose.com/email/python-net/aspose.email.tools.search/stringcomparisonfield/#stringcomparisonfield-class) class provide the capability to search emails specifying case sensitive flags:  

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

