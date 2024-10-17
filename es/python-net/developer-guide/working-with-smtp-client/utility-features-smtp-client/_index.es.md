---
title: "Características de Utilidad - Cliente SMTP"
url: /es/python-net/utility-features-smtp-client/
weight: 30
type: docs
---


## **Listando Servidores de Extensión usando Cliente SMTP**
El Pop3Client de Aspose.Email te permite recuperar las extensiones del servidor que un servidor soporta como IDLE, UNSELECT, QUOTA, etc. Esto ayuda a identificar la disponibilidad de una extensión antes de utilizar el cliente para esa funcionalidad en particular. El método GetCapabilities() devuelve los tipos de extensión soportados en forma de un array de cadenas.
### **Recuperando Extensiones del Servidor**
El siguiente fragmento de código te muestra cómo recuperar extensiones del servidor.



{{< gist "aspose-email" "356f0e128b9d45a7ee779fc813eb87e5" "Examples-SMTP-RetrieveSMTPServerExtensions-RetrieveSMTPServerExtensions.py" >}}

## **Validar Credenciales del Servidor de Correo Sin Enviar Correo Electrónico**

El método 'validate_credentials()' de la clase [SmtpClient](https://reference.aspose.com/email/python-net/aspose.email.clients.smtp/smtpclient/#smtpclient-class) se utiliza para verificar la validez de las credenciales proporcionadas estableciendo una conexión con el servidor SMTP. Si las credenciales son válidas y la conexión es exitosa, se pueden realizar más acciones. El siguiente ejemplo de código se puede utilizar para verificar las credenciales proporcionadas para la autenticación con el servidor SMTP sin enviar un correo electrónico:

```py
import aspose.email as ae

client = ae.clients.smtp.SmtpClient("Url", port, "username", "password", ae.clients.SecurityOptions.AUTO)
client.timeout = 4000

if client.validate_credentials():
  # to do something
```