---
title: "Características de utilidad"
url: /es/cpp/utility-features/
weight: 120
type: docs
---

## **Enviar un mensaje con opción de votación**
Microsoft Outlook permite a los usuarios crear una encuesta al redactar un mensaje nuevo. Esto se hace incluyendo opciones de votación como Sí, No, Quizás, etc. *FollowUpOptions* la clase ofrecida por Aspose.Email proporciona la *VotingButtons* propiedad que se puede usar para establecer u obtener el valor de las opciones de votación. Este artículo proporciona un ejemplo detallado de cómo crear un *MapiMessage* con opciones de votación para crear una encuesta y, a continuación, enviar el mensaje mediante el cliente Exchange Web Service (EWS).
### **Crear y enviar un mensaje con opciones de votación**
El siguiente fragmento de código muestra cómo crear un mensaje nuevo y, a continuación, enviarlo con opciones de votación.



{{< gist "aspose-com-gists" "525dd06c8783ebb18fb75cfc4b31d1ef" "Examples-Cpp-source-Exchange_EWS-CreateAndSendingMessageWithVotingOptions-CreateAndSendingMessageWithVotingOptions.cpp" >}}


El siguiente fragmento de código muestra la definición de *CreateTestMessage* método usado en el ejemplo anterior.



{{< gist "aspose-com-gists" "525dd06c8783ebb18fb75cfc4b31d1ef" "Examples-Cpp-source-Exchange_EWS-CreateAndSendingMessageWithVotingOptions-CreateTestMessage.cpp" >}}
## **Ignorar o omitir el certificado SSL no válido o caducado**
Aspose.Email puede gestionar los certificados SSL en Exchange Server mediante el [EWSClient](https://apireference.aspose.com/email/cpp/class/aspose.email.clients.exchange.web_service.e_w_s_client) clase. Si el certificado SSL ha caducado o deja de ser válido, Aspose.Email emite una excepción debido a que el certificado SSL no es válido. Evite estos errores en el certificado SSL ignorándolos mediante el método utilizado en el código siguiente. Registra el controlador de devolución de llamada en tu método main () o init () y agrega el siguiente método como miembro de la clase.



{{< gist "aspose-com-gists" "525dd06c8783ebb18fb75cfc4b31d1ef" "Examples-Cpp-source-Exchange_EWS-IgnoringInvalidSSLCertificates-IgnoringInvalidSSLCertificates.cpp" >}}
## **Creación de mensajes RE y FW a partir de archivos MSG**
[IEWSClient](https://apireference.aspose.com/email/cpp/class/aspose.email.clients.exchange.web_service.i_e_w_s_client) permite a los desarrolladores crear mensajes RE (Responder/Responder a todos) y FW (Reenviar) a partir de un mensaje fuente. El mensaje de origen se identifica seleccionando un mensaje en particular [ExchangeMessageInfo](https://apireference.aspose.com/email/cpp/class/aspose.email.clients.exchange.exchange_message_info) from [ExchangeMessageInfoCollection](https://apireference.aspose.com/email/cpp/class/aspose.email.clients.exchange.exchange_message_info_collection) obtenido por [ListMessages()](https://apireference.aspose.com/email/cpp/class/aspose.email.clients.exchange.web_service.i_e_w_s_client#aad8420247acd17cb1d73303ed1982d1e). El otro argumento es el actual [MailMessage](https://apireference.aspose.com/email/cpp/class/aspose.email.mail_message) para enviarse como mensaje RE o FW. El siguiente fragmento de código muestra cómo enviar un mensaje y, a continuación, responder a ese mensaje y reenviarlo. Para realizar esta tarea:

1. Inicialice el [IEWSClient](https://apireference.aspose.com/email/cpp/class/aspose.email.clients.exchange.web_service.i_e_w_s_client) objetar proporcionando credenciales válidas.
1. Envía algunos mensajes de muestra.
1. Llame al [Reply()](https://apireference.aspose.com/email/cpp/class/aspose.email.clients.exchange.web_service.i_e_w_s_client#a2d925824adc83ffdebeb7d135bd99099), [ReplyAll()](https://apireference.aspose.com/email/cpp/class/aspose.email.clients.exchange.web_service.i_e_w_s_client#ac08b12a3db4f1e20eaaa0d5f99c27c41) and [Forward()](https://apireference.aspose.com/email/cpp/class/aspose.email.clients.exchange.web_service.i_e_w_s_client#a1040eb913667b6702b0253e48a48ec27) métodos para enviar mensajes.



{{< gist "aspose-com-gists" "525dd06c8783ebb18fb75cfc4b31d1ef" "Examples-Cpp-source-Exchange_EWS-CreateREAndFWMessages-CreateREAndFWMessages.cpp" >}}
## **Agregar encabezados en las solicitudes de EWS**
La API Aspose.Email permite agregar encabezados a las solicitudes de Exchange. Esto se puede usar para agregar encabezados a las solicitudes de EWS para diferentes encabezados que se pueden usar para diferentes propósitos. Un ejemplo de ello podría ser agregar el encabezado X-AnchorMailbox, que se usa para gestionar los problemas de limitación en el servidor Exchange. El [AddHeader](https://apireference.aspose.com/email/cpp/class/aspose.email.clients.exchange.web_service.i_e_w_s_client#a93b0dd8364564686a15e720d8e5a4e9f) método del [IEWSClient](https://apireference.aspose.com/email/cpp/class/aspose.email.clients.exchange.web_service.i_e_w_s_client) se usa para agregar encabezados a las solicitudes de EWS, como se muestra en el siguiente fragmento de código.



{{< gist "aspose-com-gists" "525dd06c8783ebb18fb75cfc4b31d1ef" "Examples-Cpp-source-Exchange_EWS-AddingHeadersToEWSRequests-AddingHeadersToEWSRequests.cpp" >}}
## **Trabajando con mensajería unificada**
Aspose.Email puede recuperar información de mensajería unificada de Exchange Server 2010. En la actualidad, se admite la mensajería unificada, como la obtención de información de configuración, el inicio de una llamada saliente, la recuperación de la información de llamadas telefónicas por identificador de llamada y la desconexión de una llamada telefónica por ID. En el siguiente ejemplo de código se muestra cómo recuperar la información de configuración de la mensajería unificada de Microsoft Exchange Server 2010.



{{< gist "aspose-com-gists" "525dd06c8783ebb18fb75cfc4b31d1ef" "Examples-Cpp-source-Exchange_EWS-GettingUnifiedMessagingConfigurationInformation-GettingUnifiedMessagingConfigurationInformation.cpp" >}}
## **Consejos para recibir correo**
Microsoft Exchange Server agregó varias funciones nuevas con Exchange Server 2010 y 2013. Una de ellas permite a los usuarios recibir consejos sobre el correo electrónico a la hora de redactar un mensaje de correo electrónico. Estos consejos son muy útiles ya que proporcionan información antes de enviar el correo electrónico. Por ejemplo, si una dirección de correo electrónico es incorrecta en la lista de destinatarios, se muestra una sugerencia para que sepas que la dirección de correo electrónico no es válida. Las sugerencias de correo también le permiten ver las respuestas de los usuarios que están fuera de la oficina antes de enviar un correo electrónico: Exchange Server (2010 y 2013) envía la sugerencia cuando se redacta el correo electrónico si uno o más de los destinatarios han enviado las respuestas de fuera de la oficina. Todas las funciones que se muestran en este artículo requieren el Service Pack 1 de Microsoft Exchange Server 2010. En el siguiente fragmento de código se muestra cómo utilizar el [EWSClient](https://apireference.aspose.com/email/cpp/class/aspose.email.clients.exchange.web_service.e_w_s_client) clase que usa los servicios web de Exchange, disponible en Microsoft Exchange Server 2007 y versiones posteriores.



{{< gist "aspose-com-gists" "525dd06c8783ebb18fb75cfc4b31d1ef" "Examples-Cpp-source-Exchange_EWS-GetMailTips-GetMailTips.cpp" >}}
