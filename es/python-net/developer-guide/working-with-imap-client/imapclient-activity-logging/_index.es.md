---
title: "Registro de Actividad de ImapClient en Python"
url: /es/python-net/imapclient-activity-logging/
weight: 40
type: docs
---


## **Habilitar el Registro de Actividad**

El registro de actividad implica la grabación de conexiones al servidor, detalles de transmisión de los mensajes enviados y recibidos, mensajes de error durante el procesamiento de correos electrónicos y cualquier otra acción realizada por el cliente o el servidor. Para rastrear la actividad del cliente IMAP y las interacciones con el servidor, utiliza el siguiente ejemplo de código que usa la propiedad 'log_file_name' de la clase [ImapClient](https://reference.aspose.com/email/python-net/aspose.email.clients.imap/imapclient/#imapclient-class) para registrar la información en el archivo de registro especificado:

```py
import aspose.email as ae

client = ae.clients.imap.ImapClient("imap.domain.com", 993, "user@domain.com", "pwd", ae.clients.SecurityOptions.SSL_IMPLICIT)

# Set the path to the log file using the LogFileName property.
client.log_file_name = "C:\\Aspose.Email.IMAP.log"
# Set the UseDateInLogFileName property if it is necessary.
client.use_date_in_log_file_name = False
```