---
title: "Funciones de Utilidad - Cliente IMAP"
url: /es/net/utility-features-imap-client/
weight: 100
type: docs
---

## **Validar Credenciales del Servidor de Correo**

La API de Aspose.Email permite la validación de credenciales del servidor de correo sin enviar un correo electrónico. El método [ValidateCredentials](https://reference.aspose.com/email/net/aspose.email.clients.imap/imapclient/validatecredentials) es responsable de verificar la autenticidad y validez de las credenciales de correo electrónico proporcionadas, que normalmente se utilizan para autenticar al conectarse al servidor.

Verifica que las credenciales de correo electrónico proporcionadas, como el nombre de usuario y la contraseña, sean válidas y que el cliente pueda establecer una conexión exitosa con el servidor. Esta verificación de credenciales ayuda a garantizar que el cliente pueda acceder de manera segura a la cuenta de correo electrónico y realizar varias operaciones, como recibir correo electrónico.

```cs
using (ImapClient client = new ImapClient(server.ImapUrl, server.ImapPort, "username", "password", SecurityOptions.Auto))
{
    client.Timeout = 4000;
   
    if (client.ValidateCredentials())
    {
        //to do something
    }
}
```

Para una operación asíncrona, también hay una versión del método [ValidateCredentialsAsync](https://reference.aspose.com/email/net/aspose.email.clients.imap/imapclient/validatecredentialsasync).