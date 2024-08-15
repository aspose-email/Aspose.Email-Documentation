---
title: "Trabajando con marcas de mensajes en el servidor"
url: /es/net/working-with-message-flags-on-server/
weight: 30
type: docs
---


## **Cambiar las banderas de los mensajes**

Puede cambiar las marcas de los mensajes mediante el [ChangeMessageFlags()](https://reference.aspose.com/email/net/aspose.email.clients.imap/imapclient/changemessageflags/#changemessageflags/) método. Este método toma dos parámetros.

1. El número de secuencia de un mensaje o su identificador único.
2. [MessageFlag](https://reference.aspose.com/email/net/aspose.email.clients.imap/imapmessageflags/).

Se pueden configurar los siguientes indicadores:

- [Answered](https://reference.aspose.com/email/net/aspose.email.clients.imap/imapmessageflags/answered/)
- [Deleted](https://reference.aspose.com/email/net/aspose.email.clients.imap/imapmessageflags/deleted/)
- [Draft](https://reference.aspose.com/email/net/aspose.email.clients.imap/imapmessageflags/draft/)
- [Empty](https://reference.aspose.com/email/net/aspose.email.clients.imap/imapmessageflags/empty/)
- [Flagged](https://reference.aspose.com/email/net/aspose.email.clients.imap/imapmessageflags/flagged/)
- [IsRead](https://reference.aspose.com/email/net/aspose.email.clients.imap/imapmessageflags/isread/)
- [Recent](https://reference.aspose.com/email/net/aspose.email.clients.imap/imapmessageflags/recent/)

### **Configuración de banderas de mensajes**

El siguiente fragmento de código muestra cómo cambiar las marcas de mensajes en un servidor IMAP con Aspose.Email.

{{< gist "aspose-com-gists" "6e5185a63aec6fd70d83098e82b06a32" "Examples-CSharp-IMAP-SettingMessageFlags-SettingMessageFlags.cs" >}}

### **Eliminar marcas de mensajes**

Las marcas de mensajes también se pueden eliminar con la [RemoveMessageFlags()](https://reference.aspose.com/email/net/aspose.email.clients.imap/imapclient/removemessageflags/#removemessageflags/) método. El uso es similar al del [ChangeMessageFlags()](https://reference.aspose.com/email/net/aspose.email.clients.imap/imapclient/changemessageflags/#changemessageflags/) método. Toma un número de secuencia o un identificador de mensaje único y [MessageFlag](https://reference.aspose.com/email/net/aspose.email.clients.imap/imapmessageflags/). En el siguiente fragmento de código, se muestra cómo eliminar las marcas de mensajes.

{{< gist "aspose-com-gists" "6e5185a63aec6fd70d83098e82b06a32" "Examples-CSharp-IMAP-RemovingMessageFlags-RemovingMessageFlags.cs" >}}

## **Configuración de banderas personalizadas**

También puedes configurar marcas personalizadas para un mensaje mediante el [ImapClient](https://reference.aspose.com/email/net/aspose.email.clients.imap/imapclient/) de la API. El addMessageFlags de ImapClient ofrece la posibilidad de establecer marcas personalizadas en los mensajes.

{{< gist "aspose-com-gists" "6e5185a63aec6fd70d83098e82b06a32" "Examples-CSharp-IMAP-SetCustomFlag-SetCustomFlag.cs" >}}
