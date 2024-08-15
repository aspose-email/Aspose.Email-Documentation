---
title: "Características de utilidad"
url: /es/net/utility-features/
weight: 120
type: docs
---


## **Enviar un mensaje con opción de votación**

Microsoft Outlook permite a los usuarios crear una encuesta al redactar un mensaje nuevo. Esto se hace incluyendo opciones de votación como Sí, No, Quizás, etc. La clase FollowupOptions que ofrece Aspose.Email proporciona la propiedad VotingButtons que se puede usar para establecer u obtener el valor de las opciones de votación. Este artículo proporciona un ejemplo detallado de cómo crear un MapiMessage con opciones de votación para crear una encuesta y, a continuación, enviar el mensaje mediante el cliente de Exchange Web Service (EWS).

### **Crear y enviar un mensaje con opciones de votación**

El siguiente fragmento de código muestra cómo crear un mensaje nuevo y, a continuación, enviarlo con opciones de votación.

{{< gist "aspose-email" "9e8fbeb51a8cbc4129dc71ca8cd55f0b" "Examples-CSharp-Exchange_EWS-CreateAndSendingMessageWithVotingOptions-CreateAndSendingMessageWithVotingOptions.cs" >}}

### **Métodos de muestra utilizados en los ejemplos**

El siguiente fragmento de código muestra cómo usar los métodos utilizados en el ejemplo anterior.

{{< gist "aspose-email" "9e8fbeb51a8cbc4129dc71ca8cd55f0b" "Examples-CSharp-Exchange_EWS-CreateAndSendingMessageWithVotingOptions-CreateTestMessage.cs" >}}

## **Ignorar o omitir el certificado SSL no válido o caducado**

