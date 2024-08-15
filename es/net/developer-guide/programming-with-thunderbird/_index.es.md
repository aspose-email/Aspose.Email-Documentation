---
title: "Programación con Thunderbird"
url: /es/net/programming-with-thunderbird/
weight: 110
type: docs
---


## **Lectura de archivos MBOX**

[Mozilla Thunderbird](https://www.thunderbird.net/en-US/) es un cliente de correo electrónico multiplataforma de código abierto, desarrollado por la Fundación Mozilla. Almacena los correos electrónicos en su propia estructura de archivos, administrando los índices y subcarpetas de los mensajes a través de formatos de archivo patentados. Aspose.Email puede funcionar con las estructuras de almacenamiento de correo de Thunderbird. El [MboxrdStorageReader](https://reference.aspose.com/email/net/aspose.email.storage.mbox/mboxrdstoragereader/) La clase permite a los desarrolladores leer los mensajes del archivo de almacenamiento de correo Mozilla Thunderbird. Este artículo muestra cómo leer los mensajes del almacenamiento de correo electrónico de Thunderbird:

1. Abre el archivo de almacenamiento de Thunderbird en *FileStream*.
1. Crea una instancia del [MboxrdStorageReader](https://reference.aspose.com/email/net/aspose.email.storage.mbox/mboxrdstoragereader/) clase y pasa la secuencia anterior al constructor.
1. Call [ReadNextMessage()](https://reference.aspose.com/email/net/aspose.email.storage.mbox/mboxrdstoragereader/readnextmessage/#readnextmessage/) para recibir el primer mensaje.
1. Usa lo mismo [ReadNextMessage()](https://reference.aspose.com/email/net/aspose.email.storage.mbox/mboxrdstoragereader/readnextmessage/#readnextmessage/) en un bucle de tiempo para leer todos los mensajes.
1. Cierra todos los canales.

El siguiente fragmento de código muestra cómo leer todos los mensajes de un almacenamiento de correo de Thunderbird.

```cs
// The path to the File directory.
var dataDir = RunExamples.GetDataDir_Thunderbird();

// Open the storage file with FileStream
var stream = new FileStream(dataDir + "ExampleMbox.mbox", FileMode.Open, FileAccess.Read);
// Crea una instancia del MboxrdStorageReader class and pass the stream
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

### **Recuperar las propiedades del mensaje**

[MboxMessageInfo](https://reference.aspose.com/email/net/aspose.email.storage.mbox/mboxmessageinfo/#mboxmessageinfo-class) La clase contiene las siguientes propiedades para recuperar información sobre un mensaje:

- DateTime [Date](https://reference.aspose.com/email/net/aspose.email.storage.mbox/mboxmessageinfo/date/#mboxmessageinfodate-property) - Obtiene la fecha del mensaje
- MailAddress [From](https://reference.aspose.com/email/net/aspose.email.storage.mbox/mboxmessageinfo/from/#mboxmessageinfofrom-property) - Obtiene la dirección de origen
- string [Subject](https://reference.aspose.com/email/net/aspose.email.storage.mbox/mboxmessageinfo/subject/) - Obtiene el asunto del mensaje
- MailAddressCollection [To](https://reference.aspose.com/email/net/aspose.email.storage.mbox/mboxmessageinfo/to/) - Obtiene la colección de direcciones que contiene los destinatarios del mensaje
- MailAddressCollection [CC](https://reference.aspose.com/email/net/aspose.email.storage.mbox/mboxmessageinfo/cc/) - Obtiene la colección de direcciones que contiene los destinatarios del CC
- MailAddressCollection [Bcc](https://reference.aspose.com/email/net/aspose.email.storage.mbox/mboxmessageinfo/bcc/) - Obtiene la colección de direcciones que contiene los destinatarios BCC del mensaje

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

### **Extraer mensajes de MBOX mediante identificadores**

The [MboxStorageReader](https://reference.aspose.com/email/net/aspose.email.storage.mbox/mboxstoragereader/#mboxstoragereader-class) la clase incluye el [EnumerateMessageInfo()](https://reference.aspose.com/email/net/aspose.email.storage.mbox/mboxstoragereader/enumeratemessageinfo/) método, que le permite recorrer en iteración cada mensaje de un archivo MBOX. Al utilizar este método, es posible extraer mensajes individuales sin necesidad de recorrer todo el almacenamiento de forma repetida. Esto mejora el rendimiento y reduce el tiempo de procesamiento.

The [MboxMessageInfo](https://reference.aspose.com/email/net/aspose.email.storage.mbox/mboxmessageinfo/#mboxmessageinfo-class) la clase proporciona la [EntryId](https://reference.aspose.com/email/net/aspose.email.storage.mbox/mboxmessageinfo/entryid/) propiedad, que proporciona acceso a identificadores únicos para cada mensaje del archivo MBOX. Este identificador puede almacenarse en una base de datos o usarse como referencia para buscar y extraer rápidamente mensajes específicos cuando sea necesario.

The [ExtractMessage (identificador de cadena)](https://reference.aspose.com/email/net/aspose.email.storage.mbox/mboxstoragereader/extractmessage/) método en el [MboxStorageReader](https://reference.aspose.com/email/net/aspose.email.storage.mbox/mboxstoragereader/#mboxstoragereader-class) La clase permite a los desarrolladores extraer mensajes en función de su EntryID único. Con el [ExtractMessage (identificador de cadena)](https://reference.aspose.com/email/net/aspose.email.storage.mbox/mboxstoragereader/extractmessage/) método, puede aprovechar el EntryID almacenado para recuperar el mensaje correspondiente y realizar operaciones adicionales con él.

El siguiente ejemplo de código muestra cómo extraer mensajes de un archivo MBOX mediante identificadores:

```cs
MboxStorageReader reader = MboxStorageReader.CreateReader("my.mbox", new MboxLoadOptions());

foreach (MboxMessageInfo msgInfo in reader.EnumerateMessageInfo())
{
    MailMessage eml = reader.ExtractMessage(msgInfo.EntryId, new EmlLoadOptions());
}
```

### **Configuración de las opciones de carga al leer mensajes de MBOX**

Las siguientes funciones le permitirán especificar varias opciones relacionadas con la carga y el procesamiento de mensajes:

- Propiedad MailStorageConverter.mboxMessageOptions: obtiene o establece las opciones de carga de correo electrónico al analizar un almacenamiento de Mbox.

- Método mboxRDStorageReader.readNextMessage (opciones de emllOdOptions): el parámetro emllOdOptions especifica las opciones al leer un mensaje del almacenamiento de Mbox.

**Ejemplo de código**

```cs
var reader = new MboxrdStorageReader(fileName, new MboxLoadOptions());
// Read messages preserving tnef attachments.
var eml = reader.ReadNextMessage(new EmlLoadOptions {PreserveTnefAttachments = true});
MailStorageConverter.MboxMessageOptions(new EmlLoadOptions {PreserveTnefAttachments = true});
// Convert messages from mbox to pst preserving tnef attachments.
var pst = MailStorageConverter.mboxToPst("Input.mbox", "Output.pst");
```

### **Configuración de la codificación de texto preferida al cargar archivos Mbox para su lectura**

La opción de codificación está disponible para la clase mboxRDStorageReader. Esto proporciona opciones adicionales para cargar el archivo mbox y garantiza que los mensajes con el contenido codificado se lean y procesen correctamente. El siguiente fragmento de código muestra cómo puede configurar la codificación del texto para que satisfaga sus necesidades:

```cs
var reader = new MboxrdStorageReader("sample.mbox", new MboxLoadOptions() { PreferredTextEncoding = Encoding.UTF8});
var message = reader.ReadNextMessage();
```

### **Obtener el número total de mensajes del archivo MBox**

The [MboxrdStorageReader](https://reference.aspose.com/email/net/aspose.email.storage.mbox/mboxrdstoragereader/) La clase proporciona la capacidad de leer la cantidad de elementos disponibles en un archivo MBox. Esto se puede usar para desarrollar aplicaciones que muestren el progreso de la actividad mientras se procesa dicho archivo.

```cs
// The path to the File directory.
var dataDir = RunExamples.GetDataDir_Thunderbird();

using (var stream = new FileStream(dataDir + "ExampleMbox.mbox", FileMode.Open, FileAccess.Read))
using (var reader = new MboxrdStorageReader(stream, false))
{
    Console.WriteLine("Total number of messages in Mbox file: " + reader.GetTotalItemsCount());
}
```

### **Obtener el tamaño actual del mensaje**

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

### **Conversión de MBOX a PST Conservar o eliminar una firma**

Para eliminar la firma de un archivo durante el proceso de conversión, defina [MboxToPstConversionOptions.RemoveSignature](https://reference.aspose.com/email/net/aspose.email.storage/mboxtopstconversionoptions/removesignature/) propiedad a *true*.

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

The [MboxrdStorageWriter](https://reference.aspose.com/email/net/aspose.email.storage.mbox/mboxrdstoragewriter/) La clase proporciona la posibilidad de escribir nuevos mensajes en el archivo de almacenamiento de correo de Thunderbird. Para escribir mensajes:

1. Abre el archivo de almacenamiento de Thunderbird en *FileStream*.
1. Crea una instancia del [MboxrdStorageWriter](https://reference.aspose.com/email/net/aspose.email.storage.mbox/mboxrdstoragewriter/) clase y pasa la secuencia anterior al constructor.
1. Prepare un mensaje nuevo mediante el [MailMessage](https://reference.aspose.com/email/net/aspose.email/mailmessage/) class.
1. Llame al [WriteMessage()](https://reference.aspose.com/email/net/aspose.email.storage.mbox/mboxrdstoragewriter/writemessage/#writemessage/) método y pase lo anterior [MailMessage](https://reference.aspose.com/email/net/aspose.email/mailmessage/) instancia para añadir el mensaje al almacenamiento de Thunderbird.
1. Cierra todas las transmisiones.

El siguiente fragmento de código muestra cómo escribir mensajes en el almacenamiento de correo de Thunderbird.

```cs
// Open the storage file with FileStream
var stream = new FileStream(dataDir + "ExampleMbox.mbox", FileMode.Open, FileAccess.Write);

// Initialize MboxStorageWriter and pass the above stream to it
var writer = new MboxrdStorageWriter(stream, false);
// Prepare un mensaje nuevo mediante el MailMessage class
var message = new MailMessage("from@domain.com", "to@domain.com", Guid.NewGuid().ToString(), "added from Aspose.Email");
message.IsDraft = false;
// Add this message to storage
writer.WriteMessage(message);
// Close all related streams
writer.Dispose();
stream.Close();
```

