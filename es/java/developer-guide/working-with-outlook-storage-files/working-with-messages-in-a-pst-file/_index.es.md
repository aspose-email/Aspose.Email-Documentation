---
title: "Trabajar con mensajes en un archivo PST"
url: /es/java/working-with-messages-in-a-pst-file/
weight: 30
type: docs
---


## **Agregar mensajes a archivos PST**

[Crear un nuevo archivo PST y agregar subcarpetas](/email/java/create-new-pst-add-sub-folders-and-messages) mostró cómo crear un archivo PST y agregarle una subcarpeta. Con Aspose.Email puedes añadir mensajes a las subcarpetas de un archivo PST que hayas creado o cargado. Este artículo agrega dos mensajes del disco a la subcarpeta Bandeja de entrada de un PST. Utilice el [PersonalStorage](https://reference.aspose.com/email/java/com.aspose.email/personalstorage/) and [FolderInfo](https://reference.aspose.com/email/java/com.aspose.email/folderinfo/) clases para añadir mensajes a archivos PST. Para añadir mensajes a la carpeta Bandeja de entrada de un archivo PST:

1. Crea una instancia del **FolderInfo** clase y cárguela con el contenido de la carpeta Bandeja de entrada.
1. Para agregar mensajes del disco a la carpeta Bandeja de entrada, llame al [FolderInfo.addMessage()](https://reference.aspose.com/email/java/com.aspose.email/folderinfo/#addMessage-com.aspose.email.MapiMessage-) método. El [FolderInfo](https://reference.aspose.com/email/java/com.aspose.email/folderinfo/) la clase expone el [addMessages](https://reference.aspose.com/email/java/com.aspose.email/folderinfo/#addMessages-java.lang.Iterable-com.aspose.email.MapiMessage--) método que permite agregar una gran cantidad de mensajes a la carpeta, lo que reduce las operaciones de E/S en el disco y mejora el rendimiento. Puede encontrar un ejemplo completo a continuación, en [Añadir mensajes masivos](#adding-bulk-messages).

Los fragmentos de código que aparecen a continuación muestran cómo agregar mensajes a una subcarpeta de PST llamada Bandeja de entrada.

~~~Java
// For complete examples and data files, please go to https://github.com/aspose-email/Aspose.Email-for-Java

// Create new PST
PersonalStorage personalStorage = PersonalStorage.create(dataDir, FileFormatVersion.Unicode);

// Add new folder "Inbox"
personalStorage.getRootFolder().addSubFolder("Inbox");

// Select the "Inbox" folder
FolderInfo inboxFolder = personalStorage.getRootFolder().getSubFolder("Inbox");

// Add some messages to "Inbox" folder
inboxFolder.addMessage(MapiMessage.fromFile(dataDir + "MapiMsgWithPoll.msg"));
~~~

### **Añadir mensajes masivos**

Agregar mensajes individuales a un PST implica más operaciones de E/S en el disco y, por lo tanto, puede ralentizar el rendimiento. Para mejorar el rendimiento, los mensajes se pueden agregar al PST de forma masiva para minimizar las operaciones de E/S. El [addMessages(Iterable<MapiMessage> messages)](https://reference.aspose.com/email/java/com.aspose.email/folderinfo/#addMessages-java.lang.Iterable-com.aspose.email.MapiMessage--) El método le permite definir un rango de mensajes que se agregarán al PST para mejorar el rendimiento y se puede usar en los siguientes escenarios. Además, el evento MessageAdded se produce cuando se agrega un mensaje a la carpeta.

### **Carga de mensajes desde un disco**

El siguiente fragmento de código muestra cómo cargar mensajes desde un disco.

~~~Java
// For complete examples and data files, please go to https://github.com/aspose-email/Aspose.Email-for-Java
private static void addMessagesInBulkMode(String fileName, String msgFolderName) {
    try (PersonalStorage personalStorage = PersonalStorage.fromFile(fileName)) {
        FolderInfo folder = personalStorage.getRootFolder().getSubFolder("myInbox");
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

### **Implementación iterable**

El siguiente fragmento de código muestra cómo crear una implementación iterable.

~~~Java
// For complete examples and data files, please go to https://github.com/aspose-email/Aspose.Email-for-Java
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

### **Agregar mensajes de otro PST**

Para agregar mensajes de otro PST, utilice el [FolderInfo.enumerateMapiMessages()](https://reference.aspose.com/email/java/com.aspose.email/folderinfo/#enumerateMapiMessages--) método que devuelve Iterable<MapiMessage>. El siguiente fragmento de código muestra cómo agregar mensajes desde otro PST.

~~~Java
// For complete examples and data files, please go to https://github.com/aspose-email/Aspose.Email-for-Java
private static void bulkAddFromAnotherPst(String source) {
    // The path to the File directory.
    String dataDir = "data/";

    try (PersonalStorage pst = PersonalStorage.fromFile(source, false)) {
        try (PersonalStorage pstDest = PersonalStorage.fromFile(dataDir + "PersonalStorageFile1.pst")) {
            // Get the folder by name
            FolderInfo folderInfo = pst.getRootFolder().getSubFolder("Contacts");
            MessageInfoCollection ms = folderInfo.getContents();

            // Get the folder by name
            FolderInfo f = pstDest.getRootFolder().getSubFolder("myInbox");
            f.MessageAdded.add(new MessageAddedEventHandler() {
                public void invoke(Object sender, MessageAddedEventArgs e) {
                    onMessageAdded(sender, e);
                }
            });
            f.addMessages(folderInfo.enumerateMapiMessages());
            FolderInfo fi = pstDest.getRootFolder().getSubFolder("myInbox");
            MessageInfoCollection msgs = fi.getContents();
        }
    }
}

// Handles the MessageAdded event.
static void onMessageAdded(Object sender, MessageAddedEventArgs e) {
    System.out.println(e.getEntryId());
    System.out.println(e.getMessage().getSubject());
}
~~~

## **Obtener información de mensajes de un archivo PST de Outlook**

In [Lea el archivo PST de Outlook y obtenga información sobre carpetas y subcarpetas](/email/java/read-outlook-pst-file-and-get-folders-and-subfolders-information/), hablamos de cargar un archivo PST de Outlook y examinar sus carpetas para obtener los nombres de las carpetas y el número de mensajes que contienen. En este artículo se explica cómo leer todas las carpetas y subcarpetas del archivo PST y cómo mostrar la información sobre los mensajes, por ejemplo, el asunto, el remitente y los destinatarios. El [FolderInfo.getContents()](https://reference.aspose.com/email/java/com.aspose.email/folderinfo/#getContents--) el método se usa para mostrar [información breve del mensaje](https://reference.aspose.com/email/java/com.aspose.email/folderinfo/#enumerateMapiMessages--) como el asunto, el remitente y los destinatarios.
En términos de rendimiento, esta es la opción más adecuada para obtener información primaria sobre los mensajes. Para [extract](#extracting-messages-form-pst-files) datos completos del mensaje, el [PersonalStorage.extractMessage()](https://reference.aspose.com/email/java/com.aspose.email/personalstorage/#extractMessage-com.aspose.email.MessageInfo-) se proporciona el método.
El archivo PST de Outlook puede contener carpetas anidadas. Para obtener información sobre los mensajes de estas carpetas, así como de las carpetas de nivel superior, utilice un método recursivo para leer todas las carpetas. El siguiente fragmento de código muestra cómo leer un archivo PST de Outlook y mostrar el contenido de la carpeta y el mensaje de forma recursiva.

~~~Java
// For complete examples and data files, please go to https://github.com/aspose-email/Aspose.Email-for-Java
public static void run() {
    // The path to the File directory.
    String dataDir = "data/";

    // Load the Outlook file
    String path = dataDir + "PersonalStorage.pst";

    try {

        // Load the Outlook PST file
        PersonalStorage personalStorage = PersonalStorage.fromFile(path);

        // Get the Display Format of the PST file
        System.out.println("Display Format: " + personalStorage.getFormat());

        // Get the folders and messages information
        FolderInfo folderInfo = personalStorage.getRootFolder();

        // Call the recursive method to display the folder contents
        displayFolderContents(folderInfo, personalStorage);
    } catch (Exception ex) {
        System.out.println(ex.getMessage());
    }
}

// This is a recursive method to display contents of a folder
private static void displayFolderContents(FolderInfo folderInfo, PersonalStorage pst) {
    // Display the folder name
    System.out.println("Folder: " + folderInfo.getDisplayName());
    System.out.println("==================================");
    // Display information about messages inside this folder
    MessageInfoCollection messageInfoCollection = folderInfo.getContents();
    for (MessageInfo messageInfo : messageInfoCollection) {
        System.out.println("Subject: " + messageInfo.getSubject());
        System.out.println("Sender: " + messageInfo.getSenderRepresentativeName());
        System.out.println("Recipients: " + messageInfo.getDisplayTo());
        System.out.println("------------------------------");
    }

    // Call this method recursively for each subfolder
    if (folderInfo.hasSubFolders() == true) {
        for (FolderInfo subfolderInfo : folderInfo.getSubFolders()) {
            displayFolderContents(subfolderInfo, pst);
        }
    }
}
~~~

## **Extracción de mensajes de archivos PST**

Este artículo muestra cómo leer archivos PST de Microsoft Outlook y [extraer mensajes](#extracting-messages-form-pst-files). Luego, los mensajes se guardan en el disco en formato MSG. El artículo también muestra cómo [extraer un número específico de mensajes](#extracting-n-number-of-messages-from-a-pst-file) desde un archivo PST. Utilice un método recursivo para examinar todas las carpetas (incluidas las carpetas anidadas) y llame al [PersonalStorage.extractMessage()](https://reference.aspose.com/email/java/com.aspose.email/personalstorage/#extractMessage-com.aspose.email.MessageInfo-) método para llevar los mensajes de Outlook a una instancia del [MapiMessage](https://reference.aspose.com/email/java/com.aspose.email/mapimessage/) clase. Después de eso, llama al [MapiMessage.save()](https://reference.aspose.com/email/java/com.aspose.email/mapimessage/#save-java.lang.String-) método para guardar el mensaje en el disco o en la transmisión en formato MSG. El siguiente fragmento de código muestra cómo extraer mensajes de un archivo PST.

~~~Java
// For complete examples and data files, please go to https://github.com/aspose-email/Aspose.Email-for-Java
public static void run() {
    // The path to the File directory.
    String dataDir = "data/";

    // Load the Outlook file
    String path = dataDir + "PersonalStorage.pst";

    try {
        // load the Outlook PST file
        PersonalStorage pst = PersonalStorage.fromFile(path);

        // get the Display Format of the PST file
        System.out.println("Display Format: " + pst.getFormat());

        // get the folders and messages information
        FolderInfo folderInfo = pst.getRootFolder();

        // Call the recursive method to extract msg files from each folder
        extractMsgFiles(folderInfo, pst);
    } catch (Exception ex) {
        System.out.println(ex.getMessage());
    }
}

// This is a recursive method to display contents of a folder
private static void extractMsgFiles(FolderInfo folderInfo, PersonalStorage pst) {
    // display the folder name
    System.out.println("Folder: " + folderInfo.getDisplayName());
    System.out.println("==================================");
    // loop through all the messages in this folder
    MessageInfoCollection messageInfoCollection = folderInfo.getContents();
    for (MessageInfo messageInfo : messageInfoCollection) {
        System.out.println("Saving message {0} ...." + messageInfo.getSubject());
        // get the message in MapiMessage instance
        MapiMessage message = pst.extractMessage(messageInfo);
        // save this message to disk in msg format
        message.save(message.getSubject().replace(":", " ") + ".msg");
        // save this message to stream in msg format
        ByteArrayOutputStream messageStream = new ByteArrayOutputStream();
        message.save(messageStream);
    }

    // Call this method recursively for each subfolder
    if (folderInfo.hasSubFolders() == true) {
        for (FolderInfo subfolderInfo : folderInfo.getSubFolders()) {
            extractMsgFiles(subfolderInfo, pst);
        }
    }
}
~~~

### **Guardar mensajes directamente desde PST para transmitirlos**

Para guardar los mensajes de un archivo PST directamente para transmitirlos, sin extraer la información de MSG de los mensajes, utilice el [saveMessageToStream()](https://reference.aspose.com/email/java/com.aspose.email/personalstorage/#saveMessageToStream-java.lang.String-java.io.OutputStream-) método. El siguiente fragmento de código muestra cómo guardar mensajes directamente desde PST para transmitirlos.

~~~Java
// For complete examples and data files, please go to https://github.com/aspose-email/Aspose.Email-for-Java
// The path to the File directory.
String dataDir = "data/";

// Load the Outlook file
String path = dataDir + "PersonalStorage.pst";

// Save message to MemoryStream
try (PersonalStorage personalStorage = PersonalStorage.fromFile(path)) {
    FolderInfo inbox = personalStorage.getRootFolder().getSubFolder("Inbox");
    for (MessageInfo messageInfo : inbox.enumerateMessages()) {
        try (ByteArrayOutputStream memeorystream = new ByteArrayOutputStream()) {
            personalStorage.saveMessageToStream(messageInfo.getEntryIdString(), memeorystream);
        }
    }
}

// Save message to file
try (PersonalStorage pst = PersonalStorage.fromFile(path)) {
    FolderInfo inbox = pst.getRootFolder().getSubFolder("Inbox");
    for (MessageInfo messageInfo : inbox.enumerateMessages()) {
        try (FileOutputStream fs = new FileOutputStream(new File(dataDir + messageInfo.getSubject() + ".msg"))) {
            pst.saveMessageToStream(messageInfo.getEntryIdString(), fs);
        }
    }
}

try (PersonalStorage pst = PersonalStorage.fromFile(path)) {
    FolderInfo inbox = pst.getRootFolder().getSubFolder("Inbox");

    // To enumerate entryId of messages you may use FolderInfo.EnumerateMessagesEntryId() method:
    for (String entryId : inbox.enumerateMessagesEntryId()) {
        try (ByteArrayOutputStream ms = new ByteArrayOutputStream()) {
            pst.saveMessageToStream(entryId, ms);
        }
    }
}
~~~

### **Extraer un número n de mensajes de un archivo PST**

El siguiente fragmento de código muestra cómo extraer un número determinado de mensajes de un PST. Simplemente proporcione el índice del primer mensaje y el número total de mensajes que se van a extraer.

~~~Java
// For complete examples and data files, please go to https://github.com/aspose-email/Aspose.Email-for-Java
FolderInfo inbox = personalStorage.getRootFolder().getSubFolder("Inbox");

// Extracts messages starting from 10th index top and extract total 100 messages
MessageInfoCollection messages = inbox.getContents(10, 100);
~~~

### **Obtener el número total de elementos de un archivo PST**

Aspose.Email proporciona la [GetTotalItemsCount()](https://reference.aspose.com/email/java/com.aspose.email/messagestore/#getTotalItemsCount--) método del [PersonalStorage.Store](https://reference.aspose.com/email/java/com.aspose.email/personalstorage/#getStore--) propiedad. Devuelve el número total de elementos de mensaje contenidos en el PST.

El siguiente ejemplo de código muestra cómo recuperar el recuento total de elementos (mensajes, citas, contactos, etc.) almacenados en el archivo PST:

```java
try (PersonalStorage pst = PersonalStorage.fromFile("my.pst", false)) {
    int count = pst.getStore().getTotalItemsCount();
}
```

## **Eliminar elementos de archivos PST**

[Agregar mensajes a archivos PST](#adding-messages-to-pst-files) mostró cómo agregar mensajes a archivos PST. Por supuesto, también es posible eliminar elementos (contenidos) de un archivo PST y también puede ser conveniente eliminar los mensajes de forma masiva. Los elementos de un archivo PST se pueden eliminar mediante el [FolderInfo.deleteChildItem()](https://reference.aspose.com/email/java/com.aspose.email/folderinfo/#deleteChildItem-byte---) método. La API también proporciona [FolderInfo.deleteChildItems()](https://reference.aspose.com/email/java/com.aspose.email/folderinfo/#deleteChildItems-java.lang.Iterable-java.lang.String--) método para eliminar elementos de forma masiva del archivo PST.

### **Eliminar mensajes de archivos PST**

En este artículo se muestra cómo utilizar el [FolderInfo](https://reference.aspose.com/email/java/com.aspose.email/folderinfo/) clase para acceder a carpetas específicas de un archivo PST. Para eliminar mensajes de la subcarpeta Enviados de un archivo PST previamente cargado o creado:

1. Crea una instancia del [FolderInfo](https://reference.aspose.com/email/java/com.aspose.email/folderinfo/) clase y cárguela con el contenido de la subcarpeta enviada.
1. Para eliminar los mensajes de la carpeta Enviados, llame al [FolderInfo.deleteChildItem()](https://reference.aspose.com/email/java/com.aspose.email/folderinfo/#deleteChildItem-byte---) método y pasar el [MessageInfo.EntryId](https://reference.aspose.com/email/java/com.aspose.email/messageinfo/#getEntryId--) como parámetro. El siguiente fragmento de código muestra cómo eliminar mensajes de la subcarpeta Enviados de un archivo PST.

~~~Java
// For complete examples and data files, please go to https://github.com/aspose-email/Aspose.Email-for-Java
// The path to the File directory.
String dataDir = "data/" + "Sub.pst";

// Load the Outlook PST file
PersonalStorage personalStorage = PersonalStorage.fromFile(dataDir);

// Get the Sent items folder
FolderInfo folderInfo = personalStorage.getPredefinedFolder(StandardIpmFolder.SentItems);

MessageInfoCollection msgInfoColl = folderInfo.getContents();
for (MessageInfo msgInfo : msgInfoColl) {
    System.out.println(msgInfo.getSubject() + ": " + msgInfo.getEntryIdString());
    if (msgInfo.getSubject().equals("some delete condition")) {
        // Delete this item
        folderInfo.deleteChildItem(msgInfo.getEntryId());
        System.out.println("Deleted this message");
    }
}
~~~

### **Eliminar carpetas de archivos PST**

Puede eliminar una carpeta PST moviéndola a la carpeta Elementos eliminados.

~~~Java
try (PersonalStorage pst = PersonalStorage.fromFile("test.pst")) {
    FolderInfo deletedItemsFolder = pst.getPredefinedFolder(StandardIpmFolder.DeletedItems);
    FolderInfo emptyFolder = pst.getRootFolder().getSubFolder("Empty folder");
    FolderInfo someFolder = pst.getRootFolder().getSubFolder("Some folder");
    pst.moveItem(emptyFolder, deletedItemsFolder);
    pst.moveItem(someFolder, deletedItemsFolder);
}
~~~
La ventaja de este método es que la carpeta eliminada se puede recuperar fácilmente.


~~~Java
FolderInfo someFolder = deletedItemsFolder.getSubFolder("Some folder");
pst.moveItem(someFolder, pst.getRootFolder());
~~~
También puede eliminar permanentemente una carpeta de la carpeta Elementos eliminados, si es necesario.


~~~Java
deletedItemsFolder.deleteChildItem(emptyFolder.getEntryId());
~~~
The [deleteChildItem()](https://apireference.aspose.com/email/java/com.aspose.email/FolderInfo#deleteChildItem\(byte[]\)) el método se puede usar para cualquier carpeta si desea eliminar la subcarpeta de forma inmediata y permanente, sin pasar por la carpeta Elementos eliminados.


~~~Java
FolderInfo someFolder = pst.getRootFolder().getSubFolder("Some folder");
pst.getRootFolder().deleteChildItem(someFolder.getEntryId());
~~~

### **Eliminar artículos de forma masiva del archivo PST**

La API Aspose.Email se puede usar para eliminar elementos de forma masiva de un archivo PST. Esto se logra mediante el [deleteChildItems()](https://reference.aspose.com/email/java/com.aspose.email/folderinfo/#deleteChildItems-java.lang.Iterable-java.lang.String--) método que acepta una lista de elementos de ID de entrada que hacen referencia a los elementos que se eliminarán. El siguiente fragmento de código muestra cómo eliminar elementos de forma masiva del archivo PST.


~~~Java
// For complete examples and data files, please go to https://github.com/aspose-email/Aspose.Email-for-Java
// The path to the File directory.
String dataDir = "data/" + "Sub.pst";

try (PersonalStorage personalStorage = PersonalStorage.fromFile(dataDir)) {
    // Get Inbox SubFolder from Outlook file
    FolderInfo inbox = personalStorage.getRootFolder().getSubFolder("Inbox");

    // Create instance of PersonalStorageQueryBuilder
    PersonalStorageQueryBuilder queryBuilder = new PersonalStorageQueryBuilder();

    queryBuilder.getFrom().contains("someuser@domain.com");
    MessageInfoCollection messages = inbox.getContents(queryBuilder.getQuery());
    List<String> deleteList = new ArrayList<String>();
    for (MessageInfo messageInfo : messages) {
        deleteList.add(messageInfo.getEntryIdString());
    }

    // delete messages having From = "someuser@domain.com"
    inbox.deleteChildItems(deleteList);
}
~~~

## **Buscar mensajes y carpetas en un PST por criterio**

Los archivos de almacenamiento personal (PST) pueden contener una gran cantidad de datos y la búsqueda de datos que cumplan un criterio específico en archivos tan grandes debe incluir varios puntos de control en el código para filtrar la información. Con el [PersonalStorageQueryBuilder](https://reference.aspose.com/email/java/com.aspose.email/personalstoragequerybuilder/) La clase Aspose.Email permite buscar registros específicos en un PST en función de un criterio de búsqueda específico. Se pueden buscar mensajes en un PST en función de parámetros de búsqueda como el remitente, el destinatario, el asunto, la importancia del mensaje, la presencia de archivos adjuntos, el tamaño del mensaje e incluso el identificador del mensaje. El [PersonalStorageQueryBuilder](https://reference.aspose.com/email/java/com.aspose.email/personalstoragequerybuilder/) también se puede usar para buscar subcarpetas.

### **Búsqueda de mensajes y carpetas en PST**

El siguiente fragmento de código muestra cómo usar el [PersonalStorageQueryBuilder](https://reference.aspose.com/email/java/com.aspose.email/personalstoragequerybuilder/) clase para buscar contenido en un PST en función de diferentes criterios de búsqueda. Por ejemplo, muestra la búsqueda de un PST basada en:

- Importancia del mensaje.
- Clase de mensajes.
- Presencia de archivos adjuntos.
- Tamaño del mensaje.
- Fecha del mensaje.
- Mensajes no leídos.
- Mensajes no leídos con archivos adjuntos y
- carpetas con un nombre de subcarpeta específico.


~~~Java
// For complete examples and data files, please go to https://github.com/aspose-email/Aspose.Email-for-Java
// The path to the File directory.
String dataDir = "data/";

try (PersonalStorage personalStorage = PersonalStorage.fromFile(dataDir + "Outlook.pst")) {
    FolderInfo folder = personalStorage.getRootFolder().getSubFolder("Inbox");
    PersonalStorageQueryBuilder builder = new PersonalStorageQueryBuilder();

    // High importance messages
    builder.getImportance().equals((int) MapiImportance.High);
    MessageInfoCollection messages = folder.getContents(builder.getQuery());
    System.out.println("Messages with High Imp:" + messages.size());

    builder = new PersonalStorageQueryBuilder();
    builder.getMessageClass().equals("IPM.Note");
    messages = folder.getContents(builder.getQuery());
    System.out.println("Messages with IPM.Note:" + messages.size());

    builder = new PersonalStorageQueryBuilder();
    // Messages with attachments AND high importance
    builder.getImportance().equals((int) MapiImportance.High);
    builder.hasFlags(MapiMessageFlags.MSGFLAG_HASATTACH);
    messages = folder.getContents(builder.getQuery());
    System.out.println("Messages with atts: " + messages.size());

    builder = new PersonalStorageQueryBuilder();
    // Messages with size > 15 KB
    builder.getMessageSize().greater(15000);
    messages = folder.getContents(builder.getQuery());
    System.out.println("messags size > 15Kb:" + messages.size());

    java.util.Calendar c = java.util.Calendar.getInstance();

    builder = new PersonalStorageQueryBuilder();
    // Messages by Current Date
    // (Note that queries by date are not supported for Calendar Items in the Appointments folder)
    builder.getSentDate().on(c.getTime(), DateComparisonType.ByDate);
    messages = folder.getContents(builder.getQuery());
    System.out.println("Messages by Current Date: " + messages.size());

    builder = new PersonalStorageQueryBuilder();
    // Messages between Dates
    // (Note that queries by date are not supported for Calendar Items in the Appointments folder)
    c.set(2020,  0, 1, 0, 0, 0);
    builder.getSentDate().since(c.getTime());
    c.set(2021,  0, 1, 0, 0, 0);
    builder.getSentDate().before(c.getTime());
    messages = folder.getContents(builder.getQuery());
    System.out.println("Messages between Dates: " + messages.size());

    builder = new PersonalStorageQueryBuilder();
    // Unread messages
    builder.hasNoFlags(MapiMessageFlags.MSGFLAG_READ);
    messages = folder.getContents(builder.getQuery());
    System.out.println("Unread:" + messages.size());

    builder = new PersonalStorageQueryBuilder();
    // Unread messages with attachments
    builder.hasNoFlags(MapiMessageFlags.MSGFLAG_READ);
    builder.hasFlags(MapiMessageFlags.MSGFLAG_HASATTACH);
    messages = folder.getContents(builder.getQuery());
    System.out.println("Unread msgs with atts: " + messages.size());

    // Folder with name of 'SubInbox'
    builder = new PersonalStorageQueryBuilder();
    builder.getFolderName().equals("SubInbox");
    FolderInfoCollection folders = folder.getSubFolders(builder.getQuery());
    System.out.println("Folder having subfolder: " + folders.size());

    builder = new PersonalStorageQueryBuilder();
    // Folders with subfolders
    builder.hasSubfolders();
    folders = folder.getSubFolders(builder.getQuery());
    System.out.println(folders.size());
}
~~~

### **Búsqueda de una cadena en PST con el parámetro Ignorar mayúsculas y minúsculas**

El siguiente fragmento de código muestra cómo buscar una cadena en PST con el parámetro ignore mayúsculas y minúsculas.

~~~Java
// For complete examples and data files, please go to https://github.com/aspose-email/Aspose.Email-for-Java
// The path to the File directory.
String dataDir = "data/";

try (PersonalStorage personalStorage = PersonalStorage.create(dataDir + "CaseSensitivity.pst", FileFormatVersion.Unicode)) {
    FolderInfo folderinfo = personalStorage.createPredefinedFolder("Inbox", StandardIpmFolder.Inbox);
    folderinfo.addMessage(MapiMessage.fromMailMessage(MailMessage.load("Sample.eml")));
    PersonalStorageQueryBuilder builder = new PersonalStorageQueryBuilder();
    // IgnoreCase is True
    builder.getFrom().contains("automated", true);
    MailQuery query = builder.getQuery();
    MessageInfoCollection coll = folderinfo.getContents(query);
    System.out.println(coll.size());
}
~~~

### **Búsqueda de asuntos de mensajes por varias palabras clave en un archivo PST**

Puedes usar [MailQueryBuilder.or](https://apireference.aspose.com/email/java/com.aspose.email/MailQueryBuilder#or\(com.aspose.email.MailQuery,%20com.aspose.email.MailQuery\)) método para buscar mensajes con un asunto que contenga al menos una de las palabras especificadas, como se muestra a continuación:

~~~java
PersonalStorageQueryBuilder builder1 = new PersonalStorageQueryBuilder();
builder1.getSubject().contains("Review"); // 'Review' is key word for the search

PersonalStorageQueryBuilder builder2 = new PersonalStorageQueryBuilder();
builder2.getSubject().contains("Error"); // 'Error' is also key word for the search

PersonalStorageQueryBuilder queryBuilder = new PersonalStorageQueryBuilder();
queryBuilder.or(builder1.getQuery(), builder2.getQuery()); // message subjects must contain 'Review' or 'Error' words

try (PersonalStorage storage = PersonalStorage.fromFile("example.pst"))
{
    FolderInfo folderInfo = storage.getRootFolder().getSubFolder("Inbox");
    MessageInfoCollection messageInfos = folderInfo.getContents(queryBuilder.getQuery());

    for (MessageInfo messageInfo : messageInfos)
    {
        System.out.println(messageInfo.getSubject());
    }
}
~~~

## **Mover elementos a otras carpetas del archivo PST**

Aspose.Email permite mover elementos de una carpeta de origen a otra carpeta del mismo archivo de almacenamiento personal (PST). Esto incluye:

- Mover una carpeta especificada a una nueva carpeta principal.
- Mover un mensaje especificado a una nueva carpeta.
- Mover el contenido a una nueva carpeta.
- Mover subcarpetas a una nueva carpeta principal.

El siguiente fragmento de código muestra cómo mover elementos como mensajes y carpetas de una carpeta de origen a otra carpeta del mismo archivo PST.

~~~Java
// For complete examples and data files, please go to https://github.com/aspose-email/Aspose.Email-for-Java
try (PersonalStorage personalStorage = PersonalStorage.fromFile("test.pst")) {
    FolderInfo inbox = personalStorage.getPredefinedFolder(StandardIpmFolder.Inbox);
    FolderInfo deleted = personalStorage.getPredefinedFolder(StandardIpmFolder.DeletedItems);
    FolderInfo subfolder = inbox.getSubFolder("Subfolder");

    // Move folder and message to the Deleted Items
    personalStorage.moveItem(subfolder, deleted);
    MessageInfoCollection contents = subfolder.getContents();
    personalStorage.moveItem(contents.get(0), deleted);

    // Move all inbox subfolders and subfolder contents to the Deleted Items
    inbox.moveSubfolders(deleted);
    subfolder.moveContents(deleted);
}
~~~

## **Actualización de las propiedades de los mensajes en un archivo PST**

A veces es necesario actualizar ciertas propiedades de los mensajes, como cambiar el asunto, marcar la importancia del mensaje y otras similares. La actualización de un mensaje en un archivo PST, con estos cambios en las propiedades del mensaje, se puede realizar mediante el [FolderInfo.changeMessages](https://reference.aspose.com/email/java/com.aspose.email/folderinfo/#changeMessages-com.aspose.email.MapiPropertyCollection-) método. En este artículo se muestra cómo actualizar los mensajes de forma masiva en un archivo PST para modificar las propiedades. En el siguiente fragmento de código, se muestra cómo actualizar las propiedades de los mensajes de forma masiva para varios mensajes de un archivo PST.

~~~Java
// For complete examples and data files, please go to https://github.com/aspose-email/Aspose.Email-for-Java
// The path to the File directory.
String dataDir = "data/" + "Sub.pst";

// Load the Outlook PST file
PersonalStorage personalStorage = PersonalStorage.fromFile(dataDir);

// Get Requierd Subfolder
FolderInfo inbox = personalStorage.getRootFolder().getSubFolder("Inbox");

// find messages having From = "someuser@domain.com"
PersonalStorageQueryBuilder queryBuilder = new PersonalStorageQueryBuilder();
queryBuilder.getFrom().contains("someuser@domain.com");

// Get Contents from Query
MessageInfoCollection messages = inbox.getContents(queryBuilder.getQuery());

// Save (MessageInfo,EntryIdString) in List
List<String> changeList = new ArrayList<String>();
for (MessageInfo messageInfo : messages) {
    changeList.add(messageInfo.getEntryIdString());
}

// Compose the new properties
MapiPropertyCollection updatedProperties = new MapiPropertyCollection();
updatedProperties.add(MapiPropertyTag.PR_SUBJECT_W, new MapiProperty(MapiPropertyTag.PR_SUBJECT_W, "New Subject".getBytes(Charset.forName("utf-16le"))));
updatedProperties.add(MapiPropertyTag.PR_IMPORTANCE, new MapiProperty(MapiPropertyTag.PR_IMPORTANCE, BitConverter.getBytesInt64(2)));

// update messages having From = "someuser@domain.com" with new properties
inbox.changeMessages(changeList, updatedProperties);
~~~

## **Actualización de propiedades personalizadas en un archivo PST**

A veces es necesario marcar los elementos que se procesan en el archivo PST. La API Aspose.Email permite lograr esto utilizando MapiProperty y MapInAmedProperty. Los siguientes métodos son útiles para lograrlo.

- `constructor MapiNamedProperty(long propertyTag, String nameIdentifier, UUID propertyGuid, byte[] propertyValue)`
- `constructor MapiNamedProperty(long propertyTag, long nameIdentifier, UUID propertyGuid, byte[] propertyValue)`
- `FolderInfo.changeMessages(MapiPropertyCollection updatedProperties)` - cambia todos los mensajes de la carpeta
- `PersonalStorage.changeMessage(String entryId, MapiPropertyCollection updatedProperties)` - cambiar las propiedades de los mensajes

~~~Java
// For complete examples and data files, please go to https://github.com/aspose-email/Aspose.Email-for-Java
public static void run() {
    // The path to the File directory.
    String dataDir = "data/" + "Sub.pst";

    try (PersonalStorage personalStorage = PersonalStorage.fromFile(dataDir)) {
        FolderInfo testFolder = personalStorage.getRootFolder().getSubFolder("Inbox");

        // Create the collection of message properties for adding or updating
        MapiPropertyCollection newProperties = new MapiPropertyCollection();

        // Normal, Custom and PidLidLogFlags named property
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

## **Extraer archivos adjuntos sin extraer el mensaje completo**

La API Aspose.Email se puede usar para extraer archivos adjuntos de mensajes PST sin extraer primero el mensaje completo. El [ExtractAttachments](https://reference.aspose.com/email/java/com.aspose.email/personalstorage/#extractAttachments-com.aspose.email.MessageInfo-) método de [PersonalStorage](https://reference.aspose.com/email/java/com.aspose.email/personalstorage/) se puede usar para hacer esto. El siguiente fragmento de código muestra cómo extraer los archivos adjuntos sin extraer el mensaje completo.

~~~Java
// For complete examples and data files, please go to https://github.com/aspose-email/Aspose.Email-for-Java
// The path to the File directory.
String dataDir = "data/";

try (PersonalStorage personalstorage = PersonalStorage.fromFile(dataDir + "Outlook.pst")) {
    FolderInfo folder = personalstorage.getRootFolder().getSubFolder("Inbox");

    for (String messageInfo : folder.enumerateMessagesEntryId()) {
        MapiAttachmentCollection attachments = personalstorage.extractAttachments(messageInfo);

        if (attachments.size() != 0) {
            for (MapiAttachment attachment : attachments) {
                if (attachment.getLongFileName() != null && !attachment.getLongFileName().isEmpty()) {
                    if (attachment.getLongFileName().contains(".msg")) {
                        continue;
                    } else {
                        attachment.save(dataDir + "Attachments/" + attachment.getLongFileName());
                    }
                }
            }
        }
    }
}
~~~

## **Agregar archivos a PST**

La funcionalidad clave de Microsoft Outlook es administrar correos electrónicos, calendarios, tareas, contactos y entradas del diario. Además, los archivos también se pueden agregar a una carpeta PST y el PST resultante guarda un registro de los documentos agregados. Aspose.Email ofrece la posibilidad de agregar archivos a una carpeta de la misma manera, además de agregar mensajes, contactos, tareas y entradas de diario a PST. El siguiente fragmento de código muestra cómo agregar documentos a una carpeta PST mediante Aspose.Email.

~~~Java
// For complete examples and data files, please go to https://github.com/aspose-email/Aspose.Email-for-Java
// The path to the File directory.
String dataDir = "data/";

try (PersonalStorage personalStorage = PersonalStorage.create(dataDir + "Ps1_out.pst", FileFormatVersion.Unicode)) {
    FolderInfo folder = personalStorage.getRootFolder().addSubFolder("Files");

    // Add Document.doc file with the "IPM.Document" message class by default.
    folder.addFile(dataDir + "attachment_1.doc", null);
}
~~~
