---
title: "Registro de actividades de IMAPClient en Python"
url: /es/python-net/imapclient-activity-logging/
weight: 40
type: docs
---


## **Habilitar el registro de actividades**

El registro de actividades implica registrar las conexiones del servidor, los detalles de transmisión de los mensajes enviados y recibidos, los mensajes de error durante el procesamiento del correo electrónico y cualquier otra acción realizada por el cliente o el servidor. Para realizar un seguimiento de la actividad del cliente IMAP y las interacciones con el servidor, utilice el siguiente ejemplo de código, en el que se utiliza la propiedad «log_file_name» del [ImapClient](https://reference.aspose.com/email/python-net/aspose.email.clients.imap/imapclient/#imapclient-class) clase para registrar la información en el archivo de registro especificado:

```py
import aspose.email as ae

client = ae.clients.imap.ImapClient("imap.domain.com", 993, "user@domain.com", "pwd", ae.clients.SecurityOptions.SSL_IMPLICIT)

# Set the path to the log file using the LogFileName property.
client.log_file_name = "C:\\Aspose.Email.IMAP.log"
# Set the UseDateInLogFileName property if it is necessary.
client.use_date_in_log_file_name = False
```
