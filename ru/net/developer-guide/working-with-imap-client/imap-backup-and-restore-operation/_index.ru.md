---
title: "Операция резервного копирования и восстановления IMAP"
url: /ru/net/imap-backup-and-restore-operation/
weight: 120
type: docs
---


Aspose.Email for .NET предоставляет возможность резервного копирования и восстановления сообщений. Для этого API предоставляет следующие методы.

- [ImapClient.Backup](https://reference.aspose.com/email/net/aspose.email.clients.imap/imapclient/backup/#backup/)
- [ImapClient.Restore](https://reference.aspose.com/email/net/aspose.email.clients.imap/imapclient/restore/)

В этой статье показано, как создавать резервные копии и восстанавливать сообщения с помощью [ImapClient](https://reference.aspose.com/email/net/aspose.email.clients.imap/imapclient/) class.

## **Резервные сообщения**

Для резервного копирования сообщений используйте [ImapClient.Backup](https://reference.aspose.com/email/net/aspose.email.clients.imap/imapclient/backup/#backup/) метод, как показано в следующем фрагменте кода.

{{< gist "aspose-com-gists" "522d47278b8ca448dc1d7eb97193322c" "Examples-CSharp-IMAP-ImapBackupOperation-1.cs" >}}

## **Восстановить сообщения**

Для восстановления сообщений используйте [ImapClient.Restore](https://reference.aspose.com/email/net/aspose.email.clients.imap/imapclient/restore/) метод, как показано в следующем фрагменте кода.

{{< gist "aspose-com-gists" "522d47278b8ca448dc1d7eb97193322c" "Examples-CSharp-IMAP-ImapRestoreOperation-1.cs" >}}

## **Операция резервного копирования и восстановления IMAP с помощью MultiConnection**

При работе с большим количеством сообщений операция резервного копирования/восстановления может занять много времени. Для этого API обеспечивает поддержку нескольких подключений во время операции резервного копирования и восстановления. Чтобы включить режим MultiConnection, установите [ImapClient.UseMultiConnection](https://reference.aspose.com/email/net/aspose.email.clients/emailclient/usemulticonnection/) недвижимость для [MultiConnectionMode.Enable](https://reference.aspose.com/email/net/aspose.email.clients/multiconnectionmode/). Следующие фрагменты кода демонстрируют операцию резервного копирования и восстановления при включенном режиме MultiConnection.

### **Резервное копирование сообщений с использованием нескольких подключений**

Следующие фрагменты кода демонстрируют операцию резервного копирования при включенном режиме MultiConnection.

{{< gist "aspose-com-gists" "522d47278b8ca448dc1d7eb97193322c" "Examples-CSharp-IMAP-ImapBackupOperationWithMultiConnection-1.cs" >}}

### **Восстановление сообщений с помощью MultiConnection**

Следующие фрагменты кода демонстрируют операцию восстановления при включенном режиме MultiConnection.

{{< gist "aspose-com-gists" "522d47278b8ca448dc1d7eb97193322c" "Examples-CSharp-IMAP-ImapRestoreOperationWithMultiConnection-1.cs" >}}
