---
title: "Programación con Thunderbird"
url: /es/net/programming-with-thunderbird/
weight: 110
type: docs
---


## **Lectura de archivos MBOX**

[Mozilla Thunderbird](https://www.thunderbird.net/es-ES/) es un cliente de correo electrónico de código abierto y multiplataforma, desarrollado por la Fundación Mozilla. Almacena correos electrónicos en su propia estructura de archivos, gestionando índices de mensajes y subcarpetas a través de formatos de archivos propietarios. Aspose.Email puede trabajar con las estructuras de almacenamiento de correo de Thunderbird. La clase [MboxrdStorageReader](https://reference.aspose.com/email/net/aspose.email.storage.mbox/mboxrdstoragereader/) permite a los desarrolladores leer mensajes desde el archivo de almacenamiento de correo de Mozilla Thunderbird. Este artículo muestra cómo leer los mensajes del almacenamiento de correo de Thunderbird:

1. Abre el archivo de almacenamiento de Thunderbird en *FileStream*.
1. Crea una instancia de la clase [MboxrdStorageReader](https://reference.aspose.com/email/net/aspose.email.storage.mbox/mboxrdstoragereader/) y pasa el flujo anterior al constructor.
1. Llama a [ReadNextMessage()](https://reference.aspose.com/email/net/aspose.email.storage.mbox/mboxrdstoragereader/readnextmessage/#readnextmessage/) para obtener el primer mensaje.
1. Usa el mismo [ReadNextMessage()](https://reference.aspose.com/email/net/aspose.email.storage.mbox/mboxrdstoragereader/readnextmessage/#readnextmessage/) en un bucle while para leer todos los mensajes.
1. Cierra todos los flujos.

El siguiente fragmento de código muestra cómo leer todos los mensajes de un almacenamiento de correo de Thunderbird.

```cs
// The path to the File directory.
var dataDir = RunExamples.GetDataDir_Thunderbird();

// Open the storage file with FileStream
var stream = new FileStream(dataDir + "ExampleMbox.mbox", FileMode.Open, FileAccess.Read);
// Create an instance of the MboxrdStorageReader class and pass the stream
var reader = new MboxrdStorageReader(stream, false);
// Start reading messages
var message = reader.ReadNextMessage();

// Read all messages in a loop
while (message != null)
{
    // Manipulate message - show contents
    Console.WriteLine("Subject: " + message.Subject);
    // Save this message in EML or MSG format
    message.Save(message.Subject + ".eml", SaveOptions.DefaultEml);
    message.Save(message.Subject + ".msg", SaveOptions.DefaultMsgUnicode);

    // Get the next message
    message = reader.ReadNextMessage();
}

// Close the streams
reader.Dispose();
stream.Close();
```

### **Recuperación de propiedades del mensaje**

La clase [MboxMessageInfo](https://reference.aspose.com/email/net/aspose.email.storage.mbox/mboxmessageinfo/#mboxmessageinfo-class) contiene las siguientes propiedades para recuperar información sobre un mensaje:

- DateTime [Date](https://reference.aspose.com/email/net/aspose.email.storage.mbox/mboxmessageinfo/date/#mboxmessageinfodate-property) - Obtiene la fecha del mensaje
- MailAddress [From](https://reference.aspose.com/email/net/aspose.email.storage.mbox/mboxmessageinfo/from/#mboxmessageinfofrom-property) - Obtiene la dirección del remitente
- string [Subject](https://reference.aspose.com/email/net/aspose.email.storage.mbox/mboxmessageinfo/subject/) - Obtiene el asunto del mensaje
- MailAddressCollection [To](https://reference.aspose.com/email/net/aspose.email.storage.mbox/mboxmessageinfo/to/) - Obtiene la colección de direcciones que contiene los destinatarios del mensaje
- MailAddressCollection [CC](https://reference.aspose.com/email/net/aspose.email.storage.mbox/mboxmessageinfo/cc/) - Obtiene la colección de direcciones que contiene los destinatarios en copia
- MailAddressCollection [Bcc](https://reference.aspose.com/email/net/aspose.email.storage.mbox/mboxmessageinfo/bcc/) - Obtiene la colección de direcciones que contiene los destinatarios en copia oculta del mensaje

**Ejemplo de código**

```cs
MboxStorageReader reader = MboxStorageReader.CreateReader(fileName, new MboxLoadOptions());

foreach (var mboxMessageInfo in reader.EnumerateMessageInfo())
{
    Console.Writeline($"Subject: {mboxMessageInfo.Subject}");
    Console.Writeline($"Date: {mboxMessageInfo.Date}");
    Console.Writeline($"From: {mboxMessageInfo.From}");
    Console.Writeline($"To: {mboxMessageInfo.To}");
    Console.Writeline($"CC: {mboxMessageInfo.CC}");
    Console.Writeline($"Bcc: {mboxMessageInfo.Bcc}");
}
```

### **Extraer mensajes de MBOX por identificadores**

La clase [MboxStorageReader](https://reference.aspose.com/email/net/aspose.email.storage.mbox/mboxstoragereader/#mboxstoragereader-class) incluye el método [EnumerateMessageInfo()](https://reference.aspose.com/email/net/aspose.email.storage.mbox/mboxstoragereader/enumeratemessageinfo/), que permite iterar a través de cada mensaje en un archivo MBOX. Al usar este método, se hace posible extraer mensajes individuales sin necesidad de recorrer todo el almacenamiento repetidamente. Esto mejora el rendimiento y reduce el tiempo de procesamiento.

La clase [MboxMessageInfo](https://reference.aspose.com/email/net/aspose.email.storage.mbox/mboxmessageinfo/#mboxmessageinfo-class) proporciona la propiedad [EntryId](https://reference.aspose.com/email/net/aspose.email.storage.mbox/mboxmessageinfo/entryid/) que proporciona acceso a identificadores únicos para cada mensaje en el archivo MBOX. Este identificador puede almacenarse en una base de datos o usarse como referencia para encontrar y extraer mensajes específicos rápidamente cuando sea necesario.

El método [ExtractMessage(string id)](https://reference.aspose.com/email/net/aspose.email.storage.mbox/mboxstoragereader/extractmessage/) en la clase [MboxStorageReader](https://reference.aspose.com/email/net/aspose.email.storage.mbox/mboxstoragereader/#mboxstoragereader-class) permite a los desarrolladores extraer mensajes según su EntryId único. Con el método [ExtractMessage(string id)](https://reference.aspose.com/email/net/aspose.email.storage.mbox/mboxstoragereader/extractmessage/), puedes aprovechar el EntryId almacenado para recuperar el mensaje correspondiente y realizar operaciones adicionales con él.

El siguiente ejemplo de código demuestra cómo extraer mensajes de un archivo MBOX utilizando identificadores:

```cs
MboxStorageReader reader = MboxStorageReader.CreateReader("my.mbox", new MboxLoadOptions());

foreach (MboxMessageInfo msgInfo in reader.EnumerateMessageInfo())
{
    MailMessage eml = reader.ExtractMessage(msgInfo.EntryId, new EmlLoadOptions());
}
```

### **Configuración de opciones de carga al leer mensajes de MBOX**

Las siguientes características te permitirán especificar varias opciones relacionadas con la carga y el procesamiento de mensajes:

- La propiedad MailStorageConverter.MboxMessageOptions - Obtiene o establece las opciones de carga de correo al analizar un almacenamiento Mbox.

- El método MboxrdStorageReader.ReadNextMessage(EmlLoadOptions options) - El parámetro EmlLoadOptions especifica opciones al leer el mensaje del almacenamiento Mbox.

**Ejemplo de código**

```cs
var reader = new MboxrdStorageReader(fileName, new MboxLoadOptions());
// Read messages preserving tnef attachments.
var eml = reader.ReadNextMessage(new EmlLoadOptions {PreserveTnefAttachments = true});
MailStorageConverter.MboxMessageOptions(new EmlLoadOptions {PreserveTnefAttachments = true});
// Convert messages from mbox to pst preserving tnef attachments.
var pst = MailStorageConverter.mboxToPst("Input.mbox", "Output.pst");
```

### **Establecer la codificación de texto preferida al cargar archivos Mbox para lectura**

La opción de codificación está disponible para la clase MboxrdStorageReader. Esto proporciona opciones adicionales para cargar el archivo mbox y asegura que los mensajes con contenido codificado se lean y procesen correctamente. El siguiente fragmento de código muestra cómo puedes establecer la codificación de texto que satisfaga tus necesidades:

```cs
var reader = new MboxrdStorageReader("sample.mbox", new MboxLoadOptions() { PreferredTextEncoding = Encoding.UTF8});
var message = reader.ReadNextMessage();
```

### **Obtener el número total de mensajes de un archivo MBox**

La clase [MboxrdStorageReader](https://reference.aspose.com/email/net/aspose.email.storage.mbox/mboxrdstoragereader/) ofrece la capacidad de leer el número de elementos disponibles en un archivo MBox. Esto puede usarse para desarrollar aplicaciones que muestren el progreso de la actividad mientras procesan dicho archivo.

```cs
// The path to the File directory.
var dataDir = RunExamples.GetDataDir_Thunderbird();

using (var stream = new FileStream(dataDir + "ExampleMbox.mbox", FileMode.Open, FileAccess.Read))
using (var reader = new MboxrdStorageReader(stream, false))
{
    Console.WriteLine("Total number of messages in Mbox file: " + reader.GetTotalItemsCount());
}
```

### **Obtener el tamaño del mensaje actual**

```cs
using (var stream = new FileStream(dataDir + "ExampleMbox.mbox", FileMode.Open, FileAccess.Read))
using (var reader = new MboxrdStorageReader(stream, false))
{
    MailMessage msg;
    while ((msg = reader.ReadNextMessage()) != null)
    {
        long currentDataSize = reader.CurrentDataSize;

        msg.Dispose();
    }
}
```

### **Convertir MBOX a PST conservando o eliminando una firma**

Para eliminar la firma de un archivo durante el proceso de conversión, establece la propiedad [MboxToPstConversionOptions.RemoveSignature](https://reference.aspose.com/email/net/aspose.email.storage/mboxtopstconversionoptions/removesignature/) en *true*.

El siguiente ejemplo de código muestra cómo utilizar esta propiedad:

```cs
var pstDataStream = new MemoryStream();
var personalStorage = PersonalStorage.Create(pstDataStream, FileFormatVersion.Unicode);
MailStorageConverter.MboxToPst(new MboxrdStorageReader(new FileStream(fileName, FileMode.Open, FileAccess.Read), new MboxLoadOptions()),
personalStorage,
    "Inbox",
new MboxToPstConversionOptions() { RemoveSignature = true });
```

## **Escritura de archivos MBOX**

La clase [MboxrdStorageWriter](https://reference.aspose.com/email/net/aspose.email.storage.mbox/mboxrdstoragewriter/) proporciona la facilidad para escribir nuevos mensajes en el archivo de almacenamiento de correo de Thunderbird. Para escribir mensajes:

1. Abre el archivo de almacenamiento de Thunderbird en *FileStream*.
1. Crea una instancia de la clase [MboxrdStorageWriter](https://reference.aspose.com/email/net/aspose.email.storage.mbox/mboxrdstoragewriter/) y pasa el flujo anterior al constructor.
1. Prepara un nuevo mensaje utilizando la clase [MailMessage](https://reference.aspose.com/email/net/aspose.email/mailmessage/).
1. Llama al método [WriteMessage()](https://reference.aspose.com/email/net/aspose.email.storage.mbox/mboxrdstoragewriter/writemessage/#writemessage/) y pasa la instancia de [MailMessage](https://reference.aspose.com/email/net/aspose.email/mailmessage/) anterior para agregar el mensaje al almacenamiento de Thunderbird.
1. Cierra todos los flujos.

El siguiente fragmento de código muestra cómo escribir mensajes en el almacenamiento de correo de Thunderbird.

```cs
// Open the storage file with FileStream
var stream = new FileStream(dataDir + "ExampleMbox.mbox", FileMode.Open, FileAccess.Write);

// Initialize MboxStorageWriter and pass the above stream to it
var writer = new MboxrdStorageWriter(stream, false);
// Prepare a new message using the MailMessage class
var message = new MailMessage("from@domain.com", "to@domain.com", Guid.NewGuid().ToString(), "added from Aspose.Email");
message.IsDraft = false;
// Add this message to storage
writer.WriteMessage(message);
// Close all related streams
writer.Dispose();
stream.Close();
```