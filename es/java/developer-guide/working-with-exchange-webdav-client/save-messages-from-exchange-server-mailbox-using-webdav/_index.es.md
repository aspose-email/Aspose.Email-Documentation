---
title: "Guardar mensajes del buzón de Exchange Server mediante WebDAV"
url: /es/java/save-messages-from-exchange-server-mailbox-using-webdav/
weight: 90
type: docs
---

En este artículo se muestra cómo obtener mensajes de un buzón de Exchange Server y guardarlos en el disco en formatos EML y MSG.
## **Guardar mensajes de un buzón de Exchange Server en EML**
Para obtener mensajes y guardarlos en formato EML:

1. Crea una instancia del [ExchangeClient](https://apireference.aspose.com/email/java/com.aspose.email/exchangeclient) class.
1. Proporcione el nombre del servidor, el nombre de usuario, la contraseña y el dominio.
1. Llame al [ExchangeClient.listMessages()](https://apireference.aspose.com/email/java/com.aspose.email/exchangeclient#listMessages\(java.lang.String\)) método para obtener una instancia del [ExchangeMessagesInfoCollection](https://apireference.aspose.com/email/java/com.aspose.email/ExchangeMessageInfoCollection) collection.
1. Recorre el [ExchangeMessagesInfoCollection](https://apireference.aspose.com/email/java/com.aspose.email/ExchangeMessageInfoCollection) colección para obtener la URI única de cada mensaje.
1. Llame al [ExchangeClient.saveMessage()](https://apireference.aspose.com/email/java/com.aspose.email/exchangeclient#saveMessage\(java.lang.String,%20java.io.OutputStream\)) método y pase la URI única como parámetro.
1. Proporcione un [saveMessage()](https://apireference.aspose.com/email/java/com.aspose.email/exchangeclient#saveMessage\(java.lang.String,%20java.io.OutputStream\)) método con una ruta al lugar donde desea guardar el archivo.
 

{{< gist "aspose-com-gists" "709d733586ce50505c3bca3f6e8bd18d" "Examples-src-main-java-com-aspose-email-examples-exchange-SaveMessagesFromExchangeServerMailbox-SaveMessagesAsEML.java" >}}
## **Guardar mensajes en un OutputStream**
En lugar de guardar los archivos EML en el disco, es posible guardarlos en un OutputStream. Esto es útil cuando quieres guardar la transmisión en alguna ubicación de almacenamiento, como una base de datos. Una vez guardada la transmisión en una base de datos, puede volver a cargar el archivo EML en [MailMessage](https://apireference.aspose.com/email/java/com.aspose.email/MailMessage) class.

Los fragmentos de código que aparecen a continuación guardan los mensajes de un buzón de Exchange Server en un flujo de memoria.

{{< gist "aspose-com-gists" "709d733586ce50505c3bca3f6e8bd18d" "Examples-src-main-java-com-aspose-email-examples-exchange-SaveMessagesFromExchangeServerMailbox-SaveMessagesToOutputStream.java" >}}
## **Guardar mensajes en formato MSG**
The [ExchangeClient.saveMessage()](https://apireference.aspose.com/email/java/com.aspose.email/exchangeclient#saveMessage\(java.lang.String,%20java.io.OutputStream\)) El método puede guardar directamente el mensaje en formato EML. Para guardar los mensajes en formato MSG, primero llame al [ExchangeClient.fetchMessage()](https://apireference.aspose.com/email/java/com.aspose.email/exchangeclient#fetchMessage\(java.lang.String\)) método que devuelve una instancia del [MailMessage](https://apireference.aspose.com/email/java/com.aspose.email/MailMessage) clase. Entonces llama al [MailMessage.save()](https://apireference.aspose.com/email/java/com.aspose.email/MailMessage#save\(java.io.OutputStream\)) método para guardar el mensaje en MSG.

El siguiente fragmento de código obtiene los mensajes de un buzón de Exchange Server y los guarda en formato MSG.

{{< gist "aspose-com-gists" "709d733586ce50505c3bca3f6e8bd18d" "Examples-src-main-java-com-aspose-email-examples-exchange-SaveMessagesFromExchangeServerMailbox-SaveMessagesInMSGFormat.java" >}}
