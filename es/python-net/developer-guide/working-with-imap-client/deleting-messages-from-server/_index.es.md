---
title: "Eliminar mensajes del servidor"
url: /es/python-net/deleting-messages-from-server/
weight: 20
type: docs
---


## **Eliminar mensajes**
La clase ImapClient puede eliminar mensajes de un servidor IMAP. La función deleteMessage () de la clase IMAPClient se usa para eliminar mensajes. Toma el número de secuencia del mensaje o el identificador único como parámetro. El ImapClient proporciona los métodos DeleteMessage y DeleteMessages para eliminar los mensajes uno por uno o varios. El siguiente fragmento de código muestra cómo eliminar un mensaje de correo electrónico con el identificador de mensaje 1 de un servidor IMAP.



{{< gist "aspose-email" "356f0e128b9d45a7ee779fc813eb87e5" "Examples-IMAP-DeleteSingleMessage-DeleteSingleMessage.py" >}}
## **Eliminar varios mensajes**
Se pueden eliminar varios correos electrónicos del buzón mediante la API IMAPClient de Aspose.Email. El método DeleteMessages proporciona varias opciones para eliminar varios mensajes del servidor mediante identificadores únicos, números de secuencia o elementos de IMAPMessageInfoCollection. En el siguiente fragmento de código, se muestra cómo eliminar varios mensajes.



{{< gist "aspose-email" "356f0e128b9d45a7ee779fc813eb87e5" "Examples-IMAP-DeleteMultipleMessages-DeleteMultipleMessages.py" >}}
