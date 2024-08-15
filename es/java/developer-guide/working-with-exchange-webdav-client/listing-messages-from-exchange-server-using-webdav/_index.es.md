---
title: "Listado de mensajes de Exchange Server mediante WebDAV"
url: /es/java/listing-messages-from-exchange-server-using-webdav/
weight: 60
type: docs
---

Para obtener una lista de los mensajes de correo electrónico de un buzón de Exchange, llame al [ExchangeClient.listMessages()](https://apireference.aspose.com/email/java/com.aspose.email/exchangeclient#listMessages\(java.lang.String\)) método. Obtenga la información básica sobre los mensajes, como el asunto, el origen y el identificador del mensaje, mediante el [listMessages()](https://apireference.aspose.com/email/java/com.aspose.email/exchangeclient#listMessages\(java.lang.String\)) method.

En este artículo se muestra cómo conectarse a un servidor Exchange y enumerar los correos electrónicos de un buzón directamente o mediante WebDAV. Además, muestra cómo enumerar los mensajes de diferentes carpetas y cómo enumerar los mensajes por ID.
## **Listar mensajes de Exchange Server**
Para enumerar los mensajes de un buzón de Exchange:

1. Crea una instancia del [ExchangeClient](https://apireference.aspose.com/email/java/com.aspose.email/exchangeclient) class.
1. Llame al [listMessages](https://apireference.aspose.com/email/java/com.aspose.email/exchangeclient#listMessages\(java.lang.String\)) método y crear una colección de mensajes.
1. Recorre la colección y muestra la información del mensaje.

El siguiente fragmento de código se conecta al buzón de Exchange y obtiene la lista de mensajes de la carpeta Bandeja de entrada.

{{< gist "aspose-com-gists" "709d733586ce50505c3bca3f6e8bd18d" "Examples-src-main-java-com-aspose-email-examples-exchange-ListMessages-ListMessagesFromInboxFolderOnExchangeServer.java" >}}
## **Listar mensajes de diferentes carpetas**
Los fragmentos de código anteriores enumeran todos los mensajes de la carpeta Bandeja de entrada. También es posible obtener la lista de mensajes de otras carpetas. El [ExchangeClient.listMessages()](https://apireference.aspose.com/email/java/com.aspose.email/exchangeclient#listMessages\(java.lang.String\)) el método acepta un URI de carpeta como parámetro. Mientras el URI de la carpeta sea válido, puede obtener la lista de mensajes de esa carpeta.

Utilice ExchangeClient.getMailboxInfo () .xxxFolderURI[](https://apireference.aspose.com/email/java/com.aspose.email/exchangeclient) propiedad para obtener la URI de diferentes carpetas. El resto del código es el mismo que para obtener una lista de mensajes.

{{< gist "aspose-com-gists" "709d733586ce50505c3bca3f6e8bd18d" "Examples-src-main-java-com-aspose-email-examples-exchange-ListMessages-ListMessagesFromOtherFoldersOnExchangeServer.java" >}}
