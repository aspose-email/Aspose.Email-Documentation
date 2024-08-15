---
title: "Crear un nuevo PST, agregar subcarpetas y mensajes"
url: /es/java/create-new-pst-add-sub-folders-and-messages/
weight: 10
type: docs
---


Además de analizar un archivo PST existente, Aspose.Email proporciona los medios para crear un archivo PST desde cero. Este artículo muestra cómo crear un archivo PST de Outlook y agregarle una subcarpeta.

1. [Creación de un nuevo archivo PST](#creating-a-new-pst-file-and-add-subfolders).
1. [Cambiar la clase de contenedor de una carpeta](#changing-a-folders-container-class).
1. [Agregue mensajes masivos con un rendimiento mejorado](#add-bulk-messages-with-improved-performance)

Usa el [PersonalStorage](https://reference.aspose.com/email/java/com.aspose.email/personalstorage/) clase para crear un archivo PST en alguna ubicación de un disco local. Para crear un archivo PST desde cero:

1. Cree un PST con el [PersonalStorage.create()](https://reference.aspose.com/email/java/com.aspose.email/personalstorage/#create-java.io.OutputStream-int-) method.
1. Agregue una subcarpeta a la raíz del archivo PST; para ello, acceda a la carpeta raíz y, a continuación, llame al [addSubFolder()](https://reference.aspose.com/email/java/com.aspose.email/folderinfo/#addSubFolder-java.lang.String-) method.

El siguiente fragmento de código muestra cómo crear un archivo PST y agregar una subcarpeta denominada Bandeja de entrada.

```java
// Create new PST
try (PersonalStorage pst = PersonalStorage.create(path, FileFormatVersion.Unicode)) {
    // Add new folder "Test"
    pst.getRootFolder().addSubFolder("Inbox");
}
```
## **Cree PST con un tamaño superior a 2 Gb con OutputStream**

Los usuarios de Aspose.Email pueden optimizar la caché interna de PST mediante el constructor PersonalStorage:

- **blockSize** - El tamaño de bloque óptimo para ampliar el búfer de la caché (en bytes).

```java
PersonalStorage create(OutputStream stream, int blockSize, /*FileFormatVersion*/int version)
```
## **Reducir el tamaño del mensaje y el tamaño del archivo PST creado**

Aspose.Email ofrece la capacidad de comprimir el contenido del cuerpo, lo que puede ayudar a reducir el tamaño del mensaje. Esto puede resultar particularmente útil cuando se envían mensajes de gran tamaño o cuando hay limitaciones de ancho de banda o almacenamiento. Para ello, la biblioteca proporciona el parámetro de compresión incluido en los métodos siguientes:

- [mapiMessageItemBase.setBodyContent (contenido de cadena,/*BodyContentType*/int contentType, compresión booleana)](https://reference.aspose.com/email/java/com.aspose.email/mapimessageitembase/#setBodyContent-java.lang.String-int-boolean-) - Establece el contenido del cuerpo.
- [mapiMessageItemBase.setBodyRTF (contenido de cadena, compresión booleana)](https://reference.aspose.com/email/java/com.aspose.email/mapimessageitembase/#setBodyRtf-java.lang.String-boolean-) - Obtiene o establece el texto del mensaje con formato RTF.

El siguiente fragmento de código muestra cómo usar la compresión RTF al configurar el cuerpo del mensaje MAPI:

```java
MapiMessage msg = new MapiMessage("from@doamin.com", "to@domain.com", "subject", "body");
// set the html body and keep it compressed
// this will reduce the message size
msg.setBodyContent(htmlBody, BodyContentType.Html, true);
```
## **Cree almacenamiento personal basado en SeekableByteChannel Stream**

Aspose.Email para Java permite trabajar con archivos de almacenamiento personal (PST) mediante java.nio.channels. Permite crear una instancia de PersonalStorage mediante una transmisión de SeekableByteChannel. En el siguiente fragmento de código, se muestra cómo crear una instancia de PersonalStorage basada en una transmisión de FileChannel, agregar una subcarpeta denominada «MessageFolder» a la carpeta raíz e importar mensajes desde los archivos del directorio «MessageFolder»:


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


## **Cambiar una clase de contenedor de carpetas**

A veces es necesario cambiar una clase de carpeta. Un ejemplo común es cuando se agregan mensajes de diferentes tipos (citas, mensajes, etc.) a la misma carpeta. En estos casos, es necesario cambiar la clase de carpeta para que todos los elementos de la carpeta se muestren correctamente. El siguiente fragmento de código muestra cómo cambiar la clase contenedora de una carpeta en PST para este fin.

```java
try (PersonalStorage pst = PersonalStorage.fromFile("PersonalStorage1.pst")) {
    FolderInfo folder = pst.getRootFolder().getSubFolder("Inbox");

    folder.changeContainerClass("IPF.Note");
}
```

## **Agregue mensajes masivos con un rendimiento mejorado**

Agregar mensajes individuales a un PST implica más operaciones de E/S en el disco y puede ralentizar el rendimiento. Para mejorar el rendimiento, los mensajes se pueden agregar al PST de forma masiva para minimizar las operaciones de E/S.
El [addMessages(Iterable<MapiMessage> messages)](https://reference.aspose.com/email/java/com.aspose.email/folderinfo/#addMessages-java.lang.Iterable-com.aspose.email.MapiMessage--) El método le permite agregar mensajes de forma masiva y se puede usar en los siguientes escenarios. Además, el [MessageAdded](https://reference.aspose.com/email/java/com.aspose.email/folderinfo/#MessageAdded) el evento se produce cuando se agrega un mensaje a la carpeta.

### **Agregar mensajes de otro PST**

Para agregar mensajes de otro PST, utilice la [FolderInfo.enumerateMapiMessages()](https://reference.aspose.com/email/java/com.aspose.email/folderinfo/#enumerateMapiMessages--) método que devuelve `Iterable<MapiMessage>`:

```java
try (PersonalStorage srcPst = PersonalStorage.fromFile("source.pst", false)) {
    try (PersonalStorage destPst = PersonalStorage.fromFile("destination.pst")) {

        // Get the folder by name
        FolderInfo srcFolder = srcPst.getRootFolder().getSubFolder("SomeFolder");
        FolderInfo destFolder = destPst.getRootFolder().getSubFolder("SomeFolder");

        destFolder.MessageAdded.add(new MessageAddedEventHandler() {
            // Handles the MessageAdded event.
            public void invoke(Object sender, MessageAddedEventArgs e) {
                System.out.println("Added: " + e.getEntryId());
            }
        });
        destFolder.addMessages(srcFolder.enumerateMapiMessages());
    }
}
```

### **Agregar mensajes desde el directorio**

Para agregar mensajes desde el directorio, cree el `getMessages(String pathToDir)` método que devuelve `Iterable<MapiMessage>`:

```java
// Read messages from directory.
static Iterable<MapiMessage> getMessages (String pathToDir)
{
    return Arrays.stream(listDirectory(pathToDir, "*.msg"))
            .map(MapiMessage::load).collect(Collectors.toList());
}

try ( PersonalStorage pst = PersonalStorage.fromFile("storage.pst")) {
    FolderInfo folder = pst.getRootFolder().getSubFolder("SomeFolder");
    folder.MessageAdded.add(new MessageAddedEventHandler() {
        // Handles the MessageAdded event.
        public void invoke(Object sender, MessageAddedEventArgs e) {
            System.out.println("Added: " + e.getEntryId());
        }
    });
    folder.addMessages(getMessages("MessageDirectory"));
}
```

