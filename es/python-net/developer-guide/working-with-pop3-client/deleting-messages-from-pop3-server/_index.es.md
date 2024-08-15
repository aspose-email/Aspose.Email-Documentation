---
title: "Eliminar mensajes del servidor POP3"
url: /es/python-net/deleting-messages-from-pop3-server/
weight: 20
type: docs
---

Aspose.Email.Mail es un componente robusto que permite realizar operaciones personalizadas después de ciertas acciones. Aspose.Email.Mail desencadena muchos eventos sobre los que los usuarios pueden realizar operaciones. Esta función proporciona a los usuarios un mayor control sobre su aplicación. Por ejemplo, los usuarios pueden realizar las acciones que deseen cuando:

- Se han enviado todos los correos electrónicos masivos.
- Está a punto de enviarse un mensaje.
- Se ha enviado un correo electrónico por completo.
- Cuando un destinatario es rechazado por el servidor SMTP.

Los buzones POP3 residen en un servidor POP3. Aspose.Email.Pop3.Pop3Client puede recuperar el correo electrónico de estos buzones en su PC. El espacio de nombres Pop3Client usa el protocolo POP3 para copiar los mensajes de correo de su buzón POP3 a su PC. Una vez recuperado el correo, no necesita estar conectado a Internet mientras se lee, ya que puede leer el correo recuperado en su PC. Si no necesita o no quiere tener una copia de algunos mensajes de correo guardados en el servidor POP3, puede eliminarla. En esta sección se muestra cómo eliminar correos electrónicos mediante el espacio de nombres Pop3Client.
## **Eliminar un correo electrónico por índice**
El siguiente fragmento de código elimina todos los mensajes de correo de un buzón uno por uno, según su índice. El índice nunca debe ser <=0 en POP3Client.deleteMessage.



{{< gist "aspose-email" "356f0e128b9d45a7ee779fc813eb87e5" "Examples-POP3-DeleteEmailByIndex-DeleteEmailByIndex.py" >}}
## **Eliminar todos los correos electrónicos**
También podemos llamar a pop3Client.deleteAllMessages () para eliminar todos los mensajes. El siguiente fragmento de código muestra cómo eliminar todos los correos electrónicos.



```py
import aspose.email as ae

client = ae.clients.pop3.Pop3Client("imap.example.com", "username", "password")

# Delete all the messages
client.delete_messages()
```



Si la conexión con el servidor POP3 se interrumpe inmediatamente después de las operaciones de eliminación, ya no podrá llamar a POP3Client.cancelDeletes () para hacer lo que desee.
## **Cancelar eliminaciones**
POP3Client.UndeleteMessages se puede usar para cancelar la eliminación de mensajes de correo electrónico. El siguiente fragmento de código muestra cómo cancelar las eliminaciones.



```py
import aspose.email as ae

client = ae.clients.pop3.Pop3Client("imap.example.com", "username", "password")

# Cancel deletes
client.undelete_messages()
```
