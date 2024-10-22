---
title: "Eliminar mensajes del servidor Exchange usando WebDav"
url: /es/java/delete-messages-from-exchange-server-using-webdav/
weight: 20
type: docs
---

Puedes eliminar mensajes de correo electrónico de una carpeta con la ayuda del [ExchangeClient.deleteMessage()](https://apireference.aspose.com/email/java/com.aspose.email/ExchangeClient#deleteMessage\(java.lang.String\)) método. Toma el URI único del mensaje como parámetro.

El código de muestra a continuación elimina un mensaje de la carpeta de Entrada. Para los propósitos de este ejemplo, el código:

1. Lee mensajes de la carpeta de Entrada.
1. Procesa los mensajes en base a ciertos criterios (en este ejemplo, encontramos una palabra clave en el asunto del mensaje).
1. Elimina el mensaje.
 

{{< gist "aspose-com-gists" "709d733586ce50505c3bca3f6e8bd18d" "Examples-src-main-java-com-aspose-email-examples-exchange-DeleteMessagesFromExchangeServer-DeleteMessagesFromExchangeServer.java" >}}