---
title: "Programación con Thunderbird"
url: /es/java/programming-with-thunderbird/
weight: 100
type: docs
---

## **Leer Mensajes desde MBOX**
[Mozilla Thunderbird](https://www.thunderbird.net/en-US/) es un cliente de correo electrónico de código abierto y multiplataforma, desarrollado por la Fundación Mozilla. Almacena correos electrónicos en su propia estructura de archivos, gestionando índices de mensajes y subcarpetas a través de formatos de archivo propietarios. Aspose.Email puede trabajar con estructuras de almacenamiento de correo de Thunderbird. La clase [MboxrdStorageReader](https://apireference.aspose.com/email/java/com.aspose.email/mboxrdstoragereader) permite a los desarrolladores leer mensajes del archivo de almacenamiento de correo de Mozilla Thunderbird. Este artículo muestra cómo leer los mensajes del almacenamiento de correo de Thunderbird:

1. Abre el archivo de almacenamiento de Thunderbird en *FileStream*.
1. Crea una instancia de la clase [MboxrdStorageReader](https://apireference.aspose.com/email/java/com.aspose.email/mboxrdstoragereader) y pasa el flujo anterior al constructor.
1. Llama a [ReadNextMessage()](https://apireference.aspose.com/email/java/com.aspose.email/MboxrdStorageReader#readNextMessage\(\)) para obtener el primer mensaje.
1. Utiliza el mismo [ReadNextMessage()](https://apireference.aspose.com/email/java/com.aspose.email/MboxrdStorageReader#readNextMessage\(\)) en un bucle while para leer todos los mensajes.
1. Cierra todos los flujos.

El siguiente fragmento de código te muestra cómo leer todos los mensajes de un almacenamiento de correo de Thunderbird.
~~~Java
//Obteniendo información del marcador mientras se leen mensajes del archivo de almacenamiento Mbox
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

### **Configurar Opciones de Carga al Leer Mensajes desde MBOX**

La API Aspose.Email permite las siguientes manipulaciones con mensajes al leerlos desde un archivo MBOX:

**Convertir Mensajes de MBOX a PST Preservando Adjuntos TNEF**

```java
EmlLoadOptions emlLoadOptions = new EmlLoadOptions();
emlLoadOptions.setPreserveTnefAttachments(true);
MailStorageConverter.setMboxMessageOptions(emlLoadOptions);
// Convertir mensajes de mbox a pst preservando adjuntos tnef.
PersonalStorage storage = MailStorageConverter.mboxToPst("Input.mbox", "Output.pst");
```
La propiedad [MailStorageConverter.MboxMessageOptions()](https://reference.aspose.com/email/java/com.aspose.email/mailstorageconverter/) - Obtiene o establece las opciones de carga de correo al analizar un almacenamiento Mbox.

**Leer Mensajes Preservando Adjuntos TNEF**

```java
MboxrdStorageReader reader = new MboxrdStorageReader("Input.mbox", new MboxLoadOptions());
// Leer mensajes preservando adjuntos tnef.
EmlLoadOptions emlLoadOptions = new EmlLoadOptions();
emlLoadOptions.setPreserveTnefAttachments(true);
MailMessage eml = reader.readNextMessage(emlLoadOptions);
```
El método [MboxrdStorageReader.readNextMessage(EmlLoadOptions options)](https://reference.aspose.com/email/java/com.aspose.email/emlloadoptions/#getPreserveTnefAttachments--) - El parámetro EmlLoadOptions especifica opciones al leer un mensaje del almacenamiento Mbox.

**Enumerar Mensajes Preservando Adjuntos TNEF**

```java
EmlLoadOptions emlLoadOptions = new EmlLoadOptions();
emlLoadOptions.setPreserveTnefAttachments(true);
// Enumerar mensajes preservando adjuntos tnef.
for (MailMessage message : reader.enumerateMessages(emlLoadOptions)) {
    // hacer algo
}
```
El método [MboxrdStorageReader.enumerateMessages(EmlLoadOptions options)](https://reference.aspose.com/email/java/com.aspose.email/mboxrdstoragereader/#enumerateMessages--) - Especifica EmlLoadOptions al leer un mensaje del almacenamiento Mbox.

## **Extraer Mensajes de MBOX por Identificadores**

A veces es necesario extraer mensajes seleccionados por identificadores. Por ejemplo, tu aplicación almacena identificadores en una base de datos y extrae un mensaje a pedido. Esta es la manera eficiente de evitar recorrer todo el almacenamiento cada vez para encontrar un mensaje específico para extraer. Para implementar esta función para archivos MBOX, Aspose.Email proporciona los siguientes métodos y clases:

- La clase [MboxMessageInfo](https://reference.aspose.com/email/java/com.aspose.email/mboxmessageinfo/) con la propiedad [EntryId](https://reference.aspose.com/email/java/com.aspose.email/mboxmessageinfo/#getEntryId--) - Obtiene el identificador de entrada. 
- El método [enumerateMessageInfo()](https://reference.aspose.com/email/java/com.aspose.email/mboxstoragereader/#enumerateMessageInfo--) de la clase [MboxStorageReader](https://reference.aspose.com/email/java/com.aspose.email/mboxstoragereader/) - Expone el enumerador, que soporta la iteración de mensajes en el almacenamiento.
- El método [extractMessage(String id)](https://reference.aspose.com/email/java/com.aspose.email/mboxstoragereader/#extractMessage-java.lang.String-com.aspose.email.EmlLoadOptions-) de la clase [MboxStorageReader](https://reference.aspose.com/email/java/com.aspose.email/mboxstoragereader/) - Obtiene el mensaje de MBOX.

El siguiente ejemplo de código demuestra cómo extraer mensajes de MBOX por identificadores:

```java
MboxStorageReader reader = MboxStorageReader.createReader("my.mbox", new MboxLoadOptions());

for (MboxMessageInfo msgInfo : reader.enumerateMessageInfo()) {
    MailMessage eml = reader.extractMessage(msgInfo.getEntryId(), new EmlLoadOptions());
}
```
**Nota:** El ID del mensaje es único dentro del archivo de almacenamiento. Los ID son creados por Aspose.Email y no pueden ser utilizados en otras bibliotecas o aplicaciones de procesamiento de MBOX de terceros.

## **Escribir Mensajes**
La clase [MboxrdStorageWriter](https://apireference.aspose.com/email/java/com.aspose.email/mboxrdstoragewriter) proporciona la facilidad de escribir nuevos mensajes en el archivo de almacenamiento de correo de Thunderbird. Para escribir mensajes:

1. Abre el archivo de almacenamiento de Thunderbird en *FileStream*.
1. Crea una instancia de la clase [MboxrdStorageWriter](https://apireference.aspose.com/email/java/com.aspose.email/mboxrdstoragewriter) y pasa el flujo anterior al constructor.
1. Prepara un nuevo mensaje utilizando la clase [MailMessage](https://apireference.aspose.com/email/java/com.aspose.email/mailmessage).
1. Llama al método [WriteMessage()](https://apireference.aspose.com/email/java/com.aspose.email/MboxrdStorageWriter#writeMessage\(com.aspose.email.MailMessage\)) y pasa la instancia de [MailMessage](https://apireference.aspose.com/email/java/com.aspose.email/mailmessage) anterior para agregar el mensaje al almacenamiento de Thunderbird.
1. Cierra todos los flujos.

El siguiente fragmento de código te muestra cómo escribir mensajes en el almacenamiento de correo de Thunderbird.
~~~Java
//Obteniendo información del marcador mientras se escriben mensajes en el archivo de almacenamiento Mbox
try (FileOutputStream writeStream = new FileOutputStream(dataDir + "inbox")) {
    try (MboxrdStorageWriter writer = new MboxrdStorageWriter(writeStream, false)) {
        MailMessage msg = MailMessage.load(dataDir + "Message.msg");
        String[] fromMarker = {null};
        writer.writeMessage(msg, fromMarker);
        System.out.println(fromMarker[0]);
    }
}
~~~

## **Obteniendo el Número Total de Mensajes desde el Archivo MBox**
La clase [MboxrdStorageReader](https://apireference.aspose.com/email/java/com.aspose.email/mboxrdstoragereader) proporciona la capacidad de leer el número de elementos disponibles en un archivo MBox. Esto puede ser utilizado para desarrollar aplicaciones que muestren el progreso de la actividad mientras se procesa dicho archivo.
~~~Java
MboxLoadOptions lo = new MboxLoadOptions();
try (MboxrdStorageReader reader = new MboxrdStorageReader("inbox.dat", lo)) {
    System.out.println("Número total de mensajes en el archivo Mbox: " + reader.getTotalItemsCount());
}
~~~ 

## **Obtener Tamaño Actual del Mensaje**
~~~Java
FileInputStream stream = new FileInputStream(dataDir + "ExampleMbox.mbox");
MboxLoadOptions lo = new MboxLoadOptions();
try (MboxrdStorageReader reader = new MboxrdStorageReader(stream, lo)) {
    MailMessage msg = null;
    while ((msg = reader.readNextMessage()) != null) {
        //devuelve el número de bytes leídos
        long currentDataSize = reader.getCurrentDataSize();
        System.out.println("Bytes leídos: " + currentDataSize);
    }
}
~~~ 

## **Establecer Codificación de Texto Preferida al Cargar Archivos Mbox**

El método [setPreferredTextEncoding(Charset value)](https://reference.aspose.com/email/java/com.aspose.email/mboxloadoptions/#setPreferredTextEncoding-java.nio.charset.Charset-) de la clase [MboxLoadOptions](https://reference.aspose.com/email/java/com.aspose.email/mboxloadoptions/) obtiene o establece la codificación preferida para los mensajes. Crea un lector para el archivo Mbox con las opciones de carga especificadas y tus mensajes con el contenido codificado serán correctamente leídos y procesados. El siguiente ejemplo de código muestra cómo implementar esta función en un proyecto:

~~~Java
MboxLoadOptions lo = new MboxLoadOptions();
lo.setPreferredTextEncoding(Charset.forName("utf-8"));
MboxrdStorageReader reader = new MboxrdStorageReader("sample.mbox", lo);
MailMessage message = reader.readNextMessage();
~~~ 

## **Dividir Almacenamiento Mbox en Partes Más Pequeñas**

Aspose.Email proporciona los siguientes componentes diseñados para tener más control sobre el procesamiento de almacenamiento Mbox, permitiéndote dividir archivos grandes en partes manejables e implementar acciones personalizadas durante el proceso:

- El método [MboxStorageReader.SplitInto(long chunkSize, String outputPath)](https://reference.aspose.com/email/java/com.aspose.email/mboxstoragereader/#splitInto-long-java.lang.String-) - Te permite dividir el almacenamiento Mbox en partes más pequeñas, facilitando la gestión y el procesamiento de archivos Mbox grandes.

MboxStorageReader.SplitInto(long chunkSize, String outputPath, String partFileNamePrefix) Una variación del método anterior, este también te permite especificar un prefijo personalizado para los nombres de archivos Mbox divididos.

MboxStorageReader.setEmlCopyingEventHandler Evento Este evento ocurre antes de que un correo electrónico sea copiado a un nuevo archivo Mbox. Puedes personalizar acciones antes de que los correos sean procesados.

MboxStorageReader.setEmlCopiedEventHandler Evento Este evento ocurre después de que un correo electrónico es copiado a un nuevo archivo Mbox. Puedes realizar acciones de post-procesamiento en los correos.

MboxStorageReader.setMboxFileCreatedEventHandler Evento Este evento ocurre cuando se crea un nuevo archivo Mbox. Puedes manejar este evento para reaccionar a la creación del archivo.

MboxStorageReader.setMboxFileFilledEventHandler Evento Este evento ocurre cuando un nuevo archivo Mbox se llena con correos electrónicos. Puedes responder al archivo siendo poblado con correos.

NewStorageEventHandler(Object sender, NewStorageEventArgs e) Representa un delegado para manejar eventos que ocurren después de que se crea o procesa un nuevo archivo de almacenamiento.

MimeItemCopyEventHandler(Object sender, MimeItemCopyEventArgs e) Representa un delegado para manejar eventos relacionados con la copia de elementos Mime, típicamente usado en escenarios donde un objeto MailMessage es copiado de un almacenamiento a otro.

NewStorageEventArgs Representa argumentos usados en eventos que se generan después de que se crea un nuevo archivo de almacenamiento o después de que es procesado.

MimeItemCopyEventArgs Representa argumentos de evento relacionados con la copia de un objeto MailMessage de un almacenamiento a otro, ya sea antes de que comience la copia o después de que se complete.

El siguiente ejemplo de código demuestra cómo interactuar con archivos Mbox, manejar eventos relacionados con estos archivos y realizar operaciones como dividir el almacenamiento Mbox en partes más pequeñas mientras se lleva un seguimiento del conteo de mensajes y partes:

```java
messageCount = 0;
partCount = 0;

// Crear una instancia de MboxrdStorageReader
MboxLoadOptions lo = new MboxLoadOptions();
lo.setLeaveOpen(false);
MboxrdStorageReader mbox = new MboxrdStorageReader("my.mbox", lo);

// Suscribirse a eventos
mbox.setMboxFileCreatedEventHandler(new NewStorageEventHandler() {
    public void invoke(Object sender, NewStorageEventArgs e) {
        System.out.println("Nuevo archivo Mbox creado: " + e.getFileName());
        partCount++;
    }
});

mbox.setMboxFileFilledEventHandler(new NewStorageEventHandler() {
    public void invoke(Object sender, NewStorageEventArgs e) {
        System.out.println("Archivo Mbox lleno de mensajes: " + e.getFileName());
    }
});

mbox.setEmlCopiedEventHandler(new MimeItemCopyEventHandler() {
    public void invoke(Object sender, MimeItemCopyEventArgs e) {
        System.out.println("Mensaje añadido al nuevo archivo Mbox. Asunto: " + e.getItem().getSubject());
        messageCount++;
    }
});

// Dividir el almacenamiento Mbox en partes más pequeñas
mbox.splitInto(10000000, testOutPath, "Prefix");

// Salida del conteo final de mensajes y partes
System.out.println("Total de mensajes añadidos: " + messageCount);
System.out.println("Total de partes creadas: " + partCount);
```