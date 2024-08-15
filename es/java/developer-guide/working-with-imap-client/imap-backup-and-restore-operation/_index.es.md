---
title: "Operación de respaldo y restauración de IMAP"
url: /es/java/imap-backup-and-restore-operation/
weight: 120
type: docs
---


Aspose.Email para Java ofrece la posibilidad de realizar copias de seguridad y restaurar mensajes. Para ello, la API proporciona los siguientes métodos.

- [ImapClient.backup](https://reference.aspose.com/email/java/com.aspose.email/imapclient/#backup-com.aspose.email.IConnection-com.aspose.email.ImapFolderInfoCollection-java.io.OutputStream-com.aspose.email.BackupSettings-)
- [ImapClient.restore](https://reference.aspose.com/email/java/com.aspose.email/imapclient/#restore-com.aspose.email.PersonalStorage-com.aspose.email.ImapRestoreSettings-)

En este artículo se muestra cómo hacer copias de seguridad y restaurar los mensajes mediante el [ImapClient](https://reference.aspose.com/email/java/com.aspose.email/imapclient/) class.

## **Mensajes de respaldo**

Para hacer copias de seguridad de los mensajes, utilice la [ImapClient.backup](https://reference.aspose.com/email/java/com.aspose.email/imapclient/#backup-com.aspose.email.ImapFolderInfoCollection-java.lang.String-com.aspose.email.BackupSettings-) método como se muestra en el siguiente fragmento de código.

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

## **Restaurar mensajes**

Para hacer copias de seguridad de los mensajes, utilice la [ImapClient.restore](https://reference.aspose.com/email/java/com.aspose.email/imapclient/#restore-com.aspose.email.PersonalStorage-com.aspose.email.ImapRestoreSettings-) método como se muestra en el siguiente fragmento de código.

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

## **Operación de respaldo y restauración de IMAP con MultiConnection**

Cuando se trabaja con una gran cantidad de mensajes, la operación de copia de seguridad o restauración puede tardar mucho tiempo. Para ello, la API admite varias conexiones durante la operación de copia de seguridad y restauración. Para habilitar el modo de conexión múltiple, defina [ImapClient.UseMultiConnection](https://reference.aspose.com/email/java/com.aspose.email/imapclient/#setUseMultiConnection-int-) propiedad a [MultiConnectionMode.Enable](https://reference.aspose.com/email/java/com.aspose.email/multiconnectionmode/#Enable). Los siguientes fragmentos de código muestran las operaciones de copia de seguridad y restauración con el modo MultiConexión habilitado.

### **Mensajes de respaldo con MultiConnection**

En los siguientes fragmentos de código se muestra el funcionamiento de la copia de seguridad con el modo multiconexión activado.

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

### **Restaurar mensajes con MultiConnection**

Los siguientes fragmentos de código muestran la operación de restauración con el modo multiconexión activado.

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
