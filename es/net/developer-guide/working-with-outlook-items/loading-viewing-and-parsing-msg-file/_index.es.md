---
title: "Carga, visualización y análisis de archivos MSG"
url: /es/net/loading-viewing-and-parsing-msg-file/
weight: 20
type: docs
---


En este tema se explica cómo cargar un archivo de mensajes de Microsoft Outlook (*.msg). El [MapiMessage](https://reference.aspose.com/email/net/aspose.email.mapi/mapimessage/) La clase se usa para cargar archivos MSG y proporciona varias funciones de carga estática para diferentes escenarios. El siguiente fragmento de código muestra cómo cargar archivos MSG desde un archivo o desde una transmisión.

## **Carga de archivos MSG**

El siguiente fragmento de código muestra cómo cargar archivos MSG.

```cs
// The path to the File directory.
string dataDir = RunExamples.GetDataDir_Outlook();

// Create an instance of MapiMessage from file
MapiMessage msg = MapiMessage.Load(dataDir + @"message.msg");

// Get subject
Console.WriteLine("Subject:" + msg.Subject);

// Get from address
Console.WriteLine("From:" + msg.SenderEmailAddress);

// Get body
Console.WriteLine("Body" + msg.Body);

// Get recipients information
Console.WriteLine("Recipient: " + msg.Recipients);

// Get attachments
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

Debe tenerse en cuenta que el mensaje resultante se convierte al formato EML, incluidos los archivos adjuntos de mensajes incrustados. No utilices este método de carga si quieres conservar algunas propiedades específicas del formato de mensaje del mensaje original.

Para conservar el formato original de los archivos adjuntos de los mensajes incrustados, utilice [msgLoadOptions.PreserveEmbeddedMessageFormat](https://reference.aspose.com/email/net/aspose.email/loadoptions/preserveembeddedmessageformat/) property.

```csharp

MsgLoadOptions msgLoadOptions = new MsgLoadOptions();
msgLoadOptions.PreserveEmbeddedMessageFormat = true;
var msg = MailMessage.Load(stream, msgLoadOptions);

```

## **Cargando desde Stream**

El siguiente fragmento de código muestra cómo cargar un archivo desde una transmisión.

```cs
// Create an instance of MapiMessage from file
byte[] bytes = File.ReadAllBytes(dataDir + @"message.msg");

using (MemoryStream stream = new MemoryStream(bytes))
{
    stream.Seek(0, SeekOrigin.Begin);
    // Create an instance of MapiMessage from file
    MapiMessage msg = MapiMessage.Load(stream);

    // Get subject
    Console.WriteLine("Subject:" + msg.Subject);

    // Get from address
    Console.WriteLine("From:" + msg.SenderEmailAddress);

    // Get body
    Console.WriteLine("Body" + msg.Body);

}
```

Conversión de EML a MSG conservando el formato EML incrustado

Los archivos EML se pueden cargar en [MapiMessage](https://reference.aspose.com/email/net/aspose.email.mapi/mapimessage/) clase instanciando una [MailMessage](https://reference.aspose.com/email/net/aspose.email/mailmessage/) objeto y pasarlo a [MapiMessage.FromMailMessage](https://reference.aspose.com/email/net/aspose.email.mapi/mapimessage/frommailmessage/#frommailmessage/) método. Si el archivo EML contiene archivos EML incrustados, utilice [MapiConversionOptions.PreserveEmbeddedMessageFormat](https://reference.aspose.com/email/net/aspose.email.mapi/mapiconversionoptions/preserveembeddedmessageformat/) para conservar el formato de los archivos EML incrustados. El siguiente fragmento de código muestra cómo cargar archivos EML en [MapiMessage](https://reference.aspose.com/email/net/aspose.email.mapi/mapimessage/) conservando el formato de los archivos EML incrustados.

{{% alert %}}
**¡Pruébalo!**

Convierte correos electrónicos y archivos de mensajes en línea de forma gratuita [**Aplicación de conversión Aspose.Email**](https://products.aspose.app/email/es/Conversion).
{{% /alert %}}

{{< gist "aspose-com-gists" "6e5185a63aec6fd70d83098e82b06a32" "Examples-CSharp-Email-PreservingEmbeddedMsgFormat-PreservingEmbeddedMsgFormat.cs" >}}
