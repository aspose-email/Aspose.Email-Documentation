---
title: "Características de la utilidad: cliente POP3"
url: /es/net/utility-features-pop3-client/
weight: 10
type: docs
---

## **Validar las credenciales del servidor de correo**

The [ValidateCredentials](https://reference.aspose.com/email/net/aspose.email.clients.pop3/pop3client/validatecredentials) El método de la API Aspose.Email hace posible la validación de las credenciales del servidor de correo sin enviar un correo electrónico. Este método es responsable de verificar la autenticidad y validez de las credenciales de correo electrónico proporcionadas, que se utilizan para la autenticación al conectarse al servidor.

Verifica que las credenciales de correo electrónico, como el nombre de usuario y la contraseña, sean válidas y que el cliente pueda establecer una conexión exitosa con el servidor. Esta verificación de las credenciales ayuda a garantizar que el cliente pueda acceder de forma segura a la cuenta de correo electrónico y realizar diversas operaciones, como recibir correos electrónicos.

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
