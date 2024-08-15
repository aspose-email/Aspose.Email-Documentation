---
title: "Carga, visualización y análisis de archivos MSG"
url: /es/java/loading-viewing-and-parsing-msg-file/
weight: 20
type: docs
---


En este tema se explica cómo cargar un archivo de mensajes de Microsoft Outlook (*.msg). El [MapiMessage](https://reference.aspose.com/email/java/com.aspose.email/mapimessage/) La clase se usa para cargar archivos MSG y proporciona varias funciones de carga estática para diferentes escenarios. El siguiente fragmento de código muestra cómo cargar archivos MSG desde un archivo o desde una transmisión.

## **Carga de archivos MSG**

El siguiente fragmento de código muestra cómo cargar archivos MSG.

~~~Java
// For complete examples and data files, please go to https://github.com/aspose-email/Aspose.Email-for-Java
// The path to the File directory.
String dataDir = RunExamples.getDataDir_Outlook();

// Create an instance of MapiMessage from file
MapiMessage msg = MapiMessage.fromFile(dataDir + "message.msg");

// Get subject
System.out.println("Subject:" + msg.getSubject());

// Get from address
System.out.println("From:" + msg.getSenderEmailAddress());

// Get body
System.out.println("Body" + msg.getBody());

// Get recipients information
System.out.println("Recipient: " + msg.getRecipients());

// Get attachments
for (MapiAttachment att : msg.getAttachments())
{
    System.out.println("Attachment Name: " + att.getFileName());
    System.out.println("Attachment Display Name: " + att.getDisplayName());
}
~~~

El siguiente ejemplo de código muestra cómo usar **MailMessage** para cargar un mensaje en formato MSG.

```Java
MailMessage eml = MailMessage.load("message.msg");
```

Debe tenerse en cuenta que el mensaje resultante se convierte al formato EML, incluidos los archivos adjuntos de mensajes incrustados. No utilices este método de carga si quieres conservar algunas propiedades específicas del formato de mensaje del mensaje original.

Para conservar el formato original de los archivos adjuntos de los mensajes incrustados, utilice [MsgLoadOptions.PreserveEmbeddedMessageFormat](https://reference.aspose.com/email/java/com.aspose.email/loadoptions/#getPreserveEmbeddedMessageFormat--) property.

```Java
MsgLoadOptions msgLoadOptions = new MsgLoadOptions();
msgLoadOptions.setPreserveEmbeddedMessageFormat(true);
MailMessage msg = MailMessage.load(stream, msgLoadOptions);
```

## **Cargando desde la transmisión**

El siguiente fragmento de código muestra cómo cargar un archivo desde una transmisión.

~~~Java
// For complete examples and data files, please go to https://github.com/aspose-email/Aspose.Email-for-Java
// Create an instance of MapiMessage from file
try (FileInputStream stream = new FileInputStream(dataDir + "message.msg"))
{
    // Create an instance of MapiMessage from file
    MapiMessage msg = MapiMessage.fromStream(stream);

    // Get subject
    System.out.println("Subject:" + msg.getSubject());

    // Get from address
    System.out.println("From:" + msg.getSenderEmailAddress());

    // Get body
    System.out.println("Body" + msg.getBody());

}
~~~

## **Conversión de EML a MSG conservando el formato EML incrustado**

Los archivos EML se pueden cargar en [MapiMessage](https://reference.aspose.com/email/java/com.aspose.email/mapimessage/) clase instanciando una [MailMessage](https://reference.aspose.com/email/java/com.aspose.email/mailmessage/#getHtmlBody()) objeto y pasarlo a [MapiMessage.fromMailMessage](https://reference.aspose.com/email/java/com.aspose.email/mapimessage/#fromMailMessage-java.lang.String-) método. Si el archivo EML contiene archivos EML incrustados, utilice [MapiConversionOptions.setPreserveEmbeddedMessageFormat](https://reference.aspose.com/email/java/com.aspose.email/mapiconversionoptions/#setPreserveEmbeddedMessageFormat-boolean-) para conservar el formato de los archivos EML incrustados. El siguiente fragmento de código muestra cómo cargar archivos EML en [MapiMessage](https://reference.aspose.com/email/java/com.aspose.email/mapimessage/) conservando el formato de los archivos EML incrustados.

{{% alert %}}
**¡Pruébalo!**

Convierte correos electrónicos y archivos de mensajes en línea de forma gratuita [**Aplicación de conversión Aspose.Email**](https://products.aspose.app/email/es/Conversion).
{{% /alert %}}

~~~Java
// For complete examples and data files, please go to https://github.com/aspose-email/Aspose.Email-for-Java
String dataDir = RunExamples.getDataDir_Email();

MailMessage eml = MailMessage.load(dataDir + "sample.eml", new EmlLoadOptions());

MapiConversionOptions options = MapiConversionOptions.getUnicodeFormat();

//Preserve Embedded Message Format
options.setPreserveEmbeddedMessageFormat(true);

//Convert EML to MSG with Options
MapiMessage msg = MapiMessage.fromMailMessage(eml, options);
~~~
