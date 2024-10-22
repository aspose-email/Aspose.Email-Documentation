---
title: "Funciones de Utilidad"
url: /es/cpp/utility-features/
weight: 120
type: docs
---

## **Enviar un Mensaje con Opción de Votación**
Microsoft Outlook permite a los usuarios crear una encuesta al redactar un nuevo mensaje. Esto se realiza incluyendo opciones de votación como Sí, No, Tal vez, etc. La clase *FollowUpOptions* ofrecida por Aspose.Email proporciona la propiedad *VotingButtons* que se puede usar para establecer o obtener el valor de las opciones de votación. Este artículo proporciona un ejemplo detallado de cómo crear un *MapiMessage* con opciones de votación para crear una encuesta y luego enviar el mensaje utilizando el cliente de Exchange Web Service (EWS).
### **Crear y Enviar un Mensaje con Opciones de Votación**
El siguiente fragmento de código muestra cómo crear un nuevo mensaje y luego enviarlo con opciones de votación.



{{< gist "aspose-com-gists" "525dd06c8783ebb18fb75cfc4b31d1ef" "Examples-Cpp-source-Exchange_EWS-CreateAndSendingMessageWithVotingOptions-CreateAndSendingMessageWithVotingOptions.cpp" >}}


El siguiente fragmento de código muestra la definición del método *CreateTestMessage* utilizado en el ejemplo anterior.



