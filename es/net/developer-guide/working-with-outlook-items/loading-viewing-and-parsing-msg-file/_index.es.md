---
title: "Cargando, Visualizando y Analizando Archivos MSG"
url: /es/net/loading-viewing-and-parsing-msg-file/
weight: 20
type: docs
---

Este tema explica cómo cargar un archivo de mensaje de Microsoft Outlook (*.msg). La clase [MapiMessage](https://reference.aspose.com/email/net/aspose.email.mapi/mapimessage/) se utiliza para cargar archivos MSG y proporciona varias funciones estáticas de carga para diferentes escenarios. El siguiente fragmento de código te muestra cómo cargar archivos MSG desde un archivo o desde un flujo.

## **Cargando Archivos MSG**

El siguiente fragmento de código te muestra cómo cargar archivos MSG.

```cs
// La ruta al directorio de archivos.
string dataDir = RunExamples.GetDataDir_Outlook();

// Crear una instancia de MapiMessage desde el archivo
MapiMessage msg = MapiMessage.Load(dataDir + @"message.msg");

// Obtener asunto
Console.WriteLine("Subject:" + msg.Subject);

// Obtener dirección del remitente
Console.WriteLine("From:" + msg.SenderEmailAddress);

// Obtener cuerpo
Console.WriteLine("Body" + msg.Body);

// Obtener información de los destinatarios
Console.WriteLine("Recipient: " + msg.Recipients);

// Obtener adjuntos
foreach (MapiAttachment att in msg.Attachments)
{
    Console.Write("Attachment Name: " + att.FileName);
    Console.Write("Attachment Display Name: " + att.DisplayName);
}
```

El siguiente ejemplo de código muestra cómo usar MailMessage para cargar un mensaje en formato MSG.

```csharp

MailMessage eml = MailMessage.Load("message.msg");

```

Cabe destacar que el mensaje resultante se convierte al formato EML, incluyendo los adjuntos de mensajes incrustados. No utilices este método de carga si deseas preservar algunas propiedades específicas del formato msg del mensaje original.

Para preservar el formato original de los adjuntos de mensajes incrustados, utiliza la propiedad [msgLoadOptions.PreserveEmbeddedMessageFormat](https://reference.aspose.com/email/net/aspose.email/loadoptions/preserveembeddedmessageformat/).

```csharp

MsgLoadOptions msgLoadOptions = new MsgLoadOptions();
msgLoadOptions.PreserveEmbeddedMessageFormat = true;
var msg = MailMessage.Load(stream, msgLoadOptions);

```

## **Cargando desde un Flujo**

El siguiente fragmento de código te muestra cómo cargar un archivo desde un flujo.

```cs
// Crear una instancia de MapiMessage desde el archivo
byte[] bytes = File.ReadAllBytes(dataDir + @"message.msg");

using (MemoryStream stream = new MemoryStream(bytes))
{
    stream.Seek(0, SeekOrigin.Begin);
    // Crear una instancia de MapiMessage desde el archivo
    MapiMessage msg = MapiMessage.Load(stream);

    // Obtener asunto
    Console.WriteLine("Subject:" + msg.Subject);

    // Obtener dirección del remitente
    Console.WriteLine("From:" + msg.SenderEmailAddress);

    // Obtener cuerpo
    Console.WriteLine("Body" + msg.Body);

}
```

Convertir EML a MSG preservando el formato EML incrustado

Los archivos EML se pueden cargar en la clase [MapiMessage](https://reference.aspose.com/email/net/aspose.email.mapi/mapimessage/) instanciando un objeto [MailMessage](https://reference.aspose.com/email/net/aspose.email/mailmessage/) y pasándolo al método [MapiMessage.FromMailMessage](https://reference.aspose.com/email/net/aspose.email.mapi/mapimessage/frommailmessage/#frommailmessage/). Si el archivo EML contiene archivos EML incrustados, utiliza [MapiConversionOptions.PreserveEmbeddedMessageFormat](https://reference.aspose.com/email/net/aspose.email.mapi/mapiconversionoptions/preserveembeddedmessageformat/) para retener el formato de los archivos EML incrustados. El siguiente fragmento de código muestra cómo cargar archivos EML en [MapiMessage](https://reference.aspose.com/email/net/aspose.email.mapi/mapimessage/) mientras se preserva el formato de los archivos EML incrustados.

{{% alert %}}
**¡Pruébalo!**

Convierte correos electrónicos y archivos de mensajes en línea con la gratuita [**Aspose.Email Conversion App**](https://products.aspose.app/email/es/Conversion).
{{% /alert %}}

{{< gist "aspose-com-gists" "6e5185a63aec6fd70d83098e82b06a32" "Examples-CSharp-Email-PreservingEmbeddedMsgFormat-PreservingEmbeddedMsgFormat.cs" >}}