---
title: "Características de utilidad"
url: /es/net/utility-features/
weight: 120
type: docs
---


## **Enviar un mensaje con opción de votación**

Microsoft Outlook permite a los usuarios crear una encuesta al redactar un nuevo mensaje. Esto se hace incluyendo opciones de votación como Sí, No, Tal vez, etc. La clase FollowUpOptions ofrecida por Aspose.Email, proporciona la propiedad VotingButtons que se puede usar para establecer o obtener el valor de las opciones de votación. Este artículo proporciona un ejemplo detallado de cómo crear un MapiMessage con opciones de votación para crear una encuesta y luego enviar el mensaje utilizando el cliente de Exchange Web Service (EWS).

### **Crear y enviar un mensaje con opciones de votación**

El siguiente fragmento de código muestra cómo crear un nuevo mensaje y luego enviarlo con opciones de votación.

{{< gist "aspose-email" "9e8fbeb51a8cbc4129dc71ca8cd55f0b" "Examples-CSharp-Exchange_EWS-CreateAndSendingMessageWithVotingOptions-CreateAndSendingMessageWithVotingOptions.cs" >}}

### **Métodos de ejemplo utilizados en los ejemplos**

El siguiente fragmento de código muestra cómo usar los métodos utilizados en el ejemplo anterior.

{{< gist "aspose-email" "9e8fbeb51a8cbc4129dc71ca8cd55f0b" "Examples-CSharp-Exchange_EWS-CreateAndSendingMessageWithVotingOptions-CreateTestMessage.cs" >}}

## **Ignorar o evitar un certificado SSL inválido o caducado**

