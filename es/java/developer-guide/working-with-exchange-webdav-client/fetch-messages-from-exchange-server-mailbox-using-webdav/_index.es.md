---
title: "Obtenga mensajes del buzón de correo de Exchange Server mediante WebDAV"
url: /es/java/fetch-messages-from-exchange-server-mailbox-using-webdav/
weight: 30
type: docs
---

{{% alert color="primary" %}}

Al enumerar los mensajes de un servidor Exchange, se utilizó el [listMessages()](https://apireference.aspose.com/email/java/com.aspose.email/exchangeclient#listMessages\(java.lang.String\)) método para obtener una lista de mensajes de un buzón de Exchange Server. El [listMessages()](https://apireference.aspose.com/email/java/com.aspose.email/exchangeclient#listMessages\(java.lang.String\)) El método obtiene información básica sobre los mensajes, por ejemplo, el asunto, el ID del mensaje, el origen y el destino.

Para obtener los detalles completos del mensaje, Aspose.Email.Exchange proporciona la [ExchangeClient.fetchMessage()](https://apireference.aspose.com/email/java/com.aspose.email/exchangeclient#fetchMessage\(java.lang.String\)) método. Este método acepta el URI del mensaje como parámetro y devuelve una instancia del [MailMessage](https://apireference.aspose.com/email/java/com.aspose.email/mailmessage) clase. El [MailMessage](https://apireference.aspose.com/email/java/com.aspose.email/mailmessage) La clase luego proporciona detalles del mensaje como el cuerpo, los encabezados y los archivos adjuntos.

{{% /alert %}}
## **Obtener mensajes de un buzón de correo de Exchange Server**
Para obtener mensajes del buzón de Exchange Server:

1. Crear una instancia de tipo [ExchangeClient](https://apireference.aspose.com/email/java/com.aspose.email/exchangeclient).
1. Especifique el nombre del servidor, el nombre de usuario, la contraseña y el dominio.
1. Llame al [listMessages](https://apireference.aspose.com/email/java/com.aspose.email/exchangeclient#listMessages\(java.lang.String\)) método para obtener el [ExchangeMessageInfoCollection](https://apireference.aspose.com/email/java/com.aspose.email/exchangemessageinfocollection).
1. Recorre el [ExchangeMessageInfoCollection](https://apireference.aspose.com/email/java/com.aspose.email/exchangemessageinfocollection) colección para obtener [ExchangeMessageInfo.getUniqueUri](https://apireference.aspose.com/email/java/com.aspose.email/ExchangeMessageInfo#getUniqueUri\(\)) values.
1. Call [ExchangeClient.fetchMessage()](https://apireference.aspose.com/email/java/com.aspose.email/exchangeclient#fetchMessage\(java.lang.String\)) y pase [ExchangeMessageInfo.getUniqueUri](https://apireference.aspose.com/email/java/com.aspose.email/ExchangeMessageInfo#getUniqueUri\(\)) como parámetro.

El siguiente fragmento de código se conecta al buzón de correo de Exchange Server y recupera todos los mensajes.

{{< gist "aspose-com-gists" "709d733586ce50505c3bca3f6e8bd18d" "Examples-src-main-java-com-aspose-email-examples-exchange-FetchMessagesFromAnExchangeServerMailbox-FetchMessagesFromAnExchangeServerMailbox.java" >}}
