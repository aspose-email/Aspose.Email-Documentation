---
title: "Funciones Utilitarias para el Cliente IMAP en Python"
url: /es/python-net/utility-features-imap-client/
weight: 40
type: docs
---


## **Validar Credenciales del Servidor de Correo**

Para establecer una conexión segura con un servidor IMAP antes de realizar acciones adicionales, se verifican y validan las credenciales del usuario. El método 'validate_credentials' de la clase [ImapClient](https://reference.aspose.com/email/python-net/aspose.email.clients.imap/imapclient/#imapclient-class) ayuda a comprobar si el nombre de usuario y la contraseña proporcionados son correctos. Si las credenciales son válidas, el cliente puede autenticarse con éxito con el servidor IMAP. El siguiente ejemplo de código muestra cómo implementar este método en tu proyecto:

```py
import aspose.email as ae

with ae.clients.imap.ImapClient("your imap server", 993, "your username", "your password", ae.clients.SecurityOptions.AUTO) as client:
    client.timeout = 4000

    if client.validate_credentials():
        # To do something
```