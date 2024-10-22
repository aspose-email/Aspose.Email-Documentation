---
title: "Trabajando con Archivos Adjuntos y Objetos Insertados"
url: /es/net/working-with-attachments-and-embedded-objects/
weight: 20
type: docs
---


## **Gestionando Archivos Adjuntos de Email**

Un archivo adjunto de correo electrónico es un archivo que se envía junto con un mensaje de correo electrónico. El archivo puede enviarse como un mensaje separado, así como parte del mensaje al que está adjunto. La clase [Attachment](https://reference.aspose.com/email/net/aspose.email/attachment/) se utiliza con la clase [MailMessage](https://reference.aspose.com/email/net/aspose.email/mailmessage/). Todos los mensajes incluyen un cuerpo. Además del cuerpo, quizás desee enviar archivos adicionales. Estos se envían como archivos adjuntos y se representan como una instancia de la clase [Attachment](https://reference.aspose.com/email/net/aspose.email/attachment/). Puede enviar cualquier número de archivos adjuntos, pero el tamaño del archivo adjunto está limitado por el servidor de correo. Gmail, por ejemplo, no admite tamaños de archivos superiores a 10MB.
{{% alert %}}
**¡Pruébalo!**

Agrega o elimina archivos adjuntos de email en línea con la gratuita [**Aspose.Email Editor App**](https://products.aspose.app/email/es/editor).
{{% /alert %}}

### **Agregar un Archivo Adjunto**

Para agregar un archivo adjunto a un correo electrónico, siga estos pasos:

1. Cree una instancia de la clase [MailMessage](https://reference.aspose.com/email/net/aspose.email/mailmessage/).
1. Cree una instancia de la clase [Attachment](https://reference.aspose.com/email/net/aspose.email/attachment/).
1. Cargue el archivo adjunto en la instancia de [Attachment](https://reference.aspose.com/email/net/aspose.email/attachment/).
1. Agregue la instancia de [Attachment](https://reference.aspose.com/email/net/aspose.email/attachment/) a la instancia de [MailMessage](https://reference.aspose.com/email/net/aspose.email/mailmessage/).

El siguiente fragmento de código muestra cómo agregar un archivo adjunto a un correo electrónico.

```csharp
// Crear una instancia de la clase MailMessage
var eml = new MailMessage
{
    From = "sender@from.com",
    To = "receiver@to.com",
    Subject = "Este es un mensaje",
    Body = "Este es el cuerpo"
};

// Cargar un archivo adjunto
var attachment = new Attachment("1.txt");

// Agregar múltiples archivos adjuntos a la instancia de la clase MailMessage y guardar el mensaje en disco
eml.Attachments.Add(attachment);

eml.AddAttachment(new Attachment("1.jpg"));
eml.AddAttachment(new Attachment("1.doc"));
eml.AddAttachment(new Attachment("1.rar"));
eml.AddAttachment(new Attachment("1.pdf"));
eml.Save("AddAttachments.eml");
```

Arriba, describimos cómo agregar archivos adjuntos a su mensaje de correo electrónico con Aspose.Email. Lo que sigue muestra cómo eliminar archivos adjuntos y mostrar información sobre ellos en la pantalla.

### **Agregar un Archivo Adjunto de Referencia**

Un archivo adjunto de referencia es un tipo de archivo adjunto que incluye un enlace o una referencia a un archivo o ítem, en lugar de incluir el archivo o ítem en sí en el mensaje de correo electrónico. Cuando los destinatarios del correo electrónico hacen clic en el archivo adjunto de referencia, podrán acceder al archivo vinculado si tienen los permisos apropiados para hacerlo. Al utilizar un archivo adjunto de referencia, puede enviar un mensaje de correo electrónico más pequeño y asegurarse de que todos tengan acceso a la versión más actualizada del archivo o ítem.

El siguiente fragmento de código muestra cómo agregar un archivo adjunto de referencia a un correo electrónico. El código realiza los siguientes pasos:

1. Carga el archivo del mensaje de correo electrónico usando el método [MailMessage.Load()](https://reference.aspose.com/email/net/aspose.email/mailmessage/load/#load_2).
2. Crea un nuevo objeto ReferenceAttachment llamado refAttach, pasando la URL del archivo adjunto "https://[attach_uri]" como parámetro a su constructor.
3. Establece el nombre del archivo adjunto como "Document.docx" utilizando la propiedad [Name](https://reference.aspose.com/email/net/aspose.email/attachment/name/) del objeto refAttach.
4. Establece el tipo de proveedor del archivo adjunto como [AttachmentProviderType.OneDrivePro](https://reference.aspose.com/email/net/aspose.email/attachmentprovidertype/) utilizando la propiedad [ProviderType](https://reference.aspose.com/email/net/aspose.email/referenceattachment/providertype/) del objeto refAttach.
5. Establece el tipo de permiso del archivo adjunto como [AttachmentPermissionType.AnyoneCanEdit](https://reference.aspose.com/email/net/aspose.email/attachmentpermissiontype/) utilizando la propiedad [PermissionType](https://reference.aspose.com/email/net/aspose.email/referenceattachment/permissiontype/) del objeto refAttach.
6. Agrega el objeto refAttach a la colección [Attachments](https://reference.aspose.com/email/net/aspose.email/mailmessage/attachments/) del objeto eml utilizando el método [Add()](https://reference.aspose.com/email/net/aspose.email/attachmentcollection/).

```cs
var eml = MailMessage.Load("fileName");

var refAttach = new ReferenceAttachment("https://[attach_uri]")
{
    Name = "Document.docx",
    ProviderType = AttachmentProviderType.OneDrivePro,
    PermissionType = AttachmentPermissionType.AnyoneCanEdit
};

eml.Attachments.Add(refAttach);
```

### **Eliminar un Archivo Adjunto**

Para eliminar un archivo adjunto, siga los pasos que se indican a continuación:

- Cree una instancia de la clase [Attachment](https://reference.aspose.com/email/net/aspose.email/attachment/).
- Cargue el archivo adjunto en la instancia de la clase [Attachment](https://reference.aspose.com/email/net/aspose.email/attachment/).
- Agregue el archivo adjunto a la instancia de la clase [MailMessage](https://reference.aspose.com/email/net/aspose.email/mailmessage/).
- Elimine los archivos adjuntos de la instancia de la clase [Attachment](https://reference.aspose.com/email/net/aspose.email/attachment/) utilizando la instancia de la clase [MailMessage](https://reference.aspose.com/email/net/aspose.email/mailmessage/).

El siguiente fragmento de código muestra cómo eliminar un archivo adjunto.

```csharp
// Crear una instancia de la clase MailMessage
var eml = new MailMessage {From = "sender@sender.com", To = "receiver@gmail.com"};

// Cargar un archivo adjunto
var attachment = new Attachment("1.txt");
eml.Attachments.Add(attachment);

// Eliminar el archivo adjunto de su MailMessage
eml.Attachments.Remove(attachment);
```

### **Mostrar el Nombre del Archivo Adjunto**

Para mostrar el nombre de un archivo adjunto, siga estos pasos:

1. Recorrer los archivos adjuntos en el mensaje de correo electrónico y guardar cada archivo adjunto.
2. Mostrar cada nombre de archivo adjunto en la pantalla.

El siguiente fragmento de código muestra cómo mostrar un nombre de archivo adjunto en la pantalla.

```csharp
var eml = MailMessage.Load("Attachments.eml");

foreach (var attachment in eml.Attachments)
{
    // Mostrar el nombre del archivo adjunto
    Console.WriteLine(attachment.Name);
}
```

### **Extraer Archivos Adjuntos de Email**

Este tema explica cómo extraer un archivo adjunto de un archivo de correo electrónico. Un archivo adjunto de correo electrónico es un archivo que se envía junto con un mensaje de correo electrónico. El archivo puede enviarse como un mensaje separado, así como parte del mensaje al que está adjunto. Todos los mensajes de correo electrónico incluyen una opción para enviar archivos adicionales. Estos se envían como archivos adjuntos y se representan como instancias de la clase [Attachment](https://reference.aspose.com/email/net/aspose.email/attachment/). La clase [Attachment](https://reference.aspose.com/email/net/aspose.email/attachment/) se utiliza con la clase [MailMessage](https://reference.aspose.com/email/net/aspose.email/mailmessage/) para trabajar con archivos adjuntos. Para extraer archivos adjuntos de un mensaje de correo electrónico, siga estos pasos:

- Cree una instancia de la clase [MailMessage](https://reference.aspose.com/email/net/aspose.email/mailmessage/).
- Cargue un archivo de correo electrónico en la instancia de [MailMessage](https://reference.aspose.com/email/net/aspose.email/mailmessage/).
- Cree una instancia de la clase [Attachment](https://reference.aspose.com/email/net/aspose.email/attachment/) y utilícela en un bucle para extraer todos los archivos adjuntos.
- Guarde el archivo adjunto y muéstrelo en la pantalla.

|**Archivos adjuntos extraídos en el correo electrónico**|
| :- |
|![todo:image_alt_text](working-with-attachments-and-embedded-objects_1.png)|
El siguiente fragmento de código muestra cómo extraer archivos adjuntos de correo electrónico.

```csharp
var eml = MailMessage.Load("Message.eml", new MsgLoadOptions());

foreach (var attachment in eml.Attachments)
{
    attachment.Save("MessageEmbedded_out.eml");
    Console.WriteLine(attachment.Name);
}
```

#### **Recuperar Content-Description de un Archivo Adjunto**

Aspose.Email API proporciona la capacidad de leer la Content-Description de un archivo adjunto desde un encabezado de archivo adjunto. El siguiente fragmento de código muestra cómo recuperar la descripción del contenido del archivo adjunto.

```csharp
var eml = MailMessage.Load("EmailWithAttachEmbedded.eml");
Console.WriteLine(eml.Attachments[0].Headers["Content-Description"]);
```

#### **Determinar si el Archivo Adjunto es un Mensaje Insertado**

El siguiente fragmento de código demuestra cómo determinar si el archivo adjunto es un mensaje insertado o no.

```csharp
var eml = MailMessage.Load("EmailWithAttachEmbedded.eml");

Console.WriteLine(eml.Attachments[0].IsEmbeddedMessage
    ? "El archivo adjunto es un mensaje insertado."
    : "El archivo adjunto no es un mensaje insertado.");
```

## **Trabajando con imágenes en línea**

### **Agregar imagen en línea al cuerpo del correo electrónico**

La clase [LinkedResource](https://reference.aspose.com/email/net/aspose.email/linkedresource/) se utiliza con la clase [MailMessage](https://reference.aspose.com/email/net/aspose.email/mailmessage/) para insertar objetos en su mensaje de correo electrónico. Para agregar un objeto incrustado, siga estos pasos:

1. Cree una instancia de la clase [MailMessage](https://reference.aspose.com/email/net/aspose.email/mailmessage/).
1. Especifique los valores de de, para y asunto en la instancia de [MailMessage](https://reference.aspose.com/email/net/aspose.email/mailmessage/).
1. Cree una instancia de la clase [AlternateView](https://apireference.aspose.com/email/net/aspose.email/alternateview).
1. Cree una instancia de la clase [LinkedResource](https://reference.aspose.com/email/net/aspose.email/linkedresource/).
1. Cargue un objeto incrustado en la [LinkedResourceCollection](https://reference.aspose.com/email/net/aspose.email/linkedresourcecollection/).
1. Agregue el objeto incrustado cargado en la instancia de la clase [MailMessage](https://reference.aspose.com/email/net/aspose.email/mailmessage/).
1. Agregue la instancia de [AlternateView](https://apireference.aspose.com/email/net/aspose.email/alternateview) a la instancia de la clase [MailMessage](https://reference.aspose.com/email/net/aspose.email/mailmessage/).

Los fragmentos de código a continuación producen un mensaje de correo electrónico con cuerpo de texto plano y HTML y una imagen incrustada en el HTML.

|**Imagen incrustada en el email**|
| :- |
|![todo:image_alt_text](working-with-attachments-and-embedded-objects_2.png)|
Puede enviar cualquier número de objetos incrustados. El tamaño del archivo adjunto está limitado por el servidor de correo. Gmail, por ejemplo, no admite tamaños de archivos superiores a 10MB. Los fragmentos de código a continuación demuestran cómo incrustar objetos en un email.

```csharp
var eml = new MailMessage
{
    From = "AndrewIrwin@from.com",
    To = "SusanMarc@to.com",
    Subject = "Este es un correo electrónico"
};

// Crear la parte de texto plano. Es visible para aquellos clientes que no soportan HTML
var plainView =
    AlternateView.CreateAlternateViewFromString("Este es mi contenido de texto plano", null, "text/plain");

// Crear la parte HTML. Para incrustar imágenes, necesitamos usar el prefijo 'cid' en el valor src de la imagen.
// El valor cid se mapeará al Content-Id de un recurso vinculado. Así <img src='cid:barcode'>
// se mapeará a un LinkedResource con un ContentId de 'barcode'.
var htmlView =
    AlternateView.CreateAlternateViewFromString("Aquí hay una imagen incrustada.<img src=cid:barcode>", null,
        "text/html");

// Crear el LinkedResource (imagen incrustada) y agregar el LinkedResource a la vista apropiada
var barcode = new LinkedResource("1.jpg", MediaTypeNames.Image.Jpeg)
{
    ContentId = "barcode"
};

eml.LinkedResources.Add(barcode);
eml.AlternateViews.Add(plainView);
eml.AlternateViews.Add(htmlView);

eml.Save("EmbeddedImage_out.msg", SaveOptions.DefaultMsgUnicode);
```

### **Eliminar imagen en línea del cuerpo del correo electrónico**

[LinkedResourceCollection](https://reference.aspose.com/email/net/aspose.email/linkedresourcecollection/) accesible a través de la propiedad [MailMessage.LinkedResources](https://reference.aspose.com/email/net/aspose.email/mailmessage/linkedresources/). La colección [LinkedResourceCollection](https://reference.aspose.com/email/net/aspose.email/linkedresourcecollection/) proporciona un método para eliminar completamente objetos incrustados agregados en un mensaje de correo electrónico. Utilice la versión sobrecargada del método [LinkedResourceCollection.RemoveAt](https://reference.aspose.com/email/net/aspose.email/linkedresourcecollection/removeat/#removeat/) para eliminar todas las huellas de un objeto incrustado de un mensaje de correo electrónico.

El código de muestra a continuación muestra cómo eliminar objetos incrustados de un mensaje de correo electrónico.

```csharp
// Cargar el mensaje de prueba con recursos vinculados
var eml = MailMessage.Load("EmlWithLinkedResources.eml");

// Eliminar un LinkedResource
eml.LinkedResources.RemoveAt(0, true);

// Ahora limpiar la Vista Alternativa para recursos vinculados
eml.AlternateViews[0].LinkedResources.Clear(true);
```
## **Trabajando con Objetos Insertados**

Un objeto incrustado es un objeto que fue creado con una aplicación y está encerrado dentro de un documento o archivo creado por otra aplicación. Por ejemplo, una hoja de cálculo de Microsoft Excel puede estar incrustada en un informe de Microsoft Word, o un archivo de video puede estar incrustado en una presentación de Microsoft PowerPoint. Cuando un archivo está incrustado, en lugar de insertarse o pegarse en otro documento, mantiene su formato original. El documento incrustado se puede abrir en la aplicación original y modificarse.

### **Extracción de Objetos Insertados**

Este tema explica cómo extraer objetos incrustados de un archivo de correo electrónico. El documento incrustado se puede abrir en la aplicación original y ser modificado. Para extraer un objeto incrustado de un mensaje de correo electrónico, siga estos pasos:

1. Cree una instancia de la clase [MailMessage](https://reference.aspose.com/email/net/aspose.email/mailmessage/).
1. Cargue un archivo de correo electrónico en la instancia de [MailMessage](https://reference.aspose.com/email/net/aspose.email/mailmessage/).
1. Cree un bucle y cree una instancia de la clase [Attachment](https://reference.aspose.com/email/net/aspose.email/attachment/) en él.
1. Guarde el archivo adjunto y muéstrelo en la pantalla.
1. Especifique la dirección del remitente y del destinatario en la instancia de [MailMessage](https://reference.aspose.com/email/net/aspose.email/mailmessage/).
1. Envíe el correo electrónico utilizando la clase [SmtpClient](https://reference.aspose.com/email/net/aspose.email.clients.smtp/smtpclient/).

El siguiente fragmento de código extrae objetos incrustados de un correo electrónico.

|**Objetos incrustados extraídos en el email**|
| :- |
|![todo:image_alt_text](working-with-attachments-and-embedded-objects_3.png)|
El siguiente fragmento de código muestra cómo extraer objetos incrustados.

```csharp
var eml = MailMessage.Load("Message.msg", new MsgLoadOptions());

foreach (var attachment in eml.Attachments)
{
    attachment.Save("MessageEmbedded_out.msg");
    Console.WriteLine(attachment.Name);
}
```

#### **Identificar y Extraer un archivo adjunto incrustado de MSG formateado como RTF**

Para mensajes formateados como RTF, se puede utilizar el siguiente código para diferenciar y extraer archivos adjuntos que son ya sea en línea o aparecen como un ícono en el cuerpo del mensaje. El siguiente fragmento de código muestra cómo identificar y extraer un archivo adjunto incrustado de MSG formateado como RTF.

```csharp

var eml = MapiMessage.Load("MSG file with RTF Formatting.msg");

foreach (var attachment in eml.Attachments)
{
    if (IsAttachmentInline(attachment))
    {
        try
        {
            SaveAttachment(attachment, Data.Out/new Guid().ToString());
        }
        catch (Exception ex)
        {
            Console.WriteLine(ex.Message);
        }
    }
}

static bool IsAttachmentInline(MapiAttachment attachment)
{
    foreach (var property in attachment.ObjectData.Properties.Values)
    {
        if (property.Name == "\x0003ObjInfo")
        {
            var odtPersist1 = BitConverter.ToUInt16(property.Data, 0);
            return (odtPersist1 & (1 << (7 - 1))) == 0;
        }
    }
    return false;
}

static void SaveAttachment(MapiAttachment attachment, string fileName)
{
    foreach (var property in attachment.ObjectData.Properties.Values)
    {
        if (property.Name == "Package")
        {
            using var fs = new FileStream(fileName, FileMode.Create, FileAccess.Write);
            fs.Write(property.Data, 0, property.Data.Length);
        }
    }
}
```

## **Recuperar Archivos Adjuntos de Email Firmado**

Los correos electrónicos firmados contienen un único archivo adjunto **smime.p7m**. Esto significa que el correo electrónico está encriptado por SMIME. El formato de archivo **Smime.p7m** es la firma digital. Para ver los contenidos de este correo electrónico, use el método [RemoveSignature](https://reference.aspose.com/email/net/aspose.email/mailmessage/removesignature/). El método devuelve un objeto [MailMessage](https://reference.aspose.com/email/net/aspose.email/mailmessage/) sin una firma digital.

```csharp
var signedEml = MailMessage.Load("signed.eml");
        
if (signedEml.IsSigned)
{
    for (var i = 0; i < signedEml.Attachments.Count; i++)
    {
        Console.WriteLine($@"Archivo adjunto de email firmado{i}: {signedEml.Attachments[i].Name}");
    }
    
    // El correo electrónico está firmado. Eliminar la firma.
    var eml = signedEml.RemoveSignature();
    
    Console.WriteLine(@"Firma eliminada.");

    for (var i = 0; i < eml.Attachments.Count; i++)
    {
        Console.WriteLine($@"Archivo adjunto de email{i}: {eml.Attachments[i].Name}");
    }
}
```