---
title: "Cargando, Visualizando y Analizando Archivos MSG"
url: /es/java/loading-viewing-and-parsing-msg-file/
weight: 20
type: docs
---

Este tema explica cómo cargar un archivo de Mensaje de Microsoft Outlook (*.msg). La clase [MapiMessage](https://reference.aspose.com/email/java/com.aspose.email/mapimessage/) se utiliza para cargar archivos MSG y proporciona varias funciones de carga estáticas para diferentes escenarios. El siguiente fragmento de código muestra cómo cargar archivos MSG desde un archivo o desde un flujo.

## **Cargando Archivos MSG**

El siguiente fragmento de código muestra cómo cargar archivos MSG.

~~~Java
// Para ejemplos completos y archivos de datos, por favor visite https://github.com/aspose-email/Aspose.Email-for-Java
// La ruta al directorio del archivo.
String dataDir = RunExamples.getDataDir_Outlook();

// Crear una instancia de MapiMessage desde un archivo
MapiMessage msg = MapiMessage.fromFile(dataDir + "message.msg");

// Obtener el asunto
System.out.println("Asunto:" + msg.getSubject());

// Obtener la dirección del remitente
System.out.println("De:" + msg.getSenderEmailAddress());

// Obtener el cuerpo
System.out.println("Cuerpo" + msg.getBody());

// Obtener información de los destinatarios
System.out.println("Destinatario: " + msg.getRecipients());

// Obtener los adjuntos
for (MapiAttachment att : msg.getAttachments())
{
    System.out.println("Nombre del adjunto: " + att.getFileName());
    System.out.println("Nombre para mostrar del adjunto: " + att.getDisplayName());
}
~~~

El siguiente ejemplo de código muestra cómo usar **MailMessage** para cargar un mensaje en formato MSG.

```Java
MailMessage eml = MailMessage.load("message.msg");
```

Cabe señalar que un mensaje resultante se convierte a formato EML, incluidos los adjuntos de mensajes incrustados. No utilice este método de carga si desea preservar algunas propiedades de formato específicas de msg del mensaje original.

Para preservar el formato original de los adjuntos de mensajes incrustados, utilice la propiedad [MsgLoadOptions.PreserveEmbeddedMessageFormat](https://reference.aspose.com/email/java/com.aspose.email/loadoptions/#getPreserveEmbeddedMessageFormat--) .

```Java
MsgLoadOptions msgLoadOptions = new MsgLoadOptions();
msgLoadOptions.setPreserveEmbeddedMessageFormat(true);
MailMessage msg = MailMessage.load(stream, msgLoadOptions);
```

## **Cargando Desde un Flujo**

El siguiente fragmento de código muestra cómo cargar un archivo desde un flujo.

~~~Java
// Para ejemplos completos y archivos de datos, por favor visite https://github.com/aspose-email/Aspose.Email-for-Java
// Crear una instancia de MapiMessage desde un archivo
try (FileInputStream stream = new FileInputStream(dataDir + "message.msg"))
{
    // Crear una instancia de MapiMessage desde un archivo
    MapiMessage msg = MapiMessage.fromStream(stream);

    // Obtener el asunto
    System.out.println("Asunto:" + msg.getSubject());

    // Obtener la dirección del remitente
    System.out.println("De:" + msg.getSenderEmailAddress());

    // Obtener el cuerpo
    System.out.println("Cuerpo" + msg.getBody());

}
~~~

## **Convirtiendo EML a MSG Preservando el Formato EML Incrustado**

Los archivos EML se pueden cargar en la clase [MapiMessage](https://reference.aspose.com/email/java/com.aspose.email/mapimessage/) instanciando un objeto [MailMessage](https://reference.aspose.com/email/java/com.aspose.email/mailmessage/#getHtmlBody()) y pasándolo al método [MapiMessage.fromMailMessage](https://reference.aspose.com/email/java/com.aspose.email/mapimessage/#fromMailMessage-java.lang.String-). Si el archivo EML contiene archivos EML incrustados, utilice [MapiConversionOptions.setPreserveEmbeddedMessageFormat](https://reference.aspose.com/email/java/com.aspose.email/mapiconversionoptions/#setPreserveEmbeddedMessageFormat-boolean-) para retener el formato de los archivos EML incrustados. El siguiente fragmento de código muestra cómo cargar archivos EML en [MapiMessage](https://reference.aspose.com/email/java/com.aspose.email/mapimessage/) mientras se preserva el formato de los archivos EML incrustados.

{{% alert %}}
**¡Pruébalo!**

Convierte correos electrónicos y archivos de mensajes en línea con la gratuita [**Aplicación de Conversión Aspose.Email**](https://products.aspose.app/email/es/Conversion).
{{% /alert %}}

~~~Java
// Para ejemplos completos y archivos de datos, por favor visite https://github.com/aspose-email/Aspose.Email-for-Java
String dataDir = RunExamples.getDataDir_Email();

MailMessage eml = MailMessage.load(dataDir + "sample.eml", new EmlLoadOptions());

MapiConversionOptions options = MapiConversionOptions.getUnicodeFormat();

//Preservar el Formato de Mensaje Incrustado
options.setPreserveEmbeddedMessageFormat(true);

//Convertir EML a MSG con Opciones
MapiMessage msg = MapiMessage.fromMailMessage(eml, options);
~~~