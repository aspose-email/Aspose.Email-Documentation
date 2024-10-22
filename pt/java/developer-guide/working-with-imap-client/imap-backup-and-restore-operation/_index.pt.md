---
title: "Operação de Backup e Restauração IMAP"
url: /pt/java/imap-backup-and-restore-operation/
weight: 120
type: docs
---

Aspose.Email para Java fornece a capacidade de fazer backup e restaurar mensagens. Para isso, a API fornece os seguintes métodos.

- [ImapClient.backup](https://reference.aspose.com/email/java/com.aspose.email/imapclient/#backup-com.aspose.email.IConnection-com.aspose.email.ImapFolderInfoCollection-java.io.OutputStream-com.aspose.email.BackupSettings-)
- [ImapClient.restore](https://reference.aspose.com/email/java/com.aspose.email/imapclient/#restore-com.aspose.email.PersonalStorage-com.aspose.email.ImapRestoreSettings-)

Este artigo demonstra como fazer backup e restaurar mensagens usando a classe [ImapClient](https://reference.aspose.com/email/java/com.aspose.email/imapclient/).

## **Backup de Mensagens**

Para fazer backup de mensagens, use o método [ImapClient.backup](https://reference.aspose.com/email/java/com.aspose.email/imapclient/#backup-com.aspose.email.ImapFolderInfoCollection-java.lang.String-com.aspose.email.BackupSettings-) como demonstrado no seguinte trecho de código.

~~~Java
// Para exemplos completos e arquivos de dados, por favor, acesse https://github.com/aspose-email/Aspose.Email-for-Java
// O caminho para o diretório de arquivos.
String dataDir = "data/";
// Crie uma instância da classe ImapClient
ImapClient imapClient = new ImapClient();

// Especifique o host, nome de usuário e senha, e defina a porta para seu cliente
imapClient.setHost("imap.gmail.com");
imapClient.setUsername("seu.usuario@gmail.com");
imapClient.setPassword("sua.senha");
imapClient.setPort(993);
imapClient.setSecurityOptions(SecurityOptions.Auto);

ImapMailboxInfo mailboxInfo = imapClient.getMailboxInfo();

ImapFolderInfo info = imapClient.getFolderInfo(mailboxInfo.getInbox().getName());
ImapFolderInfoCollection infos = new ImapFolderInfoCollection();
infos.addItem(info);

imapClient.backup(infos, dataDir + "\\ImapBackup.pst", com.aspose.email.BackupSettings.to_BackupSettings(BackupOptions.Recursive));
~~~

## **Restauração de Mensagens**

Para restaurar mensagens, use o [ImapClient.restore](https://reference.aspose.com/email/java/com.aspose.email/imapclient/#restore-com.aspose.email.PersonalStorage-com.aspose.email.ImapRestoreSettings-) como demonstrado no seguinte trecho de código.

~~~Java
// Para exemplos completos e arquivos de dados, por favor, acesse https://github.com/aspose-email/Aspose.Email-for-Java
// O caminho para o diretório de arquivos.
String dataDir = "data/";
// Crie uma instância da classe ImapClient
ImapClient imapClient = new ImapClient();

// Especifique o host, nome de usuário e senha, e defina a porta para seu cliente
imapClient.setHost("imap.gmail.com");
imapClient.setUsername("seu.usuario@gmail.com");
imapClient.setPassword("sua.senha");
imapClient.setPort(993);
imapClient.setSecurityOptions(SecurityOptions.Auto);

ImapRestoreSettings settings = new ImapRestoreSettings();
settings.setRecursive(true);
PersonalStorage pst = PersonalStorage.fromFile(dataDir + "\\ImapBackup.pst");
imapClient.restore(pst, settings);
~~~

## **Operação de Backup e Restauração IMAP com MultiConnection**

Ao trabalhar com um grande número de mensagens, a operação de backup/restauração pode levar muito tempo. Para isso, a API oferece suporte a múltiplas conexões durante a operação de backup e restauração. Para habilitar o modo MultiConnection, defina a propriedade [ImapClient.UseMultiConnection](https://reference.aspose.com/email/java/com.aspose.email/imapclient/#setUseMultiConnection-int-) como [MultiConnectionMode.Enable](https://reference.aspose.com/email/java/com.aspose.email/multiconnectionmode/#Enable). Os seguintes trechos de código demonstram a operação de backup e restauração com o modo MultiConnection habilitado.

### **Backup de Mensagens com MultiConnection**

Os seguintes trechos de código demonstram a operação de backup com o modo MultiConnection habilitado.

~~~Java
// Para exemplos completos e arquivos de dados, por favor, acesse https://github.com/aspose-email/Aspose.Email-for-Java
// O caminho para o diretório de arquivos.
String dataDir = "data/";
// Crie uma instância da classe ImapClient
ImapClient imapClient = new ImapClient();

// Especifique o host, nome de usuário e senha, e defina a porta para seu cliente
imapClient.setHost("imap.gmail.com");
imapClient.setUsername("seu.usuario@gmail.com");
imapClient.setPassword("sua.senha");
imapClient.setPort(993);
imapClient.setSecurityOptions(SecurityOptions.Auto);

imapClient.setUseMultiConnection(MultiConnectionMode.Enable);

ImapMailboxInfo mailboxInfo = imapClient.getMailboxInfo();

ImapFolderInfo info = imapClient.getFolderInfo(mailboxInfo.getInbox().getName());
ImapFolderInfoCollection infos = new ImapFolderInfoCollection();
infos.addItem(info);

imapClient.backup(infos, dataDir + "\\ImapBackup.pst", com.aspose.email.BackupSettings.to_BackupSettings(BackupOptions.Recursive));
~~~ 

### **Restauração de Mensagens com MultiConnection**

Os seguintes trechos de código demonstram a operação de restauração com o modo MultiConnection habilitado.

~~~Java
// Para exemplos completos e arquivos de dados, por favor, acesse https://github.com/aspose-email/Aspose.Email-for-Java
// O caminho para o diretório de arquivos.
String dataDir = "data/";
// Crie uma instância da classe ImapClient
ImapClient imapClient = new ImapClient();

// Especifique o host, nome de usuário e senha, e defina a porta para seu cliente
imapClient.setHost("imap.gmail.com");
imapClient.setUsername("seu.usuario@gmail.com");
imapClient.setPassword("sua.senha");
imapClient.setPort(993);
imapClient.setSecurityOptions(SecurityOptions.Auto);

imapClient.setUseMultiConnection(MultiConnectionMode.Enable);

ImapRestoreSettings settings = new ImapRestoreSettings();
settings.setRecursive(true);
PersonalStorage pst = PersonalStorage.fromFile(dataDir + "\\Outlook.pst");
imapClient.restore(pst, settings);
~~~