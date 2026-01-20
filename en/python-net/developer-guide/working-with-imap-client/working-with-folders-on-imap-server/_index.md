---
title: Manage IMAP Folders in Python with Aspose.Email
ArticleTitle: Manage Folders on IMAP Server in Python
type: docs
weight: 50
url: /python-net/manage-imap-folders-python/
---


## **List IMAP Folders**

Retrieving folder information from an IMAP server is simple with Aspose.Email. Follow the steps below to retrieve and work with folder details:

1. Use the *list_folders()* method from the Aspose.Email [ImapClient](https://reference.aspose.com/email/python-net/aspose.email.clients.imap/imapclient/#methods) class. This method returns an instance of [ImapFolderInfoCollection](https://reference.aspose.com/email/python-net/aspose.email.clients.imap/imapfolderinfocollection/), which contains details about all folders.
2. Loop through the [ImapFolderInfoCollection](https://reference.aspose.com/email/python-net/aspose.email.clients.imap/imapfolderinfocollection/) object to access information about individual folders.
3. Retrieve subfolders (optional). The *list_folders()* method is overloaded. You can pass a folder name as a parameter to retrieve a collection of subfolders for the specified folder.

The following code snippet demonstrates how to retrieve folder information from an IMAP server using the Aspose.Email method:

{{< gist "aspose-email" "356f0e128b9d45a7ee779fc813eb87e5" "Examples-IMAP-GettingFoldersInformation-GettingFoldersInformation.py" >}}

## **Rename and Delete Folders**

Aspose.Email provides methods of the [ImapClient](https://reference.aspose.com/email/python-net/aspose.email.clients.imap/imapclient/#imapclient-class) class for managing folders on an email server via IMAP:

- *delete_folder* method - permanently removes the folder and all of the messages contained within it.
- *rename_folder* method - changes the name of the folder without altering the contents within it.

The code snippet below shows how to delete or rename folders on the IMAP server programmatically:

```py
# Delete a folder and Rename a folder
client.delete_folder("foldername")
client.rename_folder("foldername", "newfoldername")
```

## **Create and Add Messages to Specific Folders**

With Aspose.Email API, you can use the [MailMessage](https://reference.aspose.com/email/python-net/aspose.email/mailmessage/) and [ImapClient](https://reference.aspose.com/email/python-net/aspose.email.clients.imap/imapclient/) classes to add a new message to a folder. First, create a [MailMessage](https://reference.aspose.com/email/python-net/aspose.email/mailmessage/) object by specifying the subject, sender, and recipient. Then, subscribe to a folder and add the message to it. The code snippet below demonstrates how to add a new message to a folder:

1. Initialize the IMAP client using the [ImapClient](https://reference.aspose.com/email/python-net/aspose.email.clients.imap/imapclient/) class to connect to your email server. Provide the server address, port, username, and password. 
2. Select the target folder where you want to add the new message, such as "Inbox", using the *select_folder* method.
3. Create a new email using the [MailMessage](https://reference.aspose.com/email/python-net/aspose.email/mailmessage/) class. Specify the sender, recipient, subject, and message content.
4. Subscribe to the folder using the *subscribe_folder* method with the folder's name.
5. Add the newly created message to the selected folder using the *append_message* method, specifying the folder's name and the message object.

{{< gist "aspose-email" "356f0e128b9d45a7ee779fc813eb87e5" "Examples-IMAP-AppendMessageToFolder-AppendMessagetoFolder.py" >}}


## **Move Messages between Folders**

Aspose.Email for .NET allows to move messages from one mailbox folder to another using the [ImapClient](https://reference.aspose.com/email/python-net/aspose.email.clients.imap/imapclient/#imapclient-class) API. The *move_message* method uses the message's unique id and destination folder name for moving a message to the destination folder. The following code snippet shows you how to move messages between folders:


{{< gist "aspose-email" "356f0e128b9d45a7ee779fc813eb87e5" "Examples-IMAP-MoveMessageToAnotherFolder-MoveMessageToAnotherFolder.py" >}}

## **Copy Messages Between Folders**

The Aspose.Email API enables you to copy messages from one mailbox folder to another effortlessly. You can copy a single message or multiple messages using the *copy_message* and *copy_messages* methods. The *copy_messages* method allows you to transfer multiple messages from a source folder to a destination folder within the mailbox. Below is a code snippet demonstrating how to copy messages between folders: 


{{< gist "aspose-email" "356f0e128b9d45a7ee779fc813eb87e5" "Examples-IMAP-CopyMessageToAnotherFolder-CopyMessageToAnotherFolder.py" >}}


## **Work with Special-Use Mailbox Folders**

Special-use mailboxes are predefined folders in an email system designed for handling specific types of messages, such as Sent, Drafts, Junk, Trash, and Archive. The Aspose.Email library simplifies access to these mailboxes by associating attributes with their roles and purposes. This allows clients to automatically discover and display these folders without requiring any user intervention.

The following code snippet demonstrates how to retrieve information about key special-use mailboxes (Inbox, Drafts, Junk, Sent, and Trash) using the properties of the [ImapMailBoxInfo](https://reference.aspose.com/email/python-net/aspose.email.clients.imap/imapmailboxinfo/#imapmailboxinfo-class) class and print the details:


```py
import aspose.email as ae

client = ae.clients.imap.ImapClient("imap.domain.com", 993, "user@domain.com", "pwd", ae.clients.SecurityOptions.SSL_IMPLICIT)

mailboxInfo = client.mailbox_info
print(mailboxInfo.inbox)
print(mailboxInfo.draft_messages)
print(mailboxInfo.junk_messages)
print(mailboxInfo.sent_messages)
print(mailboxInfo.trash)
```

## **Access Folders and Read Messages Recursively**

[ImapClient](https://reference.aspose.com/email/python-net/aspose.email.clients.imap/imapclient/#imapclient-class) uses the recursive method to list folders and subfolders from the IMAP server. This method is also used to read and save messages to the local disk in MSG format. Both folders and messages are created and saved in the same hierarchical structure as they appear on the IMAP server.  Below is a code snippet demonstrating how to retrieve folders and messages recursively:

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

## **Use MultiConnection for Batch Folder Operations**

Aspose.Email makes it possible to configure the client to establish multiple simultaneous connections to the IMAP server. It does not necessarily increase the performance, but it's a reliable solution for concurrent operations. This is particularly useful if the client needs to perform multiple tasks at the same time, such as fetching different email folders, synchronizing large amounts of data, or processing multiple messages simultaneously. 

The code snippet below shows how to establish multiple connections to the IMAP server while uploading a collection of email messages using the 'append_messages' method of the [ImapClient](https://reference.aspose.com/email/python-net/aspose.email.clients.imap/imapclient/#imapclient-class) class: 

```py
import aspose.email as ae

client = ae.clients.imap.ImapClient("imap.domain.com", 993, "user@domain.com", "pwd", ae.clients.SecurityOptions.SSL_IMPLICIT)

client.connections_quantity = 5
client.use_multi_connection = ae.clients.MultiConnectionMode.ENABLE
client.append_messages(messages)
```