---
title: "Eliminando Mensajes del Servidor POP3"
url: /es/python-net/eliminando-mensajes-del-servidor-pop3/
weight: 20
type: docs
---

Aspose.Email.Mail es un componente robusto que permite realizar operaciones personalizadas después de ciertas acciones. Aspose.Email.Mail genera muchos eventos sobre los cuales los usuarios pueden realizar operaciones. Esta función proporciona a los usuarios un mayor control sobre su aplicación. Por ejemplo, los usuarios pueden realizar las acciones deseadas cuando:

- Se han enviado todos los correos masivos.
- Un mensaje está a punto de enviarse.
- Un correo electrónico se ha enviado completamente.
- Cuando un destinatario es rechazado por el servidor SMTP.

Las bandejas de entrada POP3 residen en un servidor POP3. El correo en estas bandejas de entrada puede ser recuperado a tu PC mediante Aspose.Email.Pop3.Pop3Client. El espacio de nombres Pop3Client utiliza el protocolo POP3 para copiar los mensajes de correo de tu bandeja de entrada POP3 a tu PC. Una vez que el correo ha sido recuperado, no es necesario estar conectado a internet mientras se está leyendo, ya que puedes leer el correo recuperado en tu PC. Si no necesitas ni deseas que se conserve una copia de algunos mensajes de correo en el servidor POP3, puedes eliminarlos. Esta sección muestra cómo eliminar correos electrónicos usando el espacio de nombres Pop3Client.
## **Eliminar un Correo por Índice**
El siguiente fragmento de código elimina todos los mensajes de correo de una bandeja de entrada uno por uno, basado en su índice. El índice nunca debe ser <=0 en Pop3Client.DeleteMessage.



{{< gist "aspose-email" "356f0e128b9d45a7ee779fc813eb87e5" "Examples-POP3-DeleteEmailByIndex-DeleteEmailByIndex.py" >}}
## **Eliminar Todos los Correos Electrónicos**
También podemos llamar a Pop3Client.DeleteAllMessages() para eliminar todos los mensajes. El siguiente fragmento de código te muestra cómo eliminar todos los correos electrónicos.



```py
import aspose.email as ae

client = ae.clients.pop3.Pop3Client("imap.example.com", "username", "password")

# Eliminar todos los mensajes
client.delete_messages()
```



Si la conexión al servidor POP3 se rompe inmediatamente después de las operaciones de eliminación, ya no podrás llamar a Pop3Client.CancelDeletes() para hacer lo que deseas.
## **Cancelar Eliminaciones**
Pop3Client.UndeleteMessages se puede utilizar para cancelar la eliminación de mensajes de correo electrónico. El siguiente fragmento de código te muestra cómo cancelar eliminaciones.



```py
import aspose.email as ae

client = ae.clients.pop3.Pop3Client("imap.example.com", "username", "password")

# Cancelar eliminaciones
client.undelete_messages()
```