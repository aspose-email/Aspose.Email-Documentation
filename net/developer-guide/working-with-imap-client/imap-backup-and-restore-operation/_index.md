---
title: IMAP Backup and Restore Operation
type: docs
weight: 120
url: /net/imap-backup-and-restore-operation/
---


Aspose.Email for .NET provides the ability to backup and restore messages. For this, the API provides the following methods.

- [ImapClient.Backup](https://reference.aspose.com/email/net/aspose.email.clients.imap/imapclient/methods/backup/index)
- [ImapClient.Restore](https://reference.aspose.com/error/404?path=email/net/aspose.email.clients.imap/imapclient/methods/restore/index)

This article demonstrates how to backup and restore messages using the [ImapClient](https://reference.aspose.com/email/net/aspose.email.clients.imap/imapclient) class.
## **Backup Messages**
To backup messages, use the [ImapClient.Backup](https://reference.aspose.com/email/net/aspose.email.clients.imap/imapclient/methods/backup/index) method as demonstrated in the following code snippet.

{{< gist "aspose-com-gists" "522d47278b8ca448dc1d7eb97193322c" "Examples-CSharp-IMAP-ImapBackupOperation-1.cs" >}}
## **Restore Messages**
To backup messages, use the [ImapClient.Restore](https://reference.aspose.com/error/404?path=email/net/aspose.email.clients.imap/imapclient/methods/restore/index) method as demonstrated in the following code snippet.

{{< gist "aspose-com-gists" "522d47278b8ca448dc1d7eb97193322c" "Examples-CSharp-IMAP-ImapRestoreOperation-1.cs" >}}
## **IMAP Backup and Restore Operation with MultiConnection**
When working with a large number of messages, the backup/restore operation can take a long time. For this, the API provides support for multiple connections during backup and restore operation. To enable the MultiConnection mode, set [ImapClient.UseMultiConnection](https://reference.aspose.com/email/net/aspose.email.clients/emailclient/properties/usemulticonnection) property to [MultiConnectionMode.Enable](https://reference.aspose.com/email/net/aspose.email.clients/multiconnectionmode). The following code snippets demonstrate backup and restore operation with MultiConnection mode enabled.
### **Backup Messages with MultiConnection**
The following code snippets demonstrate backup operation with MultiConnection mode enabled.

{{< gist "aspose-com-gists" "522d47278b8ca448dc1d7eb97193322c" "Examples-CSharp-IMAP-ImapBackupOperationWithMultiConnection-1.cs" >}}
### **Restore Messages with MultiConnection**
The following code snippets demonstrate restore operation with MultiConnection mode enabled.

{{< gist "aspose-com-gists" "522d47278b8ca448dc1d7eb97193322c" "Examples-CSharp-IMAP-ImapRestoreOperationWithMultiConnection-1.cs" >}}
