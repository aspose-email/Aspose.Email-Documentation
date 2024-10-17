---
title: "Trabajando con las Banderas de Mensaje en el Servidor"
url: /es/net/working-with-message-flags-on-server/
weight: 30
type: docs
---


## **Cambio de las Banderas de Mensaje**

Puedes cambiar las banderas de mensaje utilizando el método [ChangeMessageFlags()](https://reference.aspose.com/email/net/aspose.email.clients.imap/imapclient/changemessageflags/#changemessageflags/). Este método toma dos parámetros.

1. El número de secuencia de un mensaje o su ID único.
2. [MessageFlag](https://reference.aspose.com/email/net/aspose.email.clients.imap/imapmessageflags/).

Se pueden establecer las siguientes banderas:

- [Respondido](https://reference.aspose.com/email/net/aspose.email.clients.imap/imapmessageflags/answered/)
- [Eliminado](https://reference.aspose.com/email/net/aspose.email.clients.imap/imapmessageflags/deleted/)
- [Borrador](https://reference.aspose.com/email/net/aspose.email.clients.imap/imapmessageflags/draft/)
- [Vacío](https://reference.aspose.com/email/net/aspose.email.clients.imap/imapmessageflags/empty/)
- [Marcado](https://reference.aspose.com/email/net/aspose.email.clients.imap/imapmessageflags/flagged/)
- [Está leída](https://reference.aspose.com/email/net/aspose.email.clients.imap/imapmessageflags/isread/)
- [Reciente](https://reference.aspose.com/email/net/aspose.email.clients.imap/imapmessageflags/recent/)

### **Establecer Banderas de Mensaje**

El siguiente fragmento de código te muestra cómo cambiar las banderas de mensaje en un servidor IMAP con Aspose.Email.

{{< gist "aspose-com-gists" "6e5185a63aec6fd70d83098e82b06a32" "Examples-CSharp-IMAP-SettingMessageFlags-SettingMessageFlags.cs" >}}

### **Eliminar Banderas de Mensaje**

Las banderas de mensaje también se pueden eliminar con el método [RemoveMessageFlags()](https://reference.aspose.com/email/net/aspose.email.clients.imap/imapclient/removemessageflags/#removemessageflags/). El uso es similar al del método [ChangeMessageFlags()](https://reference.aspose.com/email/net/aspose.email.clients.imap/imapclient/changemessageflags/#changemessageflags/). Toma un número de secuencia o un ID único de mensaje y [MessageFlag](https://reference.aspose.com/email/net/aspose.email.clients.imap/imapmessageflags/). El siguiente fragmento de código te muestra cómo eliminar las banderas de mensaje.

{{< gist "aspose-com-gists" "6e5185a63aec6fd70d83098e82b06a32" "Examples-CSharp-IMAP-RemovingMessageFlags-RemovingMessageFlags.cs" >}}

## **Establecer Banderas Personalizadas**

También puedes establecer banderas personalizadas en un mensaje utilizando el [ImapClient](https://reference.aspose.com/email/net/aspose.email.clients.imap/imapclient/) de la API. El método AddMessageFlags de ImapClient proporciona la capacidad de establecer banderas personalizadas en los mensajes.

{{< gist "aspose-com-gists" "6e5185a63aec6fd70d83098e82b06a32" "Examples-CSharp-IMAP-SetCustomFlag-SetCustomFlag.cs" >}}