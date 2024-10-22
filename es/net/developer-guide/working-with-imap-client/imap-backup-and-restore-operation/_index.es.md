---
title: "Operación de Respaldo y Restauración de IMAP"
url: /es/net/imap-backup-and-restore-operation/
weight: 120
type: docs
---


Aspose.Email para .NET proporciona la capacidad de respaldar y restaurar mensajes. Para esto, la API proporciona los siguientes métodos.

- [ImapClient.Backup](https://reference.aspose.com/email/net/aspose.email.clients.imap/imapclient/backup/#backup/)
- [ImapClient.Restore](https://reference.aspose.com/email/net/aspose.email.clients.imap/imapclient/restore/)

Este artículo demuestra cómo respaldar y restaurar mensajes usando la clase [ImapClient](https://reference.aspose.com/email/net/aspose.email.clients.imap/imapclient/).

## **Respaldar Mensajes**

Para respaldar mensajes, utiliza el método [ImapClient.Backup](https://reference.aspose.com/email/net/aspose.email.clients.imap/imapclient/backup/#backup/) como se demuestra en el siguiente fragmento de código.

{{< gist "aspose-com-gists" "522d47278b8ca448dc1d7eb97193322c" "Examples-CSharp-IMAP-ImapBackupOperation-1.cs" >}}

## **Restaurar Mensajes**

Para restaurar mensajes, utiliza el método [ImapClient.Restore](https://reference.aspose.com/email/net/aspose.email.clients.imap/imapclient/restore/) como se demuestra en el siguiente fragmento de código.

{{< gist "aspose-com-gists" "522d47278b8ca448dc1d7eb97193322c" "Examples-CSharp-IMAP-ImapRestoreOperation-1.cs" >}}

## **Operación de Respaldo y Restauración de IMAP con MultiConnection**

Al trabajar con un gran número de mensajes, la operación de respaldo/restauración puede tardar mucho tiempo. Para esto, la API proporciona soporte para múltiples conexiones durante la operación de respaldo y restauración. Para habilitar el modo MultiConnection, establece la propiedad [ImapClient.UseMultiConnection](https://reference.aspose.com/email/net/aspose.email.clients/emailclient/usemulticonnection/) en [MultiConnectionMode.Enable](https://reference.aspose.com/email/net/aspose.email.clients/multiconnectionmode/). Los siguientes fragmentos de código demuestran la operación de respaldo y restauración con el modo MultiConnection habilitado.

### **Respaldar Mensajes con MultiConnection**

Los siguientes fragmentos de código demuestran la operación de respaldo con el modo MultiConnection habilitado.

{{< gist "aspose-com-gists" "522d47278b8ca448dc1d7eb97193322c" "Examples-CSharp-IMAP-ImapBackupOperationWithMultiConnection-1.cs" >}}

### **Restaurar Mensajes con MultiConnection**

Los siguientes fragmentos de código demuestran la operación de restauración con el modo MultiConnection habilitado.

{{< gist "aspose-com-gists" "522d47278b8ca448dc1d7eb97193322c" "Examples-CSharp-IMAP-ImapRestoreOperationWithMultiConnection-1.cs" >}}