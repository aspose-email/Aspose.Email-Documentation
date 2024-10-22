---
title: "Crear nuevo PST, agregar subcarpetas y mensajes"
url: /es/net/crear-nuevo-pst-agregar-subcarpetas-y-mensajes/
weight: 10
type: docs
---

Además de analizar un archivo PST existente, Aspose.Email proporciona los medios para crear un archivo PST desde cero. Este artículo demuestra cómo crear un archivo PST de Outlook y agregarle una subcarpeta.

1. [Creando un nuevo archivo PST](#creando-un-nuevo-archivo-pst).
1. [Cambiando la clase contenedora de una carpeta](#cambiando-la-clase-contenedora-de-una-carpeta).
1. [Agregar mensajes en bloque con mejor rendimiento](#agregar-mensajes-en-bloque-con-mejor-rendimiento)

## **Crear un nuevo archivo PST**

Utilice la clase [PersonalStorage](https://reference.aspose.com/email/net/aspose.email.storage.pst/personalstorage/) para crear un archivo PST en alguna ubicación en un disco local. Para crear un archivo PST desde cero:

1. Cree un PST utilizando el método [PersonalStorage.Create()](https://reference.aspose.com/email/net/aspose.email.storage.pst/personalstorage/create/#create/).
1. Agregue una subcarpeta en la raíz del archivo PST accediendo a la carpeta Raíz y luego llamando al método [AddSubFolder](https://reference.aspose.com/email/net/aspose.email.storage.pst/folderinfo/addsubfolder/#addsubfolder/).

El siguiente fragmento de código muestra cómo crear un archivo PST y agregarle una subcarpeta llamada Inbox.

```csharp
// Crear nuevo PST
using var pst = PersonalStorage.Create(path, FileFormatVersion.Unicode);

// Agregar nueva carpeta "Test"
pst.RootFolder.AddSubFolder("Inbox");
```
## **Verificación de coincidencia de clase contenedora al agregar una carpeta a PST**

Al crear nuevas carpetas o agregar elementos a carpetas existentes, es importante asegurarse de que la clase contenedora del nuevo elemento o carpeta coincida con la clase contenedora de la carpeta principal para mantener la jerarquía organizativa dentro del archivo de almacenamiento PST. Para este propósito, Aspose.Email tiene la propiedad [EnforceContainerClassMatching](https://reference.aspose.com/email/net/aspose.email.storage.pst/foldercreationoptions/enforcecontainerclassmatching/) de la clase [FolderCreationOptions](https://reference.aspose.com/email/net/aspose.email.storage.pst/foldercreationoptions/#foldercreationoptions-class). La propiedad especifica si se debe forzar la verificación de la clase contenedora de la carpeta que se está agregando en comparación con la clase contenedora de la carpeta principal. Si se establece en 'true', se generará una excepción si las clases contenedoras no coinciden. El valor predeterminado es 'false'.

El siguiente ejemplo de código demuestra el uso de la propiedad [EnforceContainerClassMatching](https://reference.aspose.com/email/net/aspose.email.storage.pst/foldercreationoptions/enforcecontainerclassmatching/) para controlar si se debe lanzar una excepción al agregar carpetas con clases contenedoras que no coinciden:

```cs
using (var pst = PersonalStorage.Create("storage.pst", FileFormatVersion.Unicode))
{
    // Crear una carpeta de Contactos estándar con la clase contenedora IPF.Contacts.
    var contacts = pst.CreatePredefinedFolder("Contacts", StandardIpmFolder.Contacts);
    
    // No se generará ninguna excepción. EnforceContainerClassMatching es falso por defecto.
    contacts.AddSubFolder("Subfolder1", "IPF.Note");
    
    // Se generará una excepción ya que la clase contenedora de la subcarpeta que se está agregando (IPF.Note) 
    // no coincide con la clase contenedora de la carpeta principal (IPF.Contact).
    contacts.AddSubFolder("Subfolder3", new FolderCreationOptions {EnforceContainerClassMatching = true, ContainerClass = "IPF.Note"});
}
```

>Nota: Asegúrese de manejar correctamente las excepciones al forzar la coincidencia de clases contenedoras para evitar comportamientos inesperados durante la creación de carpetas en PST.

## **Cambio de la clase contenedora de la carpeta**

A veces es necesario cambiar la clase contenedora de la carpeta. Un ejemplo común es cuando se agregan mensajes de diferentes tipos (citas, mensajes, etc.) a la misma carpeta. En tales casos, es necesario cambiar la clase de la carpeta para que todos los elementos en la carpeta se muestren correctamente. El siguiente fragmento de código muestra cómo cambiar la clase contenedora de una carpeta en PST para este propósito.

```csharp
using var pst = PersonalStorage.FromFile("PersonalStorage1.pst");
var folder = pst.RootFolder.GetSubFolder("Inbox");

folder.ChangeContainerClass("IPF.Note");
```

## **Agregar mensajes en bloque con mejor rendimiento**

Agregar mensajes individuales a un PST implica más operaciones de I/O en el disco y puede ralentizar el rendimiento. Para mejorar el rendimiento, se pueden agregar mensajes al PST en modo de bloque para minimizar las operaciones de I/O. El método [AddMessages](https://reference.aspose.com/email/net/aspose.email.storage.pst/folderinfo/addmessages/) permite agregar mensajes en bloque y se puede usar en los siguientes escenarios. Además, el evento [MessageAdded](https://reference.aspose.com/email/net/aspose.email.storage.pst/folderinfo/messageadded/) ocurre cuando se agrega un mensaje a la carpeta.

### **Agregar mensajes desde otro PST**

Para agregar mensajes desde otro PST, utilice el método [FolderInfo.EnumerateMapiMessages](https://reference.aspose.com/email/net/aspose.email.storage.pst/folderinfo/enumeratemapimessages/) que devuelve `IEnumerable<MapiMessage>`:

```csharp
using var srcPst = PersonalStorage.FromFile(@"source.pst", false);
using var destPst = PersonalStorage.FromFile(@"destination.pst");

// Obtener la carpeta por nombre
var srcFolder = srcPst.RootFolder.GetSubFolder("SomeFolder");
var destFolder = destPst.RootFolder.GetSubFolder("SomeFolder");

destFolder.MessageAdded += new MessageAddedEventHandler(OnMessageAdded);
destFolder.AddMessages(srcFolder.EnumerateMapiMessages());

// Maneja el evento MessageAdded.
static void OnMessageAdded(object sender, MessageAddedEventArgs e)
{
    Console.WriteLine($"Agregado: {e.EntryId}");
}
```

### **Agregar mensajes desde un directorio**

Para agregar mensajes desde un directorio, cree el método iterador nombrado `GetMessages(string pathToDir)` que devuelve `IEnumerable<MapiMessage>`:

```csharp
using var pst = PersonalStorage.FromFile(@"storage.pst");
var folder = pst.RootFolder.GetSubFolder("SomeFolder");
folder.MessageAdded += OnMessageAdded;
folder.AddMessages(GetMessages(@"MessageDirectory"));

// Método iterador nombrado para leer mensajes desde el directorio.
static IEnumerable<MapiMessage> GetMessages(string pathToDir)
{
    string[] files = Directory.GetFiles(pathToDir, "*.msg");

    foreach (var file in files)
    {
        yield return MapiMessage.Load(file);
    }
}

// Maneja el evento MessageAdded.
static void OnMessageAdded(object sender, MessageAddedEventArgs e)
{
    Console.WriteLine($"Agregado: {e.EntryId}");
}
```