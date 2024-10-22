---
title: "Operação de Backup e Restauração IMAP"
url: /pt/net/imap-backup-and-restore-operation/
weight: 120
type: docs
---

Aspose.Email para .NET fornece a capacidade de fazer backup e restaurar mensagens. Para isso, a API fornece os seguintes métodos.

- [ImapClient.Backup](https://reference.aspose.com/email/net/aspose.email.clients.imap/imapclient/backup/#backup/)
- [ImapClient.Restore](https://reference.aspose.com/email/net/aspose.email.clients.imap/imapclient/restore/)

Este artigo demonstra como fazer backup e restaurar mensagens usando a classe [ImapClient](https://reference.aspose.com/email/net/aspose.email.clients.imap/imapclient/).

## **Fazer Backup de Mensagens**

Para fazer backup de mensagens, use o método [ImapClient.Backup](https://reference.aspose.com/email/net/aspose.email.clients.imap/imapclient/backup/#backup/) como demonstrado no seguinte trecho de código.

{{< gist "aspose-com-gists" "522d47278b8ca448dc1d7eb97193322c" "Examples-CSharp-IMAP-ImapBackupOperation-1.cs" >}}

## **Restaurar Mensagens**

Para restaurar mensagens, use o método [ImapClient.Restore](https://reference.aspose.com/email/net/aspose.email.clients.imap/imapclient/restore/) como demonstrado no seguinte trecho de código.

{{< gist "aspose-com-gists" "522d47278b8ca448dc1d7eb97193322c" "Examples-CSharp-IMAP-ImapRestoreOperation-1.cs" >}}

## **Operação de Backup e Restauração IMAP com MultiConnection**

Ao trabalhar com um grande número de mensagens, a operação de backup/restauração pode demorar muito tempo. Para isso, a API fornece suporte para múltiplas conexões durante a operação de backup e restauração. Para ativar o modo MultiConnection, defina a propriedade [ImapClient.UseMultiConnection](https://reference.aspose.com/email/net/aspose.email.clients/emailclient/usemulticonnection/) como [MultiConnectionMode.Enable](https://reference.aspose.com/email/net/aspose.email.clients/multiconnectionmode/). Os seguintes trechos de código demonstram a operação de backup e restauração com o modo MultiConnection ativado.

### **Fazer Backup de Mensagens com MultiConnection**

Os seguintes trechos de código demonstram a operação de backup com o modo MultiConnection ativado.

{{< gist "aspose-com-gists" "522d47278b8ca448dc1d7eb97193322c" "Examples-CSharp-IMAP-ImapBackupOperationWithMultiConnection-1.cs" >}}

### **Restaurar Mensagens com MultiConnection**

Os seguintes trechos de código demonstram a operação de restauração com o modo MultiConnection ativado.

{{< gist "aspose-com-gists" "522d47278b8ca448dc1d7eb97193322c" "Examples-CSharp-IMAP-ImapRestoreOperationWithMultiConnection-1.cs" >}}