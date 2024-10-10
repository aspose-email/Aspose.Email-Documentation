---
title: "Операция резервного копирования и восстановления IMAP"
url: /ru/net/imap-backup-and-restore-operation/
weight: 120
type: docs
---


Aspose.Email для .NET предоставляет возможность резервного копирования и восстановления сообщений. Для этого API предоставляет следующие методы.

- [ImapClient.Backup](https://reference.aspose.com/email/net/aspose.email.clients.imap/imapclient/backup/#backup/)
- [ImapClient.Restore](https://reference.aspose.com/email/net/aspose.email.clients.imap/imapclient/restore/)

В этой статье демонстрируется, как резервировать и восстанавливать сообщения с помощью класса [ImapClient](https://reference.aspose.com/email/net/aspose.email.clients.imap/imapclient/).

## **Резервное копирование сообщений**

Для резервного копирования сообщений используйте метод [ImapClient.Backup](https://reference.aspose.com/email/net/aspose.email.clients.imap/imapclient/backup/#backup/) как показано в следующем фрагменте кода.

{{< gist "aspose-com-gists" "522d47278b8ca448dc1d7eb97193322c" "Examples-CSharp-IMAP-ImapBackupOperation-1.cs" >}}

## **Восстановление сообщений**

Для восстановления сообщений используйте метод [ImapClient.Restore](https://reference.aspose.com/email/net/aspose.email.clients.imap/imapclient/restore/) как показано в следующем фрагменте кода.

{{< gist "aspose-com-gists" "522d47278b8ca448dc1d7eb97193322c" "Examples-CSharp-IMAP-ImapRestoreOperation-1.cs" >}}

## **Операция резервного копирования и восстановления IMAP с использованием MultiConnection**

При работе с большим количеством сообщений операция резервного копирования/восстановления может занять много времени. Для этого API предоставляет поддержку нескольких соединений во время операции резервного копирования и восстановления. Чтобы включить режим MultiConnection, установите свойство [ImapClient.UseMultiConnection](https://reference.aspose.com/email/net/aspose.email.clients/emailclient/usemulticonnection/) в [MultiConnectionMode.Enable](https://reference.aspose.com/email/net/aspose.email.clients/multiconnectionmode/). Следующие фрагменты кода демонстрируют операцию резервного копирования и восстановления с включенным режимом MultiConnection.

### **Резервное копирование сообщений с использованием MultiConnection**

Следующие фрагменты кода демонстрируют операцию резервного копирования с включенным режимом MultiConnection.

{{< gist "aspose-com-gists" "522d47278b8ca448dc1d7eb97193322c" "Examples-CSharp-IMAP-ImapBackupOperationWithMultiConnection-1.cs" >}}

### **Восстановление сообщений с использованием MultiConnection**

Следующие фрагменты кода демонстрируют операцию восстановления с включенным режимом MultiConnection.

{{< gist "aspose-com-gists" "522d47278b8ca448dc1d7eb97193322c" "Examples-CSharp-IMAP-ImapRestoreOperationWithMultiConnection-1.cs" >}}