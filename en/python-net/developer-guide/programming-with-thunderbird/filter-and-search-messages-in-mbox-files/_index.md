---
title: Search and Filter MBOX Emails in Python
ArticleTitle: Retrieve Filtered Messages from MBOX Files in Python
type: docs
weight: 30
url: /python-net/filter-mbox-messages/
---

## **Filter MBOX Messages by Subject and Date**

Aspose.Email for Python via .NET provides the ability to filter or search messages within MBOX files using a query. The following methods allow you to retrieve only those messages that match specific criteria:

- [EnumerateMessages(MailQuery query)](https://reference.aspose.com/email/python-net/aspose.email.storage.mbox/mboxstoragereader/#methods) - returns an enumerable collection of [MailMessage](https://reference.aspose.com/email/python-net/aspose.email/mailmessage/#mailmessage-class) instances that match the specified query.
- [EnumerateMessageInfo(MailQuery query)](https://reference.aspose.com/email/python-net/aspose.email.storage.mbox/mboxstoragereader/#methods) - returns an enumerable collection of [MboxMessageInfo](https://reference.aspose.com/email/python-net/aspose.email.storage.mbox/mboxmessageinfo/) instances that match the specified query.

The code sample below will show you how to use these methods in message filtering:

```py
import datetime
from aspose.email.storage.mbox import MboxStorageReader, MboxLoadOptions
from aspose.email import MailQueryBuilder

# Create an MBOX reader with load options
reader = MboxStorageReader.create_reader("input.mbox", MboxLoadOptions())

# Build the mail query
mqb = MailQueryBuilder()
mqb.subject.contains("Project Update")
mqb.sent_date.before(datetime.date.today())

# Iterate over matching messages
for message in reader.enumerate_messages(mqb.get_query()):
    print("Subject:", message.subject)
```

## **Paginated Retrieval of MBOX Messages**

Aspose.Email for Python via .NET supports paginated reading of MBOX files, enabling efficient processing of large email archives. Instead of loading the entire message set into memory, you can retrieve messages in smaller, manageable batches. This is especially useful when dealing with very large archive files, helping to reduce memory usage and improve performance during processing.

The following methods can be used for paginated MBOX message retrieval:

- [enumerate_messages(start_index, count)](https://reference.aspose.com/email/python-net/aspose.email.storage.mbox/mboxstoragereader/#methods) - Retrieves a specific number of [MailMessage](https://reference.aspose.com/email/python-net/aspose.email/mailmessage/#mailmessage-class) instances. 

- [enumerate_message_info(start_index, count)](https://reference.aspose.com/email/python-net/aspose.email.storage.mbox/mboxstoragereader/#methods) - Retrieves corresponding [MboxMessageInfo](https://reference.aspose.com/email/python-net/aspose.email.storage.mbox/mboxmessageinfo/) objects.

The following code sample demonstrates how to read and retrieve messages from an MBOX file in manageable chunks using the Aspose.Email library:

```py
from aspose.email.storage.mbox import MboxStorageReader, MboxLoadOptions

# Initialize MBOX reader with load options
reader = MboxStorageReader.create_reader("input.mbox", MboxLoadOptions())

# Define pagination parameters
start_index = 0
count = 10  # Retrieve messages in batches of 10

# Enumerate and display messages in the current batch
for message in reader.enumerate_messages(start_index, count):
    print("Subject:", message.subject)
```