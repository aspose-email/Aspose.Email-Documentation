---
title: "Trabajando con Mensajes en un Archivo PST"
url: /es/java/working-with-messages-in-a-pst-file/
weight: 30
type: docs
---

## **Agregar Mensajes a Archivos PST**

[Crear un Nuevo Archivo PST y Agregar Subcarpetas](/email/java/create-new-pst-add-sub-folders-and-messages) mostró cómo crear un archivo PST y agregarle una subcarpeta. Con Aspose.Email, puedes agregar mensajes a las subcarpetas de un archivo PST que hayas creado o cargado. Este artículo agrega dos mensajes desde el disco a la subcarpeta Bandeja de entrada de un PST. Utiliza las clases [PersonalStorage](https://reference.aspose.com/email/java/com.aspose.email/personalstorage/) y [FolderInfo](https://reference.aspose.com/email/java/com.aspose.email/folderinfo/) para agregar mensajes a archivos PST. Para agregar mensajes a la carpeta Bandeja de entrada de un archivo PST:

1. Crea una instancia de la clase **FolderInfo** y cárgala con el contenido de la carpeta Bandeja de entrada.
1. Agrega mensajes desde el disco a la carpeta Bandeja de entrada llamando al método [FolderInfo.addMessage()](https://reference.aspose.com/email/java/com.aspose.email/folderinfo/#addMessage-com.aspose.email.MapiMessage-). La clase [FolderInfo](https://reference.aspose.com/email/java/com.aspose.email/folderinfo/) expone el método [addMessages](https://reference.aspose.com/email/java/com.aspose.email/folderinfo/#addMessages-java.lang.Iterable-com.aspose.email.MapiMessage--) que permite agregar una gran cantidad de mensajes a la carpeta, reduciendo las operaciones de E/S en disco y mejorando el rendimiento. Un ejemplo completo se encuentra a continuación, en [Agregando Mensajes en Masa](#adding-bulk-messages).

Los fragmentos de código a continuación muestran cómo agregar mensajes a una subcarpeta PST llamada Bandeja de entrada.

~~~Java
// Para ejemplos completos y archivos de datos, dirígete a https://github.com/aspose-email/Aspose.Email-for-Java

// Crear nuevo PST
PersonalStorage personalStorage = PersonalStorage.create(dataDir, FileFormatVersion.Unicode);

// Agregar nueva carpeta "Bandeja de entrada"
personalStorage.getRootFolder().addSubFolder("Bandeja de entrada");

// Seleccionar la carpeta "Bandeja de entrada"
FolderInfo inboxFolder = personalStorage.getRootFolder().getSubFolder("Bandeja de entrada");

// Agregar algunos mensajes a la carpeta "Bandeja de entrada"
inboxFolder.addMessage(MapiMessage.fromFile(dataDir + "MapiMsgWithPoll.msg"));
~~~

### **Agregando Mensajes en Masa**

Agregar mensajes individuales a un PST implica más operaciones de E/S en disco y, por lo tanto, puede ralentizar el rendimiento. Para mejorar el rendimiento, los mensajes pueden agregarse al PST en modo masivo para minimizar las operaciones de E/S. El método [addMessages(Iterable<MapiMessage> messages)](https://reference.aspose.com/email/java/com.aspose.email/folderinfo/#addMessages-java.lang.Iterable-com.aspose.email.MapiMessage--) permite definir un rango de mensajes que se agregarán al PST para mejorar el rendimiento y puede utilizarse en los siguientes escenarios. Además, el evento MessageAdded ocurre cuando se agrega un mensaje a la carpeta.

### **Cargando Mensajes desde Disco**

El siguiente fragmento de código te muestra cómo cargar mensajes desde el disco.

~~~Java
// Para ejemplos completos y archivos de datos, dirígete a https://github.com/aspose-email/Aspose.Email-for-Java
private static void addMessagesInBulkMode(String fileName, String msgFolderName) {
    try (PersonalStorage personalStorage = PersonalStorage.fromFile(fileName)) {
        FolderInfo folder = personalStorage.getRootFolder().getSubFolder("miBandejaDeEntrada");
        folder.MessageAdded.add(new MessageAddedEventHandler() {
            public void invoke(Object sender, MessageAddedEventArgs e) {
                onMessageAdded(sender, e);
            }
        });
        folder.addMessages(new MapiMessageCollection(msgFolderName));
    }
}

static void onMessageAdded(Object sender, MessageAddedEventArgs e) {
    System.out.println(e.getEntryId());
    System.out.println(e.getMessage().getSubject());
}
~~~

### **Implementación Iterable**

El siguiente fragmento de código muestra cómo crear una implementación Iterable.

~~~Java
// Para ejemplos completos y archivos de datos, dirígete a https://github.com/aspose-email/Aspose.Email-for-Java
public class MapiMessageCollection implements Iterable<MapiMessage> {

    private final File folder;

    public MapiMessageCollection(String folder) {
        this.folder = new File(folder);
    }

    public Iterator<MapiMessage> iterator() {
        return new MapiMessageIterator(folder.listFiles());
    }
}

public class MapiMessageIterator implements Iterator<MapiMessage> {

    private Queue<String> queue = new LinkedList<String>();

    public MapiMessageIterator(File[] listOfFiles) {
        for (File file : listOfFiles) {
            queue.offer(file.getAbsolutePath());
        }
    }

    public boolean hasNext() {
        return !queue.isEmpty();
    }

    public MapiMessage next() {
        return MapiMessage.fromFile(queue.poll());
    }
}
~~~

### **Agregando Mensajes desde Otro PST**

Para agregar mensajes desde otro PST, utiliza el método [FolderInfo.enumerateMapiMessages()](https://reference.aspose.com/email/java/com.aspose.email/folderinfo/#enumerateMapiMessages--) que devuelve Iterable<MapiMessage>. El siguiente fragmento de código te muestra cómo agregar mensajes desde otro PST.

~~~Java
// Para ejemplos completos y archivos de datos, dirígete a https://github.com/aspose-email/Aspose.Email-for-Java
private static void bulkAddFromAnotherPst(String source) {
    // La ruta al directorio de archivos.
    String dataDir = "data/";

    try (PersonalStorage pst = PersonalStorage.fromFile(source, false)) {
        try (PersonalStorage pstDest = PersonalStorage.fromFile(dataDir + "PersonalStorageFile1.pst")) {
            // Obtener la carpeta por nombre
            FolderInfo folderInfo = pst.getRootFolder().getSubFolder("Contactos");
            MessageInfoCollection ms = folderInfo.getContents();

            // Obtener la carpeta por nombre
            FolderInfo f = pstDest.getRootFolder().getSubFolder("miBandejaDeEntrada");
            f.MessageAdded.add(new MessageAddedEventHandler() {
                public void invoke(Object sender, MessageAddedEventArgs e) {
                    onMessageAdded(sender, e);
                }
            });
            f.addMessages(folderInfo.enumerateMapiMessages());
            FolderInfo fi = pstDest.getRootFolder().getSubFolder("miBandejaDeEntrada");
            MessageInfoCollection msgs = fi.getContents();
        }
    }
}

// Maneja el evento MessageAdded.
static void onMessageAdded(Object sender, MessageAddedEventArgs e) {
    System.out.println(e.getEntryId());
    System.out.println(e.getMessage().getSubject());
}
~~~

## **Obtener Información de Mensajes de un Archivo PST de Outlook**

En [Leer Archivo PST de Outlook y Obtener Información de Carpetas y Subcarpetas](/email/java/read-outlook-pst-file-and-get-folders-and-subfolders-information/), discutimos la carga de un archivo PST de Outlook y la navegación por sus carpetas para obtener los nombres de las carpetas y el número de mensajes en ellas. Este artículo explica cómo leer todas las carpetas y subcarpetas en el archivo PST y mostrar la información sobre los mensajes, por ejemplo, asunto, remitente y destinatarios. El método [FolderInfo.getContents()](https://reference.aspose.com/email/java/com.aspose.email/folderinfo/#getContents--) se utiliza para mostrar [información breve sobre mensajes](https://reference.aspose.com/email/java/com.aspose.email/folderinfo/#enumerateMapiMessages--) como asunto, remitente, destinatarios.
En términos de rendimiento, esta es la opción más adecuada para obtener información primaria sobre los mensajes. Para [extraer](#extracting-messages-form-pst-files) los datos completos del mensaje, se proporciona el método [PersonalStorage.extractMessage()](https://reference.aspose.com/email/java/com.aspose.email/personalstorage/#extractMessage-com.aspose.email.MessageInfo-).
El archivo PST de Outlook puede contener carpetas anidadas. Para obtener información de los mensajes de estas, así como de las carpetas de nivel superior, utiliza un método recursivo para leer todas las carpetas. El siguiente fragmento de código te muestra cómo leer un archivo PST de Outlook y mostrar el contenido de las carpetas y los mensajes de manera recursiva.

~~~Java
// Para ejemplos completos y archivos de datos, dirígete a https://github.com/aspose-email/Aspose.Email-for-Java
public static void run() {
    // La ruta al directorio de archivos.
    String dataDir = "data/";

    // Cargar el archivo de Outlook
    String path = dataDir + "PersonalStorage.pst";

    try {

        // Cargar el archivo PST de Outlook
        PersonalStorage personalStorage = PersonalStorage.fromFile(path);

        // Obtener el formato de visualización del archivo PST
        System.out.println("Formato de visualización: " + personalStorage.getFormat());

        // Obtener la información de carpetas y mensajes
        FolderInfo folderInfo = personalStorage.getRootFolder();

        // Llamar al método recursivo para mostrar el contenido de las carpetas
        displayFolderContents(folderInfo, personalStorage);
    } catch (Exception ex) {
        System.out.println(ex.getMessage());
    }
}

// Este es un método recursivo para mostrar el contenido de una carpeta
private static void displayFolderContents(FolderInfo folderInfo, PersonalStorage pst) {
    // Mostrar el nombre de la carpeta
    System.out.println("Carpeta: " + folderInfo.getDisplayName());
    System.out.println("==================================");
    // Mostrar información sobre los mensajes dentro de esta carpeta
    MessageInfoCollection messageInfoCollection = folderInfo.getContents();
    for (MessageInfo messageInfo : messageInfoCollection) {
        System.out.println("Asunto: " + messageInfo.getSubject());
        System.out.println("Remitente: " + messageInfo.getSenderRepresentativeName());
        System.out.println("Destinatarios: " + messageInfo.getDisplayTo());
        System.out.println("------------------------------");
    }

    // Llamar a este método recursivamente para cada subcarpeta
    if (folderInfo.hasSubFolders() == true) {
        for (FolderInfo subfolderInfo : folderInfo.getSubFolders()) {
            displayFolderContents(subfolderInfo, pst);
        }
    }
}
~~~

## **Extrayendo Mensajes de Archivos PST**

Este artículo muestra cómo leer archivos PST de Microsoft Outlook y [extraer mensajes](#extracting-messages-form-pst-files). Los mensajes se guardan en disco en formato MSG. El artículo también muestra cómo [extraer un número específico de mensajes](#extracting-n-number-of-messages-from-a-pst-file) de un archivo PST. Utiliza un método recursivo para navegar por todas las carpetas (incluidas las carpetas anidadas) y llama al método [PersonalStorage.extractMessage()](https://reference.aspose.com/email/java/com.aspose.email/personalstorage/#extractMessage-com.aspose.email.MessageInfo-) para obtener los mensajes de Outlook en una instancia de la clase [MapiMessage](https://reference.aspose.com/email/java/com.aspose.email/mapimessage/). Después de eso, llama al método [MapiMessage.save()](https://reference.aspose.com/email/java/com.aspose.email/mapimessage/#save-java.lang.String-) para guardar el mensaje en disco o en un flujo en formato MSG. El siguiente fragmento de código te muestra cómo extraer mensajes de un archivo PST.

~~~Java
// Para ejemplos completos y archivos de datos, dirígete a https://github.com/aspose-email/Aspose.Email-for-Java
public static void run() {
    // La ruta al directorio de archivos.
    String dataDir = "data/";

    // Cargar el archivo de Outlook
    String path = dataDir + "PersonalStorage.pst";

    try {
        // cargar el archivo PST de Outlook
        PersonalStorage pst = PersonalStorage.fromFile(path);

        // obtener el formato de visualización del archivo PST
        System.out.println("Formato de visualización: " + pst.getFormat());

        // obtener la información de carpetas y mensajes
        FolderInfo folderInfo = pst.getRootFolder();

        // Llamar al método recursivo para extraer archivos msg de cada carpeta
        extractMsgFiles(folderInfo, pst);
    } catch (Exception ex) {
        System.out.println(ex.getMessage());
    }
}

// Este es un método recursivo para mostrar el contenido de una carpeta
private static void extractMsgFiles(FolderInfo folderInfo, PersonalStorage pst) {
    // mostrar el nombre de la carpeta
    System.out.println("Carpeta: " + folderInfo.getDisplayName());
    System.out.println("==================================");
    // loop a través de todos los mensajes en esta carpeta
    MessageInfoCollection messageInfoCollection = folderInfo.getContents();
    for (MessageInfo messageInfo : messageInfoCollection) {
        System.out.println("Guardando mensaje {0} ...." + messageInfo.getSubject());
        // obtener el mensaje en una instancia de MapiMessage
        MapiMessage message = pst.extractMessage(messageInfo);
        // guardar este mensaje en disco en formato msg
        message.save(message.getSubject().replace(":", " ") + ".msg");
        // guardar este mensaje en flujo en formato msg
        ByteArrayOutputStream messageStream = new ByteArrayOutputStream();
        message.save(messageStream);
    }

    // Llamar a este método recursivamente para cada subcarpeta
    if (folderInfo.hasSubFolders() == true) {
        for (FolderInfo subfolderInfo : folderInfo.getSubFolders()) {
            extractMsgFiles(subfolderInfo, pst);
        }
    }
}
~~~

### **Guardar Mensajes Directamente de PST a Flujo**

Para guardar mensajes de un archivo PST directamente en flujo, sin extraer el MsgInfo para los mensajes, utiliza el método [saveMessageToStream()](https://reference.aspose.com/email/java/com.aspose.email/personalstorage/#saveMessageToStream-java.lang.String-java.io.OutputStream-). El siguiente fragmento de código te muestra cómo guardar mensajes directamente de PST a flujo.

~~~Java
// Para ejemplos completos y archivos de datos, dirígete a https://github.com/aspose-email/Aspose.Email-for-Java
// La ruta al directorio de archivos.
String dataDir = "data/";

// Cargar el archivo de Outlook
String path = dataDir + "PersonalStorage.pst";

// Guardar mensaje en MemoryStream
try (PersonalStorage personalStorage = PersonalStorage.fromFile(path)) {
    FolderInfo inbox = personalStorage.getRootFolder().getSubFolder("Bandeja de entrada");
    for (MessageInfo messageInfo : inbox.enumerateMessages()) {
        try (ByteArrayOutputStream memeorystream = new ByteArrayOutputStream()) {
            personalStorage.saveMessageToStream(messageInfo.getEntryIdString(), memeorystream);
        }
    }
}

// Guardar mensaje en archivo
try (PersonalStorage pst = PersonalStorage.fromFile(path)) {
    FolderInfo inbox = pst.getRootFolder().getSubFolder("Bandeja de entrada");
    for (MessageInfo messageInfo : inbox.enumerateMessages()) {
        try (FileOutputStream fs = new FileOutputStream(new File(dataDir + messageInfo.getSubject() + ".msg"))) {
            pst.saveMessageToStream(messageInfo.getEntryIdString(), fs);
        }
    }
}

try (PersonalStorage pst = PersonalStorage.fromFile(path)) {
    FolderInfo inbox = pst.getRootFolder().getSubFolder("Bandeja de entrada");

    // Para enumerar el entryId de los mensajes, puedes usar el método FolderInfo.EnumerateMessagesEntryId():
    for (String entryId : inbox.enumerateMessagesEntryId()) {
        try (ByteArrayOutputStream ms = new ByteArrayOutputStream()) {
            pst.saveMessageToStream(entryId, ms);
        }
    }
}
~~~ 

### **Extrayendo n Número de Mensajes de un Archivo PST**

El siguiente fragmento de código te muestra cómo extraer un número dado de mensajes de un PST. Simplemente proporciona el índice del primer mensaje y el número total de mensajes a extraer.

~~~Java
// Para ejemplos completos y archivos de datos, dirígete a https://github.com/aspose-email/Aspose.Email-for-Java
FolderInfo inbox = personalStorage.getRootFolder().getSubFolder("Bandeja de entrada");

// Extrae mensajes comenzando desde el índice 10 y extrae un total de 100 mensajes
MessageInfoCollection messages = inbox.getContents(10, 100);
~~~

### **Obtener el Total de Elementos de un Archivo PST**

Aspose.Email proporciona el método [GetTotalItemsCount()](https://reference.aspose.com/email/java/com.aspose.email/messagestore/#getTotalItemsCount--) de la propiedad [PersonalStorage.Store](https://reference.aspose.com/email/java/com.aspose.email/personalstorage/#getStore--). Devuelve el número total de elementos de mensajes contenidos en el PST.

El siguiente ejemplo de código muestra cómo recuperar el recuento total de elementos (mensajes, citas, contactos, etc.) almacenados dentro del archivo PST:

```java
try (PersonalStorage pst = PersonalStorage.fromFile("my.pst", false)) {
    int count = pst.getStore().getTotalItemsCount();
}
```

## **Eliminar Elementos de Archivos PST**

[Agregar Mensajes a Archivos PST](#adding-messages-to-pst-files) mostró cómo agregar mensajes a archivos PST. Por supuesto, también es posible eliminar elementos (contenidos) de un archivo PST y también puede ser deseable eliminar mensajes en masa. Se pueden eliminar elementos de un archivo PST utilizando el método [FolderInfo.deleteChildItem()](https://reference.aspose.com/email/java/com.aspose.email/folderinfo/#deleteChildItem-byte---). La API también proporciona el método [FolderInfo.deleteChildItems()](https://reference.aspose.com/email/java/com.aspose.email/folderinfo/#deleteChildItems-java.lang.Iterable-java.lang.String--) para eliminar elementos en masa del archivo PST.

### **Eliminando Mensajes de Archivos PST**

Este artículo muestra cómo usar la clase [FolderInfo](https://reference.aspose.com/email/java/com.aspose.email/folderinfo/) para acceder a carpetas específicas en un archivo PST. Para eliminar mensajes de la subcarpeta Enviados de un archivo PST que se ha cargado o creado anteriormente:

1. Crea una instancia de la clase [FolderInfo](https://reference.aspose.com/email/java/com.aspose.email/folderinfo/) y cárgala con el contenido de la subcarpeta Enviados.
2. Elimina mensajes de la carpeta Enviados llamando al método [FolderInfo.deleteChildItem()](https://reference.aspose.com/email/java/com.aspose.email/folderinfo/#deleteChildItem-byte---) y pasando el [MessageInfo.EntryId](https://reference.aspose.com/email/java/com.aspose.email/messageinfo/#getEntryId--) como parámetro. El siguiente fragmento de código muestra cómo eliminar mensajes de la subcarpeta Enviados de un archivo PST.

~~~Java
// Para ejemplos completos y archivos de datos, dirígete a https://github.com/aspose-email/Aspose.Email-for-Java
// La ruta al directorio de archivos.
String dataDir = "data/" + "Sub.pst";

// Cargar el archivo PST de Outlook
PersonalStorage personalStorage = PersonalStorage.fromFile(dataDir);

// Obtener la carpeta de elementos enviados
FolderInfo folderInfo = personalStorage.getPredefinedFolder(StandardIpmFolder.SentItems);

MessageInfoCollection msgInfoColl = folderInfo.getContents();
for (MessageInfo msgInfo : msgInfoColl) {
    System.out.println(msgInfo.getSubject() + ": " + msgInfo.getEntryIdString());
    if (msgInfo.getSubject().equals("alguna condición de eliminación")) {
        // Eliminar este elemento
        folderInfo.deleteChildItem(msgInfo.getEntryId());
        System.out.println("Mensaje eliminado");
    }
}
~~~

### **Eliminando Carpetas de Archivos PST**

Puedes eliminar una carpeta PST moviéndola a la carpeta de Elementos eliminados.

~~~Java
try (PersonalStorage pst = PersonalStorage.fromFile("test.pst")) {
    FolderInfo deletedItemsFolder = pst.getPredefinedFolder(StandardIpmFolder.DeletedItems);
    FolderInfo emptyFolder = pst.getRootFolder().getSubFolder("Carpeta vacía");
    FolderInfo someFolder = pst.getRootFolder().getSubFolder("Alguna carpeta");
    pst.moveItem(emptyFolder, deletedItemsFolder);
    pst.moveItem(someFolder, deletedItemsFolder);
}
~~~ 
La ventaja de este método es que la carpeta eliminada puede recuperarse fácilmente.

~~~Java
FolderInfo someFolder = deletedItemsFolder.getSubFolder("Alguna carpeta");
pst.moveItem(someFolder, pst.getRootFolder());
~~~ 
También puedes eliminar permanentemente una carpeta de la carpeta de Elementos eliminados, si es necesario.

~~~Java
deletedItemsFolder.deleteChildItem(emptyFolder.getEntryId());
~~~ 
El método [deleteChildItem()](https://apireference.aspose.com/email/java/com.aspose.email/FolderInfo#deleteChildItem\(byte[]\)) se puede utilizar para cualquier carpeta si deseas eliminar de inmediato y permanentemente la subcarpeta, eludiendo la carpeta de Elementos eliminados.

~~~Java
FolderInfo someFolder = pst.getRootFolder().getSubFolder("Alguna carpeta");
pst.getRootFolder().deleteChildItem(someFolder.getEntryId());
~~~ 

### **Eliminar Elementos en Masa de un Archivo PST**

La API de Aspose.Email se puede utilizar para eliminar elementos en masa de un archivo PST. Esto se logra utilizando el método [deleteChildItems()](https://reference.aspose.com/email/java/com.aspose.email/folderinfo/#deleteChildItems-java.lang.Iterable-java.lang.String--) que acepta una lista de elementos de ID de entrada que hacen referencia a los elementos a eliminar. El siguiente fragmento de código muestra cómo eliminar elementos en masa de un archivo PST.

~~~Java
// Para ejemplos completos y archivos de datos, dirígete a https://github.com/aspose-email/Aspose.Email-for-Java
// La ruta al directorio de archivos.
String dataDir = "data/" + "Sub.pst";

try (PersonalStorage personalStorage = PersonalStorage.fromFile(dataDir)) {
    // Obtener la subcarpeta Bandeja de entrada del archivo de Outlook
    FolderInfo inbox = personalStorage.getRootFolder().getSubFolder("Bandeja de entrada");

    // Crear una instancia de PersonalStorageQueryBuilder
    PersonalStorageQueryBuilder queryBuilder = new PersonalStorageQueryBuilder();

    queryBuilder.getFrom().contains("someuser@domain.com");
    MessageInfoCollection messages = inbox.getContents(queryBuilder.getQuery());
    List<String> deleteList = new ArrayList<String>();
    for (MessageInfo messageInfo : messages) {
        deleteList.add(messageInfo.getEntryIdString());
    }

    // eliminar mensajes cuyo Remitente = "someuser@domain.com"
    inbox.deleteChildItems(deleteList);
}
~~~ 

## **Buscar Mensajes y Carpetas en un PST por Criterio**

Los archivos de Almacenamiento Personal (PST) pueden contener una gran cantidad de datos y buscar información que cumpla con un criterio específico en archivos tan grandes requiere incluir múltiples puntos de control en el código para filtrar la información. Con la clase [PersonalStorageQueryBuilder](https://reference.aspose.com/email/java/com.aspose.email/personalstoragequerybuilder/), Aspose.Email hace posible buscar registros específicos en un PST en base a un criterio de búsqueda especificado. Se puede buscar en un PST mensajes basados en parámetros de búsqueda como remitente, receptor, asunto, importancia del mensaje, presencia de archivos adjuntos, tamaño del mensaje e incluso ID del mensaje. La [PersonalStorageQueryBuilder](https://reference.aspose.com/email/java/com.aspose.email/personalstoragequerybuilder/) también se puede utilizar para buscar subcarpetas.

### **Buscando Mensajes y Carpetas en PST**

El siguiente fragmento de código muestra cómo utilizar la clase [PersonalStorageQueryBuilder](https://reference.aspose.com/email/java/com.aspose.email/personalstoragequerybuilder/) para buscar contenidos en un PST basándose en diferentes criterios de búsqueda. Por ejemplo, muestra la búsqueda en un PST basándose en:

- Importancia del mensaje.
- Clase del mensaje.
- Presencia de archivos adjuntos.
- Tamaño del mensaje.
- Fecha del mensaje.
- Mensajes no leídos.
- Mensajes no leídos con archivos adjuntos, y
- carpetas con un nombre de subcarpeta específico.

~~~Java
// Para ejemplos completos y archivos de datos, dirígete a https://github.com/aspose-email/Aspose.Email-for-Java
// La ruta al directorio de archivos.
String dataDir = "data/";

try (PersonalStorage personalStorage = PersonalStorage.fromFile(dataDir + "Outlook.pst")) {
    FolderInfo folder = personalStorage.getRootFolder().getSubFolder("Bandeja de entrada");
    PersonalStorageQueryBuilder builder = new PersonalStorageQueryBuilder();

    // Mensajes de alta importancia
    builder.getImportance().equals((int) MapiImportance.High);
    MessageInfoCollection messages = folder.getContents(builder.getQuery());
    System.out.println("Mensajes con alta importancia: " + messages.size());

    builder = new PersonalStorageQueryBuilder();
    builder.getMessageClass().equals("IPM.Note");
    messages = folder.getContents(builder.getQuery());
    System.out.println("Mensajes con IPM.Note: " + messages.size());

    builder = new PersonalStorageQueryBuilder();
    // Mensajes con archivos adjuntos Y alta importancia
    builder.getImportance().equals((int) MapiImportance.High);
    builder.hasFlags(MapiMessageFlags.MSGFLAG_HASATTACH);
    messages = folder.getContents(builder.getQuery());
    System.out.println("Mensajes con archivos adjuntos: " + messages.size());

    builder = new PersonalStorageQueryBuilder();
    // Mensajes con tamaño > 15 KB
    builder.getMessageSize().greater(15000);
    messages = folder.getContents(builder.getQuery());
    System.out.println("Mensajes de tamaño > 15Kb: " + messages.size());

    java.util.Calendar c = java.util.Calendar.getInstance();

    builder = new PersonalStorageQueryBuilder();
    // Mensajes por la fecha actual
    // (Ten en cuenta que las consultas por fecha no son compatibles con los elementos del calendario en la carpeta Citas)
    builder.getSentDate().on(c.getTime(), DateComparisonType.ByDate);
    messages = folder.getContents(builder.getQuery());
    System.out.println("Mensajes por la fecha actual: " + messages.size());

    builder = new PersonalStorageQueryBuilder();
    // Mensajes entre fechas
    // (Ten en cuenta que las consultas por fecha no son compatibles con los elementos del calendario en la carpeta Citas)
    c.set(2020,  0, 1, 0, 0, 0);
    builder.getSentDate().since(c.getTime());
    c.set(2021,  0, 1, 0, 0, 0);
    builder.getSentDate().before(c.getTime());
    messages = folder.getContents(builder.getQuery());
    System.out.println("Mensajes entre fechas: " + messages.size());

    builder = new PersonalStorageQueryBuilder();
    // Mensajes no leídos
    builder.hasNoFlags(MapiMessageFlags.MSGFLAG_READ);
    messages = folder.getContents(builder.getQuery());
    System.out.println("No leídos: " + messages.size());

    builder = new PersonalStorageQueryBuilder();
    // Mensajes no leídos con archivos adjuntos
    builder.hasNoFlags(MapiMessageFlags.MSGFLAG_READ);
    builder.hasFlags(MapiMessageFlags.MSGFLAG_HASATTACH);
    messages = folder.getContents(builder.getQuery());
    System.out.println("Mensajes no leídos con archivos adjuntos: " + messages.size());

    // Carpeta con nombre 'SubBandejaDeEntrada'
    builder = new PersonalStorageQueryBuilder();
    builder.getFolderName().equals("SubBandejaDeEntrada");
    FolderInfoCollection folders = folder.getSubFolders(builder.getQuery());
    System.out.println("Carpeta con subcarpeta: " + folders.size());

    builder = new PersonalStorageQueryBuilder();
    // Carpetas con subcarpetas
    builder.hasSubfolders();
    folders = folder.getSubFolders(builder.getQuery());
    System.out.println(folders.size());
}
~~~ 

### **Buscar una Cadena en PST con el Parámetro Ignorar Mayúsculas**

El siguiente fragmento de código te muestra cómo buscar una cadena en un PST con el parámetro ignorar mayúsculas.

~~~Java
// Para ejemplos completos y archivos de datos, dirígete a https://github.com/aspose-email/Aspose.Email-for-Java
// La ruta al directorio de archivos.
String dataDir = "data/";

try (PersonalStorage personalStorage = PersonalStorage.create(dataDir + "CaseSensitivity.pst", FileFormatVersion.Unicode)) {
    FolderInfo folderinfo = personalStorage.createPredefinedFolder("Bandeja de entrada", StandardIpmFolder.Inbox);
    folderinfo.addMessage(MapiMessage.fromMailMessage(MailMessage.load("Sample.eml")));
    PersonalStorageQueryBuilder builder = new PersonalStorageQueryBuilder();
    // IgnoreCase es verdadero
    builder.getFrom().contains("automated", true);
    MailQuery query = builder.getQuery();
    MessageInfoCollection coll = folderinfo.getContents(query);
    System.out.println(coll.size());
}
~~~ 

### **Buscar Asuntos de Mensajes por Múltiples Palabras Clave en un Archivo PST**

Puedes utilizar el método [MailQueryBuilder.or](https://apireference.aspose.com/email/java/com.aspose.email/MailQueryBuilder#or\(com.aspose.email.MailQuery,%20com.aspose.email.MailQuery\)) para encontrar mensajes con un asunto que contenga al menos una de las palabras especificadas como se muestra a continuación:

~~~java
PersonalStorageQueryBuilder builder1 = new PersonalStorageQueryBuilder();
builder1.getSubject().contains("Revisión"); // 'Revisión' es la palabra clave para la búsqueda

PersonalStorageQueryBuilder builder2 = new PersonalStorageQueryBuilder();
builder2.getSubject().contains("Error"); // 'Error' también es la palabra clave para la búsqueda

PersonalStorageQueryBuilder queryBuilder = new PersonalStorageQueryBuilder();
queryBuilder.or(builder1.getQuery(), builder2.getQuery()); // los asuntos de los mensajes deben contener las palabras 'Revisión' o 'Error'

try (PersonalStorage storage = PersonalStorage.fromFile("example.pst"))
{
    FolderInfo folderInfo = storage.getRootFolder().getSubFolder("Bandeja de entrada");
    MessageInfoCollection messageInfos = folderInfo.getContents(queryBuilder.getQuery());

    for (MessageInfo messageInfo : messageInfos)
    {
        System.out.println(messageInfo.getSubject());
    }
}
~~~ 

## **Mover Elementos a Otras Carpetas del Archivo PST**

Aspose.Email permite mover elementos de una carpeta de origen a otra carpeta en el mismo archivo de Almacenamiento Personal (PST). Esto incluye:

- Mover una carpeta específica a una nueva carpeta principal.
- Mover un mensaje específico a una nueva carpeta.
- Mover el contenido a una nueva carpeta.
- Mover subcarpetas a una nueva carpeta principal.

El siguiente fragmento de código muestra cómo mover elementos como mensajes y carpetas de una carpeta de origen a otra carpeta en el mismo archivo PST.

~~~Java
// Para ejemplos completos y archivos de datos, dirígete a https://github.com/aspose-email/Aspose.Email-for-Java
try (PersonalStorage personalStorage = PersonalStorage.fromFile("test.pst")) {
    FolderInfo inbox = personalStorage.getPredefinedFolder(StandardIpmFolder.Inbox);
    FolderInfo deleted = personalStorage.getPredefinedFolder(StandardIpmFolder.DeletedItems);
    FolderInfo subfolder = inbox.getSubFolder("Subcarpeta");

    // Mover carpeta y mensaje a Elementos eliminados
    personalStorage.moveItem(subfolder, deleted);
    MessageInfoCollection contents = subfolder.getContents();
    personalStorage.moveItem(contents.get(0), deleted);

    // Mover todas las subcarpetas de bandeja de entrada y contenidos de subcarpeta a Elementos eliminados
    inbox.moveSubfolders(deleted);
    subfolder.moveContents(deleted);
}
~~~ 

## **Actualizar Propiedades de Mensajes en un Archivo PST**

A veces es necesario actualizar ciertas propiedades de los mensajes, como cambiar el asunto, marcar la importancia del mensaje y otras similares. Actualizar un mensaje en un archivo PST, con dichos cambios en las propiedades del mensaje, se puede lograr utilizando el método [FolderInfo.changeMessages](https://reference.aspose.com/email/java/com.aspose.email/folderinfo/#changeMessages-com.aspose.email.MapiPropertyCollection-). Este artículo muestra cómo actualizar mensajes en masa en un archivo PST para cambios en las propiedades. El siguiente fragmento de código muestra cómo actualizar propiedades de mensajes en modo masivo para múltiples mensajes en un archivo PST.

~~~Java
// Para ejemplos completos y archivos de datos, dirígete a https://github.com/aspose-email/Aspose.Email-for-Java
// La ruta al directorio de archivos.
String dataDir = "data/" + "Sub.pst";

// Cargar el archivo PST de Outlook
PersonalStorage personalStorage = PersonalStorage.fromFile(dataDir);

// Obtener la subcarpeta requerida
FolderInfo inbox = personalStorage.getRootFolder().getSubFolder("Bandeja de entrada");

// encontrar mensajes cuyo Remitente = "someuser@domain.com"
PersonalStorageQueryBuilder queryBuilder = new PersonalStorageQueryBuilder();
queryBuilder.getFrom().contains("someuser@domain.com");

// Obtener Contenidos desde la Consulta
MessageInfoCollection messages = inbox.getContents(queryBuilder.getQuery());

// Guardar (MessageInfo,EntryIdString) en la Lista
List<String> changeList = new ArrayList<String>();
for (MessageInfo messageInfo : messages) {
    changeList.add(messageInfo.getEntryIdString());
}

// Componer las nuevas propiedades
MapiPropertyCollection updatedProperties = new MapiPropertyCollection();
updatedProperties.add(MapiPropertyTag.PR_SUBJECT_W, new MapiProperty(MapiPropertyTag.PR_SUBJECT_W, "Nuevo Asunto".getBytes(Charset.forName("utf-16le"))));
updatedProperties.add(MapiPropertyTag.PR_IMPORTANCE, new MapiProperty(MapiPropertyTag.PR_IMPORTANCE, BitConverter.getBytesInt64(2)));

// actualizar mensajes cuyo Remitente = "someuser@domain.com" con nuevas propiedades
inbox.changeMessages(changeList, updatedProperties);
~~~

## **Actualizar Propiedades Personalizadas en un Archivo PST**

A veces es necesario marcar elementos que han sido procesados dentro del archivo PST. La API de Aspose.Email permite lograr esto utilizando MapiProperty y MapiNamedProperty. Los siguientes métodos son útiles para conseguir esto.

- `constructor MapiNamedProperty(long propertyTag, String nameIdentifier, UUID propertyGuid, byte[] propertyValue)`
- `constructor MapiNamedProperty(long propertyTag, long nameIdentifier, UUID propertyGuid, byte[] propertyValue)`
- `FolderInfo.changeMessages(MapiPropertyCollection updatedProperties)` - cambia todos los mensajes en la carpeta
- `PersonalStorage.changeMessage(String entryId, MapiPropertyCollection updatedProperties)` - cambia las propiedades del mensaje

~~~Java
// Para ejemplos completos y archivos de datos, dirígete a https://github.com/aspose-email/Aspose.Email-for-Java
public static void run() {
    // La ruta al directorio de archivos.
    String dataDir = "data/" + "Sub.pst";

    try (PersonalStorage personalStorage = PersonalStorage.fromFile(dataDir)) {
        FolderInfo testFolder = personalStorage.getRootFolder().getSubFolder("Bandeja de entrada");

        // Crear la colección de propiedades del mensaje para agregar o actualizar
        MapiPropertyCollection newProperties = new MapiPropertyCollection();

        // Propiedad nombrada Normal, Custom y PidLidLogFlags
        MapiProperty property = new MapiProperty(MapiPropertyTag.PR_ORG_EMAIL_ADDR_W, "test_address@org.com".getBytes(Charset.forName("utf-16le")));
        MapiProperty namedProperty1 = new MapiNamedProperty(generateNamedPropertyTag(0L, MapiPropertyType.PT_LONG), "ITEM_ID", UUID.randomUUID(),
                BitConverter.getBytesInt64(123));
        MapiProperty namedProperty2 = new MapiNamedProperty(generateNamedPropertyTag(1L, MapiPropertyType.PT_LONG), 0x0000870C,
                UUID.fromString("0006200A-0000-0000-C000-000000000046"), BitConverter.getBytesInt64(0));
        newProperties.add(namedProperty1.getTag(), namedProperty1);
        newProperties.add(namedProperty2.getTag(), namedProperty2);
        newProperties.add(property.getTag(), property);
        testFolder.changeMessages(testFolder.enumerateMessagesEntryId(), newProperties);
    }
}

private static long generateNamedPropertyTag(long index, int dataType) {
    return (((0x8000 | index) << 16) | (long) dataType) & 0x00000000FFFFFFFFL;
}
~~~ 

## **Extraer Archivos Adjuntos Sin Extraer el Mensaje Completo**

La API de Aspose.Email se puede utilizar para extraer archivos adjuntos de los mensajes PST sin extraer primero el mensaje completo. El método [ExtractAttachments](https://reference.aspose.com/email/java/com.aspose.email/personalstorage/#extractAttachments-com.aspose.email.MessageInfo-) de [PersonalStorage](https://reference.aspose.com/email/java/com.aspose.email/personalstorage/) puede ser utilizado para hacer esto. El siguiente fragmento de código muestra cómo extraer archivos adjuntos sin extraer el mensaje completo.

~~~Java
// Para ejemplos completos y archivos de datos, dirígete a https://github.com/aspose-email/Aspose.Email-for-Java
// La ruta al directorio de archivos.
String dataDir = "data/";

try (PersonalStorage personalstorage = PersonalStorage.fromFile(dataDir + "Outlook.pst")) {
    FolderInfo folder = personalstorage.getRootFolder().getSubFolder("Bandeja de entrada");

    for (String messageInfo : folder.enumerateMessagesEntryId()) {
        MapiAttachmentCollection attachments = personalstorage.extractAttachments(messageInfo);

        if (attachments.size() != 0) {
            for (MapiAttachment attachment : attachments) {
                if (attachment.getLongFileName() != null && !attachment.getLongFileName().isEmpty()) {
                    if (attachment.getLongFileName().contains(".msg")) {
                        continue;
                    } else {
                        attachment.save(dataDir + "Adjuntos/" + attachment.getLongFileName());
                    }
                }
            }
        }
    }
}
~~~ 

## **Agregar Archivos a PST**

La funcionalidad clave de Microsoft Outlook es gestionar correos electrónicos, calendarios, tareas, contactos y entradas de diario. Además, también se pueden agregar archivos a una carpeta PST y el PST resultante registra los documentos agregados. Aspose.Email proporciona la facilidad de agregar archivos a una carpeta de la misma manera además de agregar mensajes, contactos, tareas y entradas de diario a PST. El siguiente fragmento de código muestra cómo agregar documentos a una carpeta PST usando Aspose.Email.

~~~Java
// Para ejemplos completos y archivos de datos, dirígete a https://github.com/aspose-email/Aspose.Email-for-Java
// La ruta al directorio de archivos.
String dataDir = "data/";

try (PersonalStorage personalStorage = PersonalStorage.create(dataDir + "Ps1_out.pst", FileFormatVersion.Unicode)) {
    FolderInfo folder = personalStorage.getRootFolder().addSubFolder("Archivos");

    // Agregar el archivo Document.doc con la clase de mensaje "IPM.Document" de forma predeterminada.
    folder.addFile(dataDir + "attachment_1.doc", null);
}
~~~