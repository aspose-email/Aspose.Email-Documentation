---
title: "Guardar mensajes de la bandeja de entrada del servidor Exchange usando WebDav"
url: /es/java/save-messages-from-exchange-server-mailbox-using-webdav/
weight: 90
type: docs
---

Este artículo muestra cómo obtener mensajes de la bandeja de entrada de un servidor Exchange y guardarlos en disco en formatos EML y MSG.
## **Guardar mensajes de una bandeja de entrada de Exchange en EML**
Para obtener mensajes y guardarlos en formato EML:

1. Cree una instancia de la clase [ExchangeClient](https://apireference.aspose.com/email/java/com.aspose.email/exchangeclient).
1. Proporcione el nombre del servidor, el nombre de usuario, la contraseña y el dominio.
1. Llame al método [ExchangeClient.listMessages()](https://apireference.aspose.com/email/java/com.aspose.email/exchangeclient#listMessages\(java.lang.String\)) para obtener una instancia de la colección [ExchangeMessagesInfoCollection](https://apireference.aspose.com/email/java/com.aspose.email/ExchangeMessageInfoCollection).
1. Recorra la colección [ExchangeMessagesInfoCollection](https://apireference.aspose.com/email/java/com.aspose.email/ExchangeMessageInfoCollection) para obtener la URI única de cada mensaje.
1. Llame al método [ExchangeClient.saveMessage()](https://apireference.aspose.com/email/java/com.aspose.email/exchangeclient#saveMessage\(java.lang.String,%20java.io.OutputStream\)) y pase la URI única como parámetro.
1. Proporcione un método [saveMessage()](https://apireference.aspose.com/email/java/com.aspose.email/exchangeclient#saveMessage\(java.lang.String,%20java.io.OutputStream\)) con una ruta a donde desea guardar el archivo.
 

{{< gist "aspose-com-gists" "709d733586ce50505c3bca3f6e8bd18d" "Examples-src-main-java-com-aspose-email-examples-exchange-SaveMessagesFromExchangeServerMailbox-SaveMessagesAsEML.java" >}}
## **Guardar mensajes en un OutputStream**
En lugar de guardar archivos EML en el disco, es posible guardarlos en un OutputStream. Esto es útil cuando desea guardar el flujo en alguna ubicación de almacenamiento como una base de datos. Una vez que el flujo se ha guardado en una base de datos, puede recargar el archivo EML en la clase [MailMessage](https://apireference.aspose.com/email/java/com.aspose.email/MailMessage).

Los fragmentos de código a continuación guardan mensajes de una bandeja de entrada de Exchange en un flujo de memoria.

{{< gist "aspose-com-gists" "709d733586ce50505c3bca3f6e8bd18d" "Examples-src-main-java-com-aspose-email-examples-exchange-SaveMessagesFromExchangeServerMailbox-SaveMessagesToOutputStream.java" >}}
## **Guardar mensajes en formato MSG**
El método [ExchangeClient.saveMessage()](https://apireference.aspose.com/email/java/com.aspose.email/exchangeclient#saveMessage\(java.lang.String,%20java.io.OutputStream\)) puede guardar directamente el mensaje en formato EML. Para guardar los mensajes en formato MSG, primero, llame al método [ExchangeClient.fetchMessage()](https://apireference.aspose.com/email/java/com.aspose.email/exchangeclient#fetchMessage\(java.lang.String\)) que devuelve una instancia de la clase [MailMessage](https://apireference.aspose.com/email/java/com.aspose.email/MailMessage). Luego, llame al método [MailMessage.save()](https://apireference.aspose.com/email/java/com.aspose.email/MailMessage#save\(java.io.OutputStream\)) para guardar el mensaje en MSG.

El fragmento de código a continuación obtiene mensajes de una bandeja de entrada de Exchange y los guarda en formato MSG.

{{< gist "aspose-com-gists" "709d733586ce50505c3bca3f6e8bd18d" "Examples-src-main-java-com-aspose-email-examples-exchange-SaveMessagesFromExchangeServerMailbox-SaveMessagesInMSGFormat.java" >}}