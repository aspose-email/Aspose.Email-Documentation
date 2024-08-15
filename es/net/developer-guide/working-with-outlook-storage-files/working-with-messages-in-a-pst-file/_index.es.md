---
title: "Trabajar con mensajes en un archivo PST"
url: /es/net/working-with-messages-in-a-pst-file/
weight: 30
type: docs
---


## **Agregar mensajes a archivos PST**

The [Crear un nuevo archivo PST y agregar subcarpetas](https://docs.aspose.com/email/es/net/create-new-pst-add-sub-folders-and-messages/#creating-a-new-pst-file-and-add-subfolderss) El artículo muestra cómo crear un archivo PST y agregarle una subcarpeta. Con Aspose.Email puede agregar mensajes a las subcarpetas de un archivo PST que haya creado o cargado. Este artículo agrega dos mensajes del disco a la subcarpeta Bandeja de entrada de un PST. Utilice el [PersonalStorage](https://reference.aspose.com/email/net/aspose.email.storage.pst/personalstorage/) and [FolderInfo](https://reference.aspose.com/email/net/aspose.email.storage.pst/folderinfo/) clases para añadir mensajes a archivos PST. Para añadir mensajes a la carpeta Bandeja de entrada de un archivo PST:

1. Crea una instancia de la clase FolderInfo y cárgala con el contenido de la carpeta Inbox.
2. Para agregar mensajes de un disco a la carpeta Bandeja de entrada, llame al [FolderInfo.AddMessage()](https://reference.aspose.com/email/net/aspose.email.storage.pst/folderinfo/addmessage/#addmessage) método. El [FolderInfo](https://reference.aspose.com/email/net/aspose.email.storage.pst/folderinfo/) la clase expone el [AddMessages](https://reference.aspose.com/email/net/aspose.email.storage.pst/folderinfo/addmessages/#addmessages) método que permite agregar una gran cantidad de mensajes a la carpeta, lo que reduce las operaciones de E/S en un disco y mejora el rendimiento. Puede encontrar un ejemplo completo a continuación, en [Añadir mensajes masivos](https://docs.aspose.com/email/es/net/working-with-messages-in-a-pst-file/#adding-bulk-messages).

El siguiente fragmento de código muestra cómo agregar mensajes a una subcarpeta de PST llamada Bandeja de entrada.

```csharp
// For complete examples and data files, please go to https://github.com/aspose-email/Aspose.Email-for-.NET
// Create new PST           
PersonalStorage personalStorage = PersonalStorage.Create(dataDir, FileFormatVersion.Unicode);

// Add new folder "Inbox"
personalStorage.RootFolder.AddSubFolder("Inbox");

// Select the "Inbox" folder
FolderInfo inboxFolder = personalStorage.RootFolder.GetSubFolder("Inbox");

// Add some messages to "Inbox" folder
inboxFolder.AddMessage(MapiMessage.FromFile(RunExamples.GetDataDir_Outlook() + "MapiMsgWithPoll.msg"));
```

### **Añadir mensajes masivos**

Agregar mensajes individuales a un PST implica más operaciones de E/S en un disco y, por lo tanto, puede ralentizar el rendimiento. Para mejorar el rendimiento, utilice addMessages (IEnumerable)<MapiMessage> messages) en lugar del método addMessage (mensaje MAPIMessage) para minimizar las operaciones de E/S. Además, el evento messageAdded se produce cuando se agrega un mensaje a la carpeta.

### **Carga de mensajes desde un disco**

El siguiente fragmento de código muestra cómo cargar mensajes desde un disco.

```csharp
// For complete examples and data files, please go to https://github.com/aspose-email/Aspose.Email-for-.NET
private static void AddMessagesInBulkMode(string fileName, string msgFolderName)
{
    using (PersonalStorage personalStorage = PersonalStorage.FromFile(fileName))
    {
        FolderInfo folder = personalStorage.RootFolder.GetSubFolder("myInbox");
        folder.MessageAdded += OnMessageAdded;
        folder.AddMessages(new MapiMessageCollection(msgFolderName));
    }
}
static void OnMessageAdded(object sender, MessageAddedEventArgs e)
{
    Console.WriteLine(e.EntryId);
    Console.WriteLine(e.Message.Subject);
}
```

### **Implementación de IEnumerable**

El siguiente fragmento de código muestra cómo se puede usar Implementación de IEnumerable.

```csharp
// For complete examples and data files, please go to https://github.com/aspose-email/Aspose.Email-for-.NET
public class MapiMessageCollection : IEnumerable<MapiMessage>
{
    private string path;

    public MapiMessageCollection(string path)
    {
        this.path = path;
    }

    public IEnumerator<MapiMessage> GetEnumerator()
    {
        return new MapiMessageEnumerator(path);
    }

    IEnumerator IEnumerable.GetEnumerator()
    {
        return GetEnumerator();
    }
}

public class MapiMessageEnumerator : IEnumerator<MapiMessage>
{
    private readonly string[] files;

    private int position = -1;

    public MapiMessageEnumerator(string path)
    {
        string path1 = RunExamples.GetDataDir_Outlook();
        files = Directory.GetFiles(path1);
    }

    public bool MoveNext()
    {
        position++;
        return (position < files.Length);
    }

    public void Reset()
    {
        position = -1;
    }

    object IEnumerator.Current
    {
        get
        {
            return Current;
        }
    }

    public MapiMessage Current
    {
        get
        {
            try
            {
                return MapiMessage.FromFile(files[position]);
            }
            catch (IndexOutOfRangeException)
            {
                throw new InvalidOperationException();
            }
        }
    }
    public void Dispose()
    {
    }
}
```

### **Agregar mensajes de otro PST**

Para agregar mensajes de otro PST, utilice la [FolderInfo.EnumerateMapiMessages()](https://reference.aspose.com/email/net/aspose.email.storage.pst/folderinfo/enumeratemapimessages/#enumeratemapimessages) método que devuelve IEnumerable<MapiMessage>. El siguiente fragmento de código muestra cómo agregar mensajes desde otro PST.

```csharp
// For complete examples and data files, please go to https://github.com/aspose-email/Aspose.Email-for-.NET
private static void BulkAddFromAnotherPst(string source)
{
    using (PersonalStorage pst = PersonalStorage.FromFile(source, false))
    using (PersonalStorage pstDest = PersonalStorage.FromFile(RunExamples.GetDataDir_Outlook() + "PersonalStorageFile1.pst"))
    {
        // Get the folder by name
        FolderInfo folderInfo = pst.RootFolder.GetSubFolder("Contacts");
        MessageInfoCollection ms = folderInfo.GetContents();

        // Get the folder by name
        FolderInfo f = pstDest.RootFolder.GetSubFolder("myInbox");
        f.MessageAdded += new MessageAddedEventHandler(OnMessageAdded);
        f.AddMessages(folderInfo.EnumerateMapiMessages());
        FolderInfo fi = pstDest.RootFolder.GetSubFolder("myInbox");
        MessageInfoCollection msgs = fi.GetContents();

    }

}

/// <summary>
/// Handles the MessageAdded event.
/// </summary>
static void OnMessageAdded(object sender, MessageAddedEventArgs e)
{
    Console.WriteLine(e.EntryId);
    Console.WriteLine(e.Message.Subject);
}
```

## **Obtener información de mensajes de un archivo PST de Outlook**

In [Lea el archivo PST de Outlook y obtenga información sobre carpetas y subcarpetas](https://docs.aspose.com/email/es/net/read-outlook-pst-file-and-get-folders-and-subfolders-information/) En este artículo discutimos cómo cargar un archivo PST de Outlook y explorar sus carpetas para obtener los nombres de las carpetas y la cantidad de mensajes que contienen. Este artículo explica cómo leer todas las carpetas y subcarpetas del archivo PST y mostrar la información sobre los mensajes, por ejemplo, el asunto, el remitente y los destinatarios. El archivo PST de Outlook puede contener carpetas anidadas. Para obtener información sobre los mensajes de estas carpetas, así como de las carpetas de nivel superior, utilice un método recursivo para leer todas las carpetas. El siguiente fragmento de código muestra cómo leer un archivo PST de Outlook y mostrar el contenido de la carpeta y los mensajes de forma recursiva.

```csharp
// For complete examples and data files, please go to https://github.com/aspose-email/Aspose.Email-for-.NET
public static void Run()
{           
    string dataDir = RunExamples.GetDataDir_Outlook();

    // Load the Outlook file
    string path = dataDir + "PersonalStorage.pst";

    try
    {
      
        // Load the Outlook PST file
        PersonalStorage personalStorage = PersonalStorage.FromFile(path);

        // Get the Display Format of the PST file
        Console.WriteLine("Display Format: " + personalStorage.Format);

        // Get the folders and messages information
        FolderInfo folderInfo = personalStorage.RootFolder;

        // Call the recursive method to display the folder contents
        DisplayFolderContents(folderInfo, personalStorage);
    }
    catch (Exception ex)
    {
        Console.WriteLine(ex.Message);              
    }           
}

/// <summary>
/// This is a recursive method to display contents of a folder
/// </summary>
/// <param name="folderInfo"></param>
/// <param name="pst"></param>
private static void DisplayFolderContents(FolderInfo folderInfo, PersonalStorage pst)
{
    // Display the folder name
    Console.WriteLine("Folder: " + folderInfo.DisplayName);
    Console.WriteLine("==================================");
    // Display information about messages inside this folder
    MessageInfoCollection messageInfoCollection = folderInfo.GetContents();
    foreach (MessageInfo messageInfo in messageInfoCollection)
    {
        Console.WriteLine("Subject: " + messageInfo.Subject);
        Console.WriteLine("Sender: " + messageInfo.SenderRepresentativeName);
        Console.WriteLine("Recipients: " + messageInfo.DisplayTo);
        Console.WriteLine("------------------------------");
    }

    // Call this method recursively for each subfolder
    if (folderInfo.HasSubFolders == true)
    {
        foreach (FolderInfo subfolderInfo in folderInfo.GetSubFolders())
        {
            DisplayFolderContents(subfolderInfo, pst);
        }
    }
}
```

## **Extracción de mensajes de archivos PST**

Este artículo muestra cómo leer archivos PST de Microsoft Outlook y extraer mensajes. A continuación, los mensajes se guardan en un disco en formato MSG.

{{% alert %}}
**¡Pruébalo!**

Ejecute el [ConversationThread](https://github.com/aspose-email/Aspose.Email-for-.NET/tree/master/Sample%20Apps/ConversationThread) proyecto de aplicación simple y explore un uso interesante de las funciones de Aspose.Email para leer correos electrónicos de PST y encontrar hilos de conversación.
{{% /alert %}}

El siguiente fragmento de código muestra cómo extraer mensajes de un archivo PST:
- Utilice un método recursivo para examinar todas las carpetas (incluidas las carpetas anidadas) y llame al método PersonalStorage.extractMessage () para incluir los mensajes de Outlook en una instancia del [MapiMessage](https://reference.aspose.com/email/net/aspose.email.mapi/mapimessage/) class.
- Después de eso, llama al método mapiMessage.save () para guardar el mensaje en un disco o en una transmisión en formato MSG.

```csharp
// For complete examples and data files, please go to https://github.com/aspose-email/Aspose.Email-for-.NET
public static void Run()
{           
    // The path to the file directory.
    string dataDir = RunExamples.GetDataDir_Outlook();

    // Load the Outlook file
    string path = dataDir + "PersonalStorage.pst";

    try
    {
        // load the Outlook PST file
        PersonalStorage pst = PersonalStorage.FromFile(path);

        // get the Display Format of the PST file
        Console.WriteLine("Display Format: " + pst.Format);

        // get the folders and messages information
        FolderInfo folderInfo = pst.RootFolder;

        // Call the recursive method to extract msg files from each folder
        ExtractMsgFiles(folderInfo, pst);
    }
    catch (Exception ex)
    {
        Console.WriteLine(ex.Message);
    }           
}

/// <summary>
/// This is a recursive method to display contents of a folder
/// </summary>
/// <param name="folderInfo"></param>
/// <param name="pst"></param>
private static void ExtractMsgFiles(FolderInfo folderInfo, PersonalStorage pst)
{
    // display the folder name
    Console.WriteLine("Folder: " + folderInfo.DisplayName);
    Console.WriteLine("==================================");
    // loop through all the messages in this folder
    MessageInfoCollection messageInfoCollection = folderInfo.GetContents();
    foreach (MessageInfo messageInfo in messageInfoCollection)
    {
        Console.WriteLine("Saving message {0} ....", messageInfo.Subject);
        // get the message in MapiMessage instance
        MapiMessage message = pst.ExtractMessage(messageInfo);
        // save this message to disk in msg format
        message.Save(message.Subject.Replace(":", " ") + ".msg");
        // save this message to stream in msg format
        MemoryStream messageStream = new MemoryStream();
        message.Save(messageStream);
    }

    // Call this method recursively for each subfolder
    if (folderInfo.HasSubFolders == true)
    {
        foreach (FolderInfo subfolderInfo in folderInfo.GetSubFolders())
        {
            ExtractMsgFiles(subfolderInfo, pst);
        }
    }
}
```

### **Guardar mensajes directamente desde PST para transmitirlos**

Para guardar los mensajes de un archivo PST directamente en una transmisión, sin extraer el msgInfo de los mensajes, utilice el método saveMessageToStream (). En el siguiente fragmento de código, se muestra cómo guardar los mensajes directamente de PST en una transmisión.

```csharp
// For complete examples and data files, please go to https://github.com/aspose-email/Aspose.Email-for-.NET
// The path to the file directory.
string dataDir = RunExamples.GetDataDir_Outlook();

// Load the Outlook file
string path = dataDir + "PersonalStorage.pst";

// Save message to MemoryStream
using (PersonalStorage personalStorage = PersonalStorage.FromFile(path))
{
    FolderInfo inbox = personalStorage.RootFolder.GetSubFolder("Inbox");
    foreach (MessageInfo messageInfo in inbox.EnumerateMessages())
    {
        using (MemoryStream memeorystream = new MemoryStream())
        {
            personalStorage.SaveMessageToStream(messageInfo.EntryIdString, memeorystream);
        }
    }
}

// Save message to file
using (PersonalStorage pst = PersonalStorage.FromFile(path))
{
    FolderInfo inbox = pst.RootFolder.GetSubFolder("Inbox");
    foreach (MessageInfo messageInfo in inbox.EnumerateMessages())
    {
        using (FileStream fs = File.OpenWrite(messageInfo.Subject + ".msg"))
        {
            pst.SaveMessageToStream(messageInfo.EntryIdString, fs);
        }
    }
}

using (PersonalStorage pst = PersonalStorage.FromFile(path))
{
    FolderInfo inbox = pst.RootFolder.GetSubFolder("Inbox");
   
    // To enumerate entryId of messages you may use FolderInfo.EnumerateMessagesEntryId() method:
    foreach (string entryId in inbox.EnumerateMessagesEntryId())
    {
        using (MemoryStream ms = new MemoryStream())
        {
            pst.SaveMessageToStream(entryId, ms);
        }
    }
}           
```

### **Extraer un número n de mensajes de un archivo PST**

El siguiente fragmento de código muestra cómo extraer un número determinado de mensajes de un PST. Simplemente proporcione el índice del primer mensaje y el número total de mensajes que se van a extraer.

```csharp
// For complete examples and data files, please go to https://github.com/aspose-email/Aspose.Email-for-.NET
FolderInfo inbox = personalStorage.RootFolder.GetSubFolder("Inbox");

// Extracts messages starting from 10th index top and extract total 100 messages
MessageInfoCollection messages = inbox.GetContents(10, 100);
```
### **Obtener el recuento total de artículos de un archivo PST**

Aspose.Email proporciona la [GetTotalItemsCount()](https://reference.aspose.com/email/net/aspose.email.storage.pst/messagestore/gettotalitemscount/) método del [PersonalStorage.Store](https://reference.aspose.com/email/net/aspose.email.storage.pst/personalstorage/store/#personalstoragestore-property) propiedad. Devuelve el número total de elementos de mensaje contenidos en el PST.

El siguiente ejemplo de código muestra cómo recuperar el recuento total de elementos (mensajes, citas, contactos, etc.) almacenados en el archivo PST:

```cs
using (var pst = PersonalStorage.FromFile("my.pst", false))
{
    var count = pst.Store.GetTotalItemsCount();
}
```

## **Eliminar elementos de archivos PST**

The [Agregar mensajes a archivos PST](https://docs.aspose.com/email/es/net/working-with-messages-in-a-pst-file/#adding-messages-to-pst-files) el artículo muestra cómo agregar mensajes a archivos PST. Por supuesto, también es posible eliminar elementos (contenidos) de un archivo PST y también puede ser conveniente eliminar los mensajes de forma masiva. Los elementos de un archivo PST se pueden eliminar mediante el [FolderInfo.DeleteChildItem()](https://reference.aspose.com/email/net/aspose.email.storage.pst/folderinfo/deletechilditem/#deletechilditem) método. La API también proporciona [FolderInfo.DeleteChildItems()](https://reference.aspose.com/email/net/aspose.email.storage.pst/folderinfo/deletechilditem/#deletechilditem) método para eliminar elementos de forma masiva del archivo PST.

### **Eliminar mensajes de archivos PST**

En este artículo se muestra cómo utilizar el [FolderInfo](https://reference.aspose.com/email/net/aspose.email.storage.pst/folderinfo/) clase para acceder a carpetas específicas de un archivo PST. Para eliminar mensajes de la subcarpeta Enviados de un archivo PST previamente cargado o creado:

1. Crea una instancia del [FolderInfo](https://reference.aspose.com/email/net/aspose.email.storage.pst/folderinfo/) clase y cárguela con el contenido de la subcarpeta enviada.
1. Para eliminar los mensajes de la carpeta Enviados, llame al [FolderInfo.DeleteChildItem()](https://reference.aspose.com/email/net/aspose.email.storage.pst/folderinfo/deletechilditem/#deletechilditem) método y pasar el [MessageInfo.EntryId](https://reference.aspose.com/email/net/aspose.email.storage.pst/folderinfo/entryid/) como parámetro. El siguiente fragmento de código muestra cómo eliminar mensajes de la subcarpeta Enviados de un archivo PST.

```csharp
// For complete examples and data files, please go to https://github.com/aspose-email/Aspose.Email-for-.NET
// The path to the File directory.
string dataDir = RunExamples.GetDataDir_Outlook() + "Sub.pst";

// Load the Outlook PST file
PersonalStorage personalStorage = PersonalStorage.FromFile(dataDir);

// Get the Sent items folder
FolderInfo folderInfo = personalStorage.GetPredefinedFolder(StandardIpmFolder.SentItems);

MessageInfoCollection msgInfoColl = folderInfo.GetContents();
foreach (MessageInfo msgInfo in msgInfoColl)
{
    Console.WriteLine(msgInfo.Subject + ": " + msgInfo.EntryIdString);
    if (msgInfo.Subject.Equals("some delete condition") == true)
    {
        // Delete this item
        folderInfo.DeleteChildItem(msgInfo.EntryId);
        Console.WriteLine("Deleted this message");
    }
}
```

### **Eliminar carpetas de archivos PST**

Puede eliminar una carpeta PST moviéndola a la carpeta Elementos eliminados.

```csharp
using (PersonalStorage pst = PersonalStorage.FromFile(@"test.pst"))
{
    FolderInfo deletedItemsFolder = pst.GetPredefinedFolder(StandardIpmFolder.DeletedItems);
    FolderInfo emptyFolder = pst.RootFolder.GetSubFolder("Empty folder");
	  FolderInfo someFolder = pst.RootFolder.GetSubFolder("Some folder");
    pst.MoveItem(emptyFolder, deletedItemsFolder);
	  pst.MoveItem(someFolder, deletedItemsFolder);
}
```

La ventaja de este método es que la carpeta eliminada se puede recuperar fácilmente.

```csharp
FolderInfo someFolder = deletedItemsFolder.GetSubFolder("Some folder");
pst.MoveItem(someFolder, pst.RootFolder);
```

También puede eliminar permanentemente una carpeta de la carpeta Elementos eliminados, si es necesario.

```csharp
deletedItemsFolder.DeleteChildItem(emptyFolder.EntryId);
```

The [DeleteChildItem()](https://reference.aspose.com/email/net/aspose.email.storage.pst/folderinfo/deletechilditem/#deletechilditem) el método se puede usar para cualquier carpeta si desea eliminar una subcarpeta de forma inmediata y permanente, sin pasar por la carpeta Elementos eliminados.

```csharp
FolderInfo someFolder = pst.RootFolder.GetSubFolder("Some folder");
pst.RootFolder.DeleteChildItem(someFolder.EntryId);
```
### **Eliminar elementos de PST**

Elimine elementos (carpetas o mensajes) de una tabla de almacenamiento personal (PST) mediante el identificador de entrada único asociado al elemento mediante una llamada al método deleteItem (cadena entryID) del [PersonalStorage](https://reference.aspose.com/email/net/aspose.email.storage.pst/personalstorage/#personalstorage-class) class.

El siguiente fragmento de código se puede usar para llamar al método deleteItem y pasar el EntryID como parámetro:

```cs
var pst = PersonalStorage.FromFile("sample.pst");

// ...

pst.DeleteItem(entryId);

// ...
```
**Tenga en cuenta:**

- Este método eliminará permanentemente el elemento del PST y no se puede deshacer. Tenga cuidado al utilizar este método para evitar la pérdida accidental de datos.
- Según las convenciones estándar, asegúrese de que el EntryID sea válido y corresponda a un elemento existente en el PST.
- De lo contrario, se generará una excepción. Es recomendable tener una copia de seguridad del PST o implementar las medidas adecuadas para recuperar los elementos eliminados si es necesario.

### **Eliminar artículos de forma masiva del archivo PST**

La API Aspose.Email se puede usar para eliminar elementos de forma masiva de un archivo PST. Esto se logra mediante el [DeleteChildItems()](https://reference.aspose.com/email/net/aspose.email.storage.pst/folderinfo/deletechilditems/#deletechilditems) método que acepta una lista de elementos de ID de entrada que hacen referencia a los elementos que se eliminarán. El siguiente fragmento de código muestra cómo eliminar elementos de forma masiva del archivo PST.

```csharp
// For complete examples and data files, please go to https://github.com/aspose-email/Aspose.Email-for-.NET
// The path to the File directory.
string dataDir = RunExamples.GetDataDir_Outlook() + @"Sub.pst";
using (PersonalStorage personalStorage = PersonalStorage.FromFile(dataDir))
{
    // Get Inbox SubFolder from Outlook file
    FolderInfo inbox = personalStorage.RootFolder.GetSubFolder("Inbox");

    // Create instance of PersonalStorageQueryBuilder
    PersonalStorageQueryBuilder queryBuilder = new PersonalStorageQueryBuilder();

    queryBuilder.From.Contains("someuser@domain.com");
    MessageInfoCollection messages = inbox.GetContents(queryBuilder.GetQuery());
    IList<string> deleteList = new List<string>();
    foreach (MessageInfo messageInfo in messages)
    {
        deleteList.Add(messageInfo.EntryIdString);
    }

    // delete messages having From = "someuser@domain.com"
    inbox.DeleteChildItems(deleteList);
}
```

## **Buscar mensajes y carpetas en un PST por criterio**

Los archivos de almacenamiento personal (PST) pueden contener una gran cantidad de datos. La búsqueda de datos que cumplan un criterio específico en archivos tan grandes debe incluir varios puntos de control en el código para filtrar la información. Con el [PersonalStorageQueryBuilder](https://reference.aspose.com/email/net/aspose.email.storage.pst/personalstoragequerybuilder/) La clase Aspose.Email permite buscar registros específicos en un PST en función de un criterio de búsqueda específico. Se pueden buscar mensajes en un PST en función de parámetros de búsqueda como el remitente, el destinatario, el asunto, la importancia del mensaje, la presencia de archivos adjuntos, el tamaño del mensaje e incluso el identificador del mensaje. El [PersonalStorageQueryBuilder](https://reference.aspose.com/email/net/aspose.email.storage.pst/personalstoragequerybuilder/) también se puede usar para buscar subcarpetas.

### **Búsqueda de mensajes y carpetas en PST**

El siguiente fragmento de código muestra cómo usar el [PersonalStorageQueryBuilder](https://reference.aspose.com/email/net/aspose.email.storage.pst/personalstoragequerybuilder/) clase para buscar contenido en un PST en función de diferentes criterios de búsqueda. Por ejemplo, muestra la búsqueda de un PST basada en:

- Importancia del mensaje.
- Clase de mensajes.
- Presencia de archivos adjuntos.
- Tamaño del mensaje.
- Mensajes no leídos.
- Mensajes no leídos con archivos adjuntos y
- carpetas con un nombre de subcarpeta específico.

```csharp
// For complete examples and data files, please go to https://github.com/aspose-email/Aspose.Email-for-.NET
// The path to the File directory.
string dataDir = RunExamples.GetDataDir_Outlook();

using (PersonalStorage personalStorage = PersonalStorage.FromFile(dataDir + "Outlook.pst"))
{
    FolderInfo folder = personalStorage.RootFolder.GetSubFolder("Inbox");
    PersonalStorageQueryBuilder builder = new PersonalStorageQueryBuilder();

    // High importance messages
    builder.Importance.Equals((int)MapiImportance.High);
    MessageInfoCollection messages = folder.GetContents(builder.GetQuery());
    Console.WriteLine("Messages with High Imp:" + messages.Count);

    builder = new PersonalStorageQueryBuilder();
    builder.MessageClass.Equals("IPM.Note");
    messages = folder.GetContents(builder.GetQuery());
    Console.WriteLine("Messages with IPM.Note:" + messages.Count);

    builder = new PersonalStorageQueryBuilder();
    // Messages with attachments AND high importance
    builder.Importance.Equals((int)MapiImportance.High);
    builder.HasFlags(MapiMessageFlags.MSGFLAG_HASATTACH);
    messages = folder.GetContents(builder.GetQuery());
    Console.WriteLine("Messages with atts: " + messages.Count);

    builder = new PersonalStorageQueryBuilder();
    // Messages with size > 15 KB
    builder.MessageSize.Greater(15000);
    messages = folder.GetContents(builder.GetQuery());
    Console.WriteLine("messags size > 15Kb:" + messages.Count);

    builder = new PersonalStorageQueryBuilder();
    // Unread messages
    builder.HasNoFlags(MapiMessageFlags.MSGFLAG_READ);
    messages = folder.GetContents(builder.GetQuery());
    Console.WriteLine("Unread:" + messages.Count);

    builder = new PersonalStorageQueryBuilder();
    // Unread messages with attachments
    builder.HasNoFlags(MapiMessageFlags.MSGFLAG_READ);
    builder.HasFlags(MapiMessageFlags.MSGFLAG_HASATTACH);
    messages = folder.GetContents(builder.GetQuery());
    Console.WriteLine("Unread msgs with atts: " + messages.Count);

    // Folder with name of 'SubInbox'
    builder = new PersonalStorageQueryBuilder();
    builder.FolderName.Equals("SubInbox");
    FolderInfoCollection folders = folder.GetSubFolders(builder.GetQuery());
    Console.WriteLine("Folder having subfolder: " + folders.Count);

    builder = new PersonalStorageQueryBuilder();
    // Folders with subfolders
    builder.HasSubfolders();
    folders = folder.GetSubFolders(builder.GetQuery());
    Console.WriteLine(folders.Count);
}
```

### **Búsqueda de una cadena en PST con el parámetro Ignorar mayúsculas y minúsculas**

El siguiente fragmento de código muestra cómo buscar una cadena en PST con el parámetro ignore mayúsculas y minúsculas.

```csharp
// For complete examples and data files, please go to https://github.com/aspose-email/Aspose.Email-for-.NET

File.Delete("CaseSensitivity.pst");
using (PersonalStorage personalStorage = PersonalStorage.Create("CaseSensitivity.pst", FileFormatVersion.Unicode))
{
	FolderInfo folderinfo = personalStorage.CreatePredefinedFolder("Inbox", StandardIpmFolder.Inbox);
	folderinfo.AddMessage(MapiMessage.FromMailMessage(MailMessage.Load("Sample.eml")));
	PersonalStorageQueryBuilder builder = new PersonalStorageQueryBuilder();
	// IgnoreCase is True
	builder.From.Contains("automated", true);
	MailQuery query = builder.GetQuery();
	MessageInfoCollection coll = folderinfo.GetContents(query);
	Console.WriteLine(coll.Count);
}
```

### **Búsqueda de asuntos de mensajes por varias palabras clave en un archivo PST**

Puedes usar [MailQueryBuilder.Or](https://reference.aspose.com/email/net/aspose.email.tools.search/mailquerybuilder/or/#or) método para buscar mensajes con un asunto que contenga al menos una de las palabras especificadas, como se muestra a continuación:

```csharp
// For complete examples and data files, please go to https://github.com/aspose-email/Aspose.Email-for-.NET

var builder1 = new PersonalStorageQueryBuilder();
builder1.Subject.Contains("Review"); // 'Review' is key word for the search

var builder2 = new PersonalStorageQueryBuilder();
builder2.Subject.Contains("Error"); // 'Error' is also key word for the search

var queryBuilder = new PersonalStorageQueryBuilder();
queryBuilder.Or(builder1.GetQuery(), builder2.GetQuery()); // message subjects must contain 'Review' or 'Error' words

using (var storage = PersonalStorage.FromFile("example.pst"))
{
    var folderInfo = storage.RootFolder.GetSubFolder("Inbox");
    var messageInfos = folderInfo.GetContents(queryBuilder.GetQuery());

    foreach (var messageInfo in messageInfos)
    {
        Console.WriteLine(messageInfo.Subject);
    }
}
```

## **Mover elementos a otras carpetas del archivo PST**

Aspose.Email permite mover elementos de una carpeta de origen a otra carpeta del mismo archivo de almacenamiento personal (PST). Esto incluye:

- Mover una carpeta especificada a una nueva carpeta principal.
- Mover un mensaje específico a una nueva carpeta.
- Mover el contenido a una nueva carpeta.
- Mover subcarpetas a una nueva carpeta principal.

El siguiente fragmento de código muestra cómo mover elementos como mensajes y carpetas de una carpeta de origen a otra carpeta del mismo archivo PST.

```csharp
// For complete examples and data files, please go to https://github.com/aspose-email/Aspose.Email-for-.NET

using(PersonalStorage personalStorage = PersonalStorage.FromFile("test.pst"))
{
    FolderInfo inbox = personalStorage.GetPredefinedFolder(StandardIpmFolder.Inbox);
    FolderInfo deleted = personalStorage.GetPredefinedFolder(StandardIpmFolder.DeletedItems);
    FolderInfo subfolder = inbox.GetSubFolder("Subfolder");

    // Move folder and message to the Deleted Items
    personalStorage.MoveItem(subfolder, deleted);
    MessageInfoCollection contents = subfolder.GetContents();
    personalStorage.MoveItem(contents[0], deleted);

    // Move all inbox subfolders and subfolder contents to the Deleted Items
    inbox.MoveSubfolders(deleted);
    subfolder.MoveContents(deleted);
}
```
## **Combinar y dividir archivos PST**

El ejemplo de código que aparece a continuación describe el proceso de división de un archivo:

1. En primer lugar, utiliza el [FromFile](https://reference.aspose.com/email/net/aspose.email.storage.pst/personalstorage/fromfile/#fromfile) método del [PersonalStorage](https://reference.aspose.com/email/net/aspose.email.storage.pst/personalstorage/#personalstorage-class) clase para especificar el nombre del archivo.

2. Luego, llama al [StorageProcessedEventHandler](https://reference.aspose.com/email/net/aspose.email.storage.pst/storageprocessedeventhandler/#storageprocessedeventhandler-delegate) delegue para gestionar un evento StorageProcessed.

3. The [StorageProcessingEventArgs]() la clase proporciona datos para el evento PersonalStorage.storageProcessing. Es [StorageProcessingEventArgs.FileName](https://reference.aspose.com/email/net/aspose.email.storage.pst/storageprocessedeventargs/filename/#storageprocessedeventargsfilename-property) Esta propiedad le permite recuperar el nombre del archivo PST. Para [MergeWith](https://reference.aspose.com/email/net/aspose.email.storage.pst/personalstorage/mergewith/#mergewith_1) método será un nombre del pst actual que se fusionará con el principal, y para [SplitInto](https://reference.aspose.com/email/net/aspose.email.storage.pst/personalstorage/splitinto/#splitinto) método será el nombre de la parte actual.

4. Finally, [SplitInto (tamaño de fragmento largo, prefijo de nombre de archivo de sección de cadena, ruta de cadena)](https://reference.aspose.com/email/net/aspose.email.storage.pst/personalstorage/splitinto/#splitinto) El método de sobrecarga iniciará la división del almacenamiento PST en partes de menor tamaño. Toma los siguientes parámetros:

- **chunkSize**: el tamaño aproximado de cada fragmento en bytes.
- **partFileNamePrefix**: El prefijo que se añadirá al nombre de archivo de cada parte del PST. Si se proporciona, el prefijo se añadirá al principio de cada nombre de archivo. Si no se proporciona (nulo o vacío), las partes del PST se crearán sin prefijo.
- **path**: la ruta de la carpeta en la que se crearán los fragmentos.

El nombre de archivo de cada parte sigue la plantilla: {prefix} part {number} .pst, donde {prefix} representa el prefijo del nombre de archivo (si se proporciona) y {number} representa el número del archivo de fragmentos.

```cs
var pst = PersonalStorage.FromFile("sample.pst");

// ...

pst.StorageProcessing += (sender, args) =>
{
    Console.WriteLine("Storage processing event raised for file: " + args.FileName);
};

// ...

pst.SplitInto(5000000, "prefix_", outputFolderPath);
```

## **Actualización de las propiedades de los mensajes en un archivo PST**

A veces es necesario actualizar ciertas propiedades de los mensajes, como cambiar el asunto, marcar la importancia del mensaje y otras similares. La actualización de un mensaje en un archivo PST, con estos cambios en las propiedades del mensaje, se puede realizar mediante el [FolderInfo.ChangeMessages](https://reference.aspose.com/email/net/aspose.email.storage.pst/folderinfo/changemessages/#changemessages/) método. En este artículo se muestra cómo actualizar los mensajes de forma masiva en un archivo PST para modificar las propiedades. En el siguiente fragmento de código, se muestra cómo actualizar las propiedades de los mensajes de forma masiva para varios mensajes de un archivo PST.

```csharp
// For complete examples and data files, please go to https://github.com/aspose-email/Aspose.Email-for-.NET
// The path to the File directory.
string dataDir = RunExamples.GetDataDir_Outlook() + "Sub.pst";

// Load the Outlook PST file
PersonalStorage personalStorage = PersonalStorage.FromFile(dataDir);
           
// Get Requierd Subfolder
FolderInfo inbox = personalStorage.RootFolder.GetSubFolder("Inbox");

// find messages having From = "someuser@domain.com"
PersonalStorageQueryBuilder queryBuilder = new PersonalStorageQueryBuilder();
queryBuilder.From.Contains("someuser@domain.com");

// Get Contents from Query
MessageInfoCollection messages = inbox.GetContents(queryBuilder.GetQuery());

// Save (MessageInfo,EntryIdString) in List
IList<string> changeList = new List<string>();
foreach (MessageInfo messageInfo in messages)
{
    changeList.Add(messageInfo.EntryIdString);
}

// Compose the new properties
MapiPropertyCollection updatedProperties = new MapiPropertyCollection();
updatedProperties.Add(MapiPropertyTag.PR_SUBJECT_W, new MapiProperty(MapiPropertyTag.PR_SUBJECT_W, Encoding.Unicode.GetBytes("New Subject")));
updatedProperties.Add(MapiPropertyTag.PR_IMPORTANCE, new MapiProperty(MapiPropertyTag.PR_IMPORTANCE, BitConverter.GetBytes((long)2)));

// update messages having From = "someuser@domain.com" with new properties
inbox.ChangeMessages(changeList, updatedProperties);
```

## **Actualización de propiedades personalizadas en un archivo PST**

A veces es necesario marcar los elementos que se procesan en el archivo PST. La API Aspose.Email permite lograr esto utilizando MapiProperty y MapInAmedProperty. Los siguientes métodos son útiles para lograrlo.

- Actor MapInamedProperty (PropertyTag largo, nameIdentifier, Guid PropertyGuid, byte [] PropertyValue)
- Actor MapInamedProperty (PropertyTag largo, NameIdentifier largo, Guid PropertyGuid, byte [] PropertyValue)
- FolderInfo.ChangeMessages (MapiPropertyCollection UpdatedProperties): cambia todos los mensajes de la carpeta
- PersonalStorage.changeMessage (string EntryId, MapiPropertyCollection UpdatedProperties): cambia las propiedades de los mensajes

```csharp
// For complete examples and data files, please go to https://github.com/aspose-email/Aspose.Email-for-.NET

public static void Run()
{
	// Load the Outlook file
	string dataDir = RunExamples.GetDataDir_Outlook() + "Sub.pst";
	using (PersonalStorage personalStorage = PersonalStorage.FromFile(dataDir))
	{
		FolderInfo testFolder = personalStorage.RootFolder.GetSubFolder("Inbox");

		// Create the collection of message properties for adding or updating
		MapiPropertyCollection newProperties = new MapiPropertyCollection();

		// Normal,  Custom and PidLidLogFlags named  property
		MapiProperty property = new MapiProperty(MapiPropertyTag.PR_ORG_EMAIL_ADDR_W,Encoding.Unicode.GetBytes("test_address@org.com"));
		MapiProperty namedProperty1 = new MapiNamedProperty(GenerateNamedPropertyTag(0, MapiPropertyType.PT_LONG),"ITEM_ID",Guid.NewGuid(),BitConverter.GetBytes(123));
		MapiProperty namedProperty2 = new MapiNamedProperty(GenerateNamedPropertyTag(1, MapiPropertyType.PT_LONG),0x0000870C,new Guid("0006200A-0000-0000-C000-000000000046"),BitConverter.GetBytes(0));
		newProperties.Add(namedProperty1.Tag, namedProperty1);
		newProperties.Add(namedProperty2.Tag, namedProperty2);
		newProperties.Add(property.Tag, property);
		testFolder.ChangeMessages(testFolder.EnumerateMessagesEntryId(), newProperties);
	}
}

private static long GenerateNamedPropertyTag(long index, MapiPropertyType dataType)
{
	return (((0x8000 | index) << 16) | (long)dataType) & 0x00000000FFFFFFFF;
}
```

## **Extraer archivos adjuntos sin extraer el mensaje completo**

La API Aspose.Email se puede usar para extraer archivos adjuntos de mensajes PST sin extraer primero el mensaje completo. Para ello, se puede utilizar el método ExtractAttachments de IEWSClient. El siguiente fragmento de código muestra cómo extraer los archivos adjuntos sin extraer un mensaje completo.

```csharp
// For complete examples and data files, please go to https://github.com/aspose-email/Aspose.Email-for-.NET
string dataDir = RunExamples.GetDataDir_Outlook();

using (PersonalStorage personalstorage = PersonalStorage.FromFile(dataDir + "Outlook.pst"))
{
    FolderInfo folder = personalstorage.RootFolder.GetSubFolder("Inbox");

    foreach (var messageInfo in folder.EnumerateMessagesEntryId())
    {
        MapiAttachmentCollection attachments = personalstorage.ExtractAttachments(messageInfo);

        if (attachments.Count != 0)
        {
            foreach (var attachment in attachments)
            {
                if (!string.IsNullOrEmpty(attachment.LongFileName))
                {
                    if (attachment.LongFileName.Contains(".msg"))
                    {
                        continue;
                    }
                    else
                    {
                        attachment.Save(dataDir + @"\Attachments\" + attachment.LongFileName);
                    }
                }
            }
        }
    }
}
```

## **Agregar archivos a PST**

La funcionalidad clave de Microsoft Outlook es administrar los correos electrónicos, los calendarios, las tareas, los contactos y las entradas del diario. Además, los archivos también se pueden agregar a una carpeta PST y el PST resultante mantiene un registro de los documentos agregados. Aspose.Email ofrece la posibilidad de agregar archivos a una carpeta de la misma manera, además de agregar mensajes, contactos, tareas y entradas de diario a PST. El siguiente fragmento de código muestra cómo agregar documentos a una carpeta PST mediante Aspose.Email.

```csharp
// For complete examples and data files, please go to https://github.com/aspose-email/Aspose.Email-for-.NET
using (PersonalStorage personalStorage = PersonalStorage.Create(dataDir + "Ps1_out.pst", FileFormatVersion.Unicode))
{
    FolderInfo folder = personalStorage.RootFolder.AddSubFolder("Files");

    // Add Document.doc file with the "IPM.Document" message class by default.
    folder.AddFile(dataDir + "attachment_1.doc", null);
}
```
