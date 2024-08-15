---
title: "Crear un nuevo PST, agregar subcarpetas y mensajes"
url: /es/net/create-new-pst-add-sub-folders-and-messages/
weight: 10
type: docs
---


Además de analizar un archivo PST existente, Aspose.Email proporciona los medios para crear un archivo PST desde cero. Este artículo muestra cómo crear un archivo PST de Outlook y agregarle una subcarpeta.

1. [Creación de un nuevo archivo PST](#creating-a-new-pst-file).
1. [Cambiar la clase de contenedor de una carpeta](#changing-a-folders-container-class).
1. [Agregue mensajes masivos con un rendimiento mejorado](#add-bulk-messages-with-improved-performance)

## **Crear un nuevo archivo PST**

Usa el [PersonalStorage](https://reference.aspose.com/email/net/aspose.email.storage.pst/personalstorage/) clase para crear un archivo PST en alguna ubicación de un disco local. Para crear un archivo PST desde cero:

1. Cree un PST con el [PersonalStorage.Create()](https://reference.aspose.com/email/net/aspose.email.storage.pst/personalstorage/create/#create/) method.
1. Agregue una subcarpeta a la raíz del archivo PST; para ello, acceda a la carpeta raíz y, a continuación, llame al [AddSubFolder](https://reference.aspose.com/email/net/aspose.email.storage.pst/folderinfo/addsubfolder/#addsubfolder/) method.

El siguiente fragmento de código muestra cómo crear un archivo PST y agregar una subcarpeta denominada Bandeja de entrada.

```csharp
// Create new PST
using var pst = PersonalStorage.Create(path, FileFormatVersion.Unicode);

// Add new folder "Test"
pst.RootFolder.AddSubFolder("Inbox");
```
## **Comprobación de la coincidencia de clases de contenedor al agregar una carpeta a PST**

Al crear nuevas carpetas o agregar elementos a las carpetas existentes, es importante asegurarse de que la clase contenedora del nuevo elemento o carpeta esté alineada con la clase contenedora de la carpeta principal para mantener la jerarquía organizativa dentro del archivo de almacenamiento PST. Para ello, Aspose.Email cuenta con [EnforceContainerClassMatching](https://reference.aspose.com/email/net/aspose.email.storage.pst/foldercreationoptions/enforcecontainerclassmatching/) propiedad del [FolderCreationOptions](https://reference.aspose.com/email/net/aspose.email.storage.pst/foldercreationoptions/#foldercreationoptions-class) clase. La propiedad especifica si se debe forzar la comparación de la clase contenedora de la carpeta que se está añadiendo con la clase de contenedor de la carpeta principal. Si se establece en «true», se generará una excepción si las clases de contenedor no coinciden. El valor predeterminado es «falso».

El siguiente ejemplo de código demuestra el uso del [EnforceContainerClassMatching](https://reference.aspose.com/email/net/aspose.email.storage.pst/foldercreationoptions/enforcecontainerclassmatching/) propiedad para controlar si se debe lanzar una excepción al agregar carpetas con clases de contenedor que no coinciden:

```cs
using (var pst = PersonalStorage.Create("storage.pst", FileFormatVersion.Unicode))
{
    // Create a standard Contacts folder with the IPF.Contacts container class.
    var contacts = pst.CreatePredefinedFolder("Contacts", StandardIpmFolder.Contacts);
   
    // An exception will not arise. EnforceContainerClassMatching is false by default.
    contacts.AddSubFolder("Subfolder1", "IPF.Note");
   
    // An exception will occur as the container class of the subfolder being added (IPF.Note)
    // does not match the container class of the parent folder (IPF.Contact).
    contacts.AddSubFolder("Subfolder3", new FolderCreationOptions {EnforceContainerClassMatching = true, ContainerClass = "IPF.Note"});
}
```

>Nota: Asegúrese de gestionar correctamente las excepciones al imponer la coincidencia de clases de contenedor para evitar un comportamiento inesperado durante la creación de carpetas en PST.

## **Cambiar la clase de contenedor de carpetas**

A veces es necesario cambiar la clase del contenedor de la carpeta. Un ejemplo común es cuando se agregan mensajes de diferentes tipos (citas, mensajes, etc.) a la misma carpeta. En estos casos, es necesario cambiar la clase de carpeta para que todos los elementos de la carpeta se muestren correctamente. El siguiente fragmento de código muestra cómo cambiar la clase contenedora de una carpeta en PST para este fin.

```csharp
using var pst = PersonalStorage.FromFile("PersonalStorage1.pst);
var folder = pst.RootFolder.GetSubFolder("Inbox");

folder.ChangeContainerClass("IPF.Note");
```

## **Agregue mensajes masivos con un rendimiento mejorado**

Agregar mensajes individuales a un PST implica más operaciones de E/S en el disco y puede ralentizar el rendimiento. Para mejorar el rendimiento, se pueden agregar mensajes al PST de forma masiva para minimizar las operaciones de E/S.
El [AddMessages](https://reference.aspose.com/email/net/aspose.email.storage.pst/folderinfo/addmessages/) El método le permite agregar mensajes de forma masiva y se puede usar en los siguientes escenarios. Además, el [MessageAdded](https://reference.aspose.com/email/net/aspose.email.storage.pst/folderinfo/messageadded/) el evento se produce cuando se agrega un mensaje a la carpeta.

### **Agregar mensajes de otro PST**

Para agregar mensajes de otro PST, utilice la [FolderInfo.EnumerateMapiMessages](https://reference.aspose.com/email/net/aspose.email.storage.pst/folderinfo/enumeratemapimessages/) método que devuelve `IEnumerable<MapiMessage>`:

```csharp
using var srcPst = PersonalStorage.FromFile(@"source.pst", false);
using var destPst = PersonalStorage.FromFile(@"destination.pst");

// Get the folder by name
var srcFolder = srcPst.RootFolder.GetSubFolder("SomeFolder");
var destFolder = destPst.RootFolder.GetSubFolder("SomeFolder");

destFolder.MessageAdded += new MessageAddedEventHandler(OnMessageAdded);
destFolder.AddMessages(srcFolder.EnumerateMapiMessages());


// Handles the MessageAdded event.
static void OnMessageAdded(object sender, MessageAddedEventArgs e)
{
    Console.WriteLine($"Added: {e.EntryId}");
}
```

### **Agregar mensajes desde el directorio**

Para agregar mensajes desde el directorio, cree el `GetMessages(string pathToDir)` método iterador con nombre que devuelve `IEnumerable<MapiMessage>`:

```csharp
using var pst = PersonalStorage.FromFile(@"storage.pst");
var folder = pst.RootFolder.GetSubFolder("SomeFolder");
folder.MessageAdded += OnMessageAdded;
folder.AddMessages(GetMessages(@"MessageDirectory"));

// Named iterator method to read messages from directory.
static IEnumerable<MapiMessage> GetMessages(string pathToDir)
{
    string[] files = Directory.GetFiles(pathToDir, "*.msg");

    foreach (var file in files)
    {
        yield return MapiMessage.Load(file);
    }
}

// Handles the MessageAdded event.
static void OnMessageAdded(object sender, MessageAddedEventArgs e)
{
    Console.WriteLine($"Added: {e.EntryId}");
}
```

