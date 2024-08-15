---
title: "Операция резервного копирования и восстановления IMAP"
url: /ru/java/imap-backup-and-restore-operation/
weight: 120
type: docs
---


Aspose.Email для Java предоставляет возможность резервного копирования и восстановления сообщений. Для этого API предоставляет следующие методы.

- [ImapClient.backup](https://reference.aspose.com/email/java/com.aspose.email/imapclient/#backup-com.aspose.email.IConnection-com.aspose.email.ImapFolderInfoCollection-java.io.OutputStream-com.aspose.email.BackupSettings-)
- [ImapClient.restore](https://reference.aspose.com/email/java/com.aspose.email/imapclient/#restore-com.aspose.email.PersonalStorage-com.aspose.email.ImapRestoreSettings-)

В этой статье показано, как создавать резервные копии и восстанавливать сообщения с помощью [ImapClient](https://reference.aspose.com/email/java/com.aspose.email/imapclient/) class.

## **Резервные сообщения**

Для резервного копирования сообщений используйте [ImapClient.backup](https://reference.aspose.com/email/java/com.aspose.email/imapclient/#backup-com.aspose.email.ImapFolderInfoCollection-java.lang.String-com.aspose.email.BackupSettings-) метод, как показано в следующем фрагменте кода.

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

## **Восстановить сообщения**

Для резервного копирования сообщений используйте [ImapClient.restore](https://reference.aspose.com/email/java/com.aspose.email/imapclient/#restore-com.aspose.email.PersonalStorage-com.aspose.email.ImapRestoreSettings-) метод, как показано в следующем фрагменте кода.

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

## **Операция резервного копирования и восстановления IMAP с помощью MultiConnection**

При работе с большим количеством сообщений операция резервного копирования/восстановления может занять много времени. Для этого API обеспечивает поддержку нескольких подключений во время операции резервного копирования и восстановления. Чтобы включить режим MultiConnection, установите [ImapClient.UseMultiConnection](https://reference.aspose.com/email/java/com.aspose.email/imapclient/#setUseMultiConnection-int-) недвижимость для [MultiConnectionMode.Enable](https://reference.aspose.com/email/java/com.aspose.email/multiconnectionmode/#Enable). Следующие фрагменты кода демонстрируют операцию резервного копирования и восстановления при включенном режиме MultiConnection.

### **Резервное копирование сообщений с использованием нескольких подключений**

Следующие фрагменты кода демонстрируют операцию резервного копирования при включенном режиме MultiConnection.

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

### **Восстановление сообщений с помощью MultiConnection**

Следующие фрагменты кода демонстрируют операцию восстановления при включенном режиме MultiConnection.

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
