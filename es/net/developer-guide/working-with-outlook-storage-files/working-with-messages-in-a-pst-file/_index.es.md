---
title: "Trabajando con Mensajes en un Archivo PST"
url: /es/net/working-with-messages-in-a-pst-file/
weight: 30
type: docs
---

## **Agregar Mensajes a Archivos PST**

El artículo [Crear un Nuevo Archivo PST y Agregar Subcarpetas](https://docs.aspose.com/email/es/net/create-new-pst-add-sub-folders-and-messages/#creating-a-new-pst-file-and-add-subfolderss) muestra cómo crear un archivo PST y agregarle una subcarpeta. Con Aspose.Email puedes agregar mensajes a las subcarpetas de un archivo PST que hayas creado o cargado. Este artículo agrega dos mensajes desde el disco a la subcarpeta de la Bandeja de entrada de un PST. Utiliza las clases [PersonalStorage](https://reference.aspose.com/email/net/aspose.email.storage.pst/personalstorage/) y [FolderInfo](https://reference.aspose.com/email/net/aspose.email.storage.pst/folderinfo/) para agregar mensajes a los archivos PST. Para agregar mensajes a una carpeta Inbox de un archivo PST:

1. Crea una instancia de la clase FolderInfo y cárgala con el contenido de la carpeta Inbox.
2. Agrega mensajes desde el disco a la carpeta Inbox llamando al método [FolderInfo.AddMessage()](https://reference.aspose.com/email/net/aspose.email.storage.pst/folderinfo/addmessage/#addmessage). La clase [FolderInfo](https://reference.aspose.com/email/net/aspose.email.storage.pst/folderinfo/) expone el método [AddMessages](https://reference.aspose.com/email/net/aspose.email.storage.pst/folderinfo/addmessages/#addmessages) que permite agregar un gran número de mensajes a la carpeta, reduciendo las operaciones de I/O en un disco y mejorando el rendimiento. Un ejemplo completo se puede encontrar abajo, en [Agregando Mensajes en Masa](https://docs.aspose.com/email/es/net/working-with-messages-in-a-pst-file/#adding-bulk-messages).

El siguiente fragmento de código muestra cómo agregar mensajes a una subcarpeta de PST llamada Inbox.

```csharp
// Para ejemplos completos y archivos de datos, por favor visita https://github.com/aspose-email/Aspose.Email-for-.NET
// Crear nuevo PST            
PersonalStorage personalStorage = PersonalStorage.Create(dataDir, FileFormatVersion.Unicode);

// Agregar nueva carpeta "Inbox"
personalStorage.RootFolder.AddSubFolder("Inbox");

// Seleccionar la carpeta "Inbox"
FolderInfo inboxFolder = personalStorage.RootFolder.GetSubFolder("Inbox");

// Agregar algunos mensajes a la carpeta "Inbox"
inboxFolder.AddMessage(MapiMessage.FromFile(RunExamples.GetDataDir_Outlook() + "MapiMsgWithPoll.msg"));
```

### **Agregando Mensajes en Masa**

Agregar mensajes individuales a un PST implica más operaciones de I/O en un disco y, por lo tanto, puede desacelerar el rendimiento. Para mejorar el rendimiento, utiliza el método AddMessages(IEnumerable<MapiMessage> messages) en lugar del método AddMessage(MapiMessage message) para minimizar las operaciones de I/O. Además, el evento MessageAdded ocurre cuando se agrega un mensaje a la carpeta.

### **Cargando Mensajes desde el Disco**

El siguiente fragmento de código muestra cómo cargar mensajes desde un disco.

```csharp
// Para ejemplos completos y archivos de datos, por favor visita https://github.com/aspose-email/Aspose.Email-for-.NET
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

El siguiente fragmento de código muestra cómo se puede utilizar la implementación de IEnumerable.

```csharp
// Para ejemplos completos y archivos de datos, por favor visita https://github.com/aspose-email/Aspose.Email-for-.NET
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

### **Agregando Mensajes desde Otro PST**

Para agregar mensajes desde otro PST, utiliza el método [FolderInfo.EnumerateMapiMessages()](https://reference.aspose.com/email/net/aspose.email.storage.pst/folderinfo/enumeratemapimessages/#enumeratemapimessages) que devuelve IEnumerable<MapiMessage>. El siguiente fragmento de código muestra cómo agregar mensajes desde otro PST.

```csharp
// Para ejemplos completos y archivos de datos, por favor visita https://github.com/aspose-email/Aspose.Email-for-.NET
private static void BulkAddFromAnotherPst(string source)
{
    using (PersonalStorage pst = PersonalStorage.FromFile(source, false))
    using (PersonalStorage pstDest = PersonalStorage.FromFile(RunExamples.GetDataDir_Outlook() + "PersonalStorageFile1.pst"))
    {
        // Obtener la carpeta por nombre
        FolderInfo folderInfo = pst.RootFolder.GetSubFolder("Contacts");
        MessageInfoCollection ms = folderInfo.GetContents();

        // Obtener la carpeta por nombre
        FolderInfo f = pstDest.RootFolder.GetSubFolder("myInbox");
        f.MessageAdded += new MessageAddedEventHandler(OnMessageAdded);
        f.AddMessages(folderInfo.EnumerateMapiMessages());
        FolderInfo fi = pstDest.RootFolder.GetSubFolder("myInbox");
        MessageInfoCollection msgs = fi.GetContents();

    }

}

/// <summary>
/// Maneja el evento MessageAdded.
/// </summary>
static void OnMessageAdded(object sender, MessageAddedEventArgs e)
{
    Console.WriteLine(e.EntryId);
    Console.WriteLine(e.Message.Subject);
}
```

## **Obtener Información de Mensajes desde un Archivo PST de Outlook**

En el artículo [Leer Archivo PST de Outlook y Obtener Información de Carpetas y Subcarpetas](https://docs.aspose.com/email/es/net/read-outlook-pst-file-and-get-folders-and-subfolders-information/) discutimos cómo cargar un archivo PST de Outlook y navegar por sus carpetas para obtener los nombres de las carpetas y el número de mensajes en ellas. Este artículo explica cómo leer todas las carpetas y subcarpetas en el archivo PST y mostrar la información sobre los mensajes, por ejemplo, asunto, remitente y destinatarios. El archivo PST de Outlook puede contener carpetas anidadas. Para obtener información de mensajes de estas, así como de las carpetas de nivel superior, utiliza un método recursivo para leer todas las carpetas. El siguiente fragmento de código muestra cómo leer un archivo PST de Outlook y mostrar los contenidos de la carpeta y los mensajes recursivamente.

```csharp
// Para ejemplos completos y archivos de datos, por favor visita https://github.com/aspose-email/Aspose.Email-for-.NET
public static void Run()
{            
    string dataDir = RunExamples.GetDataDir_Outlook();

    // Cargar el archivo de Outlook
    string path = dataDir + "PersonalStorage.pst";

    try
    {
       
        // Cargar el archivo PST de Outlook
        PersonalStorage personalStorage = PersonalStorage.FromFile(path);

        // Obtener el formato de visualización del archivo PST
        Console.WriteLine("Formato de Visualización: " + personalStorage.Format);

        // Obtener la información de carpetas y mensajes
        FolderInfo folderInfo = personalStorage.RootFolder;

        // Llamar al método recursivo para mostrar los contenidos de la carpeta
        DisplayFolderContents(folderInfo, personalStorage);
    }
    catch (Exception ex)
    {
        Console.WriteLine(ex.Message);               
    }            
}

/// <summary>
/// Este es un método recursivo para mostrar los contenidos de una carpeta
/// </summary>
/// <param name="folderInfo"></param>
/// <param name="pst"></param>
private static void DisplayFolderContents(FolderInfo folderInfo, PersonalStorage pst)
{
    // Mostrar el nombre de la carpeta
    Console.WriteLine("Carpeta: " + folderInfo.DisplayName);
    Console.WriteLine("==================================");
    // Mostrar información sobre los mensajes dentro de esta carpeta
    MessageInfoCollection messageInfoCollection = folderInfo.GetContents();
    foreach (MessageInfo messageInfo in messageInfoCollection)
    {
        Console.WriteLine("Asunto: " + messageInfo.Subject);
        Console.WriteLine("Remitente: " + messageInfo.SenderRepresentativeName);
        Console.WriteLine("Destinatarios: " + messageInfo.DisplayTo);
        Console.WriteLine("------------------------------");
    }

    // Llamar a este método recursivamente para cada subcarpeta
    if (folderInfo.HasSubFolders == true)
    {
        foreach (FolderInfo subfolderInfo in folderInfo.GetSubFolders())
        {
            DisplayFolderContents(subfolderInfo, pst);
        }
    }
}
```

## **Extrayendo Mensajes de Archivos PST**

Este artículo muestra cómo leer archivos PST de Microsoft Outlook y extraer mensajes. Los mensajes se guardan en un disco en formato MSG. 

{{% alert %}}
**¡Pruébalo!**

Ejecuta el proyecto de la aplicación simple [ConversationThread](https://github.com/aspose-email/Aspose.Email-for-.NET/tree/master/Sample%20Apps/ConversationThread) y explora un uso interesante de las características de Aspose.Email para leer correos electrónicos de PST y encontrar hilos de conversación.
{{% /alert %}}

El siguiente fragmento de código muestra cómo extraer mensajes de un archivo PST: 
- Utiliza un método recursivo para navegar por todas las carpetas (incluyendo cualquier carpeta anidada) y llamando al método PersonalStorage.ExtractMessage() para obtener mensajes de Outlook en una instancia de la clase [MapiMessage](https://reference.aspose.com/email/net/aspose.email.mapi/mapimessage/).
- Después de eso, llama al método MapiMessage.Save() para guardar el mensaje en un disco o en un flujo en formato MSG.

```csharp
// Para ejemplos completos y archivos de datos, por favor visita https://github.com/aspose-email/Aspose.Email-for-.NET
public static void Run()
{            
    // La ruta al directorio de archivos.
    string dataDir = RunExamples.GetDataDir_Outlook();

    // Cargar el archivo de Outlook
    string path = dataDir + "PersonalStorage.pst";

    try
    {
        // cargar el archivo PST de Outlook
        PersonalStorage pst = PersonalStorage.FromFile(path);

        // obtener el formato de visualización del archivo PST
        Console.WriteLine("Formato de Visualización: " + pst.Format);

        // obtener la información de carpetas y mensajes
        FolderInfo folderInfo = pst.RootFolder;

        // Llamar al método recursivo para extraer archivos msg de cada carpeta
        ExtractMsgFiles(folderInfo, pst);
    }
    catch (Exception ex)
    {
        Console.WriteLine(ex.Message);
    }            
}

/// <summary>
/// Este es un método recursivo para mostrar los contenidos de una carpeta
/// </summary>
/// <param name="folderInfo"></param>
/// <param name="pst"></param>
private static void ExtractMsgFiles(FolderInfo folderInfo, PersonalStorage pst)
{
    // mostrar el nombre de la carpeta
    Console.WriteLine("Carpeta: " + folderInfo.DisplayName);
    Console.WriteLine("==================================");
    // recorrer todos los mensajes en esta carpeta
    MessageInfoCollection messageInfoCollection = folderInfo.GetContents();
    foreach (MessageInfo messageInfo in messageInfoCollection)
    {
        Console.WriteLine("Guardando mensaje {0} ....", messageInfo.Subject);
        // obtener el mensaje en la instancia MapiMessage
        MapiMessage message = pst.ExtractMessage(messageInfo);
        // guardar este mensaje en disco en formato msg
        message.Save(message.Subject.Replace(":", " ") + ".msg");
        // guardar este mensaje en flujo en formato msg
        MemoryStream messageStream = new MemoryStream();
        message.Save(messageStream);
    }

    // Llamar a este método recursivamente para cada subcarpeta
    if (folderInfo.HasSubFolders == true)
    {
        foreach (FolderInfo subfolderInfo in folderInfo.GetSubFolders())
        {
            ExtractMsgFiles(subfolderInfo, pst);
        }
    }
}
```

### **Guardando Mensajes Directamente de PST a Flujo**

Para guardar mensajes de un archivo PST directamente a un flujo, sin extraer el MsgInfo para los mensajes, utiliza el método SaveMessageToStream(). El siguiente fragmento de código muestra cómo guardar mensajes directamente desde PST a un flujo.

```csharp
// Para ejemplos completos y archivos de datos, por favor visita https://github.com/aspose-email/Aspose.Email-for-.NET
// La ruta al directorio de archivos.
string dataDir = RunExamples.GetDataDir_Outlook();

// Cargar el archivo de Outlook
string path = dataDir + "PersonalStorage.pst";

// Guardar mensaje en MemoryStream
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

// Guardar mensaje en archivo
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
    
    // Para enumerar el entryId de los mensajes, puedes usar el método FolderInfo.EnumerateMessagesEntryId():
    foreach (string entryId in inbox.EnumerateMessagesEntryId())
    {
        using (MemoryStream ms = new MemoryStream())
        {
            pst.SaveMessageToStream(entryId, ms);
        }
    }
}            
```

### **Extrayendo n Número de Mensajes de un Archivo PST**

El siguiente fragmento de código muestra cómo extraer un número determinado de mensajes de un PST. Simplemente proporciona el índice del primer mensaje y el número total de mensajes a extraer.

```csharp
// Para ejemplos completos y archivos de datos, por favor visita https://github.com/aspose-email/Aspose.Email-for-.NET
FolderInfo inbox = personalStorage.RootFolder.GetSubFolder("Inbox");

// Extrae mensajes comenzando desde el índice 10 y extrae un total de 100 mensajes
MessageInfoCollection messages = inbox.GetContents(10, 100);
```
### **Obteniendo el Conteo Total de Items de un Archivo PST**

Aspose.Email proporciona el método [GetTotalItemsCount()](https://reference.aspose.com/email/net/aspose.email.storage.pst/messagestore/gettotalitemscount/) de la propiedad [PersonalStorage.Store](https://reference.aspose.com/email/net/aspose.email.storage.pst/personalstorage/store/#personalstoragestore-property). Devuelve el número total de elementos de mensajes contenidos en el PST.

El siguiente fragmento de código muestra cómo recuperar el conteo total de elementos (mensajes, citas, contactos, etc.) almacenados dentro del archivo PST:

```cs
using (var pst = PersonalStorage.FromFile("my.pst", false))
{
    var count = pst.Store.GetTotalItemsCount();
}
```

## **Eliminar Items de Archivos PST**

El artículo [Agregar Mensajes a Archivos PST](https://docs.aspose.com/email/es/net/working-with-messages-in-a-pst-file/#adding-messages-to-pst-files) muestra cómo agregar mensajes a archivos PST. Por supuesto, también es posible eliminar elementos (contenidos) de un archivo PST y puede ser deseable eliminar mensajes en masa. Los elementos de un archivo PST pueden ser eliminados utilizando el método [FolderInfo.DeleteChildItem()](https://reference.aspose.com/email/net/aspose.email.storage.pst/folderinfo/deletechilditem/#deletechilditem). La API también proporciona el método [FolderInfo.DeleteChildItems()](https://reference.aspose.com/email/net/aspose.email.storage.pst/folderinfo/deletechilditem/#deletechilditem) para eliminar elementos en masa del archivo PST.

### **Eliminando Mensajes de Archivos PST**

Este artículo muestra cómo usar la clase [FolderInfo](https://reference.aspose.com/email/net/aspose.email.storage.pst/folderinfo/) para acceder a carpetas específicas en un archivo PST. Para eliminar mensajes de la subcarpeta Enviados de un PST previamente cargado o creado:

1. Crea una instancia de la clase [FolderInfo](https://reference.aspose.com/email/net/aspose.email.storage.pst/folderinfo/) y cárgala con el contenido de la subcarpeta Enviados.
1. Elimina mensajes de la carpeta Enviados llamando al método [FolderInfo.DeleteChildItem()](https://reference.aspose.com/email/net/aspose.email.storage.pst/folderinfo/deletechilditem/#deletechilditem) y pasando el [MessageInfo.EntryId](https://reference.aspose.com/email/net/aspose.email.storage.pst/folderinfo/entryid/) como parámetro. El siguiente fragmento de código muestra cómo eliminar mensajes de la subcarpeta Enviados de un archivo PST.

```csharp
// Para ejemplos completos y archivos de datos, por favor visita https://github.com/aspose-email/Aspose.Email-for-.NET
// La ruta al directorio de archivos.
string dataDir = RunExamples.GetDataDir_Outlook() + "Sub.pst";

// Cargar el archivo PST de Outlook
PersonalStorage personalStorage = PersonalStorage.FromFile(dataDir);

// Obtener la carpeta de elementos enviados
FolderInfo folderInfo = personalStorage.GetPredefinedFolder(StandardIpmFolder.SentItems);

MessageInfoCollection msgInfoColl = folderInfo.GetContents();
foreach (MessageInfo msgInfo in msgInfoColl)
{
    Console.WriteLine(msgInfo.Subject + ": " + msgInfo.EntryIdString);
    if (msgInfo.Subject.Equals("some delete condition") == true)
    {
        // Eliminar este elemento
        folderInfo.DeleteChildItem(msgInfo.EntryId);
        Console.WriteLine("Mensaje eliminado");
    }
}
```

### **Eliminando Carpetas de Archivos PST**

Puedes eliminar una carpeta PST moviéndola a la carpeta de Elementos Eliminados.

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

La ventaja de este método es que la carpeta eliminada puede ser fácilmente recuperada.

```csharp
FolderInfo someFolder = deletedItemsFolder.GetSubFolder("Some folder");
pst.MoveItem(someFolder, pst.RootFolder);
```

También puedes eliminar permanentemente una carpeta de la carpeta de Elementos Eliminados, si es necesario.

```csharp
deletedItemsFolder.DeleteChildItem(emptyFolder.EntryId);
```

El método [DeleteChildItem()](https://reference.aspose.com/email/net/aspose.email.storage.pst/folderinfo/deletechilditem/#deletechilditem) puede ser utilizado para cualquier carpeta si deseas eliminar inmediatamente y de forma permanente una subcarpeta, omitiendo la carpeta de Elementos Eliminados.

```csharp
FolderInfo someFolder = pst.RootFolder.GetSubFolder("Some folder");
pst.RootFolder.DeleteChildItem(someFolder.EntryId);
```
### **Eliminar Items de PST**

Eliminar elementos (carpetas o mensajes) de una Tabla de Almacenamiento Personal (PST) utilizando el entryId único asociado con el elemento llamando al método DeleteItem(string entryId) de la clase [PersonalStorage](https://reference.aspose.com/email/net/aspose.email.storage.pst/personalstorage/#personalstorage-class).

El siguiente fragmento de código puede ser utilizado para llamar al método DeleteItem y pasar el entryId como parámetro:

```cs
var pst = PersonalStorage.FromFile("sample.pst");

// ...

pst.DeleteItem(entryId);

// ...
```
**Por favor Nota:**

- Este método eliminará permanentemente el elemento del PST y no se puede deshacer. Ten cuidado al utilizar este método para evitar la pérdida accidental de datos.
- De acuerdo con las convenciones estándar, asegúrate de que el entryId sea válido y corresponda a un elemento existente dentro del PST. 
- De lo contrario, se lanzará una excepción. Es aconsejable tener una copia de seguridad del PST o implementar medidas adecuadas para recuperar elementos eliminados si es necesario.

### **Eliminar Items en Masa del Archivo PST**

La API de Aspose.Email puede ser utilizada para eliminar elementos en masa de un archivo PST. Esto se logra utilizando el método [DeleteChildItems()](https://reference.aspose.com/email/net/aspose.email.storage.pst/folderinfo/deletechilditems/#deletechilditems) que acepta una lista de elementos de ID de entrada que refieren a los elementos a ser eliminados. El siguiente fragmento de código muestra cómo eliminar elementos en masa de un archivo PST.

```csharp
// Para ejemplos completos y archivos de datos, por favor visita https://github.com/aspose-email/Aspose.Email-for-.NET
// La ruta al directorio de archivos.
string dataDir = RunExamples.GetDataDir_Outlook() + @"Sub.pst";
using (PersonalStorage personalStorage = PersonalStorage.FromFile(dataDir))
{
    // Obtener la subcarpeta de Inbox del archivo de Outlook
    FolderInfo inbox = personalStorage.RootFolder.GetSubFolder("Inbox");

    // Crear instancia de PersonalStorageQueryBuilder
    PersonalStorageQueryBuilder queryBuilder = new PersonalStorageQueryBuilder();

    queryBuilder.From.Contains("someuser@domain.com");
    MessageInfoCollection messages = inbox.GetContents(queryBuilder.GetQuery());
    IList<string> deleteList = new List<string>();
    foreach (MessageInfo messageInfo in messages)
    {
        deleteList.Add(messageInfo.EntryIdString);
    }

    // eliminar mensajes con From = "someuser@domain.com"
    inbox.DeleteChildItems(deleteList);
}
```

## **Buscar Mensajes y Carpetas en un PST por Criterio**

Los archivos de Almacenamiento Personal (PST) pueden contener una gran cantidad de datos. Buscar datos que cumplan con un criterio específico en tales archivos grandes, necesita incluir múltiples puntos de control en el código para filtrar la información. Con la clase [PersonalStorageQueryBuilder](https://reference.aspose.com/email/net/aspose.email.storage.pst/personalstoragequerybuilder/) Aspose.Email hace posible buscar registros específicos en un PST basado en un criterio de búsqueda especificado. Un PST puede ser buscado por mensajes basados en parámetros de búsqueda como remitente, receptor, asunto, importancia del mensaje, presencia de adjuntos, tamaño del mensaje y incluso ID del mensaje. La [PersonalStorageQueryBuilder](https://reference.aspose.com/email/net/aspose.email.storage.pst/personalstoragequerybuilder/) también puede ser utilizada para buscar subcarpetas.

### **Buscando Mensajes y Carpetas en PST**

El siguiente fragmento de código muestra cómo usar la clase [PersonalStorageQueryBuilder](https://reference.aspose.com/email/net/aspose.email.storage.pst/personalstoragequerybuilder/) para buscar contenidos en un PST basado en diferentes criterios de búsqueda. Por ejemplo, muestra cómo buscar un PST basado en:

- Importancia del mensaje.
- Clase del mensaje.
- Presencia de adjuntos.
- Tamaño del mensaje.
- Mensajes no leídos.
- Mensajes no leídos con adjuntos, y
- carpetas con un nombre de subcarpeta específico.

```csharp
// Para ejemplos completos y archivos de datos, por favor visita https://github.com/aspose-email/Aspose.Email-for-.NET
// La ruta al directorio de archivos.
string dataDir = RunExamples.GetDataDir_Outlook();

using (PersonalStorage personalStorage = PersonalStorage.FromFile(dataDir + "Outlook.pst"))
{
    FolderInfo folder = personalStorage.RootFolder.GetSubFolder("Inbox");
    PersonalStorageQueryBuilder builder = new PersonalStorageQueryBuilder();

    // Mensajes de alta importancia
    builder.Importance.Equals((int)MapiImportance.High);
    MessageInfoCollection messages = folder.GetContents(builder.GetQuery());
    Console.WriteLine("Mensajes con Alta Importancia:" + messages.Count);

    builder = new PersonalStorageQueryBuilder();
    builder.MessageClass.Equals("IPM.Note");
    messages = folder.GetContents(builder.GetQuery());
    Console.WriteLine("Mensajes con IPM.Note:" + messages.Count);

    builder = new PersonalStorageQueryBuilder();
    // Mensajes con adjuntos Y alta importancia
    builder.Importance.Equals((int)MapiImportance.High);
    builder.HasFlags(MapiMessageFlags.MSGFLAG_HASATTACH);
    messages = folder.GetContents(builder.GetQuery());
    Console.WriteLine("Mensajes con adjuntos: " + messages.Count);

    builder = new PersonalStorageQueryBuilder();
    // Mensajes con tamaño > 15 KB
    builder.MessageSize.Greater(15000);
    messages = folder.GetContents(builder.GetQuery());
    Console.WriteLine("Mensajes tamaño > 15Kb:" + messages.Count);

    builder = new PersonalStorageQueryBuilder();
    // Mensajes no leídos
    builder.HasNoFlags(MapiMessageFlags.MSGFLAG_READ);
    messages = folder.GetContents(builder.GetQuery());
    Console.WriteLine("No Leídos:" + messages.Count);

    builder = new PersonalStorageQueryBuilder();
    // Mensajes no leídos con adjuntos
    builder.HasNoFlags(MapiMessageFlags.MSGFLAG_READ);
    builder.HasFlags(MapiMessageFlags.MSGFLAG_HASATTACH);
    messages = folder.GetContents(builder.GetQuery());
    Console.WriteLine("Mensajes No Leídos con adjuntos: " + messages.Count);

    // Carpeta con nombre 'SubInbox'
    builder = new PersonalStorageQueryBuilder();
    builder.FolderName.Equals("SubInbox");
    FolderInfoCollection folders = folder.GetSubFolders(builder.GetQuery());
    Console.WriteLine("Carpeta que tiene subcarpeta: " + folders.Count);

    builder = new PersonalStorageQueryBuilder();
    // Carpetas con subcarpetas
    builder.HasSubfolders();
    folders = folder.GetSubFolders(builder.GetQuery());
    Console.WriteLine(folders.Count);
}
```

### **Buscando una Cadena en PST con el Parámetro Ignorar Mayúsculas**

El siguiente fragmento de código muestra cómo buscar una cadena en PST con el parámetro ignorar mayúsculas.

```csharp
// Para ejemplos completos y archivos de datos, por favor visita https://github.com/aspose-email/Aspose.Email-for-.NET

File.Delete("CaseSensitivity.pst");
using (PersonalStorage personalStorage = PersonalStorage.Create("CaseSensitivity.pst", FileFormatVersion.Unicode))
{
	FolderInfo folderinfo = personalStorage.CreatePredefinedFolder("Inbox", StandardIpmFolder.Inbox);
	folderinfo.AddMessage(MapiMessage.FromMailMessage(MailMessage.Load("Sample.eml")));
	PersonalStorageQueryBuilder builder = new PersonalStorageQueryBuilder();
	// IgnoreCase es Verdadero
	builder.From.Contains("automated", true);
	MailQuery query = builder.GetQuery();
	MessageInfoCollection coll = folderinfo.GetContents(query);
	Console.WriteLine(coll.Count);
}
```

### **Buscando Asuntos de Mensajes por Múltiples Palabras Clave en un Archivo PST**

Puedes usar el método [MailQueryBuilder.Or](https://reference.aspose.com/email/net/aspose.email.tools.search/mailquerybuilder/or/#or) para encontrar mensajes con un asunto que contenga al menos una de las palabras especificadas como se muestra a continuación:

```csharp
// Para ejemplos completos y archivos de datos, por favor visita https://github.com/aspose-email/Aspose.Email-for-.NET

var builder1 = new PersonalStorageQueryBuilder();
builder1.Subject.Contains("Review"); // 'Review' es la palabra clave para la búsqueda

var builder2 = new PersonalStorageQueryBuilder();
builder2.Subject.Contains("Error"); // 'Error' también es una palabra clave para la búsqueda

var queryBuilder = new PersonalStorageQueryBuilder();
queryBuilder.Or(builder1.GetQuery(), builder2.GetQuery()); // los asuntos de los mensajes deben contener las palabras 'Review' o 'Error'

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

## **Mover Items a Otras Carpetas del Archivo PST**

Aspose.Email hace posible mover elementos de una carpeta fuente a otra carpeta en el mismo archivo de Almacenamiento Personal (PST). Esto incluye:

- Mover una carpeta especificada a una nueva carpeta padre.
- Mover mensajes especificados a una nueva carpeta.
- Mover contenidos a una nueva carpeta.
- Mover subcarpetas a una nueva carpeta padre.

El siguiente fragmento de código muestra cómo mover elementos tales como mensajes y carpetas desde una carpeta fuente a otra carpeta en el mismo archivo PST.

```csharp
// Para ejemplos completos y archivos de datos, por favor visita https://github.com/aspose-email/Aspose.Email-for-.NET

using(PersonalStorage personalStorage = PersonalStorage.FromFile("test.pst"))
{
    FolderInfo inbox = personalStorage.GetPredefinedFolder(StandardIpmFolder.Inbox);
    FolderInfo deleted = personalStorage.GetPredefinedFolder(StandardIpmFolder.DeletedItems);
    FolderInfo subfolder = inbox.GetSubFolder("Subfolder");

    // Mover carpeta y mensaje a los Elementos Eliminados
    personalStorage.MoveItem(subfolder, deleted);
    MessageInfoCollection contents = subfolder.GetContents();
    personalStorage.MoveItem(contents[0], deleted);

    // Mover todas las subcarpetas de inbox y los contenidos de subcarpeta a los Elementos Eliminados
    inbox.MoveSubfolders(deleted);
    subfolder.MoveContents(deleted);
}
```
## **Combinar y Dividir Archivos PST**

El siguiente ejemplo de código describe el proceso de división de un archivo:

1. Primero, utiliza el método [FromFile](https://reference.aspose.com/email/net/aspose.email.storage.pst/personalstorage/fromfile/#fromfile) de la clase [PersonalStorage](https://reference.aspose.com/email/net/aspose.email.storage.pst/personalstorage/#personalstorage-class) para especificar el nombre del archivo.

2. Luego, llama al delegado [StorageProcessedEventHandler](https://reference.aspose.com/email/net/aspose.email.storage.pst/storageprocessedeventhandler/#storageprocessedeventhandler-delegate) para manejar un evento StorageProcessed.

3. La clase [StorageProcessingEventArgs](https://reference.aspose.com/email/net/aspose.email.storage.pst/storageprocessingepecificulturaloccasions) proporciona datos para el evento PersonalStorage.StorageProcessing. Su propiedad [StorageProcessingEventArgs.FileName](https://reference.aspose.com/email/net/aspose.email.storage.pst/storageprocessingepecificulturaloccasions/filename/#storageprocessingepecificulturaloccasions) permite recuperar el nombre del archivo PST. Para el método [MergeWith](https://reference.aspose.com/email/net/aspose.email.storage.pst/personalstorage/mergewith/#mergewith_1) será el nombre del PST actual que se fusionará con el principal, y para el método [SplitInto](https://reference.aspose.com/email/net/aspose.email.storage.pst/personalstorage/splitinto/#splitinto) será el nombre de la parte actual.

4. Por último, el método sobrecargado [SplitInto(long chunkSize, string partFileNamePrefix, string path)](https://reference.aspose.com/email/net/aspose.email.storage.pst/personalstorage/splitinto/#splitinto) lanzará la división del almacenamiento PST en partes de tamaño más pequeño. Acepta los siguientes parámetros:

- **chunkSize**: El tamaño aproximado de cada parte en bytes.
- **partFileNamePrefix**: El prefijo que se agregará al nombre del archivo de cada parte del PST. Si se proporciona, el prefijo se agregará al inicio de cada nombre de archivo. Si no se proporciona (nulo o vacío), las partes del PST se crearán sin un prefijo.
- **path**: La ruta de la carpeta donde se crearán los fragmentos.

El nombre de archivo de cada parte sigue la plantilla: {prefix}part{number}.pst, donde {prefix} representa el prefijo del nombre del archivo (si se proporciona), y {number} representa el número del archivo de fragmento.

```cs
var pst = PersonalStorage.FromFile("sample.pst");

// ...

pst.StorageProcessing += (sender, args) =>
{
    Console.WriteLine("Evento de procesamiento de almacenamiento levantado para el archivo: " + args.FileName);
};

// ...

pst.SplitInto(5000000, "prefix_", outputFolderPath);
```

## **Actualizar Propiedades de Mensajes en un Archivo PST**

A veces es necesario actualizar ciertas propiedades de los mensajes, como cambiar el asunto, marcar la importancia del mensaje y similares. Actualizar un mensaje en un archivo PST, con tales cambios en las propiedades del mensaje, se puede lograr utilizando el método [FolderInfo.ChangeMessages](https://reference.aspose.com/email/net/aspose.email.storage.pst/folderinfo/changemessages/#changemessages/). Este artículo muestra cómo actualizar mensajes en masa en un archivo PST para cambios en las propiedades. El siguiente fragmento de código muestra cómo actualizar propiedades de mensajes en modo masivo para múltiples mensajes en un archivo PST.

```csharp
// Para ejemplos completos y archivos de datos, por favor visita https://github.com/aspose-email/Aspose.Email-for-.NET
// La ruta al directorio de archivos.
string dataDir = RunExamples.GetDataDir_Outlook() + "Sub.pst";

// Cargar el archivo PST de Outlook
PersonalStorage personalStorage = PersonalStorage.FromFile(dataDir);
            
// Obtener la subcarpeta requerida 
FolderInfo inbox = personalStorage.RootFolder.GetSubFolder("Inbox");

// encontrar mensajes con From = "someuser@domain.com"
PersonalStorageQueryBuilder queryBuilder = new PersonalStorageQueryBuilder();
queryBuilder.From.Contains("someuser@domain.com");

// Obtener contenidos de la consulta
MessageInfoCollection messages = inbox.GetContents(queryBuilder.GetQuery());

// Guardar (MessageInfo,EntryIdString) en la lista
IList<string> changeList = new List<string>();
foreach (MessageInfo messageInfo in messages)
{
    changeList.Add(messageInfo.EntryIdString);
}

// Componer las nuevas propiedades
MapiPropertyCollection updatedProperties = new MapiPropertyCollection();
updatedProperties.Add(MapiPropertyTag.PR_SUBJECT_W, new MapiProperty(MapiPropertyTag.PR_SUBJECT_W, Encoding.Unicode.GetBytes("Nuevo Asunto")));
updatedProperties.Add(MapiPropertyTag.PR_IMPORTANCE, new MapiProperty(MapiPropertyTag.PR_IMPORTANCE, BitConverter.GetBytes((long)2)));

// actualizar mensajes con From = "someuser@domain.com" con nuevas propiedades
inbox.ChangeMessages(changeList, updatedProperties);
```

## **Actualizar Propiedades Personalizadas en un Archivo PST**

A veces es necesario marcar elementos que han sido procesados dentro del archivo PST. La API de Aspose.Email permite lograr esto utilizando MapiProperty y MapiNamedProperty. Los siguientes métodos son útiles para lograr esto.

- ctor MapiNamedProperty(long propertyTag, string nameIdentifier, Guid propertyGuid, byte[] propertyValue)
- ctor MapiNamedProperty(long propertyTag, long nameIdentifier, Guid propertyGuid, byte[] propertyValue)
- FolderInfo.ChangeMessages(MapiPropertyCollection updatedProperties) - cambia todos los mensajes en la carpeta
- PersonalStorage.ChangeMessage(string entryId, MapiPropertyCollection updatedProperties) - cambia las propiedades del mensaje

```csharp
// Para ejemplos completos y archivos de datos, por favor visita https://github.com/aspose-email/Aspose.Email-for-.NET

public static void Run()
{
	// Cargar el archivo de Outlook
	string dataDir = RunExamples.GetDataDir_Outlook() + "Sub.pst";
	using (PersonalStorage personalStorage = PersonalStorage.FromFile(dataDir))
	{
		FolderInfo testFolder = personalStorage.RootFolder.GetSubFolder("Inbox");

		// Crear la colección de propiedades del mensaje para agregar o actualizar
		MapiPropertyCollection newProperties = new MapiPropertyCollection();

		// Propiedad normal, personalizada y PidLidLogFlags
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

## **Extraer Adjuntos sin Extraer el Mensaje Completo**

La API de Aspose.Email puede ser utilizada para extraer adjuntos de mensajes PST sin extraer primero el mensaje completo. El método ExtractAttachments de IEWSClient puede ser utilizado para esto. El siguiente fragmento de código muestra cómo extraer adjuntos sin extraer un mensaje completo.

```csharp
// Para ejemplos completos y archivos de datos, por favor visita https://github.com/aspose-email/Aspose.Email-for-.NET
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

## **Agregar Archivos a PST**

La funcionalidad clave de Microsoft Outlook es gestionar correos electrónicos, calendarios, tareas, contactos y entradas de diario. Además, los archivos también pueden ser agregados a una carpeta PST y el PST resultante mantiene un registro de los documentos agregados. Aspose.Email ofrece la facilidad de agregar archivos a una carpeta de la misma manera que se agregan mensajes, contactos, tareas y entradas de diario al PST. El siguiente fragmento de código muestra cómo agregar documentos a una carpeta PST utilizando Aspose.Email.

```csharp
// Para ejemplos completos y archivos de datos, por favor visita https://github.com/aspose-email/Aspose.Email-for-.NET
using (PersonalStorage personalStorage = PersonalStorage.Create(dataDir + "Ps1_out.pst", FileFormatVersion.Unicode))
{
    FolderInfo folder = personalStorage.RootFolder.AddSubFolder("Files");

    // Agregar el archivo Document.doc con la clase de mensaje "IPM.Document" por defecto.
    folder.AddFile(dataDir + "attachment_1.doc", null);
}
```