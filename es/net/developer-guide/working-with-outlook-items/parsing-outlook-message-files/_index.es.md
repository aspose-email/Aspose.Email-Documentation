---
title: "Análisis de archivos de mensajes de Outlook"
url: /es/net/parsing-outlook-message-files/
weight: 40
type: docs
---

{{% alert color="primary" %}}

Con Aspose.Email para.NET, los desarrolladores no solo pueden cargar sino también analizar el contenido de los archivos de mensajes de Outlook.

- Para cargar archivos MSG desde el disco, utilice el comando estático [MapiMessage.Load](https://reference.aspose.com/email/net/aspose.email.mapi/mapimessage/load/) método del [MapiMessage](https://reference.aspose.com/email/net/aspose.email.mapi/mapimessage/) class.
- Para analizar el contenido del archivo MSG, [MapiMessage](https://reference.aspose.com/email/net/aspose.email.mapi/mapimessage/) expone una serie de métodos y propiedades.

En este tema se muestra cómo cargar y analizar un archivo MSG para mostrar su contenido.

{{% /alert %}}

Aspose.Email para.NET proporciona [MapiMessage](https://reference.aspose.com/email/net/aspose.email.mapi/mapimessage/) clase que se usa para abrir y analizar un archivo MSG. Como puede haber muchos destinatarios en un archivo MSG, [MapiMessage](https://reference.aspose.com/email/net/aspose.email.mapi/mapimessage/) la clase expone el [Recipients](https://reference.aspose.com/email/net/aspose.email.mapi/mapimessageitembase/recipients/) propiedad que devuelve un [MapiRecipientCollection](https://reference.aspose.com/email/net/aspose.email.mapi/mapirecipientcollection/) que representa una colección de [MapiRecipient](https://reference.aspose.com/email/net/aspose.email.mapi/mapirecipient/) objetos. El [MapiRecipient](https://reference.aspose.com/email/net/aspose.email.mapi/mapirecipient/) El objeto expone además los métodos para trabajar con los atributos del destinatario.

La siguiente secuencia de pasos cumple este propósito:

1. Crea una instancia del [MapiMessage](https://reference.aspose.com/email/net/aspose.email.mapi/mapimessage/) clase que usa el [MapiMessage.Load](https://reference.aspose.com/email/net/aspose.email.mapi/mapimessage/load/) método estático.
1. Muestre el nombre, el asunto y el cuerpo del remitente del archivo MSG mediante [SenderName](https://reference.aspose.com/email/net/aspose.email.mapi/mapimessage/sendername/), [Subject](https://reference.aspose.com/email/net/aspose.email.mapi/mapimessageitembase/subject/) and [Body](https://reference.aspose.com/email/net/aspose.email.mapi/mapimessage/body/) properties.
1. Usa el [Recipients](https://reference.aspose.com/email/net/aspose.email.mapi/mapimessageitembase/recipients/) propiedad para obtener una referencia a la colección de [MapiRecipient](https://reference.aspose.com/email/net/aspose.email.mapi/mapirecipient/) objetos asociados al archivo MSG.
1. Recorre el [MapiRecipientCollection](https://reference.aspose.com/email/net/aspose.email.mapi/mapirecipientcollection/) colección para mostrar el contenido de cada [MapiRecipient](https://reference.aspose.com/email/net/aspose.email.mapi/mapirecipient/) objetar a través de sus métodos públicos.

```cs
// The path to the resource directory.
string dataDir = RunExamples.GetDataDir_Email();

//Instantiate an MSG file to load an MSG file from disk
var outlookMessageFile = MapiMessage.Load(dataDir + "message.msg");
//Display sender's name
Console.WriteLine("Sender Name : " + outlookMessageFile.SenderName);
//Display Subject
Console.WriteLine("Subject : " + outlookMessageFile.Subject);
//Display Body
Console.WriteLine("Body : " + outlookMessageFile.Body);
//Display Recipient's info
Console.WriteLine("Recipients : \n");

//Recorre el recipients collection associated with the MapiMessage object
foreach (var rcp in outlookMessageFile.Recipients)
{
	//Display recipient email address
	Console.WriteLine("Email : " + rcp.EmailAddress);
	//Display recipient name
	Console.WriteLine("Name : " + rcp.DisplayName);
	//Display recipient type
	Console.WriteLine("Recipient Type : " + rcp.RecipientType);
}
```

{{% alert %}}
**¡Pruébalo!**

Analice archivos de correo electrónico en línea con la versión gratuita [**Aplicación de análisis Aspose.Email**](https://products.aspose.app/email/es/parser).
{{% /alert %}}
