---
title: "Listado de mensajes del servidor Exchange usando WebDav"
url: /es/java/listing-messages-from-exchange-server-using-webdav/
weight: 60
type: docs
---

Una lista de los mensajes de correo electrónico en un buzón de Exchange se puede obtener llamando al [método ExchangeClient.listMessages()](https://apireference.aspose.com/email/java/com.aspose.email/exchangeclient#listMessages\(java.lang.String\)). Obtenga la información básica sobre los mensajes, como el asunto, de, para y el ID del mensaje, utilizando el [método listMessages()](https://apireference.aspose.com/email/java/com.aspose.email/exchangeclient#listMessages\(java.lang.String\)).

Este artículo muestra cómo conectarse a un servidor Exchange y listar los correos electrónicos en un buzón directamente o usando WebDav. Además, muestra cómo listar mensajes de diferentes carpetas y cómo listar mensajes por ID.
## **Listar mensajes del servidor Exchange**
Para listar los mensajes en un buzón de Exchange:

1. Cree una instancia de la [clase ExchangeClient](https://apireference.aspose.com/email/java/com.aspose.email/exchangeclient).
1. Llame al [método listMessages](https://apireference.aspose.com/email/java/com.aspose.email/exchangeclient#listMessages\(java.lang.String\)) y cree una colección de mensajes.
1. Recorra la colección y muestre la información del mensaje.

El fragmento de código a continuación se conecta al buzón de Exchange y obtiene la lista de mensajes de la carpeta Bandeja de entrada.

{{< gist "aspose-com-gists" "709d733586ce50505c3bca3f6e8bd18d" "Examples-src-main-java-com-aspose-email-examples-exchange-ListMessages-ListMessagesFromInboxFolderOnExchangeServer.java" >}}
## **Listado de mensajes de diferentes carpetas**
Los fragmentos de código anteriores listan todos los mensajes en la carpeta Bandeja de entrada. También es posible obtener la lista de mensajes de otras carpetas. El [método ExchangeClient.listMessages()](https://apireference.aspose.com/email/java/com.aspose.email/exchangeclient#listMessages\(java.lang.String\)) acepta una URI de carpeta como parámetro. Siempre que la URI de la carpeta sea válida, puede obtener la lista de mensajes de esa carpeta.

Use la propiedad ExchangeClient.getMailboxInfo().xxxFolderUri[](https://apireference.aspose.com/email/java/com.aspose.email/exchangeclient) para obtener la URI de diferentes carpetas. El resto del código es el mismo que para obtener una lista de mensajes.

{{< gist "aspose-com-gists" "709d733586ce50505c3bca3f6e8bd18d" "Examples-src-main-java-com-aspose-email-examples-exchange-ListMessages-ListMessagesFromOtherFoldersOnExchangeServer.java" >}}