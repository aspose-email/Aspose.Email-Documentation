---
title: "Programación con Thunderbird"
url: /es/java/programming-with-thunderbird/
weight: 100
type: docs
---

## **Leer mensajes de MBOX**
[Mozilla Thunderbird](https://www.thunderbird.net/en-US/) es un cliente de correo electrónico multiplataforma de código abierto, desarrollado por la Fundación Mozilla. Almacena los correos electrónicos en su propia estructura de archivos, administrando los índices y subcarpetas de los mensajes a través de formatos de archivo patentados. Aspose.Email puede funcionar con las estructuras de almacenamiento de correo de Thunderbird. El [MboxrdStorageReader](https://apireference.aspose.com/email/java/com.aspose.email/mboxrdstoragereader) La clase permite a los desarrolladores leer los mensajes del archivo de almacenamiento de correo de Mozilla Thunderbird. Este artículo muestra cómo leer los mensajes del almacenamiento de correo electrónico de Thunderbird:

1. Abre el archivo de almacenamiento de Thunderbird en *FileStream*.
1. Crea una instancia del [MboxrdStorageReader](https://apireference.aspose.com/email/java/com.aspose.email/mboxrdstoragereader) clase y pasa la secuencia anterior al constructor.
1. Call [ReadNextMessage()](https://apireference.aspose.com/email/java/com.aspose.email/MboxrdStorageReader#readNextMessage\(\)) para recibir el primer mensaje.
1. Usa lo mismo [ReadNextMessage()](https://apireference.aspose.com/email/java/com.aspose.email/MboxrdStorageReader#readNextMessage\(\)) en un bucle de tiempo para leer todos los mensajes.
1. Cierra todos los canales.

El siguiente fragmento de código muestra cómo leer todos los mensajes de un almacenamiento de correo de Thunderbird.
~~~Java
//Getting Marker information while reading messages from Mbox storage file
try (FileInputStream stream = new FileInputStream(dataDir + "Outlook.pst")) {
    MboxLoadOptions lo = new MboxLoadOptions();
    lo.setLeaveOpen(false);
    try (MboxrdStorageReader reader = new MboxrdStorageReader(stream, lo)) {
        MailMessage msg;
        String[] fromMarker = {null};
        while ((msg = reader.readNextMessage(/* out */fromMarker)) != null) {
            System.out.println(fromMarker[0]);
        }
    }
}
~~~

### **Configurar las opciones de carga al leer mensajes de MBOX**

La API Aspose.Email permite las siguientes manipulaciones con los mensajes al leerlos desde un archivo MBOX:

**Convierte mensajes de MBOX a PST conservando los archivos adjuntos TNEF**

```java
EmlLoadOptions emlLoadOptions = new EmlLoadOptions();
emlLoadOptions.setPreserveTnefAttachments(true);
MailStorageConverter.setMboxMessageOptions(emlLoadOptions);
// Convert messages from mbox to pst preserving tnef attachments.
PersonalStorage storage = MailStorageConverter.mboxToPst("Input.mbox", "Output.pst");
```
[MailStorageConverter.MboxMessageOptions()](https://reference.aspose.com/email/java/com.aspose.email/mailstorageconverter/) propiedad: obtiene o establece las opciones de carga de correo electrónico al analizar un almacenamiento de Mbox.

**Lea los mensajes que conservan los archivos adjuntos de TNEF**

```java
MboxrdStorageReader reader = new MboxrdStorageReader("Input.mbox", new MboxLoadOptions());
// Read messages preserving tnef attachments.
EmlLoadOptions emlLoadOptions = new EmlLoadOptions();
emlLoadOptions.setPreserveTnefAttachments(true);
MailMessage eml = reader.readNextMessage(emlLoadOptions);
```
[mboxRDStorageReader.readNextMessage (opciones de EmllOdOptions)](https://reference.aspose.com/email/java/com.aspose.email/emlloadoptions/#getPreserveTnefAttachments--) método: el parámetro emlloAdOptions especifica las opciones al leer un mensaje del almacenamiento de Mbox.

**Enumerar los mensajes que conservan los archivos adjuntos de TNEF**

```java
EmlLoadOptions emlLoadOptions = new EmlLoadOptions();
emlLoadOptions.setPreserveTnefAttachments(true);
// Enumerate messages preserving tnef attachments.
for (MailMessage message : reader.enumerateMessages(emlLoadOptions)) {
    // do something
}
```
[mboxRDStorageReader.enumerateMessages (opciones de EmllOdOptions)](https://reference.aspose.com/email/java/com.aspose.email/mboxrdstoragereader/#enumerateMessages--) método: especifica emllodOptions al leer un mensaje del almacenamiento de Mbox.

## **Extraer mensajes de MBOX mediante identificadores**

A veces es necesario extraer los mensajes seleccionados por identificadores. Por ejemplo, su aplicación almacena los identificadores en una base de datos y extrae un mensaje cuando lo solicita. Esta es la forma eficaz de evitar tener que recorrer todo el almacenamiento cada vez para encontrar un mensaje específico que extraer. Para implementar esta función en los archivos MBOX, Aspose.Email proporciona los siguientes métodos y clases:

- [MboxMessageInfo](https://reference.aspose.com/email/java/com.aspose.email/mboxmessageinfo/) clase con el [EntryId](https://reference.aspose.com/email/java/com.aspose.email/mboxmessageinfo/#getEntryId--) propiedad: obtiene el identificador de entrada.
- [enumerateMessageInfo()](https://reference.aspose.com/email/java/com.aspose.email/mboxstoragereader/#enumerateMessageInfo--) método del [MboxStorageReader](https://reference.aspose.com/email/java/com.aspose.email/mboxstoragereader/) class: expone el enumerador, que admite una iteración de los mensajes almacenados.
- [ExtractMessage (identificador de cadena)](https://reference.aspose.com/email/java/com.aspose.email/mboxstoragereader/#extractMessage-java.lang.String-com.aspose.email.EmlLoadOptions-) método del [MboxStorageReader](https://reference.aspose.com/email/java/com.aspose.email/mboxstoragereader/) class: obtiene el mensaje de MBOX.

El ejemplo de código que aparece a continuación muestra cómo extraer mensajes de MBOX mediante identificadores:

```java
MboxStorageReader reader = MboxStorageReader.createReader("my.mbox", new MboxLoadOptions());

for (MboxMessageInfo msgInfo : reader.enumerateMessageInfo()) {
    MailMessage eml = reader.extractMessage(msgInfo.getEntryId(), new EmlLoadOptions());
}
```
**Note:** El identificador del mensaje es único en el archivo de almacenamiento. Los ID los crea Aspose.Email y no se pueden usar en bibliotecas o aplicaciones de procesamiento de MBOX de terceros.

## **Redacción de mensajes**
The [MboxrdStorageWriter](https://apireference.aspose.com/email/java/com.aspose.email/mboxrdstoragewriter) La clase ofrece la posibilidad de escribir nuevos mensajes en el archivo de almacenamiento de correo de Thunderbird. Para escribir mensajes:

1. Abre el archivo de almacenamiento de Thunderbird en *FileStream*.
1. Crea una instancia del [MboxrdStorageWriter](https://apireference.aspose.com/email/java/com.aspose.email/mboxrdstoragewriter) clase y pasa la secuencia anterior al constructor.
1. Prepare un mensaje nuevo mediante el [MailMessage](https://apireference.aspose.com/email/java/com.aspose.email/mailmessage) class.
1. Llame al [WriteMessage()](https://apireference.aspose.com/email/java/com.aspose.email/MboxrdStorageWriter#writeMessage\(com.aspose.email.MailMessage\)) método y pase lo anterior [MailMessage](https://apireference.aspose.com/email/java/com.aspose.email/mailmessage) instancia para añadir el mensaje al almacenamiento de Thunderbird.
1. Cierra todas las transmisiones.

El siguiente fragmento de código muestra cómo escribir mensajes en el almacenamiento de correo de Thunderbird.
~~~Java
//Getting marker information while writing messages to Mbox storage file
try (FileOutputStream writeStream = new FileOutputStream(dataDir + "inbox")) {
    try (MboxrdStorageWriter writer = new MboxrdStorageWriter(writeStream, false)) {
        MailMessage msg = MailMessage.load(dataDir + "Message.msg");
        String[] fromMarker = {null};
        writer.writeMessage(msg, fromMarker);
        System.out.println(fromMarker[0]);
    }
}
~~~

## **Obtener el número total de mensajes del archivo MBox**
The [MboxrdStorageReader](https://apireference.aspose.com/email/java/com.aspose.email/mboxrdstoragereader) La clase proporciona la capacidad de leer la cantidad de elementos disponibles en un archivo MBox. Esto se puede usar para desarrollar aplicaciones que muestren el progreso de la actividad mientras se procesa dicho archivo.
~~~Java
MboxLoadOptions lo = new MboxLoadOptions();
try (MboxrdStorageReader reader = new MboxrdStorageReader("inbox.dat", lo)) {
    System.out.println("Total number of messages in Mbox file: " + reader.getTotalItemsCount());
}
~~~

## **Obtener el tamaño actual del mensaje**
~~~Java
FileInputStream stream = new FileInputStream(dataDir + "ExampleMbox.mbox");
MboxLoadOptions lo = new MboxLoadOptions();
try (MboxrdStorageReader reader = new MboxrdStorageReader(stream, lo)) {
    MailMessage msg = null;
    while ((msg = reader.readNextMessage()) != null) {
        //returns the number of bytes read
        long currentDataSize = reader.getCurrentDataSize();
        System.out.println("Bytes read: " + currentDataSize);
    }
}
~~~

## **Establecer la codificación de texto preferida al cargar archivos Mbox**

The [setPreferredTextEncoding (valor del conjunto de caracteres)](https://reference.aspose.com/email/java/com.aspose.email/mboxloadoptions/#setPreferredTextEncoding-java.nio.charset.Charset-) método del [MboxLoadOptions](https://reference.aspose.com/email/java/com.aspose.email/mboxloadoptions/) la clase obtiene o establece la codificación preferida para los mensajes. Cree un lector para el archivo Mbox con las opciones de carga especificadas y sus mensajes con el contenido codificado se leerán y procesarán correctamente. El siguiente ejemplo de código muestra cómo implementar esta función en un proyecto:

~~~Java
MboxLoadOptions lo = new MboxLoadOptions();
lo.setPreferredTextEncoding(Charset.forName("utf-8"));
MboxrdStorageReader reader = new MboxrdStorageReader("sample.mbox", lo);
MailMessage message = reader.readNextMessage();
~~~

## **Divida el almacenamiento de Mbox en partes más pequeñas**

Aspose.Email proporciona los siguientes componentes diseñados para tener un mayor control sobre el procesamiento del almacenamiento de Mbox, lo que le permite dividir archivos grandes en partes manejables e implementar acciones personalizadas durante el proceso:

- [mboxStorageReader.splitInto (tamaño de fragmento largo, ruta de salida de cadena)](https://reference.aspose.com/email/java/com.aspose.email/mboxstoragereader/#splitInto-long-java.lang.String-) método: permite dividir el almacenamiento de Mbox en partes más pequeñas, lo que facilita la administración y el procesamiento de archivos Mbox de gran tamaño.

mboxStorageReader.splitInto (long ChunkSize, String outputPath, String PartFilenamePrefix) Este método es una variante del método anterior y también permite especificar un prefijo personalizado para los nombres de los archivos de Mbox divididos.

Evento mboxStorageReader.setEmlCoptingEventHandler Este evento se produce antes de que un correo electrónico se copie en un nuevo archivo de Mbox. Puede personalizar las acciones antes de procesar los correos electrónicos.

Evento mboxStorageReader.setEmlCopiedEventHandler Este evento se produce después de copiar un correo electrónico en un archivo Mbox nuevo. Puede realizar acciones de posprocesamiento en los correos electrónicos.

Evento mboxStorageReader.setMboxFileCreateEventHandler Este evento se produce cuando se crea un archivo Mbox nuevo. Puede gestionar este evento para reaccionar a la creación de un archivo.

Evento mboxStorageReader.setMboxFileFilledEventHandler Este evento se produce cuando un nuevo archivo Mbox se llena de correos electrónicos. Puede responder a que el archivo se esté rellenando con correos electrónicos.

NewStorageEventHandler (Object sender, newStorageEventArgs e) Representa un delegado para gestionar los eventos que se producen después de crear o procesar un nuevo archivo de almacenamiento.

mimeItemCopyEventHandler (remitente del objeto, mimeItemCopyEventArgs e) Representa un delegado para gestionar los eventos relacionados con la copia de elementos Mime, que normalmente se usa en situaciones en las que un objeto MailMessage se copia de un almacenamiento a otro.

NewStorageEventArgs Representa los argumentos utilizados en los eventos que se generan después de crear o procesar un nuevo archivo de almacenamiento.

mimeItemCopyEventArgs Representa los argumentos de eventos relacionados con la copia de un objeto MailMessage de un almacenamiento a otro, antes de que comience la copia o una vez finalizada.

El ejemplo de código que aparece a continuación muestra cómo interactuar con los archivos Mbox, gestionar los eventos relacionados con estos archivos y realizar operaciones como dividir el almacenamiento de Mbox en partes más pequeñas y, al mismo tiempo, realizar un seguimiento del recuento de mensajes y el recuento de partes:

```java
messageCount = 0;
partCount = 0;

// Create an instance of MboxrdStorageReader
MboxLoadOptions lo = new MboxLoadOptions();
lo.setLeaveOpen(false);
MboxrdStorageReader mbox = new MboxrdStorageReader("my.mbox", lo);

// Subscribe to events
mbox.setMboxFileCreatedEventHandler(new NewStorageEventHandler() {
    public void invoke(Object sender, NewStorageEventArgs e) {
        System.out.println("New Mbox file created: " + e.getFileName());
        partCount++;
    }
});

mbox.setMboxFileFilledEventHandler(new NewStorageEventHandler() {
    public void invoke(Object sender, NewStorageEventArgs e) {
        System.out.println("Mbox file filled with messages: " + e.getFileName());
    }
});

mbox.setEmlCopiedEventHandler(new MimeItemCopyEventHandler() {
    public void invoke(Object sender, MimeItemCopyEventArgs e) {
        System.out.println("Message added to new Mbox file. Subject: " + e.getItem().getSubject());
        messageCount++;
    }
});

// Split the Mbox storage into smaller parts
mbox.splitInto(10000000, testOutPath, "Prefix");

// Output the final messageCount and partCount
System.out.println("Total messages added: " + messageCount);
System.out.println("Total parts created: " + partCount);
```