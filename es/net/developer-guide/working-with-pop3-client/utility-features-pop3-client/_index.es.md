---
title: "Funciones de Utilidad - Cliente POP3"
url: /es/net/utility-features-pop3-client/
weight: 10
type: docs
---

## **Validar Credenciales del Servidor de Correo**

El método [ValidateCredentials](https://reference.aspose.com/email/net/aspose.email.clients.pop3/pop3client/validatecredentials) de la API Aspose.Email permite la validación de las credenciales del servidor de correo sin enviar un correo electrónico. Este método es responsable de verificar la autenticidad y validez de las credenciales de correo electrónico proporcionadas, que se utilizan para la autenticación al conectarse al servidor.

Verifica que las credenciales de correo electrónico, como el nombre de usuario y la contraseña, sean válidas y que sea posible para el cliente establecer una conexión exitosa con el servidor. Esta verificación de credenciales ayuda a garantizar que el cliente pueda acceder de manera segura a la cuenta de correo electrónico y realizar diversas operaciones, como recibir correo electrónico.

```cs
using (Pop3Client client = new Pop3Client(server.Pop3Url, server.Pop3Port, "userName", "password", SecurityOptions.Auto))
{
    client.Timeout = 4000;
   
    if (client.ValidateCredentials())
    {
        //to do something
    }
}
```

Para realizar una operación asincrónica, también hay una versión del método [ValidateCredentialsAsync](https://reference.aspose.com/email/net/aspose.email.clients.pop3/pop3client/validatecredentialsasync/).