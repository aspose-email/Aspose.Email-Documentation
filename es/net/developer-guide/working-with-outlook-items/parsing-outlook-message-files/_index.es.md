---
title: "Análisis de Archivos de Mensajes de Outlook"
url: /es/net/parsing-outlook-message-files/
weight: 40
type: docs
---

{{% alert color="primary" %}} 

Usando Aspose.Email para .NET, los desarrolladores no solo pueden cargar, sino también analizar el contenido de archivos de mensajes de Outlook.

- Para cargar archivos MSG desde el disco, use el método estático [MapiMessage.Load](https://reference.aspose.com/email/net/aspose.email.mapi/mapimessage/load/) de la clase [MapiMessage](https://reference.aspose.com/email/net/aspose.email.mapi/mapimessage/).
- Para analizar el contenido de un archivo MSG, la [MapiMessage](https://reference.aspose.com/email/net/aspose.email.mapi/mapimessage/) expone una serie de métodos y propiedades.

Este tema muestra cómo cargar y analizar un archivo MSG para mostrar su contenido.

{{% /alert %}} 

Aspose.Email para .NET proporciona la clase [MapiMessage](https://reference.aspose.com/email/net/aspose.email.mapi/mapimessage/) que se utiliza para abrir y analizar un archivo MSG. Dado que puede haber muchos destinatarios en un archivo MSG, la clase [MapiMessage](https://reference.aspose.com/email/net/aspose.email.mapi/mapimessage/) expone la propiedad [Recipients](https://reference.aspose.com/email/net/aspose.email.mapi/mapimessageitembase/recipients/) que devuelve una [MapiRecipientCollection](https://reference.aspose.com/email/net/aspose.email.mapi/mapirecipientcollection/) que representa una colección de objetos [MapiRecipient](https://reference.aspose.com/email/net/aspose.email.mapi/mapirecipient/). El objeto [MapiRecipient](https://reference.aspose.com/email/net/aspose.email.mapi/mapirecipient/) expone además métodos para trabajar con atributos de destinatarios.

La siguiente secuencia de pasos sirve para este propósito:

1. Crear una instancia de la clase [MapiMessage](https://reference.aspose.com/email/net/aspose.email.mapi/mapimessage/) utilizando el método estático [MapiMessage.Load](https://reference.aspose.com/email/net/aspose.email.mapi/mapimessage/load/).
1. Mostrar el nombre del remitente, el asunto y el cuerpo del archivo MSG utilizando las propiedades [SenderName](https://reference.aspose.com/email/net/aspose.email.mapi/mapimessage/sendername/), [Subject](https://reference.aspose.com/email/net/aspose.email.mapi/mapimessageitembase/subject/) y [Body](https://reference.aspose.com/email/net/aspose.email.mapi/mapimessage/body/).
1. Usar la propiedad [Recipients](https://reference.aspose.com/email/net/aspose.email.mapi/mapimessageitembase/recipients/) para obtener una referencia a la colección de objetos [MapiRecipient](https://reference.aspose.com/email/net/aspose.email.mapi/mapirecipient/) asociados con el archivo MSG.
1. Recorrer la colección [MapiRecipientCollection](https://reference.aspose.com/email/net/aspose.email.mapi/mapirecipientcollection/) para mostrar el contenido de cada objeto [MapiRecipient](https://reference.aspose.com/email/net/aspose.email.mapi/mapirecipient/) a través de sus métodos públicos.

```cs
// La ruta al directorio de recursos.
string dataDir = RunExamples.GetDataDir_Email();

//Instanciar un archivo MSG para cargar un archivo MSG desde el disco
var outlookMessageFile = MapiMessage.Load(dataDir + "message.msg");
//Mostrar el nombre del remitente
Console.WriteLine("Nombre del remitente : " + outlookMessageFile.SenderName);
//Mostrar Asunto
Console.WriteLine("Asunto : " + outlookMessageFile.Subject);
//Mostrar Cuerpo
Console.WriteLine("Cuerpo : " + outlookMessageFile.Body);
//Mostrar información del destinatario
Console.WriteLine("Destinatarios : \n");

//Recorrer la colección de destinatarios asociada con el objeto MapiMessage
foreach (var rcp in outlookMessageFile.Recipients)
{
	//Mostrar dirección de correo electrónico del destinatario
	Console.WriteLine("Email : " + rcp.EmailAddress);
	//Mostrar nombre del destinatario
	Console.WriteLine("Nombre : " + rcp.DisplayName);
	//Mostrar tipo de destinatario
	Console.WriteLine("Tipo de destinatario : " + rcp.RecipientType);
}
```

{{% alert %}}
**¡Pruébalo!**

Analiza archivos de correo electrónico en línea con la gratuita [**Aplicación Aspose.Email Parser**](https://products.aspose.app/email/es/parser).
{{% /alert %}}