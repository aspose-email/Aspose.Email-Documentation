---
title: "Recuperar mensajes de la bandeja de entrada del servidor Exchange utilizando WebDav"
url: /es/java/fetch-messages-from-exchange-server-mailbox-using-webdav/
weight: 30
type: docs
---

{{% alert color="primary" %}} 

Listar mensajes en un servidor Exchange utilizó el [listMessages()](https://apireference.aspose.com/email/java/com.aspose.email/exchangeclient#listMessages\(java.lang.String\)) método para obtener una lista de mensajes de una bandeja de entrada del servidor Exchange. El [listMessages()](https://apireference.aspose.com/email/java/com.aspose.email/exchangeclient#listMessages\(java.lang.String\)) método obtiene información básica sobre los mensajes, por ejemplo, el asunto, el ID del mensaje, de y para.

Para obtener los detalles completos del mensaje, Aspose.Email.Exchange proporciona el [ExchangeClient.fetchMessage()](https://apireference.aspose.com/email/java/com.aspose.email/exchangeclient#fetchMessage\(java.lang.String\)) método. Este método acepta la URI del mensaje como parámetro y devuelve una instancia de la clase [MailMessage](https://apireference.aspose.com/email/java/com.aspose.email/mailmessage). La clase [MailMessage](https://apireference.aspose.com/email/java/com.aspose.email/mailmessage) proporciona detalles del mensaje como el cuerpo, los encabezados y los archivos adjuntos.

{{% /alert %}} 
## **Recuperar mensajes de una bandeja de entrada del servidor Exchange**
Para recuperar mensajes de la bandeja de entrada del servidor Exchange:

1. Cree una instancia del tipo [ExchangeClient](https://apireference.aspose.com/email/java/com.aspose.email/exchangeclient).
1. Especifique el nombre del servidor, el nombre de usuario, la contraseña y el dominio.
1. Llame al [listMessages](https://apireference.aspose.com/email/java/com.aspose.email/exchangeclient#listMessages\(java.lang.String\)) método para obtener la [ExchangeMessageInfoCollection](https://apireference.aspose.com/email/java/com.aspose.email/exchangemessageinfocollection).
1. Recorra la colección [ExchangeMessageInfoCollection](https://apireference.aspose.com/email/java/com.aspose.email/exchangemessageinfocollection) para obtener los valores de [ExchangeMessageInfo.getUniqueUri](https://apireference.aspose.com/email/java/com.aspose.email/ExchangeMessageInfo#getUniqueUri\(\)).
1. Llame a [ExchangeClient.fetchMessage()](https://apireference.aspose.com/email/java/com.aspose.email/exchangeclient#fetchMessage\(java.lang.String\)) y pase [ExchangeMessageInfo.getUniqueUri](https://apireference.aspose.com/email/java/com.aspose.email/ExchangeMessageInfo#getUniqueUri\(\)) como parámetro.

El siguiente fragmento de código se conecta a la bandeja de entrada del servidor Exchange y recupera todos los mensajes.

{{< gist "aspose-com-gists" "709d733586ce50505c3bca3f6e8bd18d" "Examples-src-main-java-com-aspose-email-examples-exchange-FetchMessagesFromAnExchangeServerMailbox-FetchMessagesFromAnExchangeServerMailbox.java" >}}