---
title: Fetch and List Emails from IMAP Server in Python
ArticleTitle: Fetch and List Emails from IMAP Server
type: docs
weight: 70
url: /python-net/fetch-list-emails-from-imap-server/
---


## **List Messages from Mailbox**

The 'list_messages' method  of the [ImapClient](https://reference.aspose.com/email/python-net/aspose.email.clients.imap/imapclient/#imapclient-class) class fetches a list of all messages from the currently selected folder (the "Inbox" in this case). This list contains message metadata objects, which typically include information like message IDs, sequence numbers, UIDs, and possibly summary data such as subject lines or sender information.

The code snippet below demonstrates how to retrieve the messages metadata from the Inbox, and print out the total number of messages it contains: 

```py
import aspose.email as ae

client = ae.clients.imap.ImapClient("imap.domain.com", 993, "user@domain.com", "pwd", ae.clients.SecurityOptions.SSL_IMPLICIT)

client.select_folder("Inbox")

messages = client.list_messages()
print(f"Total Messages: {len(messages)}")
```


## **List Messages with Paging Support**

In scenarios, where the email server contains a large number of messages in the mailbox, it is often desired to list or retrieve messages with paging support. The Aspose.Email [ImapClient](https://reference.aspose.com/email/python-net/aspose.email.clients.imap/imapclient/#imapclient-class) class allows you to retreive messages from the server with paging support.


{{< gist "aspose-email" "356f0e128b9d45a7ee779fc813eb87e5" "Examples-IMAP-ListingMessagesWithPagingSupport-ListingMessagesWithPagingSupport.py" >}}

## **List Messages Recursively**

The IMAP protocol allows for the recursive listing of messages from a mailbox folder. It makes possible listing messages from its subfolders as well. The code snippet below demonstrates how to list messages recursively:


{{< gist "aspose-email" "356f0e128b9d45a7ee779fc813eb87e5" "Examples-IMAP-ListingMessagesRecursively-ListingMessagesRecursively.py" >}}


## **List MIME Message IDs**

The [ImapMessageInfo](https://reference.aspose.com/email/python-net/aspose.email.clients.imap/imapmessageinfo/) class offers a convenient way to access the MIME MessageId for identifying messages without the need for extracting the entire message content. Below is a code snippet that demonstrates how to list MIME MessageId:


{{< gist "aspose-email" "356f0e128b9d45a7ee779fc813eb87e5" "Examples-IMAP-ListingMIMEMessageIdInImapMessageInfo-ListingMIMEMessageIdInImapMessageInfo.py" >}}


## **List Messages with MultiConnection**

The [ImapClient](https://reference.aspose.com/email/python-net/aspose.email.clients.imap/imapclient/#imapclient-class) class offers a **use_multi_connection** property, which enables the use of multiple connections for operations with heavy loads. Additionally, you can specify the number of connections in multi-connection mode using the **connections_quantity** property. The following code snippet illustrates how to utilize multi-connection mode for listing messages:
  

```py
import aspose.email as ae

client = ae.clients.imap.ImapClient("imap.domain.com", 993, "user@domain.com", "pwd", ae.clients.SecurityOptions.SSL_IMPLICIT)

client.select_folder("Inbox")
client.connections_quantity = 5
client.use_multi_connection = ae.clients.MultiConnectionMode.ENABLE

message_info_col = client.list_messages(True)
```

*Please note that using this mode does not necessarily have to lead to performance increase.*


## **Retrieve Messages by Sequence Number or Unique ID**

The Aspose.Email API allows you to generate two lists of messages, one containing the sequence numbers and another containing the unique IDs of all the messages in the inbox. To fetch messages from the IMAP server by their identifiers, use the **fetch_messages** method of the [ImapClient](https://reference.aspose.com/email/python-net/aspose.email.clients.imap/imapclient/#imapclient-class) class. The code snipet below demonstrates how to list messages by identifiers:


```py
import aspose.email as ae

client = ae.clients.imap.ImapClient("imap.domain.com", 993, "user@domain.com", "pwd", ae.clients.SecurityOptions.SSL_IMPLICIT)

# List messages
message_info_col = client.list_messages()
print("ListMessages Count:", message_info_col.count)

# Get sequence numbers and unique IDs
sequence_number_ar = [mi.sequence_number for mi in message_info_col]
unique_id_ar = [mi.unique_id for mi in message_info_col]

# Fetch messages by sequence number
fetched_messages_by_snum = client.fetch_messages(sequence_number_ar)
print("FetchMessages-sequenceNumberAr Count:", len(fetched_messages_by_snum))

# Fetch messages by UID
fetched_messages_by_uid = client.fetch_messages(unique_id_ar)
print("FetchMessages-uniqueIdAr Count:", len(fetched_messages_by_uid))
```


## **Get Messages in Descending Order**

The task is achieved by defining pagination settings for message retrieval. For this purpose, use the **ascending_sorting** property of the [PageSettings](https://reference.aspose.com/email/python-net/aspose.email.clients.imap/pagesettings/#pagesettings-class) class which is a part of the IMAP client's module. Set the **ascending_sorting** attribute on the [PageSettings](https://reference.aspose.com/email/python-net/aspose.email.clients.imap/pagesettings/#pagesettings-class) object to False. This indicates that messages should be sorted in descending order by default during retrieval. The following code snippet shows how to retrieve messages in descending order:

```py
import aspose.email as ae

client = ae.clients.imap.ImapClient("imap.domain.com", 993, "user@domain.com", "pwd", ae.clients.SecurityOptions.SSL_IMPLICIT)

page_settings = ae.clients.imap.PageSettings
page_settings.ascending_sorting = False
page_info = client.list_messages_by_page(5, page_settings)
messages = page_info.items

for message in messages:
    print(message.subject)
```

## **Fetch Messages from Server and Save to Disk**

The [ImapClient](https://reference.aspose.com/email/python-net/aspose.email.clients.imap/imapclient/) class can fetch messages from an IMAP server and save them in EML format to a local disk. The following steps are required to save the messages to disk:

1. Use the [ImapClient](https://reference.aspose.com/email/python-net/aspose.email.clients.imap/imapclient/) class with necessary parameters (host, port, username, password) to connect to the IMAP server.  
1. Select the desired folder by calling the **select_folder** method (e.g., "Inbox")
1. Retrieve messages by iterating through them using the **list_messages** method.  
1. To save messages, for each message, use the **save_message** method specifying the directory, and appending the unique ID to the file name for uniqueness.

The following code snippet shows you how to fetch email messages from a server and save them:


{{< gist "aspose-email" "356f0e128b9d45a7ee779fc813eb87e5" "Examples-IMAP-FetchEmailMessageFromServer-FetchEmailMessageFromServer.py" >}}

## **Save Messages in MSG Format**

To save emails in MSG format, call the **fetch_message** method of the [ImapClient](https://reference.aspose.com/email/python-net/aspose.email.clients.imap/imapclient/) class. It returns the message in an instance of the [MailMessage](https://reference.aspose.com/email/python-net/aspose.email/mailmessage/) class. The **MailMessage.save()** method can then be called to save the message to MSG. The following code snippet shows you how to save messages in MSG Format.



{{< gist "aspose-email" "356f0e128b9d45a7ee779fc813eb87e5" "Examples-IMAP-SavingMessageFromIMAPServer-SavingMessageFromIMAPServer.py" >}}

## **Retrieve Extra Message Parameters (Summary Info)**

The code snippet below demonstrates how to interact with an email server using the Aspose.Email [ImapClient](https://reference.aspose.com/email/python-net/aspose.email.clients.imap/imapclient/#imapclient-class) to send and manipulate email messages. The code uses the message UID to retrieve summary information with extra parameters ("X-GM-MSGID", "X-GM-THRID"). Similar information is retrieved using the sequence number.


{{< gist "aspose-email" "356f0e128b9d45a7ee779fc813eb87e5" "Examples-IMAP-RetreiveExtraParametersAsSummaryInformation-RetreiveExtraParametersAsSummaryInformation.py" >}}


## **Get List-Unsubscribe Header**

The "ListUnsubscribe" header is commonly included in the headers of email messages sent by mailing lists or automated email systems. It provides a link or email address that recipients can use to unsubscribe from the mailing list or automated emails. Aspose.Email provides the 'list_unsubscribe' property of the [ImapMessageInfo](https://reference.aspose.com/email/python-net/aspose.email.clients.imap/imapmessageinfo/#imapmessageinfo-class) class to retrieve this header. The code snippet below demonstrates the use of the property and can be used as part of a system to automate the process of unsubscribing from unwanted emails:

```py
import aspose.email as ae

client = ae.clients.imap.ImapClient("imap.domain.com", 993, "user@domain.com", "pwd", ae.clients.SecurityOptions.SSL_IMPLICIT)

message_info_col = client.list_messages()

# Iterate through each message
for imap_message_info in message_info_col:
    print("ListUnsubscribe Header:", imap_message_info.list_unsubscribe)
```


## **Get Message Identification Information**

When retrieving and processing email messages, you can fetch the details of the messages using their sequence numbers. 

The following features are used to interact with an IMAP mailbox:

- [Aspose.Email.ImapMessageInfo](https://reference.aspose.com/email/python-net/aspose.email.clients.imap/imapmessageinfo/#imapmessageinfo-class) class - Represents identification information about message in a mailbox.

- [Aspose.Email.ImapMessageInfo.sequence_number](https://reference.aspose.com/email/python-net/aspose.email.clients.imap/imapmessageinfo/#imapmessageinfo-class) property - The sequence number of a message.

- [Aspose.Email.ImapMessageInfo.unique_id](https://reference.aspose.com/email/python-net/aspose.email.clients.imap/imapmessageinfo/#imapmessageinfo-class) property - The unique id of a message.


The code snippet below shows how to obtain identification info about messages:

```py
import aspose.email as ae

client = ae.clients.imap.ImapClient("imap.domain.com", 993, "user@domain.com", "pwd", ae.clients.SecurityOptions.SSL_IMPLICIT)

msg_infos = client.list_messages("INBOX")

for msg_info in msg_infos:
    # fetch by sequence number
    msg = client.fetch_message(msg_info.sequence_number)

    # fetch by unique id
    msg = client.fetch_message(msg_info.unique_id)
```

## **List Attachments from IMAP Email Messages**

To get information about attachments such as name, size without fetching the attachment data, use the following library resources:

- [ImapAttachmentInfo](https://reference.aspose.com/email/python-net/aspose.email.clients.imap/imapattachmentinfo/#imapattachmentinfo-class) class - Represents an attachment information (size, name, media type).

- [ImapAttachmentInfoCollection](https://reference.aspose.com/email/python-net/aspose.email.clients.imap/imapattachmentinfocollection/#imapattachmentinfocollection-class) class - Represents the collection of [ImapAttachmentInfo]((https://reference.aspose.com/email/python-net/aspose.email.clients.imap/imapattachmentinfo/#imapattachmentinfo-class)).

- **list_attachments(sequence_number)** method of the [ImapClient](https://reference.aspose.com/email/python-net/aspose.email.clients.imap/imapclient/#imapclient-class) class - Gets an iterable or collection of attachment information for the message.

The code sample below demonstrates how to list attachments for each email message using the Aspose.Email [ImapClient](https://reference.aspose.com/email/python-net/aspose.email.clients.imap/imapclient/#imapclient-class):

```py
# List messages
message_info_col = client.list_messages()

# Iterate through each message
for message_info in message_info_col:
    print(f"Attachments for message with sequence number {message_info.sequence_number}:")

    # List attachments for the current message
    attachment_info_col = client.list_attachments(message_info.sequence_number)

    # Iterate through each attachment
    for attachment_info in attachment_info_col:
        print(f"Attachment: {attachment_info.name} (size: {attachment_info.size})")
```