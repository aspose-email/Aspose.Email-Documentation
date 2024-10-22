---
title: "Mover mensajes de una carpeta a otra usando WebDav"
url: /es/java/move-messages-from-one-folder-to-another-using-webdav/
weight: 70
type: docs
---

Puede mover mensajes de correo electrónico de una carpeta a otra con la ayuda del método [ExchangeClient.moveMessage()](https://apireference.aspose.com/email/java/com.aspose.email/ExchangeClient#moveMessage\(com.aspose.email.ExchangeMessageInfo,%20java.lang.String\)). Toma los parámetros:

- El URI único del mensaje que se va a mover.
- El URI único de la carpeta de destino.
## **Mover mensajes entre carpetas**
El código de ejemplo a continuación mueve un mensaje en un buzón de la carpeta de Entrada a una carpeta llamada Procesados. En este ejemplo, la aplicación:

1. Lee los mensajes de la carpeta de Entrada.
1. Procesa algunos de los mensajes en base a ciertos criterios (en este ejemplo, encontramos una palabra clave en el asunto del mensaje).
1. Mueve los mensajes que cumplen con la condición dada a la carpeta Procesados.

{{< gist "aspose-com-gists" "709d733586ce50505c3bca3f6e8bd18d" "Examples-src-main-java-com-aspose-email-examples-exchange-MoveMessageFromOneFolderToAnother-MoveMessagesBetweenFolders.java" >}}