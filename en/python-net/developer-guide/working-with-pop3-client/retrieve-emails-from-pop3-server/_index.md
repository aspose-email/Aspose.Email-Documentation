---
title: Retrieving Emails from POP3 Server in Python
ArticleTitle: Retrieving Emails from POP3 Server
type: docs
weight: 40
url: /python-net/retrieve-email-from-pop3-server-python/
---

## **Get Mailbox Information and Message Count**

Aspose.Email API allows you to perform various operations with messages on the server including getting information about the mailbox such as the number of messages and the mailbox size using the [get_mailbox_size()](https://reference.aspose.com/email/python-net/aspose.email.clients.pop3/pop3client/#methods) and [get_mailbox_info()](https://reference.aspose.com/email/python-net/aspose.email.clients.pop3/pop3client/#methods) methods.

- The `get_mailbox_size()` method returns the size of the mailbox in bytes.
- The `get_mailbox_info()` method returns an object of type [Pop3MailBoxInfo](https://reference.aspose.com/email/python-net/aspose.email.clients.pop3/pop3mailboxinfo/).

It is also possible to get the number of messages using the `message_count` property and the size using the `occupied_size`` property. The following sample code shows how to get information about the mailbox. It shows how to:

1. Create a [Pop3Client](https://reference.aspose.com/email/python-net/aspose.email.clients.pop3/pop3client/).
1. Connect to a POP3 server.
1. Get the size of the mailbox.
1. Get mailbox info.
1. Get the number of messages in the mailbox.
1. Get the occupied size.


{{< gist "aspose-email" "356f0e128b9d45a7ee779fc813eb87e5" "Examples-POP3-GettingMailboxInfo-GettingMailboxInfo.py" >}}

### **Get Message Count Only**

The code sample above demonstrates how to get mailbox statistics like size or space used together with the total number of messages in the mailbox. The following code sample will show you how to directly retrieve the number of email messages in the mailbox. This method is simpler and faster if you only need the message count.


{{< gist "aspose-email" "356f0e128b9d45a7ee779fc813eb87e5" "Examples-POP3-GetEmailCountInMailbox-GetEmailCountInMailbox.py" >}}


## **Retrieve Email Headers Only**

Aspose.Email allows developers to access email metadata without downloading full message content. In many scenarios, it's useful to examine only the email headers - such as sender, subject, and received date - to determine whether a message is worth retrieving. This approach reduces server load and improves performance, especially when working with large mailboxes over a POP3 connection.

The following code sample demonstrates how to connect to a POP3 server and retrieve only the headers of a specific message using its sequence number. This lightweight operation helps you make informed decisions about which emails to download or ignore.


{{< gist "aspose-email" "356f0e128b9d45a7ee779fc813eb87e5" "Examples-POP3-RetrievingEmailHeaders-RetrievingEmailHeaders.py" >}}

## **Download Email Messages from Server**

The Aspose.Email [Pop3Client](https://reference.aspose.com/email/python-net/aspose.email.clients.pop3/pop3client/) class provides the capability to retrieve email messages from a POP3 server, and convert them into MailMessage instances. This is made possible through the properties and methods of the [MailMessage](https://reference.aspose.com/email/python-net/aspose.email/mailmessage/) class, which facilitate the manipulation of email content. By using the `fetch_message` method of the [Pop3Client](https://reference.aspose.com/email/python-net/aspose.email.clients.pop3/pop3client/) class, you can get a [MailMessage](https://reference.aspose.com/email/python-net/aspose.email/mailmessage/) instance directly from the POP3 server. The following code snippet demonstrates how to retrieve an entire email message from the server:


{{< gist "aspose-email" "356f0e128b9d45a7ee779fc813eb87e5" "Examples-POP3-RetrievingEmailMessages-RetrievingEmailMessages.py" >}}

## **Retrieve Message Summary by Unique ID**

The API's POP3 Client allows you to retrieve summary information about messages from the server using their unique IDs. This feature provides quick access to essential details about a message without the need to download the entire content first. The following code snippet illustrates how to access message summary information using the Aspose.Email Python API:


{{< gist "aspose-email" "356f0e128b9d45a7ee779fc813eb87e5" "Examples-POP3-RetrieveMessageSummaryInformationUsingUniqueId-RetrieveMessageSummaryInformationUsingUniqueId.py" >}}

## **List Messages Using Multiple Connections**

For heavy-loaded operations Aspose.Email offers the `use_multi_connection` property of the [Pop3Client](https://reference.aspose.com/email/python-net/aspose.email.clients.pop3/pop3client/#pop3client-class) class to use multiple connections while retrieving emails. It's important to note that enabling this mode doesn't always guarantee improved performance. The following code snippet shows you how to establish a connection to a POP3 server, configure the client to allow up to 5 concurrent connections and enable multi-connection mode to retrieve information about the messages stored on the server:

```py
import aspose.email as ae

client = ae.clients.pop3.Pop3Client("host", 995, "username", "password", ae.clients.SecurityOptions.AUTO)

client.connections_quantity = 5
client.use_multi_connection = ae.clients.MultiConnectionMode.ENABLE
message_info_coll = client.list_messages()
```