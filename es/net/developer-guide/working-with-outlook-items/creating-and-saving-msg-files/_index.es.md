---
title: "Creación y almacenamiento de archivos MSG"
url: /es/net/creating-and-saving-msg-files/
weight: 10
type: docs
---


Aspose.Email admite la creación de archivos de mensajes de Outlook (MSG). En este artículo se explica cómo:

- Crea mensajes MSG.
- Crea mensajes MSG con archivos adjuntos.
- Crea un mensaje MSG con un cuerpo RTF.
- Guarda un mensaje como borrador.
- Trabaja con compresión corporal.
 
## **Creación y almacenamiento de mensajes de Outlook**

The [MailMessage](https://reference.aspose.com/email/net/aspose.email/mailmessage/) la clase tiene la [Save()](https://reference.aspose.com/email/net/aspose.email/mailmessage/save/#save/) método que puede guardar archivos MSG de Outlook en un disco o transmisión. Los fragmentos de código que aparecen a continuación crean una instancia del [MailMessage](https://reference.aspose.com/email/net/aspose.email/mailmessage/) clase, establece propiedades como desde, hasta, sujeto y cuerpo. El [Save()](https://reference.aspose.com/email/net/aspose.email/mailmessage/save/#save/) el método toma el nombre del archivo como argumento. Además, los mensajes de Outlook se pueden crear con un [cuerpo RTF comprimido]([/email/net/managing-message-files-with-aspose-email-outlook/#managingmessagefileswithaspose-email-outlook-creatingmsgfileswithrtfbody](https://docs.aspose.com/email/net/managing-message-files-with-aspose-email-outlook/#managingmessagefileswithaspose-email-outlook-creatingmsgfileswithrtfbody)) utilizando el [MapiConversionOptions](https://reference.aspose.com/email/net/aspose.email.mapi/mapiconversionoptions/). Para configurarla, cree una nueva aplicación de Windows y añada una referencia a la dll Aspose.Email en el proyecto.

1. Cree una nueva instancia del [MailMessage](https://reference.aspose.com/email/net/aspose.email/mailmessage/) clasifica y establece las propiedades Desde, Hasta, Subject y Body.
2. Llame al [MapiMessage](https://reference.aspose.com/email/net/aspose.email.mapi/mapimessage/) class [FromMailMessage](https://reference.aspose.com/email/net/aspose.email.mapi/mapimessage/frommailmessage/#frommailmessage/) método que acepta el objeto del [MailMessage](https://reference.aspose.com/email/net/aspose.email/mailmessage/) tipo. El [FromMailMessage](https://reference.aspose.com/email/net/aspose.email.mapi/mapimessage/frommailmessage/#frommailmessage/) el método convierte el [MailMessage](https://reference.aspose.com/email/net/aspose.email/mailmessage/) en un [MapiMessage](https://reference.aspose.com/email/net/aspose.email.mapi/mapimessage/) (MSG).
3. Llame al [MapiMessage.Save()](https://reference.aspose.com/email/net/aspose.email.mapi/mapimessage/save/#save/) método para guardar el archivo MSG.

Escriba el siguiente código en el evento de clic del botón de control de la aplicación Windows.

{{< gist "aspose-com-gists" "6e5185a63aec6fd70d83098e82b06a32" "Examples-CSharp-Outlook-CreatingAndSavingOutlookMessages-CreatingAndSavingOutlookMessages.cs" >}}

## **Creación de archivos MSG con archivos adjuntos**

[En el ejemplo anterior](https://docs.aspose.com/email/es/net/managing-message-files-with-aspose-email-outlook/#managingmessagefileswithaspose-email-outlook-creatingandsavingoutlookmessages), hemos creado un archivo MSG sencillo. Aspose.Email también permite guardar archivos de mensajes con archivos adjuntos. Todo lo que necesita hacer es agregar los archivos adjuntos al [MailMessage](https://reference.aspose.com/email/net/aspose.email/mailmessage/) instancia. Añada archivos adjuntos llamando al *Add()* método en el [MailMessage.Attachments](https://reference.aspose.com/email/net/aspose.email/mailmessage/attachments/) colección. Añada un cuadro de lista al formulario creado anteriormente y añada dos botones, uno para añadir y eliminar archivos adjuntos cada uno. La aplicación que agrega aplicaciones funciona así:

1. Cuando el **Agregar archivo adjunto** se hace clic en un botón, un **Cuadro de diálogo Abrir archivo** se muestra para ayudar a los usuarios a buscar y seleccionar el adjunto.
2. Cuando se selecciona un archivo, la ruta completa se añade a la lista.
3. Cuando se crea el archivo MSG, las rutas de los archivos adjuntos se extraen de la lista y se añaden a la [MailMessage.Attachments](https://reference.aspose.com/email/net/aspose.email/mailmessage/attachments/) collection.

Escriba el siguiente código en el **Agregar archivo adjunto** evento de clic en un botón.

{{< gist "aspose-com-gists" "6e5185a63aec6fd70d83098e82b06a32" "Examples-CSharp-Outlook-WorkingWithMSGAttachments-CreateMessagesWithAttachments.cs" >}}

Cuando el **Eliminar archivo adjunto** se hace clic en el botón, elimina los elementos seleccionados del cuadro de lista. Escriba el siguiente código en el evento de clic del botón Eliminar datos adjuntos.

{{< gist "aspose-com-gists" "6e5185a63aec6fd70d83098e82b06a32" "Examples-CSharp-Outlook-WorkingWithMSGAttachments-RemoveAttachment.cs" >}}

Agregue el código para agregar los archivos adjuntos al [MailMessage](https://reference.aspose.com/email/net/aspose.email/mailmessage/) instancia. El código final de la función Write Msg se escribe como se muestra a continuación.

{{< gist "aspose-com-gists" "6e5185a63aec6fd70d83098e82b06a32" "Examples-CSharp-Outlook-WorkingWithMSGAttachments-AddingMSGAttachments.cs" >}}

## **Creación de archivos MSG con RTF Body**

También puede crear archivos de mensajes de Outlook (MSG) con cuerpos de texto enriquecido (RTF) con Aspose.Email. El cuerpo RTF admite el formato de texto. Cree uno configurando el [MailMessage.HtmlBody](https://reference.aspose.com/email/net/aspose.email/mailmessage/htmlbody/) propiedad. Cuando conviertes un [MailMessage](https://reference.aspose.com/email/net/aspose.email/mailmessage/) instancia en un [MapiMessage](https://reference.aspose.com/email/net/aspose.email.mapi/mapimessage/) por ejemplo, el cuerpo HTML se convierte en RTF. De esta forma, se conserva el formato del cuerpo del correo electrónico.

El siguiente ejemplo crea un archivo MSG con un cuerpo RTF. Hay un formato de encabezado, negrita y subrayado aplicado en el cuerpo del HTML. Este formato se conserva cuando el HTML se convierte a RTF.

{{< gist "aspose-com-gists" "6e5185a63aec6fd70d83098e82b06a32" "Examples-CSharp-Outlook-CreatingMSGFilesWithRTFBody-CreatingMSGFilesWithRTFBody.cs" >}}

## **Guardar el mensaje en estado de borrador**

Los correos electrónicos se guardan como borradores cuando alguien ha empezado a editarlos pero quiere volver a ellos para completarlos más tarde. Aspose.Email permite guardar los mensajes de correo electrónico en estado de borrador mediante la configuración de una marca de mensaje. A continuación se muestra un ejemplo de código para guardar un mensaje de correo electrónico de Outlook (MSG) como borrador.

{{< gist "aspose-com-gists" "6e5185a63aec6fd70d83098e82b06a32" "Examples-CSharp-Outlook-SavingMessageInDraftStatus-SavingMessageInDraftStatus.cs" >}}

## **Compresión RTF al configurar el cuerpo del mensaje MAPI**

> **_NOTE:_** El proceso de compresión puede ralentizar el rendimiento al crear mensajes. Si comprenden este hecho y configuran el indicador de compresión en función de los requisitos específicos y el equilibrio entre el tamaño del archivo y el rendimiento, los desarrolladores pueden gestionar de forma eficaz la creación de archivos MSG y PST cuando se trata de mensajes de correo electrónico.

En esta sección, aprenderá a usar la compresión RTF al configurar el cuerpo del mensaje MAPI. La compresión RTF tiene por objeto reducir el tamaño de un mensaje, así como los archivos PST (tabla de almacenamiento personal) resultantes que Microsoft Outlook utiliza para almacenar los mensajes de correo electrónico y otros datos. Al utilizar la compresión RTF al configurar el cuerpo del mensaje, los programadores pueden reducir la cantidad de memoria necesaria para almacenar los mensajes de correo electrónico u optimizar el ancho de banda de la red al transmitir los mensajes.

Para ello, se han diseñado dos métodos sobrecargados:

- [MapiMessageItemBase.SetBodyContent](https://reference.aspose.com/email/net/aspose.email.mapi/mapimessageitembase/setbodycontent/)(contenido de cadena, BodyContentType ContentType, compresión bool): este método permite establecer el contenido del cuerpo del mensaje utilizando el contenido de la cadena especificado y especificando el tipo de contenido del cuerpo (por ejemplo, texto sin formato, HTML, etc.). El parámetro de compresión opcional es un valor que especifica si el contenido se debe comprimir mediante la compresión RTF. Si el parámetro de compresión es verdadero, el contenido se comprimirá, lo que reducirá el tamaño del mensaje.

- [MapiMessageItemBase.SetBodyRtf](https://reference.aspose.com/email/net/aspose.email.mapi/mapimessageitembase/setbodyrtf/)(contenido de cadena, compresión bool): este método establece específicamente el contenido del cuerpo del mensaje en formato RTF. El parámetro de contenido es una cadena que representa el contenido RTF que se establecerá como cuerpo del mensaje. Al igual que en el método anterior, el parámetro de compresión determina si se debe aplicar la compresión RTF al contenido. Si la compresión es verdadera, el contenido RTF se comprimirá para reducir el tamaño.

El siguiente ejemplo de código muestra cómo configurar el cuerpo html y mantenerlo comprimido:

```cs
var msg = new MapiMessage("from@doamin.com", "to@domain.com", "subject", "body");
// set the html body and keep it compressed
// this will reduce the message size
msg.SetBodyContent(htmlBody, BodyContentType.Html, true);
```

También hay un [MapiConversionOptions.UseBodyCompression](https://reference.aspose.com/email/net/aspose.email.mapi/mapiconversionoptions/usebodycompression/) propiedad. Cuando esta propiedad está habilitada, la compresión del cuerpo RTF se aplica durante la conversión de MailMessage a MapiMessage, lo que reduce el tamaño del archivo MSG. Se muestra en el ejemplo de código que aparece a continuación:

```cs
var message = MailMessage.Load(fileName);
var options = new MapiConversionOptions();
options.UseBodyCompression = true;
var msg = MapiMessage.FromMailMessage(message, options);
```