Aspose.Email puede manejar certificados SSL en el servidor Exchange utilizando tanto las clases [ExchangeClient](https://reference.aspose.com/email/net/aspose.email.clients.exchange.dav/exchangeclient/) como [EWSClient](https://reference.aspose.com/email/net/aspose.email.clients.exchange.webservice/ewsclient/). Si el certificado SSL ha caducado o se ha vuelto inválido, Aspose.Email lanza una excepción debido al certificado SSL inválido. Evite tales errores de certificados SSL ignorándolos utilizando el método que se usa en el código a continuación. Registre el controlador de devolución de llamada en su método main() o init() y agregue el método a continuación como miembro de la clase.

{{< gist "aspose-email" "9e8fbeb51a8cbc4129dc71ca8cd55f0b" "Examples-CSharp-Exchange_EWS-IgnoringInvalidSSLCertificates-IgnoringInvalidSSLCertificates.cs" >}}

## **Crear mensajes RE y FW a partir de archivos MSG**

[IEWSClient](https://reference.aspose.com/email/net/aspose.email.clients.exchange.webservice/iewsclient/) permite a los desarrolladores crear mensajes RE (Respuesta/Responder a Todos) y FW (Reenviar) a partir de un mensaje fuente. El mensaje fuente se identifica seleccionando un [ExchangeMessageInfo](https://reference.aspose.com/email/net/aspose.email.clients.exchange/exchangemessageinfo/) particular de [ExchangeMessageInfoCollection](https://reference.aspose.com/email/net/aspose.email.clients.exchange/exchangemessageinfocollection/exchangemessageinfocollection/) obtenido mediante [IEWSClient.ListMessages()](https://reference.aspose.com/email/net/aspose.email.clients.exchange.webservice/iewsclient/listmessages/). El otro argumento es el [MailMessage](https://reference.aspose.com/email/net/aspose.email/mailmessage/) que se enviará como mensaje RE o FW. El siguiente fragmento de código muestra cómo crear una cuenta de muestra que se utiliza para enviar un mensaje y luego se demuestran las características de respuesta y reenvío contra ese mensaje de muestra. Para realizar esta tarea:

1. Inicializar el objeto [IEWSClient](https://reference.aspose.com/email/net/aspose.email.clients.exchange.webservice/iewsclient/) proporcionando credenciales válidas.
1. Enviar algunos mensajes de muestra.
1. Llamar a las funciones [IEWSClient.Reply()](https://reference.aspose.com/email/net/aspose.email.clients.exchange.webservice/iewsclient/reply/), [IEWSClient.ReplyAll()](https://reference.aspose.com/email/net/aspose.email.clients.exchange.webservice/iewsclient/replyall/) y [IEWSClient.Forward()](https://reference.aspose.com/email/net/aspose.email.clients.exchange.webservice/iewsclient/forward/) para enviar mensajes.

{{< gist "aspose-email" "9e8fbeb51a8cbc4129dc71ca8cd55f0b" "Examples-CSharp-Exchange_EWS-CreateREAndFWMessages-CreateREAndFWMessages.cs" >}}

## **Soporte para el seguimiento de correos electrónicos**

La API de Aspose.Email proporciona soporte para el seguimiento de correos electrónicos utilizando la Notificación de Disposición de Mensajes (MDN). Esto se logra solicitando los recibos de lectura y creando la información requerida. La propiedad [MailMessage.ReadReceiptTo](https://reference.aspose.com/email/net/aspose.email/mailmessage/readreceiptto/) obtiene o establece la dirección del recibo de lectura. Los métodos [CreateReadReceipt](https://reference.aspose.com/email/net/aspose.email/mailmessage/createreadreceipt/) y [ReadReceiptRequested](https://reference.aspose.com/email/net/aspose.email.mapi/mapimessage/readreceiptrequested/) se utilizan para crear y recuperar la información sobre si se han solicitado recibos de lectura. El siguiente fragmento de código muestra cómo rastrear correos electrónicos utilizando la API de Aspose.Email.

{{< gist "aspose-email" "9e8fbeb51a8cbc4129dc71ca8cd55f0b" "Examples-CSharp-Exchange-EmailTracking-EmailTracking.cs" >}}

## **Soporte para la creación de registros en clientes de Exchange**

La API de Aspose.Email proporciona la capacidad de proporcionar una instalación de registro para el cliente de Exchange Web Service. Esto se puede lograr configurando el archivo App.config.

### **Registro para el cliente EWS**

{{< gist "aspose-email" "9e8fbeb51a8cbc4129dc71ca8cd55f0b" "LoggingForEWSClient.xml" >}}

## **Agregar encabezados en las solicitudes de EWS**

La API de Aspose.Email permite agregar encabezados a las solicitudes de Exchange. Esto se puede usar para agregar encabezados a las solicitudes de EWS para diferentes encabezados que pueden usarse para diferentes propósitos. Un ejemplo podría ser agregar el encabezado X-AnchorMailbox que se utiliza para gestionar problemas de limitación en el servidor Exchange. El método [AddHeader](https://reference.aspose.com/email/net/aspose.email.clients.exchange.webservice/iewsclient/addheader/) de la clase [IEWSClient](https://reference.aspose.com/email/net/aspose.email.clients.exchange.webservice/iewsclient/) se utiliza para agregar encabezados a las solicitudes de EWS como se muestra en el siguiente fragmento de código.

{{< gist "aspose-email" "9e8fbeb51a8cbc4129dc71ca8cd55f0b" "Examples-CSharp-Exchange_EWS-AddingHeadersToEWSRequests-AddingHeadersToEWSRequests.cs" >}}

## **Trabajando con mensajería unificada**

Aspose.Email puede recuperar información de mensajería unificada desde el servidor Exchange 2010. Se admite la mensajería unificada, como obtener información de configuración, iniciar una llamada saliente, recuperar información de llamadas telefónicas por ID de llamada y desconectar una llamada telefónica por ID. El siguiente fragmento de código muestra cómo recuperar información de configuración de mensajería unificada del servidor Microsoft Exchange 2010.

{{< gist "aspose-email" "9e8fbeb51a8cbc4129dc71ca8cd55f0b" "Examples-CSharp-Exchange_EWS-GettingUnifiedMessagingConfigurationInformation-GettingUnifiedMessagingConfigurationInformation.cs" >}}

## **Obtener consejos de correo**

Microsoft Exchange Server agregó varias nuevas características con Exchange Server 2010 y 2013. Una de ellas permite a los usuarios obtener consejos de correo al redactar un mensaje de correo electrónico. Estos consejos son muy útiles ya que proporcionan información antes de enviar el correo electrónico. Por ejemplo, si una dirección de correo electrónico es incorrecta en la lista de destinatarios, se muestra un consejo para hacerle saber que la dirección de correo electrónico es inválida. Los consejos de correo también le permiten ver respuestas automáticas antes de enviar un correo electrónico: el servidor Exchange (2010 y 2013) envía el consejo de correo cuando se está redactando el correo electrónico si uno o más de los destinatarios han configurado respuestas automáticas. Se requiere Microsoft Exchange Server 2010 Service Pack 1 para todas las funciones demostradas en este artículo. El siguiente fragmento de código muestra cómo usar la clase [EWSClient](https://reference.aspose.com/email/net/aspose.email.clients.exchange.webservice/ewsclient/) que utiliza los Servicios Web de Exchange, disponibles en Microsoft Exchange Server 2007 y versiones posteriores.

{{< gist "aspose-email" "9e8fbeb51a8cbc4129dc71ca8cd55f0b" "Examples-CSharp-Exchange_EWS-GetMailTips-GetMailTips.cs" >}}

## **Impersonación en Exchange**

La impersonación en Exchange permite que alguien imite a otra cuenta y realice tareas y operaciones utilizando los permisos de la cuenta impersonada en lugar de los suyos. Mientras que la delegación permite a los usuarios actuar en nombre de otros usuarios, la impersonación les permite actuar como otros usuarios. Aspose.Email admite la impersonación de Exchange. La clase [EWSClient](https://reference.aspose.com/email/net/aspose.email.clients.exchange.webservice/ewsclient/) proporciona los métodos [ImpersonateUser](https://reference.aspose.com/email/net/aspose.email.clients.exchange.webservice/iewsclient/impersonateuser/) y [ResetImpersonation](https://reference.aspose.com/email/net/aspose.email.clients.exchange.webservice/iewsclient/resetimpersonation/) para facilitar esta función.

Para realizar esta tarea:

1. Inicializar el ExchangeWebServiceClient para el usuario 1.
1. Inicializar el ExchangeWebServiceClient para el usuario 2.
1. Anexar mensajes de prueba a las cuentas.
1. Habilitar la impersonación.
1. Reiniciar la impersonación.

El siguiente fragmento de código muestra cómo usar la clase [EWSClient](https://reference.aspose.com/email/net/aspose.email.clients.exchange.webservice/ewsclient/) para implementar la función de impersonación.

{{< gist "aspose-email" "9e8fbeb51a8cbc4129dc71ca8cd55f0b" "Examples-CSharp-Exchange_EWS-ExchangeImpersonationUsingEWS-ExchangeImpersonationUsingEWS.cs" >}}

## **Función de descubrimiento automático usando EWS**

La API de Aspose.Email le permite descubrir la configuración del servidor Exchange utilizando el cliente EWS.

{{< gist "aspose-email" "9e8fbeb51a8cbc4129dc71ca8cd55f0b" "Examples-CSharp-Exchange_EWS-AutoDiscoverUsingEWS-AutoDiscoverUsingEWS.cs" >}}

## **Abortar la operación de restauración de PST al servidor Exchange**

La API de Aspose.Email le permite restaurar un archivo PST al servidor Exchange. Sin embargo, si la operación está tardando mucho debido al gran tamaño del archivo PST, puede ser necesario especificar un criterio para abortar la operación. Esto se puede lograr utilizando la API como se muestra en el siguiente código de ejemplo.

**Nota:** El ejemplo necesita que se agregue la siguiente clase también.

``` cs

 public class CustomAbortRestoreException : Exception { }

```

{{< gist "aspose-email" "9e8fbeb51a8cbc4129dc71ca8cd55f0b" "Examples-CSharp-Exchange_EWS-AbortPSTToExchangeServerOperation-AbortPSTToExchangeServerOperation.cs" >}}