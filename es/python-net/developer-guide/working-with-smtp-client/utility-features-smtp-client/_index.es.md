---
title: "Características de la utilidad: cliente SMTP"
url: /es/python-net/utility-features-smtp-client/
weight: 30
type: docs
---


## **Listado de servidores de extensión que utilizan un cliente SMTP**
Pop3Client de Aspose.Email le permite recuperar las extensiones de servidor que admite un servidor, como IDLE, UNSELECT, QUOTA, etc. Esto ayuda a identificar la disponibilidad de una extensión antes de usar el cliente para esa funcionalidad en particular. El método getCapabilities () devuelve los tipos de extensión admitidos en forma de una matriz de cadenas.
### **Recuperación de extensiones de servidor**
El siguiente fragmento de código muestra cómo recuperar las extensiones de servidor.



{{< gist "aspose-email" "356f0e128b9d45a7ee779fc813eb87e5" "Examples-SMTP-RetrieveSMTPServerExtensions-RetrieveSMTPServerExtensions.py" >}}

## **Valide las credenciales del servidor de correo sin enviar correo electrónico**

El método 'validate_credentials () 'del [SmtpClient](https://reference.aspose.com/email/python-net/aspose.email.clients.smtp/smtpclient/#smtpclient-class) La clase se usa para comprobar la validez de las credenciales proporcionadas mediante el establecimiento de una conexión con el servidor SMTP. Si las credenciales son válidas y la conexión se realiza correctamente, se pueden realizar otras acciones. El siguiente ejemplo de código se puede usar para verificar las credenciales proporcionadas para la autenticación con el servidor SMTP sin enviar un correo electrónico:

```py
import aspose.email as ae

client = ae.clients.smtp.SmtpClient("Url", port, "username", "password", ae.clients.SecurityOptions.AUTO)
client.timeout = 4000

if client.validate_credentials():
  # to do something
```
