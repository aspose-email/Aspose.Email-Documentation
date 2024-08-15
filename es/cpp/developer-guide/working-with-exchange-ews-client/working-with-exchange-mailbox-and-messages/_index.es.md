---
title: "Trabajar con el buzón y los mensajes de Exchange"
url: /es/cpp/working-with-exchange-mailbox-and-messages/
weight: 20
type: docs
---

## **Obtención de información de buzones mediante EWS**
Para obtener información sobre los buzones de correo de un servidor Exchange, llame al [GetMailboxInfo ](https://apireference.aspose.com/email/cpp/class/aspose.email.clients.exchange.web_service.i_e_w_s_client#ab7a471f46b5ebe0e3bf2c7f9166e2927)método del [IEWSClient](https://apireference.aspose.com/email/cpp/class/aspose.email.clients.exchange.web_service.i_e_w_s_client) clase. Devuelve una instancia de tipo [ExchangeMailboxInfo](https://apireference.aspose.com/email/cpp/class/aspose.email.clients.exchange.exchange_mailbox_info). Obtenga información sobre los buzones de correo de propiedades como MailboxURI, InboxURI y DraftSuri. En este artículo se muestra cómo acceder a la información de los buzones de correo mediante los servicios web de Exchange.

Para conectarse al servidor de Exchange mediante los servicios web de Exchange (EWS), utilice [IEWSClient](https://apireference.aspose.com/email/cpp/class/aspose.email.clients.exchange.web_service.i_e_w_s_client) clase. Esta clase usa EWS para conectarse a los elementos de un servidor Exchange y administrarlos. El siguiente fragmento de código muestra cómo obtener información sobre los buzones de correo mediante los servicios web de Exchange.



{{< gist "aspose-com-gists" "525dd06c8783ebb18fb75cfc4b31d1ef" "Examples-Cpp-source-Exchange_EWS-GetMailboxInformationFromExchangeWebServices-GetMailboxInformationFromExchangeWebServices.cpp" >}}
## **Envío de mensajes de correo electrónico**
Puede enviar mensajes de correo electrónico mediante un servidor Exchange con el [IEWSClient->Send()](https://apireference.aspose.com/email/cpp/class/aspose.email.clients.exchange.web_service.i_e_w_s_client#a02875ffd55c4033e7d88007a9ac2a83c) el método acepta un [MailMessage](https://apireference.aspose.com/email/cpp/class/aspose.email.mail_message) instancia como parámetro y envía el correo electrónico. En este artículo se explica cómo enviar mensajes de correo electrónico mediante los servicios web de Exchange.

El siguiente fragmento de código muestra cómo enviar mensajes de correo electrónico mediante [IEWSClient](https://apireference.aspose.com/email/cpp/class/aspose.email.clients.exchange.web_service.i_e_w_s_client).



{{< gist "aspose-com-gists" "525dd06c8783ebb18fb75cfc4b31d1ef" "Examples-Cpp-source-Exchange_EWS-SendEmailMessagesUsingExchangeWebServices-SendEmailMessagesUsingExchangeWebServices.cpp" >}}
## **Lectura de correos electrónicos del buzón de otro usuario**
Algunas cuentas de los servidores de Exchange tienen derecho a acceder a varios buzones de correo y algunos usuarios tienen varias cuentas de correo electrónico en el mismo servidor de Exchange. En ambos casos, los usuarios pueden acceder a los buzones de otros usuarios mediante Aspose.Email. Esta API proporciona un mecanismo para acceder a las carpetas y correos electrónicos de otros buzones mediante el [IEWSClient](https://apireference.aspose.com/email/cpp/class/aspose.email.clients.exchange.web_service.i_e_w_s_client) clase. Esta funcionalidad se puede lograr utilizando el sistema sobrecargado [GetMailboxInfo()](https://apireference.aspose.com/email/cpp/class/aspose.email.clients.exchange.web_service.i_e_w_s_client#ac95e7c7a5e8678b70b4f5c4356d88582) método y proporcionar la dirección de correo electrónico del usuario como parámetro.

En el siguiente fragmento de código se muestra cómo leer los correos electrónicos mediante el [IEWSClient](https://apireference.aspose.com/email/cpp/class/aspose.email.clients.exchange.web_service.i_e_w_s_client) class.



{{< gist "aspose-com-gists" "525dd06c8783ebb18fb75cfc4b31d1ef" "Examples-Cpp-source-Exchange_EWS-AccessAnotherMailboxUsingExchangeWebServiceClient-1.cpp" >}}
## **Publicar mensajes**
Para obtener una lista de los mensajes de correo electrónico de un buzón de Exchange, llame al [ListMessages](https://apireference.aspose.com/email/cpp/class/aspose.email.clients.exchange.web_service.i_e_w_s_client#a37cfefda7e1ab560a073b3e31f4d27ca) método. Obtenga la información básica sobre los mensajes, como el asunto, el origen y el identificador del mensaje, mediante el [ListMessages](https://apireference.aspose.com/email/cpp/class/aspose.email.clients.exchange.web_service.i_e_w_s_client#a37cfefda7e1ab560a073b3e31f4d27ca) method.
### **Listado de mensajes simples**
Para enumerar los mensajes de un buzón de Exchange:

1. Crea una instancia del [IEWSClient](https://apireference.aspose.com/email/cpp/class/aspose.email.clients.exchange.web_service.i_e_w_s_client) class.
1. Llame al [ListMessages](https://apireference.aspose.com/email/cpp/class/aspose.email.clients.exchange.web_service.i_e_w_s_client#a37cfefda7e1ab560a073b3e31f4d27ca) método para obtener la colección de mensajes.
1. Recorre la colección y muestra la información del mensaje.

El siguiente fragmento de código muestra cómo conectarse a un servidor de Exchange mediante EWS y muestra los mensajes de la carpeta de la bandeja de entrada.



{{< gist "aspose-com-gists" "525dd06c8783ebb18fb75cfc4b31d1ef" "Examples-Cpp-source-Exchange_EWS-ListingMessagesUsingEWS-ListingMessagesUsingEWS.cpp" >}}
### **Listar mensajes de diferentes carpetas**
El fragmento de código anterior muestra todos los mensajes de la carpeta Bandeja de entrada. También es posible obtener la lista de mensajes de otras carpetas. El [ListMessages](https://apireference.aspose.com/email/cpp/class/aspose.email.clients.exchange.web_service.i_e_w_s_client#a37cfefda7e1ab560a073b3e31f4d27ca) el método acepta un URI de carpeta como parámetro. Mientras el URI de la carpeta sea válido, puede obtener la lista de mensajes de esa carpeta. Usa el [IEWSClient](https://apireference.aspose.com/email/cpp/class/aspose.email.clients.exchange.web_service.i_e_w_s_client)->[get_MailboxInfo](https://apireference.aspose.com/email/cpp/class/aspose.email.clients.exchange.web_service.i_e_w_s_client#a63b3972a738e652a9bab4e3fcfd23a26)->Propiedad xxxFolderURI para obtener la URI de diferentes carpetas. El resto del código es el mismo que para obtener una lista de mensajes. El siguiente fragmento de código muestra cómo enumerar los mensajes de diferentes carpetas mediante EWS.



{{< gist "aspose-com-gists" "525dd06c8783ebb18fb75cfc4b31d1ef" "Examples-Cpp-source-Exchange_EWS-ListingMessagesFromFolders-ListingMessagesFromFolders.cpp" >}}
### **Listar mensajes con soporte de paginación**
El siguiente fragmento de código muestra cómo obtener una lista de mensajes con soporte de paginación.

{{< gist "aspose-com-gists" "525dd06c8783ebb18fb75cfc4b31d1ef" "Examples-Cpp-source-Exchange_EWS-PagingSupportForListingMessages-PagingSupportForListingMessages.cpp" >}}
### **Obtener información sobre el tipo de mensaje de ExchangeMessageInfo**
{{< gist "aspose-com-gists" "525dd06c8783ebb18fb75cfc4b31d1ef" "Examples-Cpp-source-Exchange_EWS-GetMessageTypeFromExchangeMessageInfo-GetMessageTypeFromExchangeMessageInfo.cpp" >}}
## **Guardar mensajes**
En este artículo se muestra cómo obtener mensajes de un buzón de Exchange Server y guardarlos en el disco en formatos EML y MSG:

- Guardar como EML en el disco.
- Guardar en la secuencia de memoria.
- Guardar como MSG.
### **Guardar mensajes en EML**
Para obtener mensajes y guardarlos en formato EML:

1. Crea una instancia del [IEWSClient](https://apireference.aspose.com/email/cpp/class/aspose.email.clients.exchange.web_service.i_e_w_s_client) class.
1. Proporcione la URI del buzón, el nombre de usuario, la contraseña y el dominio.
1. Llame al [IEWSClient->ListMessages()](https://apireference.aspose.com/email/cpp/class/aspose.email.clients.exchange.web_service.i_e_w_s_client#a37cfefda7e1ab560a073b3e31f4d27ca) método para obtener una instancia del [ExchangeMessagesInfoCollection](https://apireference.aspose.com/email/cpp/class/aspose.email.clients.exchange.exchange_message_info_collection) collection.
1. Recorre el [ExchangeMessagesInfoCollection](https://apireference.aspose.com/email/cpp/class/aspose.email.clients.exchange.exchange_message_info_collection) colección para obtener la URI única de cada mensaje.
1. Llame al [IEWSClient->SaveMessage()](https://apireference.aspose.com/email/cpp/class/aspose.email.clients.exchange.web_service.i_e_w_s_client#a1a735b25973171ac5111c3469a54f7fa) método y pase el URI único y guarde la ubicación como parámetros.

El siguiente fragmento de código muestra cómo usar EWS para conectarse al servidor Exchange y guardar los mensajes como archivos EML.



{{< gist "aspose-com-gists" "525dd06c8783ebb18fb75cfc4b31d1ef" "Examples-Cpp-source-Exchange_EWS-SaveMessagesUsingExchangeWebServices-SaveMessagesUsingExchangeWebServices.cpp" >}}
### **Guardar mensajes en un flujo de memoria**
En lugar de guardar los archivos EML en el disco, es posible guardarlos en una secuencia de memoria. Esto es útil cuando quieres guardar la transmisión en alguna ubicación de almacenamiento, como una base de datos. Una vez guardada la transmisión en una base de datos, puede volver a cargar el archivo EML en [MailMessage](https://apireference.aspose.com/email/cpp/class/aspose.email.mail_message) clase. El siguiente fragmento de código muestra cómo guardar los mensajes de un buzón de Exchange Server en un flujo de memoria mediante EWS.



{{< gist "aspose-com-gists" "525dd06c8783ebb18fb75cfc4b31d1ef" "Examples-Cpp-source-Exchange_EWS-SaveMessagesToMemoryStreamUsingEWS-SaveMessagesToMemoryStream.cpp" >}}
### **Guardar mensajes en formato MSG**
The [IEWSClient->SaveMessage()](https://apireference.aspose.com/email/cpp/class/aspose.email.clients.exchange.web_service.i_e_w_s_client#a1a735b25973171ac5111c3469a54f7fa) El método puede guardar directamente el mensaje en formato EML. Para guardar los mensajes en formato MSG, primero llame al [IEWSClient->FetchMessage()](https://apireference.aspose.com/email/cpp/class/aspose.email.clients.exchange.web_service.i_e_w_s_client#ae0edf4afafbe6339541687aeacc84905) método que devuelve una instancia del [MailMessage](https://apireference.aspose.com/email/cpp/class/aspose.email.mail_message) clase. Entonces llama al [MailMessage->Save()](https://apireference.aspose.com/email/cpp/class/aspose.email.mail_message#a41d3ada3ca8b7ca8130629b616f0b91c) método para guardar el mensaje en MSG. El siguiente fragmento de código muestra cómo obtener mensajes de un buzón de Exchange Server y guardarlos en formato MSG mediante EWS.



{{< gist "aspose-com-gists" "525dd06c8783ebb18fb75cfc4b31d1ef" "Examples-Cpp-source-Exchange_EWS-SaveMessagesInMSGFormatExchangeEWS-SaveMessagesInMSGFormatExchangeEWS.cpp" >}}
## **Obtener ExchangeMessageInfo del URI del mensaje**
Un mensaje de correo electrónico se representa mediante su identificador único, el URI, y es una parte integral del objeto ExchangeMessageInfo. En caso de que solo esté disponible el URI del mensaje, [ExchangeMessageInfo](https://apireference.aspose.com/email/cpp/class/aspose.email.clients.exchange.exchange_message_info) el objeto también se puede recuperar utilizando esta información disponible. La versión de sobrecarga de [ListMessages](https://apireference.aspose.com/email/cpp/class/aspose.email.clients.exchange.web_service.i_e_w_s_client#a2b3b4ebfdd9423eeb63d59b5e74cc53a) toma una lista de identificadores y devuelve un [ExchangeMessageInfoCollection](https://apireference.aspose.com/email/cpp/class/aspose.email.clients.exchange.exchange_message_info_collection) colección. El siguiente fragmento de código muestra cómo obtener [ExchangeMessageInfo](https://apireference.aspose.com/email/cpp/class/aspose.email.clients.exchange.exchange_message_info) del URI del mensaje.



{{< gist "aspose-com-gists" "525dd06c8783ebb18fb75cfc4b31d1ef" "Examples-Cpp-source-Exchange_EWS-GetExchangeMessageInfoFromMessageURI-GetExchangeMessageInfoFromMessageURI.cpp" >}}
## **Obtener mensajes de un buzón de correo de Exchange Server**
The [ListMessages()](https://apireference.aspose.com/email/cpp/class/aspose.email.clients.exchange.web_service.i_e_w_s_client#aad8420247acd17cb1d73303ed1982d1e) el método se usa para obtener una lista de mensajes de un buzón de Exchange Server. El [ListMessages()](https://apireference.aspose.com/email/cpp/class/aspose.email.clients.exchange.web_service.i_e_w_s_client#aad8420247acd17cb1d73303ed1982d1e) El método obtiene información básica sobre los mensajes, por ejemplo, el asunto, el identificador del mensaje, el origen y el destino. Para obtener los detalles completos del mensaje, Aspose.Email proporciona [IEWSClient->FetchMessage()](https://apireference.aspose.com/email/cpp/class/aspose.email.clients.exchange.web_service.i_e_w_s_client#ae0edf4afafbe6339541687aeacc84905) método. Este método acepta el URI del mensaje como parámetro y devuelve una instancia del [MailMessage](https://apireference.aspose.com/email/cpp/class/aspose.email.mail_message) clase. El [MailMessage](https://apireference.aspose.com/email/cpp/class/aspose.email.mail_message) La clase luego proporciona detalles del mensaje como el cuerpo, los encabezados y los archivos adjuntos. Para obtener mensajes del buzón de Exchange Server:

1. Crear una instancia de tipo [IEWSClient](https://apireference.aspose.com/email/cpp/class/aspose.email.clients.exchange.web_service.i_e_w_s_client).
1. Especifique el nombre del servidor, el nombre de usuario, la contraseña y el dominio.
1. Call [IEWSClient->ListMessages()](https://apireference.aspose.com/email/cpp/class/aspose.email.clients.exchange.web_service.i_e_w_s_client#a37cfefda7e1ab560a073b3e31f4d27ca) método para obtener el [ExchangeMessagesInfoCollection](https://apireference.aspose.com/email/cpp/class/aspose.email.clients.exchange.exchange_message_info_collection).
1. Recorre el [ExchangeMessagesInfoCollection](https://apireference.aspose.com/email/cpp/class/aspose.email.clients.exchange.exchange_message_info_collection) colección para obtener [ExchangeMessageInfo->get_UniqueUri()](https://apireference.aspose.com/email/cpp/class/aspose.email.clients.exchange.exchange_message_info#a3cb9feb99e2ac195529cf9e5e7867cb7) values.
1. Call [IEWSClient->FetchMessage()](https://apireference.aspose.com/email/cpp/class/aspose.email.clients.exchange.web_service.i_e_w_s_client#ae0edf4afafbe6339541687aeacc84905) y pase [ExchangeMessageInfo->get_UniqueUri()](https://apireference.aspose.com/email/cpp/class/aspose.email.clients.exchange.exchange_message_info#a3cb9feb99e2ac195529cf9e5e7867cb7) como parámetro.

El siguiente fragmento de código muestra cómo obtener todos los mensajes mediante EWS.



{{< gist "aspose-com-gists" "525dd06c8783ebb18fb75cfc4b31d1ef" "Examples-Cpp-source-Exchange_EWS-FetchMessageUsingEWS-FetchMessageUsingEWS.cpp" >}}
## **Tamaño del mensaje de captura previa**
Microsoft Outlook InterOp proporciona la función de recuperar el tamaño del mensaje antes de obtener el mensaje completo del servidor. En el caso de la API Aspose.Email, la información resumida recuperada del servidor de Exchange está representada por el [ExchangeMessageInfo](https://apireference.aspose.com/email/cpp/class/aspose.email.clients.exchange.exchange_message_info) clase. Proporciona la función de recuperar el tamaño del mensaje mediante el [Size](https://apireference.aspose.com/email/cpp/class/aspose.email.clients.message_info_base#a04bc106203ed5cfec65f4d0320d14e8a) propiedad. Para recuperar el tamaño del mensaje, la llamada estándar a [IEWSClient->ListMessages()](https://apireference.aspose.com/email/cpp/class/aspose.email.clients.exchange.web_service.i_e_w_s_client#a37cfefda7e1ab560a073b3e31f4d27ca) se usa para recuperar el [ExchangeMessagesInfoCollection](https://apireference.aspose.com/email/cpp/class/aspose.email.clients.exchange.exchange_message_info_collection). En el siguiente fragmento de código se muestra cómo mostrar el tamaño de los mensajes mediante el [ExchangeMessageInfo](https://apireference.aspose.com/email/cpp/class/aspose.email.clients.exchange.exchange_message_info) class.



{{< gist "aspose-com-gists" "525dd06c8783ebb18fb75cfc4b31d1ef" "Examples-Cpp-source-Exchange_EWS-PreFetchMessageSizeUsingIEWSClient-PreFetchMessageSizeUsingIEWSClient.cpp" >}}
## **Descargar mensajes de carpetas públicas**
Microsoft Exchange Server permite a los usuarios crear carpetas públicas y publicar mensajes en ellas. Para hacerlo a través de su aplicación, utilice Aspose.Email [EWSClient](https://apireference.aspose.com/email/cpp/class/aspose.email.clients.exchange.web_service.e_w_s_client) clase para conectarse al servidor Exchange y leer y descargar mensajes y publicaciones de carpetas públicas. En el siguiente fragmento de código se muestra cómo leer todas las carpetas y subcarpetas públicas, y cómo mostrar y descargar los mensajes que se encuentran en estas carpetas. Este ejemplo solo funciona con Microsoft Exchange Server 2007 o superior, ya que solo estos son compatibles con EWS.



{{< gist "aspose-com-gists" "525dd06c8783ebb18fb75cfc4b31d1ef" "Examples-Cpp-source-Exchange_EWS-DownloadMessagesFromPublicFolders-DownloadMessagesFromPublicFolders.cpp" >}}
## **Mensajes en movimiento**
Puede mover los mensajes de correo electrónico de una carpeta a otra con la ayuda del [IEWSClient](https://apireference.aspose.com/email/cpp/class/aspose.email.clients.exchange.web_service.i_e_w_s_client) método class Move. Toma los siguientes parámetros:

- El URI único del mensaje que se va a mover.
- El URI único de la carpeta de destino.
### **Mover mensajes entre carpetas**
El siguiente fragmento de código muestra cómo mover un mensaje de un buzón de la carpeta Bandeja de entrada a una carpeta denominada Procesado. En este ejemplo, la aplicación:

1. Lee los mensajes de la carpeta Bandeja de entrada.
1. Procesa algunos de los mensajes en función de algunos criterios (en este ejemplo, encontramos una palabra clave en el asunto del mensaje).
1. Mueve los mensajes que cumplen la condición dada a la carpeta procesada.

{{< gist "aspose-com-gists" "525dd06c8783ebb18fb75cfc4b31d1ef" "Examples-Cpp-source-Exchange_EWS-MoveMessageFromOneFolderToAnotherusingEWS-MoveMessageFromOneFolderToAnotherusingEWS.cpp" >}}
## **Eliminar mensajes**
Puede eliminar los mensajes de correo electrónico de una carpeta con la ayuda del [IEWSClient->DeleteMessage](https://apireference.aspose.com/email/cpp/class/aspose.email.clients.exchange.web_service.i_e_w_s_client#a576fb78dcbac3bdb8b2bb87cab5d33c1) método. Toma el URI único del mensaje como parámetro.

El siguiente fragmento de código muestra cómo eliminar un mensaje de la carpeta Bandeja de entrada. Para este ejemplo, el código:

1. Lee los mensajes de la carpeta Bandeja de entrada.
1. Procesa los mensajes en función de algunos criterios (en este ejemplo, encontramos una palabra clave en el asunto del mensaje).
1. Elimina el mensaje.

{{< gist "aspose-com-gists" "525dd06c8783ebb18fb75cfc4b31d1ef" "Examples-Cpp-source-Exchange_EWS-DeleteMessagesFromUsingEWS-DeleteMessagesFromusingEWS.cpp" >}}
## **Copiar mensajes**
La API Aspose.Email permite copiar un mensaje de una carpeta a otra mediante el [IEWSClient->CopyItem](https://apireference.aspose.com/email/cpp/class/aspose.email.clients.exchange.web_service.i_e_w_s_client#a6e340250e1e0f51d68d4ffe7727f4e7f) método. La versión sobrecargada de este método devuelve el URI único del mensaje copiado, como se muestra en este artículo.
### **Copiar un mensaje a otra carpeta**
El siguiente fragmento de código muestra cómo copiar un mensaje a otra carpeta.



{{< gist "aspose-com-gists" "525dd06c8783ebb18fb75cfc4b31d1ef" "Examples-Cpp-source-Exchange_EWS-CopyingMessageToAnotherFolder-CopyingMessageToAnotherFolder.cpp" >}}
