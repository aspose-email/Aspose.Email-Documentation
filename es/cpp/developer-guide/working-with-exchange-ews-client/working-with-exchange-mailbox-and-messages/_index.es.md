---
title: "Trabajando con el Buzón de Exchange y Mensajes"
url: /es/cpp/working-with-exchange-mailbox-and-messages/
weight: 20
type: docs
---

## **Obteniendo Información del Buzón Usando EWS**
Puedes obtener información del buzón de un servidor Exchange llamando al método [GetMailboxInfo](https://apireference.aspose.com/email/cpp/class/aspose.email.clients.exchange.web_service.i_e_w_s_client#ab7a471f46b5ebe0e3bf2c7f9166e2927) de la clase [IEWSClient](https://apireference.aspose.com/email/cpp/class/aspose.email.clients.exchange.web_service.i_e_w_s_client). Retorna una instancia del tipo [ExchangeMailboxInfo](https://apireference.aspose.com/email/cpp/class/aspose.email.clients.exchange.exchange_mailbox_info). Obtén información del buzón desde propiedades como MailboxUri, InboxUri, y DraftsUri. Este artículo muestra cómo acceder a la información del buzón usando los Servicios Web de Exchange.

Para conectarte al servidor Exchange usando los Servicios Web de Exchange (EWS), utiliza la clase [IEWSClient](https://apireference.aspose.com/email/cpp/class/aspose.email.clients.exchange.web_service.i_e_w_s_client). Esta clase utiliza EWS para conectarse y gestionar elementos en un servidor Exchange. El siguiente fragmento de código te muestra cómo obtener información del buzón usando los servicios web de exchange.

{{< gist "aspose-com-gists" "525dd06c8783ebb18fb75cfc4b31d1ef" "Examples-Cpp-source-Exchange_EWS-GetMailboxInformationFromExchangeWebServices-GetMailboxInformationFromExchangeWebServices.cpp" >}}
## **Enviando Mensajes de Correo Electrónico**
Puedes enviar mensajes de correo electrónico usando un servidor Exchange con el método [IEWSClient->Send()](https://apireference.aspose.com/email/cpp/class/aspose.email.clients.exchange.web_service.i_e_w_s_client#a02875ffd55c4033e7d88007a9ac2a83c) que acepta una instancia de [MailMessage](https://apireference.aspose.com/email/cpp/class/aspose.email.mail_message) como parámetro y envía el correo. Este artículo explica cómo enviar mensajes de correo electrónico usando los Servicios Web de Exchange.

El siguiente fragmento de código te muestra cómo enviar mensajes de correo electrónico usando [IEWSClient](https://apireference.aspose.com/email/cpp/class/aspose.email.clients.exchange.web_service.i_e_w_s_client).

{{< gist "aspose-com-gists" "525dd06c8783ebb18fb75cfc4b31d1ef" "Examples-Cpp-source-Exchange_EWS-SendEmailMessagesUsingExchangeWebServices-SendEmailMessagesUsingExchangeWebServices.cpp" >}}
## **Leyendo Correos Electrónicos del Buzón de Otro Usuario**
Algunas cuentas en los servidores Exchange tienen el derecho de acceder a múltiples buzones, y algunos usuarios tienen múltiples cuentas de correo electrónico en el mismo servidor Exchange. En ambos casos, los usuarios pueden acceder a los buzones de otros usuarios usando Aspose.Email. Esta API proporciona un mecanismo para acceder a carpetas y correos electrónicos de otros buzones usando la clase [IEWSClient](https://apireference.aspose.com/email/cpp/class/aspose.email.clients.exchange.web_service.i_e_w_s_client). Esta funcionalidad se puede lograr utilizando el método sobrecargado [GetMailboxInfo()](https://apireference.aspose.com/email/cpp/class/aspose.email.clients.exchange.web_service.i_e_w_s_client#ac95e7c7a5e8678b70b4f5c4356d88582) y proporcionando la dirección de correo electrónico del usuario como un parámetro.

El siguiente fragmento de código te muestra cómo leer correos electrónicos usando la clase [IEWSClient](https://apireference.aspose.com/email/cpp/class/aspose.email.clients.exchange.web_service.i_e_w_s_client).

{{< gist "aspose-com-gists" "525dd06c8783ebb18fb75cfc4b31d1ef" "Examples-Cpp-source-Exchange_EWS-AccessAnotherMailboxUsingExchangeWebServiceClient-1.cpp" >}}
## **Listando Mensajes**
Una lista de los mensajes de correo electrónico en un buzón de Exchange se puede obtener llamando al método [ListMessages](https://apireference.aspose.com/email/cpp/class/aspose.email.clients.exchange.web_service.i_e_w_s_client#a37cfefda7e1ab560a073b3e31f4d27ca). Obtén la información básica sobre los mensajes, como asunto, de, a y ID del mensaje, usando el método [ListMessages](https://apireference.aspose.com/email/cpp/class/aspose.email.clients.exchange.web_service.i_e_w_s_client#a37cfefda7e1ab560a073b3e31f4d27ca).
### **Listado Simple de Mensajes**
Para listar los mensajes en un buzón de Exchange:

1. Crea una instancia de la clase [IEWSClient](https://apireference.aspose.com/email/cpp/class/aspose.email.clients.exchange.web_service.i_e_w_s_client).
1. Llama al método [ListMessages](https://apireference.aspose.com/email/cpp/class/aspose.email.clients.exchange.web_service.i_e_w_s_client#a37cfefda7e1ab560a073b3e31f4d27ca) para obtener la colección de mensajes.
1. Recorre la colección y muestra la información del mensaje.

El siguiente fragmento de código te muestra cómo conectarte a un servidor exchange usando EWS y listar mensajes de la carpeta de entrada.

{{< gist "aspose-com-gists" "525dd06c8783ebb18fb75cfc4b31d1ef" "Examples-Cpp-source-Exchange_EWS-ListingMessagesUsingEWS-ListingMessagesUsingEWS.cpp" >}}
### **Listando Mensajes desde Diferentes Carpetas**
El fragmento de código anterior lista todos los mensajes en la carpeta de entrada. También es posible obtener la lista de mensajes de otras carpetas. El método [ListMessages](https://apireference.aspose.com/email/cpp/class/aspose.email.clients.exchange.web_service.i_e_w_s_client#a37cfefda7e1ab560a073b3e31f4d27ca) acepta una URI de carpeta como parámetro. Siempre que la URI de la carpeta sea válida, puedes obtener la lista de mensajes de esa carpeta. Usa el [IEWSClient](https://apireference.aspose.com/email/cpp/class/aspose.email.clients.exchange.web_service.i_e_w_s_client)->[get_MailboxInfo](https://apireference.aspose.com/email/cpp/class/aspose.email.clients.exchange.web_service.i_e_w_s_client#a63b3972a738e652a9bab4e3fcfd23a26)->xxxFolderUri propiedad para obtener la URI de diferentes carpetas. El resto del código es el mismo que para obtener una lista de mensajes. El siguiente fragmento de código te muestra cómo listar mensajes desde diferentes carpetas usando EWS.

{{< gist "aspose-com-gists" "525dd06c8783ebb18fb75cfc4b31d1ef" "Examples-Cpp-source-Exchange_EWS-ListingMessagesFromFolders-ListingMessagesFromFolders.cpp" >}}
### **Listando Mensajes con Soporte de Paginación**
El siguiente fragmento de código te muestra cómo obtener una lista de mensajes con soporte de paginación.

{{< gist "aspose-com-gists" "525dd06c8783ebb18fb75cfc4b31d1ef" "Examples-Cpp-source-Exchange_EWS-PagingSupportForListingMessages-PagingSupportForListingMessages.cpp" >}}
### **Obteniendo Información del Tipo de Mensaje desde ExchangeMessageInfo**
{{< gist "aspose-com-gists" "525dd06c8783ebb18fb75cfc4b31d1ef" "Examples-Cpp-source-Exchange_EWS-GetMessageTypeFromExchangeMessageInfo-GetMessageTypeFromExchangeMessageInfo.cpp" >}}
## **Guardando Mensajes**
Este artículo muestra cómo obtener mensajes de un buzón de servidor Exchange y guardarlos en disco en formatos EML y MSG:

- Guardar como EML en disco.
- Guardar en un flujo de memoria.
- Guardar como MSG.
### **Guardando Mensajes en EML**
Para obtener mensajes y guardar en formato EML:

1. Crea una instancia de la clase [IEWSClient](https://apireference.aspose.com/email/cpp/class/aspose.email.clients.exchange.web_service.i_e_w_s_client).
1. Proporciona el mailboxUri, nombre de usuario, contraseña y dominio.
1. Llama al método [IEWSClient->ListMessages()](https://apireference.aspose.com/email/cpp/class/aspose.email.clients.exchange.web_service.i_e_w_s_client#a37cfefda7e1ab560a073b3e31f4d27ca) para obtener una instancia de la colección [ExchangeMessagesInfoCollection](https://apireference.aspose.com/email/cpp/class/aspose.email.clients.exchange.exchange_message_info_collection).
1. Recorre la colección [ExchangeMessagesInfoCollection](https://apireference.aspose.com/email/cpp/class/aspose.email.clients.exchange.exchange_message_info_collection) para obtener la URI única de cada mensaje.
1. Llama al método [IEWSClient->SaveMessage()](https://apireference.aspose.com/email/cpp/class/aspose.email.clients.exchange.web_service.i_e_w_s_client#a1a735b25973171ac5111c3469a54f7fa) y pasa la URI única y la ubicación de guardado como parámetros.

El siguiente fragmento de código te muestra cómo usar EWS para conectarte al servidor Exchange y guardar mensajes como archivos EML.

{{< gist "aspose-com-gists" "525dd06c8783ebb18fb75cfc4b31d1ef" "Examples-Cpp-source-Exchange_EWS-SaveMessagesUsingExchangeWebServices-SaveMessagesUsingExchangeWebServices.cpp" >}}
### **Guardando Mensajes en un Flujo de Memoria**
En lugar de guardar archivos EML en disco, es posible guardarlos en un flujo de memoria. Esto es útil cuando deseas guardar el flujo en algún lugar de almacenamiento como una base de datos. Una vez que el flujo ha sido guardado en una base de datos, puedes recargar el archivo EML en la clase [MailMessage](https://apireference.aspose.com/email/cpp/class/aspose.email.mail_message). El siguiente fragmento de código te muestra cómo guardar mensajes de un buzón de servidor Exchange en un flujo de memoria usando EWS.

{{< gist "aspose-com-gists" "525dd06c8783ebb18fb75cfc4b31d1ef" "Examples-Cpp-source-Exchange_EWS-SaveMessagesToMemoryStreamUsingEWS-SaveMessagesToMemoryStream.cpp" >}}
### **Guardando Mensajes en Formato MSG**
El método [IEWSClient->SaveMessage()](https://apireference.aspose.com/email/cpp/class/aspose.email.clients.exchange.web_service.i_e_w_s_client#a1a735b25973171ac5111c3469a54f7fa) puede guardar directamente el mensaje en formato EML. Para guardar los mensajes en formato MSG, primero, llama al método [IEWSClient->FetchMessage()](https://apireference.aspose.com/email/cpp/class/aspose.email.clients.exchange.web_service.i_e_w_s_client#ae0edf4afafbe6339541687aeacc84905) que retorna una instancia de la clase [MailMessage](https://apireference.aspose.com/email/cpp/class/aspose.email.mail_message). Luego, llama al método [MailMessage->Save()](https://apireference.aspose.com/email/cpp/class/aspose.email.mail_message#a41d3ada3ca8b7ca8130629b616f0b91c) para guardar el mensaje en MSG. El siguiente fragmento de código te muestra cómo obtener mensajes de un buzón de servidor Exchange y guardarlos en formato MSG usando EWS.

{{< gist "aspose-com-gists" "525dd06c8783ebb18fb75cfc4b31d1ef" "Examples-Cpp-source-Exchange_EWS-SaveMessagesInMSGFormatExchangeEWS-SaveMessagesInMSGFormatExchangeEWS.cpp" >}}
## **Obteniendo ExchangeMessageInfo desde la URI del Mensaje**
Un mensaje de correo electrónico se representa por su identificador único, URI, y es una parte integral del objeto ExchangeMessageInfo. En caso de que solo se disponga de la URI del mensaje, entonces el objeto [ExchangeMessageInfo](https://apireference.aspose.com/email/cpp/class/aspose.email.clients.exchange.exchange_message_info) también se puede recuperar usando esta información disponible. La versión sobrecargada de [ListMessages](https://apireference.aspose.com/email/cpp/class/aspose.email.clients.exchange.web_service.i_e_w_s_client#a2b3b4ebfdd9423eeb63d59b5e74cc53a) toma una lista de Ids y retorna una colección de [ExchangeMessageInfoCollection](https://apireference.aspose.com/email/cpp/class/aspose.email.clients.exchange.exchange_message_info_collection). El siguiente fragmento de código te muestra cómo obtener [ExchangeMessageInfo](https://apireference.aspose.com/email/cpp/class/aspose.email.clients.exchange.exchange_message_info) desde la URI del mensaje.

{{< gist "aspose-com-gists" "525dd06c8783ebb18fb75cfc4b31d1ef" "Examples-Cpp-source-Exchange_EWS-GetExchangeMessageInfoFromMessageURI-GetExchangeMessageInfoFromMessageURI.cpp" >}}
## **Obteniendo Mensajes de un Buzón de Servidor Exchange**
El método [ListMessages()](https://apireference.aspose.com/email/cpp/class/aspose.email.clients.exchange.web_service.i_e_w_s_client#aad8420247acd17cb1d73303ed1982d1e) se usa para obtener una lista de mensajes de un buzón del servidor Exchange. El método [ListMessages()](https://apireference.aspose.com/email/cpp/class/aspose.email.clients.exchange.web_service.i_e_w_s_client#aad8420247acd17cb1d73303ed1982d1e) obtiene información básica sobre los mensajes, por ejemplo, el asunto, el ID del mensaje, de y a. Para obtener los detalles completos del mensaje, Aspose.Email proporciona el método [IEWSClient->FetchMessage()](https://apireference.aspose.com/email/cpp/class/aspose.email.clients.exchange.web_service.i_e_w_s_client#ae0edf4afafbe6339541687aeacc84905). Este método acepta la URI del mensaje como parámetro y retorna una instancia de la clase [MailMessage](https://apireference.aspose.com/email/cpp/class/aspose.email.mail_message). La clase [MailMessage](https://apireference.aspose.com/email/cpp/class/aspose.email.mail_message) proporciona detalles del mensaje como el cuerpo, encabezados y adjuntos. Para obtener mensajes del Buzón del Servidor Exchange:

1. Crea una instancia del tipo [IEWSClient](https://apireference.aspose.com/email/cpp/class/aspose.email.clients.exchange.web_service.i_e_w_s_client).
1. Especifica el nombre del servidor, nombre de usuario, contraseña y dominio.
1. Llama al método [IEWSClient->ListMessages()](https://apireference.aspose.com/email/cpp/class/aspose.email.clients.exchange.web_service.i_e_w_s_client#a37cfefda7e1ab560a073b3e31f4d27ca) para obtener la [ExchangeMessagesInfoCollection](https://apireference.aspose.com/email/cpp/class/aspose.email.clients.exchange.exchange_message_info_collection).
1. Recorre la colección [ExchangeMessagesInfoCollection](https://apireference.aspose.com/email/cpp/class/aspose.email.clients.exchange.exchange_message_info_collection) para obtener los valores de [ExchangeMessageInfo->get_UniqueUri()](https://apireference.aspose.com/email/cpp/class/aspose.email.clients.exchange.exchange_message_info#a3cb9feb99e2ac195529cf9e5e7867cb7).
1. Llama a [IEWSClient->FetchMessage()](https://apireference.aspose.com/email/cpp/class/aspose.email.clients.exchange.web_service.i_e_w_s_client#ae0edf4afafbe6339541687aeacc84905) y pasa [ExchangeMessageInfo->get_UniqueUri()](https://apireference.aspose.com/email/cpp/class/aspose.email.clients.exchange.exchange_message_info#a3cb9feb99e2ac195529cf9e5e7867cb7) como parámetro.

El siguiente fragmento de código demuestra la obtención de todos los mensajes usando EWS.

{{< gist "aspose-com-gists" "525dd06c8783ebb18fb75cfc4b31d1ef" "Examples-Cpp-source-Exchange_EWS-FetchMessageUsingEWS-FetchMessageUsingEWS.cpp" >}}
## **Tamaño del Mensaje Preobtenido**
Microsoft Outlook InterOp proporciona la función de recuperar el tamaño del mensaje antes de realmente obtener el mensaje completo del servidor. En el caso de la API de Aspose.Email, la información resumida recuperada del servidor Exchange está representada por la clase [ExchangeMessageInfo](https://apireference.aspose.com/email/cpp/class/aspose.email.clients.exchange.exchange_message_info). Proporciona la función de recuperar el tamaño del mensaje usando la propiedad [Size](https://apireference.aspose.com/email/cpp/class/aspose.email.clients.message_info_base#a04bc106203ed5cfec65f4d0320d14e8a). Con el fin de recuperar el tamaño del mensaje, se utiliza la llamada estándar a [IEWSClient->ListMessages()](https://apireference.aspose.com/email/cpp/class/aspose.email.clients.exchange.web_service.i_e_w_s_client#a37cfefda7e1ab560a073b3e31f4d27ca) para recuperar la [ExchangeMessagesInfoCollection](https://apireference.aspose.com/email/cpp/class/aspose.email.clients.exchange.exchange_message_info_collection). El siguiente fragmento de código te muestra cómo mostrar el tamaño del mensaje usando la [ExchangeMessageInfo](https://apireference.aspose.com/email/cpp/class/aspose.email.clients.exchange.exchange_message_info) clase.

{{< gist "aspose-com-gists" "525dd06c8783ebb18fb75cfc4b31d1ef" "Examples-Cpp-source-Exchange_EWS-PreFetchMessageSizeUsingIEWSClient-PreFetchMessageSizeUsingIEWSClient.cpp" >}}
## **Descargar Mensajes de Carpetas Públicas**
Microsoft Exchange Server permite a los usuarios crear carpetas públicas y publicar mensajes en ellas. Para hacer esto a través de tu aplicación, usa la clase [EWSClient](https://apireference.aspose.com/email/cpp/class/aspose.email.clients.exchange.web_service.e_w_s_client) de Aspose.Email para conectarte al servidor Exchange y leer y descargar mensajes y publicaciones de carpetas públicas. El siguiente fragmento de código te muestra cómo leer todas las carpetas públicas y subcarpetas, y listar y descargar cualquier mensaje encontrado en estas carpetas. Este ejemplo solo funciona con Microsoft Exchange Server 2007 o superior, ya que solo estos son compatibles con EWS.

{{< gist "aspose-com-gists" "525dd06c8783ebb18fb75cfc4b31d1ef" "Examples-Cpp-source-Exchange_EWS-DownloadMessagesFromPublicFolders-DownloadMessagesFromPublicFolders.cpp" >}}
## **Moviendo Mensajes**
Puedes mover mensajes de correo electrónico de una carpeta a otra con la ayuda del método Move de la clase [IEWSClient](https://apireference.aspose.com/email/cpp/class/aspose.email.clients.exchange.web_service.i_e_w_s_client). Toma los siguientes parámetros:

- La URI única del mensaje que se va a mover.
- La URI única de la carpeta de destino.
### **Moviendo Mensajes entre Carpetas**
El siguiente fragmento de código te muestra cómo mover un mensaje en un buzón de la carpeta de entrada a una carpeta llamada Procesados. En este ejemplo, la aplicación:

1. Lee los mensajes de la carpeta de entrada.
1. Procesa algunos de los mensajes según algunos criterios (en este ejemplo, encontramos una palabra clave en el asunto del mensaje).
1. Mueve los mensajes que cumplen con la condición dada a la carpeta procesada.

{{< gist "aspose-com-gists" "525dd06c8783ebb18fb75cfc4b31d1ef" "Examples-Cpp-source-Exchange_EWS-MoveMessageFromOneFolderToAnotherusingEWS-MoveMessageFromOneFolderToAnotherusingEWS.cpp" >}}
## **Eliminando Mensajes**
Puedes eliminar mensajes de correo electrónico de una carpeta con la ayuda del método [IEWSClient->DeleteMessage](https://apireference.aspose.com/email/cpp/class/aspose.email.clients.exchange.web_service.i_e_w_s_client#a576fb78dcbac3bdb8b2bb87cab5d33c1). Toma la URI única del mensaje como parámetro.

El siguiente fragmento de código te muestra cómo eliminar un mensaje de la carpeta de entrada. Para el propósito de este ejemplo, el código:

1. Lee los mensajes de la carpeta de entrada.
1. Procesa los mensajes según algunos criterios (en este ejemplo, encontramos una palabra clave en el asunto del mensaje).
1. Elimina el mensaje.

{{< gist "aspose-com-gists" "525dd06c8783ebb18fb75cfc4b31d1ef" "Examples-Cpp-source-Exchange_EWS-DeleteMessagesFromUsingEWS-DeleteMessagesFromusingEWS.cpp" >}}
## **Copiando Mensajes**
La API de Aspose.Email permite copiar un mensaje de una carpeta a otra utilizando el método [IEWSClient->CopyItem](https://apireference.aspose.com/email/cpp/class/aspose.email.clients.exchange.web_service.i_e_w_s_client#a6e340250e1e0f51d68d4ffe7727f4e7f). La versión sobrecargada de este método devuelve la URI única del mensaje copiado como se muestra en este artículo.
### **Copiando un Mensaje a Otra Carpeta**
El siguiente fragmento de código te muestra cómo copiar un mensaje a otra carpeta.

{{< gist "aspose-com-gists" "525dd06c8783ebb18fb75cfc4b31d1ef" "Examples-Cpp-source-Exchange_EWS-CopyingMessageToAnotherFolder-CopyingMessageToAnotherFolder.cpp" >}}