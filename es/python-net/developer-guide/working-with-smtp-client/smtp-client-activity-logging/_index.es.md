---
title: "Registro de actividad de SMTPClient"
url: /es/python-net/smtpclient-activity-logging/
weight: 30
type: docs
---


## **Habilitar el registro de actividades en el código del programa**

Aspose.Email permite registrar o documentar sistemáticamente actividades, eventos o transacciones durante un período de tiempo. También conocido como registro de actividades, se puede lograr con las siguientes propiedades del [SmtpClient](https://reference.aspose.com/email/python-net/aspose.email.clients.smtp/smtpclient/#smtpclient-class) class:

- La propiedad 'log_file_name' obtiene o establece el nombre del archivo de registro.
- 'use_date_in_log_file_name' obtiene o establece un valor que indica si la fecha debe usarse en el nombre del archivo de registro.

El ejemplo de código que aparece a continuación muestra cómo habilitar el registro de actividades en el código del programa:

```py
import aspose.email as ae

# Set username, password, port, and security options
client = ae.clients.smtp.SmtpClient
client.host = "<HOST>"
client.username = "<USERNAME>"
client.password = "<PASSWORD>"
client.port = 587
client.security_options = ae.clients.SecurityOptions.SSL_EXPLICIT

# Set the path to the log file using the LogFileName property
client.log_file_name = "C:\Aspose.Email.Smtp.log"

# Set the UseDateInLogFileName property if it is necessary.
client.use_date_in_log_file_name = False

eml = ae.MailMessage("from address", "to address", "this is a test subject", "this is a test body")
client.send(eml)
```