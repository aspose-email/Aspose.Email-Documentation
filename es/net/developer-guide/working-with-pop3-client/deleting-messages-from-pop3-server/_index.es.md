---
title: "Eliminar mensajes del servidor POP3"
url: /es/net/deleting-messages-from-pop3-server/
weight: 20
type: docs
---


Aspose.Email es un componente robusto que permite realizar operaciones personalizadas después de ciertas acciones. Aspose.Email admite muchos eventos en los que los usuarios pueden realizar operaciones. Esta función proporciona a los usuarios un mayor control sobre su aplicación. Por ejemplo, los usuarios pueden realizar las acciones que deseen cuando:

- Se han enviado todos los correos electrónicos masivos.
- Está a punto de enviarse un mensaje.
- Se ha enviado un correo electrónico por completo.
- Cuando un destinatario es rechazado por el servidor SMTP.

Los buzones POP3 residen en un servidor POP3. El correo electrónico de estos buzones se puede recuperar en su PC de la siguiente manera [Pop3Client](https://reference.aspose.com/email/net/aspose.email.clients.pop3/pop3client/). El [Pop3Client](https://reference.aspose.com/email/net/aspose.email.clients.pop3/pop3client/) La clase usa el protocolo POP3 para copiar los mensajes de correo de su buzón POP3 a su PC. Una vez que se ha recuperado el correo, no necesita estar conectado a Internet mientras se lee, ya que puede leer el correo recuperado en su PC. Si no necesita o no quiere tener una copia de algunos mensajes de correo guardados en el servidor POP3, puede eliminarla. En esta sección se muestra cómo eliminar correos electrónicos mediante [Pop3Client](https://reference.aspose.com/email/net/aspose.email.clients.pop3/pop3client/) class.

## **Eliminar un correo electrónico por índice**

El siguiente fragmento de código elimina todos los mensajes de correo de un buzón uno por uno, según su índice. El índice nunca debe ser <=0 en [Pop3Client.DeleteMessage](https://reference.aspose.com/email/net/aspose.email.clients.pop3/pop3client/deletemessage/#deletemessage/).

{{< gist "aspose-com-gists" "6e5185a63aec6fd70d83098e82b06a32" "Examples-CSharp-POP3-DeleteEmailByIndex-DeleteEmailByIndex.cs" >}}

## **Eliminar todos los correos electrónicos**

También podemos llamar [Pop3Client.DeleteMessages](https://reference.aspose.com/email/net/aspose.email.clients.pop3/pop3client/deletemessage/#deletemessage/) para borrar todos los mensajes. El siguiente fragmento de código muestra cómo eliminar todos los correos electrónicos.

```cs
// Delete all the messages
client.DeleteMessages();
```

Si la conexión con el servidor POP3 se interrumpe inmediatamente después de las operaciones de eliminación, ya no podrá llamar a Cancelar eliminaciones para hacer lo que desea.

## **Cancelar eliminaciones**

[Pop3Client.UndeleteMessages](https://reference.aspose.com/email/net/aspose.email.clients.pop3/pop3client/undeletemessages/#undeletemessages/) se puede usar para cancelar la eliminación de mensajes de correo electrónico. El siguiente fragmento de código muestra cómo cancelar las eliminaciones.

```cs
// Cancel deletes
client.UndeleteMessages();
```