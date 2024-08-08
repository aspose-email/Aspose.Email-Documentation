---
title: Working with Messages from IMAP Server
type: docs
weight: 70
url: /python-net/working-with-messages-from-imap-server/
---


## **Obtaining the Identification Info for Messages received from a Mailbox**

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


## **Listing MIME Message IDs from Server**
ImapMessageInfo provides the MIME MessageId for message identification without extracting the complete message. The following code snippet shows you how to list MIME messageId.



{{< gist "aspose-email" "356f0e128b9d45a7ee779fc813eb87e5" "Examples-IMAP-ListingMIMEMessageIdInImapMessageInfo-ListingMIMEMessageIdInImapMessageInfo.py" >}}

## **Listing Messages from Server**

The 'list_messages' method  of the [ImapClient](https://reference.aspose.com/email/python-net/aspose.email.clients.imap/imapclient/#imapclient-class) class fetches a list of all messages from the currently selected folder (the "Inbox" in this case). This list contains message metadata objects, which typically include information like message IDs, sequence numbers, UIDs, and possibly summary data such as subject lines or sender information.

The code snippet below demonstrates how to retrieve the messages metadata from the Inbox, and print out the total number of messages it contains: 

```py
import aspose.email as ae

client = ae.clients.imap.ImapClient("imap.domain.com", 993, "user@domain.com", "pwd", ae.clients.SecurityOptions.SSL_IMPLICIT)

client.select_folder("Inbox")

messages = client.list_messages()
print(f"Total Messages: {len(messages)}")
```

## **Listing Messages from Server Recursively**
The IMAP protocol supports listing messages recursively from a mailbox folder. This helps list messages from subfolders of a folder as well. The following code snippet shows you how to list messages recursively.



{{< gist "aspose-email" "356f0e128b9d45a7ee779fc813eb87e5" "Examples-IMAP-ListingMessagesRecursively-ListingMessagesRecursively.py" >}}

## **Listing Messages with MultiConnection**

The [ImapClient](https://reference.aspose.com/email/python-net/aspose.email.clients.imap/imapclient/#imapclient-class) class provides a 'use_multi_connection' property to use multiple connections for heavy loaded operations. You can also set the number of connections in multy-connection mode using the 'connections_quantity' property. The code snippet below demonstrates the use of the multy-connection mode in listing messages:  

```py
import aspose.email as ae

client = ae.clients.imap.ImapClient("imap.domain.com", 993, "user@domain.com", "pwd", ae.clients.SecurityOptions.SSL_IMPLICIT)

client.select_folder("Inbox")
client.connections_quantity = 5
client.use_multi_connection = ae.clients.MultiConnectionMode.ENABLE

message_info_col = client.list_messages(True)
```
*Please note that using this mode does not necessarily have to lead to performance increase.*

## **Get Messages in descending order**

The task is achieved by defining pagination settings for message retrieval. For this purpose use the 'ascending_sorting' property of the [PageSettings](https://reference.aspose.com/email/python-net/aspose.email.clients.imap/pagesettings/#pagesettings-class) class which is a part of the IMAP client's module. Set the 'ascending_sorting' attribute on the PageSettings object to False. This indicates that messages should be sorted in descending order by default during retrieval. The following code snippet shows how to retrieve messages in descending order:

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

## **Fetch Messages from Server and Save to disc**
The ImapClient class can fetch messages from an IMAP server and save the messages in EML format to a local disk. The following steps are required to save the messages to disk:

1. Create an instance of the ImapClient class.
1. Specify hostname, username and password in the ImapClient constructor .
1. Select the folder using SelectFolder() method.
1. Call the ListMessages method to get the ImapMessageInfoCollection object.
1. Iterate through the ImapMessageInfoCollection collection, call the SaveMessage() method and provide the output path and file name.

The following code snippet shows you how to fetch email messages from a server and save them.



{{< gist "aspose-email" "356f0e128b9d45a7ee779fc813eb87e5" "Examples-IMAP-FetchEmailMessageFromServer-FetchEmailMessageFromServer.py" >}}
## **Saving Messages in MSG Format**
In the above example, the emails are saved in EML format. To save emails in MSG format, the ImapClient.FetchMessage() method needs to be called. It returns the message in an instance of the MailMessage class. The MailMessage.Save() method can then be called to save the message to MSG. The following code snippet shows you how to save messages in MSG Format.



{{< gist "aspose-email" "356f0e128b9d45a7ee779fc813eb87e5" "Examples-IMAP-SavingMessageFromIMAPServer-SavingMessageFromIMAPServer.py" >}}

## **Fetch Messages by Sequence Number or Unique ID**

The library allows you to generate two lists of messages, one containing the sequence numbers and another containing the unique IDs of all the messages in the inbox. To fetch messages from the IMAP server by these identifiers, use the 'fetch_messages' method of the [ImapClient](https://reference.aspose.com/email/python-net/aspose.email.clients.imap/imapclient/#imapclient-class) class. The code snipet below demonstrates how to list messages by identifiers:

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

## **Listing Messages with Paging Support**
In scenarios, where the email server contains a large number of messages in mailbox, it is often desired to list or retrieve the messages with paging support. Aspose.Email API's ImapClient lets you retreive the messages from the server with paging support.



{{< gist "aspose-email" "356f0e128b9d45a7ee779fc813eb87e5" "Examples-IMAP-ListingMessagesWithPagingSupport-ListingMessagesWithPagingSupport.py" >}}

## **Listing Message Attachments**

To get information about attachments such as name, size without fetching the attachment data, use the following resources of the library:

- [ImapAttachmentInfo](https://reference.aspose.com/email/python-net/aspose.email.clients.imap/imapattachmentinfo/#imapattachmentinfo-class) class - Represents an attachment information (size, name, media type).

- [ImapAttachmentInfoCollection](https://reference.aspose.com/email/python-net/aspose.email.clients.imap/imapattachmentinfocollection/#imapattachmentinfocollection-class) class - Represents the collection of [ImapAttachmentInfo]((https://reference.aspose.com/email/python-net/aspose.email.clients.imap/imapattachmentinfo/#imapattachmentinfo-class)).

- 'list_attachments(sequence_number)' method of the [ImapClient](https://reference.aspose.com/email/python-net/aspose.email.clients.imap/imapclient/#imapclient-class) class - Gets an iterable or collection of attachment information for the message.

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
## **Getting Folders and Reading Messages Recursively**

[ImapClient](https://reference.aspose.com/email/python-net/aspose.email.clients.imap/imapclient/#imapclient-class) uses the recursive method to list folders and subfolders from the IMAP server. The same method is also used to read and save messages to the local disk in MSG format. Folders and messages are created and saved in the same hierarchical structure as on the IMAP server. The following code snippet shows you how to get folders and messages recursively:

```py
import aspose.email as ae
import os

# Recursive method to get messages from folders and sub-folders
def list_messages_in_folder(folder_info, root_folder, client):
    # Create the folder on disk (same name as on the IMAP server)
    current_folder = os.path.join(root_folder, folder_info.name)
    os.makedirs(current_folder, exist_ok=True)

    # Read the messages from the current folder, if it is selectable
    if folder_info.selectable:
        # Send a status command to get folder info
        folder_info_status = client.get_folder_info(folder_info.name)
        print(
            f"{folder_info_status.name} folder selected. New messages: {folder_info_status.new_message_count}, "
            f"Total messages: {folder_info_status.total_message_count}"
        )

        # Select the current folder and list messages
        client.select_folder(folder_info.name)
        msg_info_coll = client.list_messages()
        print("Listing messages....")
        for msg_info in msg_info_coll:
            # Get subject and other properties of the message
            print("Subject:", msg_info.subject)
            print(
                f"Read: {msg_info.is_read}, Recent: {msg_info.recent}, Answered: {msg_info.answered}"
            )

            # Get rid of characters like ? and :, which should not be included in a file name
            # Save the message in MSG format
            file_name = (
                msg_info.subject.replace(":", " ").replace("?", " ")
                + "-"
                + str(msg_info.sequence_number)
                + ".msg"
            )
            msg = client.fetch_message(msg_info.sequence_number)
            msg.save(
                os.path.join(current_folder, file_name),
                ae.SaveOptions.default_msg_unicode,
            )
        print("============================\n")
    else:
        print(f"{folder_info.name} is not selectable.")

    try:
        # If this folder has sub-folders, call this method recursively to get messages
        folder_info_collection = client.list_folders(folder_info.name)
        for subfolder_info in folder_info_collection:
            list_messages_in_folder(subfolder_info, root_folder, client)
    except Exception:
        pass



client = ae.clients.imap.ImapClient("imap.domain.com", 993, "user@domain.com", "pwd", ae.clients.SecurityOptions.SSL_IMPLICIT)

try:
    # The root folder (which will be created on disk) consists of host and username
    root_folder = f"{client.host}-{client.username}"

    # Create the root folder and list all the folders from the IMAP server
    os.makedirs(root_folder, exist_ok=True)
    folder_info_collection = client.list_folders()
    for folder_info in folder_info_collection:
        # Call the recursive method to read messages and get sub-folders
        list_messages_in_folder(folder_info, root_folder, client)
except Exception as ex:
        print("\n", ex)

print("\nDownloaded messages recursively from IMAP server.")
```


## **Retrieving Extra Parameters as Summary Information**


{{< gist "aspose-email" "356f0e128b9d45a7ee779fc813eb87e5" "Examples-IMAP-RetreiveExtraParametersAsSummaryInformation-RetreiveExtraParametersAsSummaryInformation.py" >}}

## **Getting List-Unsubscribe Header Information**

The "ListUnsubscribe" header is commonly included in the headers of email messages sent by mailing lists or automated email systems. It provides a link or email address that recipients can use to unsubscribe from the mailing list or automated emails. Aspose.Email provides the 'list_unsubscribe' property of the [ImapMessageInfo](https://reference.aspose.com/email/python-net/aspose.email.clients.imap/imapmessageinfo/#imapmessageinfo-class) class to retrieve this header. The code snippet below demonstrates the use of the property and can be used as part of a system to automate the process of unsubscribing from unwanted emails:

```py
import aspose.email as ae

client = ae.clients.imap.ImapClient("imap.domain.com", 993, "user@domain.com", "pwd", ae.clients.SecurityOptions.SSL_IMPLICIT)

message_info_col = client.list_messages()

# Iterate through each message
for imap_message_info in message_info_col:
    print("ListUnsubscribe Header:", imap_message_info.list_unsubscribe)
```
