---
title: "Crear nuevo PST, agregar subcarpetas y mensajes"
url: /es/java/create-new-pst-add-sub-folders-and-messages/
weight: 10
type: docs
---

Además de analizar un archivo PST existente, Aspose.Email proporciona los medios para crear un archivo PST desde cero. Este artículo demuestra cómo crear un archivo PST de Outlook y agregarle una subcarpeta.

1. [Crear un nuevo archivo PST](#creating-a-new-pst-file-and-add-subfolders).
1. [Cambiar la clase del contenedor de una carpeta](#changing-a-folders-container-class).
1. [Agregar mensajes en masa con un rendimiento mejorado](#add-bulk-messages-with-improved-performance) 

Utiliza la clase [PersonalStorage](https://reference.aspose.com/email/java/com.aspose.email/personalstorage/) para crear un archivo PST en alguna ubicación en un disco local. Para crear un archivo PST desde cero:

1. Crea un PST usando el método [PersonalStorage.create()](https://reference.aspose.com/email/java/com.aspose.email/personalstorage/#create-java.io.OutputStream-int-) .
1. Agrega una subcarpeta en la raíz del archivo PST accediendo a la carpeta raíz y luego llamando al método [addSubFolder()](https://reference.aspose.com/email/java/com.aspose.email/folderinfo/#addSubFolder-java.lang.String-) .

El siguiente fragmento de código te muestra cómo crear un archivo PST y agregar una subcarpeta llamada Inbox.

```java
// Crear nuevo PST
try (PersonalStorage pst = PersonalStorage.create(path, FileFormatVersion.Unicode)) {
    // Agregar nueva carpeta "Test"
    pst.getRootFolder().addSubFolder("Inbox");
}
```
## **Crear PST con tamaño superior a 2Gb usando OutputStream**

Los usuarios de Aspose.Email pueden optimizar la caché interna de PST usando el constructor PersonalStorage:

- **blockSize** - El tamaño óptimo del bloque para expandir el búfer de caché (en bytes).

```java
PersonalStorage create(OutputStream stream, int blockSize, /*FileFormatVersion*/int version)
```
## **Reducir el tamaño del mensaje y el tamaño del archivo PST creado**

Aspose.Email ofrece la capacidad de comprimir el contenido del cuerpo, lo que puede ayudar a reducir el tamaño del mensaje. Esto puede ser particularmente útil al enviar mensajes grandes o cuando se trata de limitaciones de ancho de banda o almacenamiento. Para este propósito, la biblioteca proporciona el parámetro de compresión incluido en los siguientes métodos:

- [MapiMessageItemBase.setBodyContent(String content, /*BodyContentType*/int contentType, boolean compression)](https://reference.aspose.com/email/java/com.aspose.email/mapimessageitembase/#setBodyContent-java.lang.String-int-boolean-) - Establece el contenido del cuerpo.
- [MapiMessageItemBase.setBodyRtf(String content, boolean compression)](https://reference.aspose.com/email/java/com.aspose.email/mapimessageitembase/#setBodyRtf-java.lang.String-boolean-) - Obtiene o establece el texto del mensaje formateado en RTF.

El siguiente fragmento de código demuestra cómo utilizar la compresión RTF al establecer el cuerpo del mensaje MAPI:

```java
MapiMessage msg = new MapiMessage("from@doamin.com", "to@domain.com", "subject", "body");
// establecer el cuerpo html y mantenerlo comprimido
// esto reducirá el tamaño del mensaje
msg.setBodyContent(htmlBody, BodyContentType.Html, true);
```
## **Crear PersonalStorage basado en la corriente SeekableByteChannel**

Aspose.Email para Java hace posible trabajar con archivos de Almacenamiento Personal (PST) usando java.nio.channels. Te permite crear una instancia de PersonalStorage utilizando una corriente SeekableByteChannel. El siguiente fragmento de código demuestra cómo crear una instancia de PersonalStorage basada en una corriente FileChannel, agregar una subcarpeta llamada "messageFolder" a la carpeta raíz e importar mensajes de archivos en el directorio "messageFolder": 

```cs
try (RandomAccessFile raf = new RandomAccessFile("test.pst", "rw")) {
    FileChannel channel = raf.getChannel();
    try (PersonalStorage pst = PersonalStorage.create(channel, FileFormatVersion.Unicode)) {
        FolderInfo messageFolder = pst.getRootFolder().addSubFolder("messageFolder");

        for (File f : new File("messageFolder").listFiles()) {
            messageFolder.addMessage(MapiMessage.load(f.getAbsolutePath()));
        }
    }
}
```

## **Cambio de la clase del contenedor de una carpeta**

A veces es necesario cambiar la clase de una carpeta. Un ejemplo común es cuando se agregan mensajes de diferentes tipos (citas, mensajes, etc.) a la misma carpeta. En tales casos, la clase de la carpeta debe cambiarse para que todos los elementos en la carpeta se muestren correctamente. El siguiente fragmento de código te muestra cómo cambiar la clase del contenedor de una carpeta en PST para este propósito.

```java
try (PersonalStorage pst = PersonalStorage.fromFile("PersonalStorage1.pst")) {
    FolderInfo folder = pst.getRootFolder().getSubFolder("Inbox");

    folder.changeContainerClass("IPF.Note");
}
```

## **Agregar mensajes en masa con un rendimiento mejorado**

Agregar mensajes individuales a un PST implica más operaciones de E/S en disco y puede ralentizar el rendimiento. Para mejorar el rendimiento, los mensajes se pueden agregar al PST en modo masivo para minimizar las operaciones de E/S. 
El método [addMessages(Iterable<MapiMessage> messages)](https://reference.aspose.com/email/java/com.aspose.email/folderinfo/#addMessages-java.lang.Iterable-com.aspose.email.MapiMessage--) permite agregar mensajes en masa y se puede usar en los siguientes escenarios. Además, el evento [MessageAdded](https://reference.aspose.com/email/java/com.aspose.email/folderinfo/#MessageAdded) ocurre cuando se agrega un mensaje a la carpeta.

### **Agregar mensajes desde otro PST**

Para agregar mensajes desde otro PST, utiliza el método [FolderInfo.enumerateMapiMessages()](https://reference.aspose.com/email/java/com.aspose.email/folderinfo/#enumerateMapiMessages--) que devuelve `Iterable<MapiMessage>`:

```java
try (PersonalStorage srcPst = PersonalStorage.fromFile("source.pst", false)) {
    try (PersonalStorage destPst = PersonalStorage.fromFile("destination.pst")) {

        // Obtener la carpeta por nombre
        FolderInfo srcFolder = srcPst.getRootFolder().getSubFolder("SomeFolder");
        FolderInfo destFolder = destPst.getRootFolder().getSubFolder("SomeFolder");

        destFolder.MessageAdded.add(new MessageAddedEventHandler() {
            // Maneja el evento MessageAdded.
            public void invoke(Object sender, MessageAddedEventArgs e) {
                System.out.println("Agregado: " + e.getEntryId());
            }
        });
        destFolder.addMessages(srcFolder.enumerateMapiMessages());
    }
}
```

### **Agregar mensajes desde un directorio**

Para agregar mensajes desde un directorio, crea el método `getMessages(String pathToDir)` que devuelve `Iterable<MapiMessage>`:

```java
// Leer mensajes desde el directorio.
static Iterable<MapiMessage> getMessages (String pathToDir)
{
    return Arrays.stream(listDirectory(pathToDir, "*.msg"))
            .map(MapiMessage::load).collect(Collectors.toList());
}

try ( PersonalStorage pst = PersonalStorage.fromFile("storage.pst")) {
    FolderInfo folder = pst.getRootFolder().getSubFolder("SomeFolder");
    folder.MessageAdded.add(new MessageAddedEventHandler() {
        // Maneja el evento MessageAdded.
        public void invoke(Object sender, MessageAddedEventArgs e) {
            System.out.println("Agregado: " + e.getEntryId());
        }
    });
    folder.addMessages(getMessages("MessageDirectory"));
}
```