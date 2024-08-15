---
title: "Funciones de utilidad para el cliente IMAP en Python"
url: /es/python-net/utility-features-imap-client/
weight: 40
type: docs
---


## **Validar las credenciales del servidor de correo**

Para establecer una conexión segura con un servidor IMAP antes de realizar otras acciones, se comprueban y validan las credenciales de usuario. El método «validate_credentials» del [ImapClient](https://reference.aspose.com/email/python-net/aspose.email.clients.imap/imapclient/#imapclient-class) La clase ayuda a comprobar si el nombre de usuario y la contraseña proporcionados son correctos. Si las credenciales son realmente válidas, el cliente puede autenticarse correctamente con el servidor IMAP. El siguiente ejemplo de código muestra cómo implementar este método en su proyecto:

```py
import aspose.email as ae

with ae.clients.imap.ImapClient("your imap server", 993, "your username", "your password", ae.clients.SecurityOptions.AUTO) as client:
    client.timeout = 4000

    if client.validate_credentials():
        # To do something
```
