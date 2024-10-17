---
title: "Operación de Copia de Seguridad y Restauración IMAP"
url: /es/java/imap-backup-and-restore-operation/
weight: 120
type: docs
---

Aspose.Email para Java proporciona la capacidad de hacer copias de seguridad y restaurar mensajes. Para esto, la API proporciona los siguientes métodos.

- [ImapClient.backup](https://reference.aspose.com/email/java/com.aspose.email/imapclient/#backup-com.aspose.email.IConnection-com.aspose.email.ImapFolderInfoCollection-java.io.OutputStream-com.aspose.email.BackupSettings-)
- [ImapClient.restore](https://reference.aspose.com/email/java/com.aspose.email/imapclient/#restore-com.aspose.email.PersonalStorage-com.aspose.email.ImapRestoreSettings-)

Este artículo demuestra cómo hacer copias de seguridad y restaurar mensajes utilizando la clase [ImapClient](https://reference.aspose.com/email/java/com.aspose.email/imapclient/).

## **Copia de Seguridad de Mensajes**

Para hacer copias de seguridad de mensajes, utiliza el método [ImapClient.backup](https://reference.aspose.com/email/java/com.aspose.email/imapclient/#backup-com.aspose.email.ImapFolderInfoCollection-java.lang.String-com.aspose.email.BackupSettings-) como se demuestra en el siguiente fragmento de código.

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

## **Restaurar Mensajes**

Para restaurar mensajes, utiliza el método [ImapClient.restore](https://reference.aspose.com/email/java/com.aspose.email/imapclient/#restore-com.aspose.email.PersonalStorage-com.aspose.email.ImapRestoreSettings-) como se demuestra en el siguiente fragmento de código.

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

## **Operación de Copia de Seguridad y Restauración IMAP con MultiConnection**

Al trabajar con un gran número de mensajes, la operación de copia de seguridad/restauración puede tardar mucho tiempo. Para esto, la API proporciona soporte para múltiples conexiones durante la operación de copia de seguridad y restauración. Para habilitar el modo MultiConnection, establece la propiedad [ImapClient.UseMultiConnection](https://reference.aspose.com/email/java/com.aspose.email/imapclient/#setUseMultiConnection-int-) en [MultiConnectionMode.Enable](https://reference.aspose.com/email/java/com.aspose.email/multiconnectionmode/#Enable). Los siguientes fragmentos de código demuestran la operación de copia de seguridad y restauración con el modo MultiConnection habilitado.

### **Copia de Seguridad de Mensajes con MultiConnection**

Los siguientes fragmentos de código demuestran la operación de copia de seguridad con el modo MultiConnection habilitado.

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

### **Restaurar Mensajes con MultiConnection**

Los siguientes fragmentos de código demuestran la operación de restauración con el modo MultiConnection habilitado.

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