Aspose.Email puede gestionar los certificados SSL en Exchange Server mediante ambos [ExchangeClient](https://reference.aspose.com/email/net/aspose.email.clients.exchange.dav/exchangeclient/) and [EWSClient](https://reference.aspose.com/email/net/aspose.email.clients.exchange.webservice/ewsclient/) clases. Si el certificado SSL ha caducado o deja de ser válido, Aspose.Email emite una excepción debido a que el certificado SSL no es válido. Evite estos errores en el certificado SSL ignorándolos mediante el método utilizado en el código siguiente. Registra el controlador de devolución de llamada en tu método main () o init () y agrega el siguiente método como miembro de la clase.

{{< gist "aspose-email" "9e8fbeb51a8cbc4129dc71ca8cd55f0b" "Examples-CSharp-Exchange_EWS-IgnoringInvalidSSLCertificates-IgnoringInvalidSSLCertificates.cs" >}}

## **Creación de mensajes RE y FW a partir de archivos MSG**

[IEWSClient](https://reference.aspose.com/email/net/aspose.email.clients.exchange.webservice/iewsclient/) permite a los desarrolladores crear mensajes RE (Responder/Responder a todos) y FW (Reenviar) a partir de un mensaje fuente. El mensaje de origen se identifica seleccionando un mensaje en particular [ExchangeMessageInfo](https://reference.aspose.com/email/net/aspose.email.clients.exchange/exchangemessageinfo/) from [ExchangeMessageInfoCollection](https://reference.aspose.com/email/net/aspose.email.clients.exchange/exchangemessageinfocollection/exchangemessageinfocollection/) obtenido por [IEWSClient.ListMessages()](https://reference.aspose.com/email/net/aspose.email.clients.exchange.webservice/iewsclient/listmessages/). El otro argumento es el actual [MailMessage](https://reference.aspose.com/email/net/aspose.email/mailmessage/) para enviarse como mensaje RE o FW. En el siguiente fragmento de código se muestra cómo crear una cuenta de ejemplo que se utilice para enviar un mensaje y, a continuación, se muestran las funciones de respuesta y reenvío de mensajes comparándolas con ese mensaje de ejemplo. Para realizar esta tarea:

1. Inicialice el [IEWSClient](https://reference.aspose.com/email/net/aspose.email.clients.exchange.webservice/iewsclient/) objetar proporcionando credenciales válidas.
1. Envía algunos mensajes de muestra.
1. Llame al [IEWSClient.Reply()](https://reference.aspose.com/email/net/aspose.email.clients.exchange.webservice/iewsclient/reply/), [IEWSClient.ReplyAll()](https://reference.aspose.com/email/net/aspose.email.clients.exchange.webservice/iewsclient/replyall/) and [IEWSClient.Forward()](https://reference.aspose.com/email/net/aspose.email.clients.exchange.webservice/iewsclient/forward/) funciones para enviar mensajes.

{{< gist "aspose-email" "9e8fbeb51a8cbc4129dc71ca8cd55f0b" "Examples-CSharp-Exchange_EWS-CreateREAndFWMessages-CreateREAndFWMessages.cs" >}}

## **Soporte para el seguimiento de correo electrónico**

La API Aspose.Email admite el seguimiento del correo electrónico mediante la notificación de disposición de mensajes (MDN). Esto se logra solicitando las confirmaciones de lectura y creando la información requerida. El [MailMessage.ReadReceiptTo](https://reference.aspose.com/email/net/aspose.email/mailmessage/readreceiptto/) la propiedad obtiene o establece la dirección de confirmación de lectura establecida. El [CreateReadReceipt](https://reference.aspose.com/email/net/aspose.email/mailmessage/createreadreceipt/) and [ReadReceiptRequested](https://reference.aspose.com/email/net/aspose.email.mapi/mapimessage/readreceiptrequested/) los métodos se utilizan para crear y recuperar la información si se solicitan confirmaciones de lectura. El siguiente fragmento de código muestra cómo realizar un seguimiento por correo electrónico mediante la API Aspose.Email.

{{< gist "aspose-email" "9e8fbeb51a8cbc4129dc71ca8cd55f0b" "Examples-CSharp-Exchange-EmailTracking-EmailTracking.cs" >}}

## **Soporte para iniciar sesión en clientes de Exchange**

La API Aspose.Email brinda la capacidad de proporcionar la función de registro del cliente de Exchange Web Service. Esto se puede lograr configurando el archivo App.config.

### **Registro para el cliente EWS**

{{< gist "aspose-email" "9e8fbeb51a8cbc4129dc71ca8cd55f0b" "LoggingForEWSClient.xml" >}}

## **Agregar encabezados en las solicitudes de EWS**

La API Aspose.Email permite agregar encabezados a las solicitudes de Exchange. Esto se puede usar para agregar encabezados a las solicitudes de EWS para diferentes encabezados que se pueden usar para diferentes propósitos. Un ejemplo de este tipo podría ser agregar el encabezado X-AnchorMailbox, que se usa para gestionar los problemas de limitación en el servidor Exchange. El [AddHeader](https://reference.aspose.com/email/net/aspose.email.clients.exchange.webservice/iewsclient/addheader/) método del [IEWSClient](https://reference.aspose.com/email/net/aspose.email.clients.exchange.webservice/iewsclient/) se usa para agregar encabezados a las solicitudes de EWS, como se muestra en el siguiente fragmento de código.

{{< gist "aspose-email" "9e8fbeb51a8cbc4129dc71ca8cd55f0b" "Examples-CSharp-Exchange_EWS-AddingHeadersToEWSRequests-AddingHeadersToEWSRequests.cs" >}}

## **Trabajando con mensajería unificada**

Aspose.Email puede recuperar información de mensajería unificada de Exchange Server 2010. En la actualidad, se admite la mensajería unificada, como la obtención de información de configuración, el inicio de una llamada saliente, la recuperación de la información de llamadas telefónicas por identificador de llamada y la desconexión de una llamada telefónica por ID. En el siguiente ejemplo de código se muestra cómo recuperar la información de configuración de la mensajería unificada de Microsoft Exchange Server 2010.

{{< gist "aspose-email" "9e8fbeb51a8cbc4129dc71ca8cd55f0b" "Examples-CSharp-Exchange_EWS-GettingUnifiedMessagingConfigurationInformation-GettingUnifiedMessagingConfigurationInformation.cs" >}}

## **Consejos para recibir correo**

Microsoft Exchange Server agregó varias funciones nuevas con Exchange Server 2010 y 2013. Una de ellas permite a los usuarios recibir consejos sobre el correo electrónico a la hora de redactar un mensaje de correo electrónico. Estos consejos son muy útiles ya que proporcionan información antes de enviar el correo electrónico. Por ejemplo, si una dirección de correo electrónico es incorrecta en la lista de destinatarios, se muestra una sugerencia para informarle de que la dirección de correo electrónico no es válida. Las sugerencias de correo también le permiten ver las respuestas de fuera de la oficina antes de enviar un correo electrónico: Exchange Server (2010 y 2013) envía la sugerencia de correo cuando se redacta el correo electrónico si uno o más de los destinatarios han establecido las respuestas de fuera de la oficina. Todas las funciones que se muestran en este artículo requieren el Service Pack 1 de Microsoft Exchange Server 2010. En el siguiente fragmento de código se muestra cómo utilizar el [EWSClient](https://reference.aspose.com/email/net/aspose.email.clients.exchange.webservice/ewsclient/) clase que usa los servicios web de Exchange, disponible en Microsoft Exchange Server 2007 y versiones posteriores.

{{< gist "aspose-email" "9e8fbeb51a8cbc4129dc71ca8cd55f0b" "Examples-CSharp-Exchange_EWS-GetMailTips-GetMailTips.cs" >}}

## **Suplantación de identidad de Exchange**

La suplantación de identidad de Exchange permite a alguien hacerse pasar por otra cuenta y realizar tareas y operaciones con los permisos de la cuenta suplantada en lugar de los suyos propios. Mientras que la delegación permite a los usuarios actuar en nombre de otros usuarios, la suplantación les permite actuar como otros usuarios. Aspose.Email admite la suplantación de identidad en Exchange. El [EWSClient](https://reference.aspose.com/email/net/aspose.email.clients.exchange.webservice/ewsclient/) la clase proporciona la [ImpersonateUser](https://reference.aspose.com/email/net/aspose.email.clients.exchange.webservice/iewsclient/impersonateuser/) and [ResetImpersonation](https://reference.aspose.com/email/net/aspose.email.clients.exchange.webservice/iewsclient/resetimpersonation/) métodos para facilitar esta función.

Para realizar esta tarea:

1. Inicialice el ExchangeWebServiceClient para el usuario 1.
1. Inicialice el ExchangeWebServiceClient para el usuario 2.
1. Añada mensajes de prueba a las cuentas.
1. Habilite la suplantación de identidad.
1. Restablecer la suplantación de identidad.

El siguiente fragmento de código muestra cómo usar el [EWSClient](https://reference.aspose.com/email/net/aspose.email.clients.exchange.webservice/ewsclient/) clase para implementar la función de suplantación.

{{< gist "aspose-email" "9e8fbeb51a8cbc4129dc71ca8cd55f0b" "Examples-CSharp-Exchange_EWS-ExchangeImpersonationUsingEWS-ExchangeImpersonationUsingEWS.cs" >}}

## **Función de detección automática mediante EWS**

La API Aspose.Email le permite conocer la configuración del servidor Exchange mediante el cliente EWS. 

{{< gist "aspose-email" "9e8fbeb51a8cbc4129dc71ca8cd55f0b" "Examples-CSharp-Exchange_EWS-AutoDiscoverUsingEWS-AutoDiscoverUsingEWS.cs" >}}

## **Abortar la operación de restauración de PST a Exchange Server**

La API Aspose.Email le permite restaurar un archivo PST en Exchange Server. Sin embargo, si la operación tarda mucho debido a que el archivo PST es de gran tamaño, es posible que sea necesario especificar un criterio para abortar la operación. Esto se puede lograr mediante la API, tal y como se muestra en el siguiente código de ejemplo.

**Note:** El ejemplo también necesita que se añada la siguiente clase.

``` cs

 public class CustomAbortRestoreException : Exception { }

```

{{< gist "aspose-email" "9e8fbeb51a8cbc4129dc71ca8cd55f0b" "Examples-CSharp-Exchange_EWS-AbortPSTToExchangeServerOperation-AbortPSTToExchangeServerOperation.cs" >}}
