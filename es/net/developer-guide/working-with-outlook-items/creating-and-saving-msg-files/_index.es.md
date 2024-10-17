---
title: "Creación y Guardado de Archivos MSG"
url: /es/net/creating-and-saving-msg-files/
weight: 10
type: docs
---

Aspose.Email admite la creación de archivos de mensaje de Outlook (MSG). Este artículo explica cómo:

- Crear mensajes MSG.
- Crear mensajes MSG con archivos adjuntos.
- Crear un mensaje MSG con un cuerpo RTF.
- Guardar un mensaje como borrador.
- Trabajar con la compresión del cuerpo.

## **Creación y Guardado de Mensajes de Outlook**

La clase [MailMessage](https://reference.aspose.com/email/net/aspose.email/mailmessage/) tiene el método [Save()](https://reference.aspose.com/email/net/aspose.email/mailmessage/save/#save/) que puede guardar archivos MSG de Outlook en el disco o en un flujo. Los fragmentos de código a continuación crean una instancia de la clase [MailMessage](https://reference.aspose.com/email/net/aspose.email/mailmessage/), establecen propiedades como de, para, asunto y cuerpo. El método [Save()](https://reference.aspose.com/email/net/aspose.email/mailmessage/save/#save/) toma el nombre del archivo como argumento. Además, los mensajes de Outlook pueden ser creados con un [cuerpo RTF comprimido]([/email/net/managing-message-files-with-aspose-email-outlook/#managingmessagefileswithaspose-email-outlook-creatingmsgfileswithrtfbody](https://docs.aspose.com/email/net/managing-message-files-with-aspose-email-outlook/#managingmessagefileswithaspose-email-outlook-creatingmsgfileswithrtfbody)) utilizando las [MapiConversionOptions](https://reference.aspose.com/email/net/aspose.email.mapi/mapiconversionoptions/). Para configurar, crea una nueva aplicación de Windows y agrega una referencia al dll de Aspose.Email en el proyecto.

1. Crea una nueva instancia de la clase [MailMessage](https://reference.aspose.com/email/net/aspose.email/mailmessage/) y establece las propiedades From, To, Subject y Body.
2. Llama al método [FromMailMessage](https://reference.aspose.com/email/net/aspose.email.mapi/mapimessage/frommailmessage/#frommailmessage/) de la clase [MapiMessage](https://reference.aspose.com/email/net/aspose.email.mapi/mapimessage/) que acepta el objeto del tipo [MailMessage](https://reference.aspose.com/email/net/aspose.email/mailmessage/). El método [FromMailMessage](https://reference.aspose.com/email/net/aspose.email.mapi/mapimessage/frommailmessage/#frommailmessage/) convierte el [MailMessage](https://reference.aspose.com/email/net/aspose.email/mailmessage/) en un [MapiMessage](https://reference.aspose.com/email/net/aspose.email.mapi/mapimessage/) (MSG).
3. Llama al método [MapiMessage.Save()](https://reference.aspose.com/email/net/aspose.email.mapi/mapimessage/save/#save/) para guardar el archivo MSG.

Escribe el siguiente código en el evento click del control del botón de la aplicación de Windows.

{{< gist "aspose-com-gists" "6e5185a63aec6fd70d83098e82b06a32" "Examples-CSharp-Outlook-CreatingAndSavingOutlookMessages-CreatingAndSavingOutlookMessages.cs" >}}

## **Creación de Archivos MSG con Archivos Adjuntos**

[En el ejemplo anterior](https://docs.aspose.com/email/es/net/managing-message-files-with-aspose-email-outlook/#managingmessagefileswithaspose-email-outlook-creatingandsavingoutlookmessages), creamos un archivo MSG simple. Aspose.Email también admite guardar archivos de mensajes con archivos adjuntos. Todo lo que necesitas hacer es agregar los archivos adjuntos a la instancia de [MailMessage](https://reference.aspose.com/email/net/aspose.email/mailmessage/). Agrega archivos adjuntos llamando al método *Add()* sobre la colección [MailMessage.Attachments](https://reference.aspose.com/email/net/aspose.email/mailmessage/attachments/). Agrega un cuadro de lista al formulario creado anteriormente y dos botones, uno para agregar y otro para eliminar archivos adjuntos. La aplicación que agrega archivos adjuntos funciona así:

1. Cuando se hace clic en el botón **Agregar Archivo Adjunto**, se muestra un **Diálogo para Abrir Archivo** para ayudar a los usuarios a navegar y seleccionar el archivo adjunto.
2. Cuando se ha seleccionado un archivo, la ruta completa se agrega a una lista.
3. Cuando se crea el archivo MSG, las rutas de los archivos adjuntos se obtienen de la lista y se agregan a la colección [MailMessage.Attachments](https://reference.aspose.com/email/net/aspose.email/mailmessage/attachments/).

Escribe el siguiente código en el evento click del botón **Agregar Archivo Adjunto**.

{{< gist "aspose-com-gists" "6e5185a63aec6fd70d83098e82b06a32" "Examples-CSharp-Outlook-WorkingWithMSGAttachments-CreateMessagesWithAttachments.cs" >}}

Cuando se hace clic en el botón **Eliminar Archivo Adjunto**, elimina los elementos seleccionados de la lista. Escribe el siguiente código en el evento click del botón Eliminar Archivo Adjunto.

{{< gist "aspose-com-gists" "6e5185a63aec6fd70d83098e82b06a32" "Examples-CSharp-Outlook-WorkingWithMSGAttachments-RemoveAttachment.cs" >}}

Agrega el código para añadir los archivos adjuntos a la instancia de [MailMessage](https://reference.aspose.com/email/net/aspose.email/mailmessage/). El código final para la función Write Msg está escrito como se muestra a continuación.

{{< gist "aspose-com-gists" "6e5185a63aec6fd70d83098e82b06a32" "Examples-CSharp-Outlook-WorkingWithMSGAttachments-AddingMSGAttachments.cs" >}}

## **Creación de Archivos MSG con Cuerpo RTF**

También puedes crear archivos de Mensaje de Outlook (MSG) con cuerpos de texto enriquecido (RTF) con Aspose.Email. El cuerpo RTF admite el formato de texto. Crea uno estableciendo la propiedad [MailMessage.HtmlBody](https://reference.aspose.com/email/net/aspose.email/mailmessage/htmlbody/). Cuando conviertes una instancia de [MailMessage](https://reference.aspose.com/email/net/aspose.email/mailmessage/) en una instancia de [MapiMessage](https://reference.aspose.com/email/net/aspose.email.mapi/mapimessage/), el cuerpo HTML se convierte en RTF. De esta manera, se conserva el formato del cuerpo del correo electrónico.

El siguiente ejemplo crea un archivo MSG con un cuerpo RTF. Hay un encabezado, formato en negrita y subrayado aplicado en el cuerpo HTML. Este formato se mantiene cuando el HTML se convierte en RTF.

{{< gist "aspose-com-gists" "6e5185a63aec6fd70d83098e82b06a32" "Examples-CSharp-Outlook-CreatingMSGFilesWithRTFBody-CreatingMSGFilesWithRTFBody.cs" >}}

## **Guardando Mensajes en Estado de Borrador**

Los correos electrónicos se guardan como borradores cuando alguien ha comenzado a editarlos pero quiere volver a ellos para completarlos más tarde. Aspose.Email admite el guardado de mensajes de correo electrónico en estado de borrador estableciendo una bandera de mensaje. A continuación se muestra un código de ejemplo para guardar un mensaje de correo electrónico de Outlook (MSG) como borrador.

{{< gist "aspose-com-gists" "6e5185a63aec6fd70d83098e82b06a32" "Examples-CSharp-Outlook-SavingMessageInDraftStatus-SavingMessageInDraftStatus.cs" >}}

## **Compresión RTF al establecer el cuerpo del mensaje MAPI**

> **_NOTA:_** El proceso de compresión puede ralentizar el rendimiento al crear mensajes. Al comprender este hecho y configurar la bandera de compresión según requisitos específicos y el compromiso entre el tamaño del archivo y el rendimiento, los desarrolladores pueden gestionar eficazmente la creación de archivos MSG y PST al tratar con mensajes de correo electrónico.

En esta sección aprenderás a utilizar la compresión RTF al establecer el cuerpo del mensaje MAPI. La compresión RTF está destinada a reducir el tamaño de un mensaje así como los archivos PST (Tabla de Almacenamiento Personal) resultantes que Microsoft Outlook utiliza para almacenar mensajes de correo electrónico y otros datos. Al utilizar la compresión RTF al configurar el cuerpo del mensaje, los desarrolladores pueden reducir la cantidad de memoria necesaria para almacenar mensajes de correo electrónico u optimizar el ancho de banda de la red al transmitir mensajes.

Para ello, se han diseñado dos métodos sobrecargados:

- [MapiMessageItemBase.SetBodyContent](https://reference.aspose.com/email/net/aspose.email.mapi/mapimessageitembase/setbodycontent/)(string content, BodyContentType contentType, bool compression): Este método permite establecer el contenido del cuerpo del mensaje utilizando el contenido de cadena especificado y especificando el tipo de contenido del cuerpo (por ejemplo, texto plano, HTML, etc.). El parámetro opcional de compresión es un valor que especifica si el contenido debe ser comprimido utilizando compresión RTF. Si el parámetro de compresión es verdadero, el contenido será comprimido, resultando en un tamaño de mensaje más pequeño.

- [MapiMessageItemBase.SetBodyRtf](https://reference.aspose.com/email/net/aspose.email.mapi/mapimessageitembase/setbodyrtf/)(string content, bool compression): Este método establece específicamente el contenido del cuerpo del mensaje en formato RTF. El parámetro de contenido es una cadena que representa el contenido RTF que se establecerá como el cuerpo del mensaje. Como en el método anterior, el parámetro de compresión determina si se debe aplicar compresión RTF al contenido. Si la compresión es verdadera, el contenido RTF será comprimido para reducir el tamaño.

El siguiente ejemplo de código muestra cómo establecer el cuerpo HTML y mantenerlo comprimido:

```cs
var msg = new MapiMessage("from@doamin.com", "to@domain.com", "subject", "body");
// establecer el cuerpo html y mantenerlo comprimido
// esto reducirá el tamaño del mensaje
msg.SetBodyContent(htmlBody, BodyContentType.Html, true);
```

También hay una propiedad [MapiConversionOptions.UseBodyCompression](https://reference.aspose.com/email/net/aspose.email.mapi/mapiconversionoptions/usebodycompression/). Cuando esta propiedad está habilitada, se aplica compresión del cuerpo RTF durante la conversión de MailMessage a MapiMessage, resultando en un tamaño de archivo MSG más pequeño. Se muestra en el siguiente ejemplo de código:

```cs
var message = MailMessage.Load(fileName);
var options = new MapiConversionOptions();
options.UseBodyCompression = true;
var msg = MapiMessage.FromMailMessage(message, options);
```