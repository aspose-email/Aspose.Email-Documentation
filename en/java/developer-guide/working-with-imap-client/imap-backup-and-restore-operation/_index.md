---
title: IMAP Backup and Restore Operation
ArticleTitle: IMAP Backup and Restore Operation
type: docs
weight: 120
url: /java/imap-backup-and-restore-operation/
---


Aspose.Email for Java provides the ability to backup and restore messages. For this, the API provides the following methods.

- [ImapClient.backup](https://reference.aspose.com/email/java/com.aspose.email/imapclient/#backup-com.aspose.email.IConnection-com.aspose.email.ImapFolderInfoCollection-java.io.OutputStream-com.aspose.email.BackupSettings-)
- [ImapClient.restore](https://reference.aspose.com/email/java/com.aspose.email/imapclient/#restore-com.aspose.email.PersonalStorage-com.aspose.email.ImapRestoreSettings-)

This article demonstrates how to backup and restore messages using the [ImapClient](https://reference.aspose.com/email/java/com.aspose.email/imapclient/) class.

## **Backup Messages**

To backup messages, use the [ImapClient.backup](https://reference.aspose.com/email/java/com.aspose.email/imapclient/#backup-com.aspose.email.ImapFolderInfoCollection-java.lang.String-com.aspose.email.BackupSettings-) method as demonstrated in the following code snippet.

~~~Java
// For complete examples and data files, please go to https://github.com/aspose-email/Aspose.Email-for-Java
// The path to the File directory.
String dataDir = "data/";
// Create an instance of the ImapClient class
ImapClient imapClient = new ImapClient();

// Specify host, username and password, and set port for your client
imapClient.setHost("imap.gmail.com");
imapClient.setUsername("your.username@gmail.com");
imapClient.setPassword("your.password");
imapClient.setPort(993);
imapClient.setSecurityOptions(SecurityOptions.Auto);

ImapMailboxInfo mailboxInfo = imapClient.getMailboxInfo();

ImapFolderInfo info = imapClient.getFolderInfo(mailboxInfo.getInbox().getName());
ImapFolderInfoCollection infos = new ImapFolderInfoCollection();
infos.addItem(info);

imapClient.backup(infos, dataDir + "\\ImapBackup.pst", com.aspose.email.BackupSettings.to_BackupSettings(BackupOptions.Recursive));
~~~

## **Restore Messages**

To backup messages, use the [ImapClient.restore](https://reference.aspose.com/email/java/com.aspose.email/imapclient/#restore-com.aspose.email.PersonalStorage-com.aspose.email.ImapRestoreSettings-) method as demonstrated in the following code snippet.

~~~Java
// For complete examples and data files, please go to https://github.com/aspose-email/Aspose.Email-for-Java
// The path to the File directory.
String dataDir = "data/";
// Create an instance of the ImapClient class
ImapClient imapClient = new ImapClient();

// Specify host, username and password, and set port for your client
imapClient.setHost("imap.gmail.com");
imapClient.setUsername("your.username@gmail.com");
imapClient.setPassword("your.password");
imapClient.setPort(993);
imapClient.setSecurityOptions(SecurityOptions.Auto);

ImapRestoreSettings settings = new ImapRestoreSettings();
settings.setRecursive(true);
PersonalStorage pst = PersonalStorage.fromFile(dataDir + "\\ImapBackup.pst");
imapClient.restore(pst, settings);
~~~

## **IMAP Backup and Restore Operation with MultiConnection**

When working with a large number of messages, the backup/restore operation can take a long time. For this, the API provides support for multiple connections during backup and restore operation. To enable the MultiConnection mode, set [ImapClient.UseMultiConnection](https://reference.aspose.com/email/java/com.aspose.email/imapclient/#setUseMultiConnection-int-) property to [MultiConnectionMode.Enable](https://reference.aspose.com/email/java/com.aspose.email/multiconnectionmode/#Enable). The following code snippets demonstrate backup and restore operation with MultiConnection mode enabled.

### **Backup Messages with MultiConnection**

The following code snippets demonstrate backup operation with MultiConnection mode enabled.

~~~Java
// For complete examples and data files, please go to https://github.com/aspose-email/Aspose.Email-for-Java
// The path to the File directory.
String dataDir = "data/";
// Create an instance of the ImapClient class
ImapClient imapClient = new ImapClient();

// Specify host, username and password, and set port for your client
imapClient.setHost("imap.gmail.com");
imapClient.setUsername("your.username@gmail.com");
imapClient.setPassword("your.password");
imapClient.setPort(993);
imapClient.setSecurityOptions(SecurityOptions.Auto);

imapClient.setUseMultiConnection(MultiConnectionMode.Enable);

ImapMailboxInfo mailboxInfo = imapClient.getMailboxInfo();

ImapFolderInfo info = imapClient.getFolderInfo(mailboxInfo.getInbox().getName());
ImapFolderInfoCollection infos = new ImapFolderInfoCollection();
infos.addItem(info);

imapClient.backup(infos, dataDir + "\\ImapBackup.pst", com.aspose.email.BackupSettings.to_BackupSettings(BackupOptions.Recursive));
~~~

### **Restore Messages with MultiConnection**

The following code snippets demonstrate restore operation with MultiConnection mode enabled.

~~~Java
// For complete examples and data files, please go to https://github.com/aspose-email/Aspose.Email-for-Java
// The path to the File directory.
String dataDir = "data/";
// Create an instance of the ImapClient class
ImapClient imapClient = new ImapClient();

// Specify host, username and password, and set port for your client
imapClient.setHost("imap.gmail.com");
imapClient.setUsername("your.username@gmail.com");
imapClient.setPassword("your.password");
imapClient.setPort(993);
imapClient.setSecurityOptions(SecurityOptions.Auto);

imapClient.setUseMultiConnection(MultiConnectionMode.Enable);

ImapRestoreSettings settings = new ImapRestoreSettings();
settings.setRecursive(true);
PersonalStorage pst = PersonalStorage.fromFile(dataDir + "\\Outlook.pst");
imapClient.restore(pst, settings);
~~~
