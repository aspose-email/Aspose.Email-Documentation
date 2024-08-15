---
title: "Operación de respaldo y restauración de IMAP"
url: /es/net/imap-backup-and-restore-operation/
weight: 120
type: docs
---


Aspose.Email para.NET ofrece la posibilidad de realizar copias de seguridad y restaurar mensajes. Para ello, la API proporciona los siguientes métodos.

- [ImapClient.Backup](https://reference.aspose.com/email/net/aspose.email.clients.imap/imapclient/backup/#backup/)
- [ImapClient.Restore](https://reference.aspose.com/email/net/aspose.email.clients.imap/imapclient/restore/)

En este artículo se muestra cómo hacer copias de seguridad y restaurar los mensajes mediante el [ImapClient](https://reference.aspose.com/email/net/aspose.email.clients.imap/imapclient/) class.

## **Mensajes de respaldo**

Para hacer copias de seguridad de los mensajes, utilice la [ImapClient.Backup](https://reference.aspose.com/email/net/aspose.email.clients.imap/imapclient/backup/#backup/) método como se muestra en el siguiente fragmento de código.

{{< gist "aspose-com-gists" "522d47278b8ca448dc1d7eb97193322c" "Examples-CSharp-IMAP-ImapBackupOperation-1.cs" >}}

## **Restaurar mensajes**

Para restaurar los mensajes, utilice el [ImapClient.Restore](https://reference.aspose.com/email/net/aspose.email.clients.imap/imapclient/restore/) método como se muestra en el siguiente fragmento de código.

{{< gist "aspose-com-gists" "522d47278b8ca448dc1d7eb97193322c" "Examples-CSharp-IMAP-ImapRestoreOperation-1.cs" >}}

## **Operación de respaldo y restauración de IMAP con MultiConnection**

Cuando se trabaja con una gran cantidad de mensajes, la operación de copia de seguridad o restauración puede tardar mucho tiempo. Para ello, la API admite varias conexiones durante la operación de copia de seguridad y restauración. Para habilitar el modo de conexión múltiple, defina [ImapClient.UseMultiConnection](https://reference.aspose.com/email/net/aspose.email.clients/emailclient/usemulticonnection/) propiedad a [MultiConnectionMode.Enable](https://reference.aspose.com/email/net/aspose.email.clients/multiconnectionmode/). Los siguientes fragmentos de código muestran las operaciones de copia de seguridad y restauración con el modo MultiConexión habilitado.

### **Mensajes de respaldo con MultiConnection**

En los siguientes fragmentos de código se muestra el funcionamiento de la copia de seguridad con el modo multiconexión activado.

{{< gist "aspose-com-gists" "522d47278b8ca448dc1d7eb97193322c" "Examples-CSharp-IMAP-ImapBackupOperationWithMultiConnection-1.cs" >}}

### **Restaurar mensajes con MultiConnection**

Los siguientes fragmentos de código muestran la operación de restauración con el modo multiconexión activado.

{{< gist "aspose-com-gists" "522d47278b8ca448dc1d7eb97193322c" "Examples-CSharp-IMAP-ImapRestoreOperationWithMultiConnection-1.cs" >}}
