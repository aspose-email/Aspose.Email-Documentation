---
title: Backup and Restore IMAP Messages in Python
ArticleTitle: Backup and Restore IMAP Messages in Python
type: docs
weight: 120
url: /python-net/backup-and-restore-imap-messages-python/
---


Aspose.Email for Python offers methods of the [ImapClient](https://reference.aspose.com/email/python-net/aspose.email.clients.imap/imapclient/#imapclient-class) class for managing email messages over the IMAP protocol: 

- **'backup'** method
- **'restore'** method

This article demonstrates how to use the [ImapClient](https://reference.aspose.com/email/python-net/aspose.email.clients.imap/imapclient/#imapclient-class) class and its methods to back up and restore email messages to and from a PST file. It also covers how to improve performance for large mailboxes using multi-connection mode.

## **Backup IMAP Messages**

To create a backup of email messages from an IMAP server, use the `backup` method of the [ImapClient](https://reference.aspose.com/email/python-net/aspose.email.clients.imap/imapclient/#imapclient-class) class. The following code sample shows how to back up the Inbox folder to a .pst file: 

```py
import aspose.email as ae

# Create an instance of the ImapClient class
imap_client = ae.clients.imap.ImapClient()

# Specify host, username, password, and set port for your client
imap_client.host = "imap.gmail.com"
imap_client.username = username
imap_client.password = password
imap_client.port = 993
imap_client.security_options = ae.clients.SecurityOptions.AUTO

# Get mailbox info
mailbox_info = imap_client.mailbox_info

# Get folder info for the Inbox folder
inbox_info = imap_client.get_folder_info(mailbox_info.inbox.name)

# Create an ImapFolderInfoCollection and add the Inbox folder info
infos = ae.clients.imap.ImapFolderInfoCollection()
infos.add(inbox_info)

# Specify the path to the directory
data_dir = "path/to/your/data/directory"

# Perform the backup operation
settings = ae.clients.imap.BackupSettings
settings.execute_recursively = True
imap_client.backup(infos, data_dir + "\\ImapBackup.pst", settings)
```

## **Restore IMAP Messages**

To restore messages from a .pst file back to an IMAP server, use the `restore` method of the [ImapClient](https://reference.aspose.com/email/python-net/aspose.email.clients.imap/imapclient/#imapclient-class) class:

```py
import aspose.email as ae

# Create an instance of the ImapClient class
imap_client = ae.clients.imap.ImapClient()

# Specify host, username, password, and set port for your client
imap_client.host = "imap.gmail.com"
imap_client.username = username
imap_client.password = password
imap_client.port = 993
imap_client.security_options = ae.clients.SecurityOptions.Auto

# Create RestoreSettings with Recursive set to true
settings = ae.clients.imap.RestoreSettings()
settings.recursive = True

# Specify the path to the directory
data_dir = "path/to/your/data/directory"

# Load the PST file
pst = ae.storage.pst.PersonalStorage.from_file(data_dir + "\\ImapBackup.pst")

# Perform the restore operation
imap_client.restore(pst, settings)
```

## **Boost Performance with Multi-Connection Mode**

For tasks that involve a large amount of data or numerous email messages, Aspose.Email offers the 'use_multi_connection' property of the [ImapClient](https://reference.aspose.com/email/python-net/aspose.email.clients.imap/imapclient/#imapclient-class) class to optimize the performance of the operations by allowing the client to open multiple connections to the email server simultaneously. When [MultiConnectionMode](https://reference.aspose.com/email/python-net/aspose.email.clients/multiconnectionmode/#multiconnectionmode-enumeration) is enabled, the IMAP client can carry out various tasks (such as fetching emails, synchronizing folders, and backing up data) in parallel across different connections. This can lead to a significant reduction in the overall time required to complete operations. The following code snippets demonstrate how to enable [MultiConnection](https://reference.aspose.com/email/python-net/aspose.email.clients/multiconnectionmode/#multiconnectionmode-enumeration) mode for backup and restore operations.

> **Note:** The use of multiple connections may be subjected to limitations and policies set by the email server. Some servers may impose restrictions on the number of concurrent connections that can be made from a single user account to avoid overloading the server. Always check the terms of service or policies of the email provider to ensure compliance with their usage guidelines before enabling MultiConnectionMode.

### **Backup Messages with MultiConnection Enabled**

The following code snippet demonstrates how to perform a backup operation with MultiConnection mode enabled:

```py
import aspose.email as ae

# Create an instance of the ImapClient class
imap_client = ae.clients.imap.ImapClient()

# Specify host, username, password, and set port for your client
imap_client.host = "imap.gmail.com"
imap_client.username = username
imap_client.password = password
imap_client.port = 993
imap_client.security_options = ae.clients.SecurityOptions.Auto

# Enable MultiConnectionMode
imap_client.use_multi_connection = ae.clients.MultiConnectionMode.ENABLE

# Get mailbox info
mailbox_info = imap_client.mailbox_info

# Get folder info for the Inbox folder
inbox_info = imap_client.get_folder_info(mailbox_info.inbox.name)

# Create an ImapFolderInfoCollection and add the Inbox folder info
infos = ae.clients.imap.ImapFolderInfoCollection()
infos.add(inbox_info)

# Specify the path to the directory
data_dir = "path/to/your/data/directory"

# Perform the backup operation
settings = ae.clients.imap.BackupSettings
settings.execute_recursively = True
imap_client.backup(infos, data_dir + "\\ImapBackup.pst", settings)
```

### **Restore Messages with MultiConnection**

The following code snippet demonstrates how to perform a restore operation with MultiConnection mode enabled.

```py
import aspose.email as ae

# Create an instance of the ImapClient class
imap_client = ae.clients.imap.ImapClient()

# Specify host, username, password, and set port for your client
imap_client.host = "imap.gmail.com"
imap_client.username = username
imap_client.password = password
imap_client.port = 993
imap_client.security_options = ae.clients.SecurityOptions.Auto

# Enable MultiConnectionMode
imap_client.use_multi_connection = ae.clients.MultiConnectionMode.ENABLE

# Create RestoreSettings with Recursive set to true
settings = ae.clients.imap.RestoreSettings()
settings.recursive = True

# Specify the path to the directory
data_dir = "path/to/your/data/directory"

# Load the PST file
pst = ae.storage.pst.PersonalStorage.from_file(data_dir + "\\Outlook.pst")

# Perform the restore operation
imap_client.restore(pst, settings)
```
