---
title: "Eliminación de Mensajes del Servidor POP3"
url: /es/net/deleting-messages-from-pop3-server/
weight: 20
type: docs
---


Aspose.Email es un componente robusto que permite realizar operaciones personalizadas después de ciertas acciones. Aspose.Email admite muchos eventos sobre los cuales los usuarios pueden realizar operaciones. Esta función proporciona a los usuarios más control sobre su aplicación. Por ejemplo, los usuarios pueden realizar las acciones deseadas cuando:

- Se han enviado todos los correos electrónicos masivos.
- Un mensaje está a punto de ser enviado.
- Un correo electrónico se ha enviado completamente.
- Cuando un destinatario es rechazado por el servidor SMTP.

Las bandejas de entrada POP3 residen en un servidor POP3. El correo en estas bandejas puede ser recuperado a tu PC mediante [Pop3Client](https://reference.aspose.com/email/net/aspose.email.clients.pop3/pop3client/). La clase [Pop3Client](https://reference.aspose.com/email/net/aspose.email.clients.pop3/pop3client/) utiliza el protocolo POP3 para copiar los mensajes de correo de tu bandeja POP3 a tu PC. Una vez que se ha recuperado el correo, no necesitas estar conectado a Internet mientras se lee, ya que puedes leer el correo recuperado en tu PC. Si no necesitas o quieres que una copia de algunos mensajes de correo se mantenga en el servidor POP3, puedes eliminarla. Esta sección muestra cómo eliminar correos electrónicos usando la clase [Pop3Client](https://reference.aspose.com/email/net/aspose.email.clients.pop3/pop3client/).

## **Eliminar un Correo Electrónico por Índice**

El siguiente fragmento de código elimina todos los mensajes de correo de una bandeja de entrada uno por uno, basado en su índice. El índice nunca debe ser <=0 en [Pop3Client.DeleteMessage](https://reference.aspose.com/email/net/aspose.email.clients.pop3/pop3client/deletemessage/#deletemessage/).

{{< gist "aspose-com-gists" "6e5185a63aec6fd70d83098e82b06a32" "Examples-CSharp-POP3-DeleteEmailByIndex-DeleteEmailByIndex.cs" >}}

## **Eliminar Todos los Correos Electrónicos**

También podemos llamar a [Pop3Client.DeleteMessages](https://reference.aspose.com/email/net/aspose.email.clients.pop3/pop3client/deletemessage/#deletemessage/) para eliminar todos los mensajes. El siguiente fragmento de código te muestra cómo eliminar todos los correos electrónicos.

```cs
// Eliminar todos los mensajes
client.DeleteMessages();
```

Si la conexión al servidor POP3 se interrumpe inmediatamente después de las operaciones de eliminación, ya no puedes llamar a Cancel Delete para hacer las cosas que deseas.

## **Cancelar Eliminaciones**

[Pop3Client.UndeleteMessages](https://reference.aspose.com/email/net/aspose.email.clients.pop3/pop3client/undeletemessages/#undeletemessages/) se puede utilizar para cancelar la eliminación de mensajes de correo electrónico. El siguiente fragmento de código te muestra cómo cancelar eliminaciones.

```cs
// Cancelar eliminaciones
client.UndeleteMessages();
```