---
title: "Trabajo con archivos adjuntos y objetos incrustados"
url: /es/net/working-with-attachments-and-embedded-objects/
weight: 20
type: docs
---


## **Administración de archivos adjuntos de correo electrónico**

Un archivo adjunto de correo electrónico es un archivo que se envía junto con un mensaje de correo electrónico. El archivo puede enviarse como un mensaje independiente o como parte del mensaje al que está adjunto. El [Attachment](https://reference.aspose.com/email/net/aspose.email/attachment/) la clase se usa con [MailMessage](https://reference.aspose.com/email/net/aspose.email/mailmessage/) clase. Todos los mensajes incluyen un cuerpo. Además del cuerpo, es posible que desee enviar archivos adicionales. Se envían como archivos adjuntos y se representan como una instancia del [Attachment](https://reference.aspose.com/email/net/aspose.email/attachment/) clase. Puede enviar cualquier cantidad de archivos adjuntos, pero el servidor de correo limita el tamaño de los archivos adjuntos. Gmail, por ejemplo, no admite archivos de más de 10 MB.
{{% alert %}}
**¡Pruébalo!**

Agregue o elimine archivos adjuntos de correo electrónico en línea con la versión gratuita [**Aplicación Aspose.Email Editor**](https://products.aspose.app/email/es/editor).
{{% /alert %}}

### **Agregar un archivo adjunto**

Para añadir un archivo adjunto a un correo electrónico, sigue estos pasos:

1. Crea una instancia del [MailMessage](https://reference.aspose.com/email/net/aspose.email/mailmessage/) class.
1. Crea una instancia del [Attachment](https://reference.aspose.com/email/net/aspose.email/attachment/) class.
1. Cargue el accesorio en el [Attachment](https://reference.aspose.com/email/net/aspose.email/attachment/) instance.
1. Añada el [Attachment](https://reference.aspose.com/email/net/aspose.email/attachment/) instancia en el [MailMessage](https://reference.aspose.com/email/net/aspose.email/mailmessage/) instance.

El siguiente fragmento de código muestra cómo añadir un archivo adjunto a un correo electrónico.

```csharp
// Crea una instancia de MailMessage class
var eml = new MailMessage
{
    From = "sender@from.com",
    To = "receiver@to.com",
    Subject = "This is message",
    Body = "This is body"
};

// Load an attachment
var attachment = new Attachment("1.txt");

// Add Multiple Attachment in instance of MailMessage class and Save message to disk
eml.Attachments.Add(attachment);

eml.AddAttachment(new Attachment("1.jpg"));
eml.AddAttachment(new Attachment("1.doc"));
eml.AddAttachment(new Attachment("1.rar"));
eml.AddAttachment(new Attachment("1.pdf"));
eml.Save("AddAttachments.eml");
```

Anteriormente, describimos cómo agregar archivos adjuntos a su mensaje de correo electrónico con Aspose.Email. A continuación se muestra cómo eliminar los archivos adjuntos y mostrar la información sobre ellos en la pantalla.

### **Añadir un adjunto de referencia**

Un adjunto de referencia es un tipo de archivo adjunto que incluye un enlace o una referencia a un archivo o elemento, en lugar de incluir el propio archivo o elemento en el mensaje de correo electrónico.
Cuando los destinatarios del correo electrónico hagan clic en el archivo adjunto de referencia, podrán acceder al archivo vinculado si tienen los permisos adecuados para hacerlo.
Al usar un archivo adjunto de referencia, puede enviar un mensaje de correo electrónico más pequeño y asegurarse de que todos tengan acceso a la versión más actualizada del archivo o elemento.

El siguiente fragmento de código muestra cómo añadir un adjunto de referencia a un correo electrónico. El código lleva a cabo los siguientes pasos:

1. Carga el archivo del mensaje de correo electrónico mediante [MailMessage.Load()](https://reference.aspose.com/email/net/aspose.email/mailmessage/load/#load_2) method.
2. Crea un nuevo objeto ReferenceAttachment denominado RefAttach y pasa la URL del adjunto \"https://[attach_uri]» como parámetro a su constructor.
3. Establece el nombre del archivo adjunto en \"Document.docx\" mediante el [Name](https://reference.aspose.com/email/net/aspose.email/attachment/name/) propiedad del objeto RefAttach.
4. Establece el tipo de proveedor del adjunto en [AttachmentProviderType.OneDrivePro](https://reference.aspose.com/email/net/aspose.email/attachmentprovidertype/) utilizando el [ProviderType](https://reference.aspose.com/email/net/aspose.email/referenceattachment/providertype/) propiedad del objeto RefAttach.
5. Establece el tipo de permiso del adjunto en [AttachmentPermissionType.AnyoneCanEdit](https://reference.aspose.com/email/net/aspose.email/attachmentpermissiontype/) utilizando el [PermissionType](https://reference.aspose.com/email/net/aspose.email/referenceattachment/permissiontype/) propiedad del objeto RefAttach.
6. Añade el objeto RefAttach al [Attachments](https://reference.aspose.com/email/net/aspose.email/mailmessage/attachments/) colección del objeto eml utilizando el [Add()](https://reference.aspose.com/email/net/aspose.email/attachmentcollection/) method.

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

### **Eliminar un archivo adjunto**

Para eliminar un archivo adjunto, siga los pasos que se indican a continuación:

- Crea una instancia de [Attachment](https://reference.aspose.com/email/net/aspose.email/attachment/) class.
- Cargue el archivo adjunto en el caso de [Attachment](https://reference.aspose.com/email/net/aspose.email/attachment/) class.
- Agregue el archivo adjunto a la instancia de [MailMessage](https://reference.aspose.com/email/net/aspose.email/mailmessage/) class.
- Elimine los archivos adjuntos de la instancia de [Attachment](https://reference.aspose.com/email/net/aspose.email/attachment/) clase que usa el [MailMessage](https://reference.aspose.com/email/net/aspose.email/mailmessage/) instancia de clase.

En el siguiente fragmento de código se muestra cómo eliminar un archivo adjunto.

```csharp
// Crea una instancia de MailMessage class
var eml = new MailMessage {From = "sender@sender.com", To = "receiver@gmail.com"};

// Load an attachment
var attachment = new Attachment("1.txt");
eml.Attachments.Add(attachment);

// Remove attachment from your MailMessage
eml.Attachments.Remove(attachment);
```

### **Mostrar el nombre del archivo adjunto**

Para mostrar el nombre de un archivo adjunto, sigue estos pasos:

1. Revisa los archivos adjuntos del mensaje de correo electrónico y guarda cada uno de ellos.
2. Muestra el nombre de cada adjunto en la pantalla.

El siguiente fragmento de código muestra cómo mostrar el nombre de un archivo adjunto en la pantalla.

```csharp
var eml = MailMessage.Load("Attachments.eml");

foreach (var attachment in eml.Attachments)
{
    // Display the the attachment file name
    Console.WriteLine(attachment.Name);
}
```

### **Extraer archivos adjuntos de correo electrónico**

En este tema se explica cómo extraer un archivo adjunto de un archivo de correo electrónico. Un archivo adjunto de correo electrónico es un archivo que se envía junto con un mensaje de correo electrónico. El archivo puede enviarse como un mensaje independiente o como parte del mensaje al que está adjunto. Todos los mensajes de correo electrónico incluyen la opción de enviar archivos adicionales. Se envían como archivos adjuntos y se representan como instancias del [Attachment](https://reference.aspose.com/email/net/aspose.email/attachment/) clase. El [Attachment](https://reference.aspose.com/email/net/aspose.email/attachment/) la clase se usa con [MailMessage](https://reference.aspose.com/email/net/aspose.email/mailmessage/) clase para trabajar con archivos adjuntos. Para extraer los archivos adjuntos de un mensaje de correo electrónico, sigue estos pasos:

- Crea una instancia del [MailMessage](https://reference.aspose.com/email/net/aspose.email/mailmessage/) class.
- Cargue un archivo de correo electrónico en [MailMessage](https://reference.aspose.com/email/net/aspose.email/mailmessage/) instance.
- Crea una instancia del [Attachment](https://reference.aspose.com/email/net/aspose.email/attachment/) clase y úsala en bucle para extraer todos los archivos adjuntos.
- Guarde el archivo adjunto y muéstrelo en la pantalla.

|**Archivos adjuntos extraídos en el correo electrónico**|
|: - |
|![todo:image_alt_text](working-with-attachments-and-embedded-objects_1.png)|
El siguiente fragmento de código muestra cómo extraer los archivos adjuntos de un correo electrónico.

```csharp
var eml = MailMessage.Load("Message.eml", new MsgLoadOptions());

foreach (var attachment in eml.Attachments)
{
    attachment.Save("MessageEmbedded_out.eml");
    Console.WriteLine(attachment.Name);
}
```

#### **Recuperar la descripción del contenido del archivo adjunto**

La API Aspose.Email ofrece la capacidad de leer la descripción del contenido de un archivo adjunto desde el encabezado del archivo adjunto. El siguiente fragmento de código muestra cómo recuperar la descripción del contenido del archivo adjunto.

```csharp
var eml = MailMessage.Load("EmailWithAttachEmbedded.eml");
Console.WriteLine(eml.Attachments[0].Headers["Content-Description"]);
```

#### **Determinar si el adjunto es un mensaje incrustado**

El siguiente fragmento de código muestra cómo determinar si el adjunto es un mensaje incrustado o no.

```csharp
var eml = MailMessage.Load("EmailWithAttachEmbedded.eml");

Console.WriteLine(eml.Attachments[0].IsEmbeddedMessage
    ? "Attachment is an embedded message."
    : "Attachment isn't an embedded message.");
```

## **Trabajar con imágenes en línea**

### **Agregar imagen en línea al cuerpo del correo electrónico**

The [LinkedResource](https://reference.aspose.com/email/net/aspose.email/linkedresource/) la clase se usa con [MailMessage](https://reference.aspose.com/email/net/aspose.email/mailmessage/) clase para incrustar objetos en tu mensaje de correo electrónico. Para añadir un objeto incrustado, sigue estos pasos

1. Crea una instancia del [MailMessage](https://reference.aspose.com/email/net/aspose.email/mailmessage/) class.
1. Especifique los valores de origen, destino y asunto en [MailMessage](https://reference.aspose.com/email/net/aspose.email/mailmessage/) instance.
1. Crea una instancia del [AlternateView](https://apireference.aspose.com/email/net/aspose.email/alternateview) class.
1. Crea una instancia del [LinkedResource](https://reference.aspose.com/email/net/aspose.email/linkedresource/) class.
1. Cargue un objeto incrustado en [LinkedResourceCollection](https://reference.aspose.com/email/net/aspose.email/linkedresourcecollection/).
1. Agregue el objeto incrustado cargado al [MailMessage](https://reference.aspose.com/email/net/aspose.email/mailmessage/) instancia de clase.
1. Añada el [AlternateView](https://apireference.aspose.com/email/net/aspose.email/alternateview) instancia a la [MailMessage](https://reference.aspose.com/email/net/aspose.email/mailmessage/) instancia de clase.

Los fragmentos de código siguientes producen un mensaje de correo electrónico con texto sin formato y cuerpos HTML y una imagen incrustada en el HTML.

|**Imagen incrustada en el correo electrónico**|
|: - |
|![todo:image_alt_text](working-with-attachments-and-embedded-objects_2.png)|
Puede enviar cualquier cantidad de objetos incrustados. El servidor de correo limita el tamaño del archivo adjunto. Gmail, por ejemplo, no admite archivos de más de 10 MB. Los fragmentos de código que aparecen a continuación muestran cómo incrustar objetos en un correo electrónico.

```csharp
var eml = new MailMessage
{
    From = "AndrewIrwin@from.com",
    To = "SusanMarc@to.com",
    Subject = "This is an email"
};

// Create the plain text part It is viewable by those clients that don't support HTML
var plainView =
    AlternateView.CreateAlternateViewFromString("This is my plain text content", null, "text/plain");

// Create the HTML part.To embed images, we need to use the prefix 'cid' in the img src value.
// The cid value will map to the Content-Id of a Linked resource. Thus <img src='cid:barcode'>
// will map to a LinkedResource with a ContentId of 'barcode'.
var htmlView =
    AlternateView.CreateAlternateViewFromString("Here is an embedded image.<img src=cid:barcode>", null,
        "text/html");

// Create the LinkedResource (embedded image) and Añada el LinkedResource to the appropriate view
var barcode = new LinkedResource("1.jpg", MediaTypeNames.Image.Jpeg)
{
    ContentId = "barcode"
};

eml.LinkedResources.Add(barcode);
eml.AlternateViews.Add(plainView);
eml.AlternateViews.Add(htmlView);

eml.Save("EmbeddedImage_out.msg", SaveOptions.DefaultMsgUnicode);
```

### **Eliminar la imagen en línea del cuerpo del correo electrónico**

[LinkedResourceCollection](https://reference.aspose.com/email/net/aspose.email/linkedresourcecollection/) accedido a través de [MailMessage.LinkedResources](https://reference.aspose.com/email/net/aspose.email/mailmessage/linkedresources/) propiedad. El [LinkedResourceCollection](https://reference.aspose.com/email/net/aspose.email/linkedresourcecollection/) La colección proporciona un método para eliminar por completo los objetos incrustados agregados a un mensaje de correo electrónico. Utilice la versión sobrecargada de [LinkedResourceCollection.RemoveAt](https://reference.aspose.com/email/net/aspose.email/linkedresourcecollection/removeat/#removeat/) método para eliminar todos los rastros de un objeto incrustado de un mensaje de correo electrónico.

El código de ejemplo que aparece a continuación muestra cómo eliminar objetos incrustados de un mensaje de correo electrónico.

```csharp
//Load the test message with Linked Resources
var eml = MailMessage.Load("EmlWithLinkedResources.eml");

//Remove a LinkedResource
eml.LinkedResources.RemoveAt(0, true);

//Now clear the Alternate View for linked Resources
eml.AlternateViews[0].LinkedResources.Clear(true);
```
## **Trabajo con objetos incrustados**

Un objeto incrustado es un objeto que se creó con una aplicación y se incluyó en un documento o un archivo creado por otra aplicación. Por ejemplo, una hoja de cálculo de Microsoft Excel se puede incrustar en un informe de Microsoft Word o se puede incrustar un archivo de vídeo en una presentación de Microsoft PowerPoint. Cuando un archivo se incrusta, en lugar de insertarlo o pegarlo en otro documento, conserva su formato original. El documento incrustado se puede abrir en la aplicación original y modificarlo.

### **Extracción de objetos incrustados**

En este tema se explica cómo extraer objetos incrustados de un archivo de correo electrónico. El documento incrustado se puede abrir en la aplicación original y modificarlo. Para extraer un objeto incrustado de un mensaje de correo electrónico, sigue estos pasos:

1. Crea una instancia del [MailMessage](https://reference.aspose.com/email/net/aspose.email/mailmessage/) class.
1. Cargue un archivo de correo electrónico en [MailMessage](https://reference.aspose.com/email/net/aspose.email/mailmessage/) instance.
1. Cree un bucle y cree una instancia del [Attachment](https://reference.aspose.com/email/net/aspose.email/attachment/) clase en él.
1. Guarde el archivo adjunto y muéstrelo en la pantalla.
1. Especifique la dirección del remitente y del destinatario en el [MailMessage](https://reference.aspose.com/email/net/aspose.email/mailmessage/) instance.
1. Enviar un correo electrónico mediante [SmtpClient](https://reference.aspose.com/email/net/aspose.email.clients.smtp/smtpclient/) class.

El siguiente fragmento de código extrae los objetos incrustados de un correo electrónico.

|**Objetos incrustados extraídos en el correo electrónico**|
|: - |
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

#### **Identificar y extraer un archivo adjunto incrustado de un MSG formateado como RTF**

Para los mensajes formateados como RTF, se puede usar el siguiente código para diferenciar y extraer los archivos adjuntos que están en línea o que aparecen como un icono en el cuerpo del mensaje. En el siguiente fragmento de código, se muestra cómo identificar y extraer un archivo adjunto incrustado de un mensaje con formato RTF.

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

## **Recuperar archivos adjuntos de un correo electrónico firmado**

Los correos electrónicos firmados contienen una **smime.p7m** adjunto. Significa que el correo electrónico está encriptado por SMIME. **Smime.p7m** el formato del archivo es la firma digital.
Para ver el contenido de este correo electrónico, utilice el [RemoveSignature](https://reference.aspose.com/email/net/aspose.email/mailmessage/removesignature/) método. El método devuelve un [MailMessage](https://reference.aspose.com/email/net/aspose.email/mailmessage/) objeto sin firma digital.

```csharp
var signedEml = MailMessage.Load("signed.eml");
       
if (signedEml.IsSigned)
{
    for (var i = 0; i < signedEml.Attachments.Count; i++)
    {
        Console.WriteLine($@"Signed email attachment{i}: {signedEml.Attachments[i].Name}");
    }
   
    // The email is signed. Remove a signature.
    var eml = signedEml.RemoveSignature();
   
    Console.WriteLine(@"Signature removed.");

    for (var i = 0; i < eml.Attachments.Count; i++)
    {
        Console.WriteLine($@"Email attachment{i}: {eml.Attachments[i].Name}");
    }
}
```
