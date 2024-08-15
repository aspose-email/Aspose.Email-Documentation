---
title: "Mover mensajes de una carpeta a otra con WebDAV"
url: /es/java/move-messages-from-one-folder-to-another-using-webdav/
weight: 70
type: docs
---

Puede mover los mensajes de correo electrónico de una carpeta a otra con la ayuda del [ExchangeClient.moveMessage()](https://apireference.aspose.com/email/java/com.aspose.email/ExchangeClient#moveMessage\(com.aspose.email.ExchangeMessageInfo,%20java.lang.String\)) método. Toma los parámetros:

- El URI único del mensaje que se va a mover.
- El URI único de la carpeta de destino.
## **Mover mensajes entre carpetas**
El siguiente código de ejemplo que mueve un mensaje de un buzón de correo de la carpeta Bandeja de entrada a una carpeta denominada Procesado. En este ejemplo, la aplicación:

1. Lee los mensajes de la carpeta Bandeja de entrada.
1. Procesa algunos de los mensajes en función de algunos criterios (en este ejemplo, encontramos una palabra clave en el asunto del mensaje).
1. Mueve los mensajes que cumplen la condición dada a la carpeta Procesados.

{{< gist "aspose-com-gists" "709d733586ce50505c3bca3f6e8bd18d" "Examples-src-main-java-com-aspose-email-examples-exchange-MoveMessageFromOneFolderToAnother-MoveMessagesBetweenFolders.java" >}}