{{< gist "aspose-com-gists" "525dd06c8783ebb18fb75cfc4b31d1ef" "Examples-Cpp-source-Exchange_EWS-CreateAndSendingMessageWithVotingOptions-CreateTestMessage.cpp" >}}
## **Ignorar o Pasar por Alto Certificados SSL Inválidos o Caducados**
Aspose.Email puede manejar certificados SSL en Exchange Server utilizando la clase [EWSClient](https://apireference.aspose.com/email/cpp/class/aspose.email.clients.exchange.web_service.e_w_s_client). Si el certificado SSL ha caducado o se ha vuelto inválido, Aspose.Email lanza una excepción debido al certificado SSL inválido. Evite tales errores de certificado SSL ignorándolos utilizando el método que se muestra en el código a continuación. Registre el controlador de retorno en su método *main()* o *init()* y añada el método a continuación como miembro de la clase.



{{< gist "aspose-com-gists" "525dd06c8783ebb18fb75cfc4b31d1ef" "Examples-Cpp-source-Exchange_EWS-IgnoringInvalidSSLCertificates-IgnoringInvalidSSLCertificates.cpp" >}}
## **Crear mensajes RE y FW a partir de archivos MSG**
[IEWSClient](https://apireference.aspose.com/email/cpp/class/aspose.email.clients.exchange.web_service.i_e_w_s_client) permite a los desarrolladores crear mensajes RE (Responder/Responder a Todos) y FW (Reenviar) a partir de un mensaje fuente. El mensaje fuente se identifica seleccionando un *[ExchangeMessageInfo](https://apireference.aspose.com/email/cpp/class/aspose.email.clients.exchange.exchange_message_info)* particular de la *[ExchangeMessageInfoCollection](https://apireference.aspose.com/email/cpp/class/aspose.email.clients.exchange.exchange_message_info_collection)* obtenida mediante *[ListMessages()](https://apireference.aspose.com/email/cpp/class/aspose.email.clients.exchange.web_service.i_e_w_s_client#aad8420247acd17cb1d73303ed1982d1e)*. El otro argumento es el *[MailMessage](https://apireference.aspose.com/email/cpp/class/aspose.email.mail_message)* real que se enviará como mensaje RE o FW. El siguiente fragmento de código muestra cómo enviar un mensaje y luego responder a ese mensaje y reenviarlo. Para realizar esta tarea:

1. Inicialice el objeto *[IEWSClient](https://apireference.aspose.com/email/cpp/class/aspose.email.clients.exchange.web_service.i_e_w_s_client)* proporcionando credenciales válidas.
1. Envíe algunos mensajes de muestra.
1. Llame a los métodos *[Reply()](https://apireference.aspose.com/email/cpp/class/aspose.email.clients.exchange.web_service.i_e_w_s_client#a2d925824adc83ffdebeb7d135bd99099)*, *[ReplyAll()](https://apireference.aspose.com/email/cpp/class/aspose.email.clients.exchange.web_service.i_e_w_s_client#ac08b12a3db4f1e20eaaa0d5f99c27c41)* y *[Forward()](https://apireference.aspose.com/email/cpp/class/aspose.email.clients.exchange.web_service.i_e_w_s_client#a1040eb913667b6702b0253e48a48ec27)* para enviar mensajes.



{{< gist "aspose-com-gists" "525dd06c8783ebb18fb75cfc4b31d1ef" "Examples-Cpp-source-Exchange_EWS-CreateREAndFWMessages-CreateREAndFWMessages.cpp" >}}
## **Agregar Encabezados en Solicitudes de EWS**
La API de Aspose.Email permite agregar encabezados a las solicitudes de Exchange. Esto se puede usar para agregar encabezados a las solicitudes de EWS para diferentes encabezados que se pueden usar con diferentes propósitos. Un ejemplo de esto podría ser agregar el encabezado X-AnchorMailbox que se utiliza para gestionar los problemas de limitación en el servidor de Exchange. El método *[AddHeader](https://apireference.aspose.com/email/cpp/class/aspose.email.clients.exchange.web_service.i_e_w_s_client#a93b0dd8364564686a15e720d8e5a4e9f)* de *[IEWSClient](https://apireference.aspose.com/email/cpp/class/aspose.email.clients.exchange.web_service.i_e_w_s_client)* se utiliza para agregar encabezados a las solicitudes de EWS como se muestra en el siguiente fragmento de código.



{{< gist "aspose-com-gists" "525dd06c8783ebb18fb75cfc4b31d1ef" "Examples-Cpp-source-Exchange_EWS-AddingHeadersToEWSRequests-AddingHeadersToEWSRequests.cpp" >}}
## **Trabajando con Mensajería Unificada**
Aspose.Email puede recuperar información de mensajería unificada desde Exchange Server 2010. La mensajería unificada, como obtener información de configuración, iniciar una llamada saliente, recuperar información de llamadas telefónicas por ID de llamada y desconectar una llamada telefónica por ID, es compatible en este momento. El siguiente ejemplo de código muestra cómo recuperar información de configuración de mensajería unificada desde Microsoft Exchange Server 2010.



{{< gist "aspose-com-gists" "525dd06c8783ebb18fb75cfc4b31d1ef" "Examples-Cpp-source-Exchange_EWS-GettingUnifiedMessagingConfigurationInformation-GettingUnifiedMessagingConfigurationInformation.cpp" >}}
## **Obtener Consejos de Correo**
Microsoft Exchange Server agregó varias nuevas funciones con Exchange Server 2010 y 2013. Una de ellas permite a los usuarios obtener consejos de correo al redactar un mensaje de correo electrónico. Estos consejos son muy útiles ya que brindan información antes de que se envíe el correo electrónico. Por ejemplo, si una dirección de correo electrónico es incorrecta en la lista de destinatarios, se muestra un consejo para avisarle que la dirección de correo electrónico es inválida. Los consejos de correo también le permiten ver respuestas automáticas de fuera de la oficina antes de enviar un correo electrónico: el servidor de Exchange (2010 y 2013) envía el consejo de correo cuando se está redactando el correo electrónico si uno o más de los destinatarios han configurado respuestas automáticas fuera de la oficina. Se requiere Microsoft Exchange Server 2010 Service Pack 1 para todas las funciones demostradas en este artículo. El siguiente fragmento de código muestra cómo utilizar la clase *[EWSClient](https://apireference.aspose.com/email/cpp/class/aspose.email.clients.exchange.web_service.e_w_s_client)* que utiliza los Servicios Web de Exchange, disponibles en Microsoft Exchange Server 2007 y versiones posteriores.



{{< gist "aspose-com-gists" "525dd06c8783ebb18fb75cfc4b31d1ef" "Examples-Cpp-source-Exchange_EWS-GetMailTips-GetMailTips.cpp" >}}