---
title: "Eliminando Mensajes del Servidor"
url: /es/python-net/eliminando-mensajes-del-servidor/
weight: 20
type: docs
---


## **Eliminando Mensajes**
La clase ImapClient puede eliminar mensajes de un servidor IMAP. La función DeleteMessage() de la clase ImapClient se utiliza para eliminar mensajes. Toma el número de secuencia del mensaje o el ID único como parámetro. El ImapClient proporciona métodos DeleteMessage y DeleteMessages para eliminar mensajes uno por uno o múltiples. El siguiente fragmento de código muestra cómo eliminar un mensaje de correo electrónico con el ID de mensaje 1 de un servidor IMAP.



{{< gist "aspose-email" "356f0e128b9d45a7ee779fc813eb87e5" "Examples-IMAP-DeleteSingleMessage-DeleteSingleMessage.py" >}}
## **Eliminando Múltiples Mensajes**
Se pueden eliminar múltiples correos electrónicos de la bandeja de entrada utilizando el ImapClient de la API Aspose.Email. El método DeleteMessages proporciona una serie de opciones para eliminar múltiples mensajes del servidor utilizando IDs únicos, números de secuencia o elementos de ImapMessageInfoCollection. El siguiente fragmento de código muestra cómo eliminar múltiples mensajes.



{{< gist "aspose-email" "356f0e128b9d45a7ee779fc813eb87e5" "Examples-IMAP-DeleteMultipleMessages-DeleteMultipleMessages.py" >}}