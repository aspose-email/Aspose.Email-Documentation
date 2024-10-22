---
title: "Características de Utilidad - Cliente POP3"
url: /es/python-net/utility-features-pop3-client/
weight: 30
type: docs
---

## **Validar Credenciales del Servidor de Correo**

Aspose.Email proporciona el método 'validate_credentials()' de la clase [Pop3Client](https://reference.aspose.com/email/python-net/aspose.email.clients.pop3/pop3client/#pop3client-class) para verificar las credenciales (nombre de usuario y contraseña) proporcionadas por el usuario para acceder a un servidor de correo POP3. Este método asegura que las credenciales de inicio de sesión del usuario sean precisas y válidas, permitiéndoles autenticarse y acceder a su cuenta de correo electrónico utilizando el protocolo POP3. Si las credenciales proporcionadas son incorrectas, el método puede devolver un error o lanzar una excepción, indicando que el proceso de inicio de sesión ha fallado.

El fragmento de código a continuación demuestra el método de verificación proporcionado por la API:

```py
import aspose.email as ae

client = ae.clients.pop3.Pop3Client("host", 995, "username", "password", ae.clients.SecurityOptions.AUTO)
client.timeout = 40000
if client.validate_credentials():
# to do something
```