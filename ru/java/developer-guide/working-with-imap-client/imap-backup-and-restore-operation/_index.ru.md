---
title: "Операция резервного копирования и восстановления IMAP"
url: /ru/java/imap-backup-and-restore-operation/
weight: 120
type: docs
---

Aspose.Email для Java предоставляет возможность резервного копирования и восстановления сообщений. Для этого API предоставляет следующие методы.

- [ImapClient.backup](https://reference.aspose.com/email/java/com.aspose.email/imapclient/#backup-com.aspose.email.IConnection-com.aspose.email.ImapFolderInfoCollection-java.io.OutputStream-com.aspose.email.BackupSettings-)
- [ImapClient.restore](https://reference.aspose.com/email/java/com.aspose.email/imapclient/#restore-com.aspose.email.PersonalStorage-com.aspose.email.ImapRestoreSettings-)

В этой статье показано, как выполнять резервное копирование и восстановление сообщений с использованием класса [ImapClient](https://reference.aspose.com/email/java/com.aspose.email/imapclient/).

## **Резервное копирование сообщений**

Для резервного копирования сообщений используйте метод [ImapClient.backup](https://reference.aspose.com/email/java/com.aspose.email/imapclient/#backup-com.aspose.email.ImapFolderInfoCollection-java.lang.String-com.aspose.email.BackupSettings-) как показано в следующем фрагменте кода.

~~~Java
// Для получения полных примеров и файлов данных, пожалуйста, посетите https://github.com/aspose-email/Aspose.Email-for-Java
// Путь к каталогу файлов.
String dataDir = "data/";
// Создаем экземпляр класса ImapClient
ImapClient imapClient = new ImapClient();

// Укажите хост, имя пользователя и пароль, а также установите порт для вашего клиента
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

## **Восстановление сообщений**

Для восстановления сообщений используйте метод [ImapClient.restore](https://reference.aspose.com/email/java/com.aspose.email/imapclient/#restore-com.aspose.email.PersonalStorage-com.aspose.email.ImapRestoreSettings-) как показано в следующем фрагменте кода.

~~~Java
// Для получения полных примеров и файлов данных, пожалуйста, посетите https://github.com/aspose-email/Aspose.Email-for-Java
// Путь к каталогу файлов.
String dataDir = "data/";
// Создаем экземпляр класса ImapClient
ImapClient imapClient = new ImapClient();

// Укажите хост, имя пользователя и пароль, а также установите порт для вашего клиента
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

## **Операция резервного копирования и восстановления IMAP с MultiConnection**

При работе с большим количеством сообщений операция резервного копирования/восстановления может занять много времени. Для этого API предоставляет поддержку нескольких соединений во время резервного копирования и восстановления. Чтобы включить режим MultiConnection, установите свойство [ImapClient.UseMultiConnection](https://reference.aspose.com/email/java/com.aspose.email/imapclient/#setUseMultiConnection-int-) в [MultiConnectionMode.Enable](https://reference.aspose.com/email/java/com.aspose.email/multiconnectionmode/#Enable). Следующие фрагменты кода демонстрируют операцию резервного копирования и восстановления с включенным режимом MultiConnection.

### **Резервное копирование сообщений с MultiConnection**

Следующие фрагменты кода демонстрируют операцию резервного копирования с включенным режимом MultiConnection.

~~~Java
// Для получения полных примеров и файлов данных, пожалуйста, посетите https://github.com/aspose-email/Aspose.Email-for-Java
// Путь к каталогу файлов.
String dataDir = "data/";
// Создаем экземпляр класса ImapClient
ImapClient imapClient = new ImapClient();

// Укажите хост, имя пользователя и пароль, а также установите порт для вашего клиента
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

### **Восстановление сообщений с MultiConnection**

Следующие фрагменты кода демонстрируют операцию восстановления с включенным режимом MultiConnection.

~~~Java
// Для получения полных примеров и файлов данных, пожалуйста, посетите https://github.com/aspose-email/Aspose.Email-for-Java
// Путь к каталогу файлов.
String dataDir = "data/";
// Создаем экземпляр класса ImapClient
ImapClient imapClient = new ImapClient();

// Укажите хост, имя пользователя и пароль, а также установите порт для вашего клиента
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