---
title: "Eliminar mensajes de Exchange Server mediante WebDAV"
url: /es/java/delete-messages-from-exchange-server-using-webdav/
weight: 20
type: docs
---

Puede eliminar los mensajes de correo electrónico de una carpeta con la ayuda del [ExchangeClient.deleteMessage()](https://apireference.aspose.com/email/java/com.aspose.email/ExchangeClient#deleteMessage\(java.lang.String\)) método. Toma el URI único del mensaje como parámetro.

El código de ejemplo que aparece a continuación elimina un mensaje de la carpeta Bandeja de entrada. Para este ejemplo, el código:

1. Lee los mensajes de la carpeta Bandeja de entrada.
1. Procesa los mensajes en función de algunos criterios (en este ejemplo, encontramos una palabra clave en el asunto del mensaje).
1. Elimine el mensaje.
 

{{< gist "aspose-com-gists" "709d733586ce50505c3bca3f6e8bd18d" "Examples-src-main-java-com-aspose-email-examples-exchange-DeleteMessagesFromExchangeServer-DeleteMessagesFromExchangeServer.java" >}}
