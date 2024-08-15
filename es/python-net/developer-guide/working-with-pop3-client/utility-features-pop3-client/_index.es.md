---
title: "Características de la utilidad: cliente POP3"
url: /es/python-net/utility-features-pop3-client/
weight: 30
type: docs
---

## **Validar las credenciales del servidor de correo**

Aspose.Email proporciona el método 'validate_credentials () 'del [Pop3Client](https://reference.aspose.com/email/python-net/aspose.email.clients.pop3/pop3client/#pop3client-class) clase para verificar las credenciales (nombre de usuario y contraseña) proporcionadas por el usuario para acceder a un servidor de correo electrónico POP3. Este método garantiza que las credenciales de inicio de sesión del usuario sean precisas y válidas, lo que le permite autenticarse correctamente y acceder a su cuenta de correo electrónico mediante el protocolo POP3. Si las credenciales proporcionadas son incorrectas, el método puede devolver un error o generar una excepción que indique que el proceso de inicio de sesión ha fallado.

El siguiente fragmento de código muestra el método de verificación que proporciona la API:

```py
import aspose.email as ae

client = ae.clients.pop3.Pop3Client("host", 995, "username", "password", ae.clients.SecurityOptions.AUTO)
client.timeout = 40000
if client.validate_credentials():
# to do something
```