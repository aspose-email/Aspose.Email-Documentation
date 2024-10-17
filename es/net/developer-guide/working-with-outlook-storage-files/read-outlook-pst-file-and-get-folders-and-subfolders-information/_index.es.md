---
title: "Leer archivo PST de Outlook y obtener información sobre carpetas y subcarpetas"
url: /es/net/read-outlook-pst-file-and-get-folders-and-subfolders-information/
weight: 110
type: docs
---

Aspose.Email para .NET proporciona una API para leer archivos PST de Microsoft Outlook. Puedes cargar un archivo PST desde el disco o un flujo en una instancia de la clase [PersonalStorage](https://reference.aspose.com/email/net/aspose.email.storage.pst/personalstorage/) y obtener información sobre su contenido, por ejemplo, carpetas, subcarpetas y mensajes. La API también proporciona la capacidad de incluir carpetas de búsqueda al recorrer los mensajes de las carpetas PST.

## **Cargando un archivo PST**

Un archivo PST de Outlook puede ser cargado en una instancia de la clase [PersonalStorage](https://reference.aspose.com/email/net/aspose.email.storage.pst/personalstorage/). El siguiente fragmento de código te muestra cómo cargar el archivo PST.

{{< gist "aspose-com-gists" "6e5185a63aec6fd70d83098e82b06a32" "Examples-CSharp-Outlook-PST-LoadingPSTFile-LoadingPSTFile.cs" >}}

## **Mostrando información de carpetas**

Después de cargar el archivo PST en la clase [PersonalStorage](https://reference.aspose.com/email/net/aspose.email.storage.pst/personalstorage/), puedes obtener información sobre el nombre para mostrar del archivo, la carpeta raíz, la cantidad de subcarpetas y mensajes. El siguiente fragmento de código te muestra cómo mostrar el nombre del archivo PST, las carpetas y el número de mensajes en las carpetas.

{{< gist "aspose-com-gists" "6e5185a63aec6fd70d83098e82b06a32" "Examples-CSharp-Outlook-PST-DisplayInformationOfPSTFile-DisplayInformationOfPSTFile.cs" >}}

## **Obtener solo carpetas definidas por el usuario**

Los archivos PST/OST pueden contener carpetas que fueron creadas por un usuario. Aspose.Email proporciona la capacidad de acceder solo a carpetas definidas por el usuario utilizando la propiedad [PersonalStorageQueryBuilder.OnlyFoldersCreatedByUser](https://reference.aspose.com/email/net/aspose.email.storage.pst/personalstoragequerybuilder/onlyfolderscreatedbyuser/). Puedes establecer la propiedad [PersonalStorageQueryBuilder.OnlyFoldersCreatedByUser](https://reference.aspose.com/email/net/aspose.email.storage.pst/personalstoragequerybuilder/onlyfolderscreatedbyuser/) en **true** para obtener solo carpetas definidas por el usuario. El siguiente fragmento de código demuestra el uso de [PersonalStorageQueryBuilder.OnlyFoldersCreatedByUser](https://reference.aspose.com/email/net/aspose.email.storage.pst/personalstoragequerybuilder/onlyfolderscreatedbyuser/) para obtener carpetas definidas por el usuario.

{{< gist "aspose-com-gists" "522d47278b8ca448dc1d7eb97193322c" "Examples-CSharp-Outlook-PST-GetFoldersCreatedByUserOnly-1.cs" >}}

## **Verificando si la carpeta está en una carpeta predefinida**

Al abrir e inspeccionar las carpetas dentro de un archivo PST (Tabla de Almacenamiento Personal), puedes verificar si cada carpeta es un tipo de carpeta predefinida o una subcarpeta de un tipo de carpeta predefinida, y obtener información sobre cada carpeta.

El método [FolderInfo.GetPredefinedType](https://reference.aspose.com/email/net/aspose.email.storage.pst/folderinfo/getpredefinedtype/#folderinfogetpredefinedtype-method)(bool getForTopLevelParent) permite verificar si una carpeta es de [StandardIpmFolder](https://reference.aspose.com/email/net/aspose.email.storage.pst/standardipmfolder/). Si el parámetro *getForTopLevelParent* es verdadero, el método devuelve un valor enum [StandardIpmFolder](https://reference.aspose.com/email/net/aspose.email.storage.pst/standardipmfolder/) para la carpeta principal de nivel superior. Esto determina si la carpeta actual es una subcarpeta de una carpeta predefinida. Si el parámetro *getForTopLevelParent* es falso, devuelve un valor enum [StandardIpmFolder](https://reference.aspose.com/email/net/aspose.email.storage.pst/standardipmfolder/) para la carpeta actual.

El siguiente fragmento de código muestra cómo implementar esta función en tu proyecto:

```cs
PersonalStorage.FromFile("my.pst"))
        {
            FolderInfoCollection folders = pst.RootFolder.GetSubFolders();

            foreach (FolderInfo folder in folders)
            {
                Console.WriteLine($"Carpeta: {folder.DisplayName}");
                Console.WriteLine($"Es predefinida: {folder.GetPredefinedType(false) != StandardIpmFolder.Unspecified}");
                Console.WriteLine("-----------------------------------");
            }
        }
    }
```

## **Obteniendo y añadiendo una carpeta de fuentes RSS estándar en PersonalStorage**

Aspose.Email hace posible recuperar una referencia a la carpeta predefinida que contiene fuentes RSS. Esto puede ser útil si deseas acceder y manipular programáticamente las fuentes RSS almacenadas en un archivo PST de Outlook. Da el valor de RssFeeds al enum [StandardIpmFolder](https://reference.aspose.com/email/net/aspose.email.storage.pst/standardipmfolder/#standardipmfolder-enumeration).   

El siguiente ejemplo de código muestra cómo obtener una carpeta de fuentes RSS.

```cs
using (var pst = PersonalStorage.FromFile("my.pst", false))
{
    var rssFolder = pst.GetPredefinedFolder(StandardIpmFolder.RssFeeds);
}
```

Para agregar una carpeta de fuentes RSS, utiliza el siguiente fragmento de código:

```cs
using (var pst = PersonalStorage.Create("my.pst", FileFormatVersion.Unicode))
{
    var rssFolder = pst.CreatePredefinedFolder("RSS Feeds", StandardIpmFolder.RssFeeds);
}
```

## **Analizando carpetas buscables**

Un PST/OST puede contener carpetas buscables además del tipo normal de carpetas. Aspose.Email proporciona el enumerador [FolderKind](https://reference.aspose.com/email/net/aspose.email.storage.pst/folderkind/) para especificar los mensajes de tales carpetas de búsqueda con los métodos [EnumerateFolders](https://reference.aspose.com/email/net/aspose.email.storage.pst/folderinfo/enumeratefolders/#enumeratefolders/) y [GetSubFolders](https://reference.aspose.com/email/net/aspose.email.storage.pst/folderinfo/getsubfolders/#getsubfolders/). El siguiente fragmento de código te muestra cómo analizar carpetas buscables.

```cs
using (PersonalStorage pst = PersonalStorage.FromFile("my.pst"))
        {
            FolderInfoCollection folders = pst.RootFolder.GetSubFolders(FolderKind.Search | FolderKind.Normal);

            // Recorrer cada carpeta para mostrar el nombre de la carpeta y el número de mensajes
            foreach (FolderInfo folder in folders)
            {
                Console.WriteLine($"Carpeta: {folder.DisplayName}");

                FolderInfoCollection subFolders = folder.GetSubFolders(FolderKind.Search | FolderKind.Normal);
                foreach (FolderInfo subFolder in subFolders)
                {
                    Console.WriteLine($"Subcarpeta: {subFolder.DisplayName}");
                }
            }
        }
```

## **Recuperando información de la carpeta padre desde MessageInfo**

El siguiente fragmento de código te muestra cómo recuperar información de la carpeta padre desde [MessageInfo](https://reference.aspose.com/email/net/aspose.email.storage.pst/messageinfo/).

{{< gist "aspose-com-gists" "6e5185a63aec6fd70d83098e82b06a32" "Examples-CSharp-PST-RetreivingParentFolderInformationFromMessageInfo-RetreivingParentFolderInformationFromMessageInfo.cs" >}}

## **Recuperar una subcarpeta PST por ruta**

El método sobrecargado [FolderInfo.GetSubFolder(string name, bool ignoreCase, bool handlePathSeparator)](https://reference.aspose.com/email/net/aspose.email.storage.pst/folderinfo/getsubfolder/#getsubfolder_2) te permitirá recuperar una subcarpeta con el nombre especificado de la carpeta PST actual.

El método toma los siguientes parámetros:

- **name** - especifica el nombre de la subcarpeta a recuperar.
- **ignoreCase** - determina si la búsqueda del nombre de la subcarpeta debe ser sensible a mayúsculas y minúsculas o no. Si se establece en *true*, la búsqueda será insensible a mayúsculas y minúsculas; de lo contrario, será sensible.
- **handlePathSeparator** - especifica si el nombre de la carpeta especificada debe ser tratado como una ruta si contiene barras invertidas. Si se establece en *true*, el método interpretará el nombre de la carpeta como una ruta, intentando navegar a la subcarpeta usando la ruta. Si se establece en *false*, el método tratará el nombre de la carpeta como un nombre simple, buscando una subcarpeta con una coincidencia exacta del nombre.

El siguiente fragmento de código demuestra cómo implementar este método en tu proyecto:

```cs
var folder = pst.RootFolder.GetSubFolder(@"Inbox\Reports\Jan", true, true);
En este ejemplo, el método devolverá una carpeta llamada ‘Jan’ que se encuentra en la ruta Inbox\Reports\ relativa a la carpeta raíz.
```

## **API de recorrido de archivos PST**

La API de recorrido permite extraer todos los elementos PST tanto como sea posible, sin lanzar excepciones, incluso si algunos datos del archivo original están dañados. Los siguientes pasos muestran cómo utilizar esta API.

Usa el constructor [PersonalStorage](https://reference.aspose.com/email/net/aspose.email.storage.pst/personalstorage/) y el método [Load](https://reference.aspose.com/email/net/aspose.email.storage.pst/personalstorage/load/) en lugar del método FromFile.

El constructor permite definir un método de retorno de llamada.

```csharp
using (var currentPst = new PersonalStorage((exception, itemId) => { /* Código de manejo de excepciones. */ }))
```

Las excepciones de carga y recorrido estarán disponibles a través del método de retorno de llamada.

El método [Load](https://reference.aspose.com/email/net/aspose.email.storage.pst/personalstorage/load/) devuelve 'true' si el archivo se ha cargado correctamente y el recorrido posterior es posible. Si un archivo está dañado y no es posible recorrerlo, se devuelve 'false'.

```csharp
if (currentPst.Load(inputStream))
```

Esto permite abrir y recorrer incluso archivos PST dañados sin lanzar excepciones. Y las excepciones y elementos dañados serán manejados por el método de retorno de llamada.

```csharp
using (PersonalStorage pst = new PersonalStorage((exception, itemId) => { /* Código de manejo de excepciones. */ }))
{
    if (pst.Load(@"test.pst"))
	{
		GetAllMessages(pst, pst.RootFolder);
	}
}

private static void GetAllMessages(PersonalStorage pst, FolderInfo folder)
{
    foreach (var messageEntryId in folder.EnumerateMessagesEntryId())
    {
        MapiMessage message = pst.ExtractMessage(messageEntryId);
    }
    foreach (var subFolder in folder.GetSubFolders())
    {
        GetAllMessages(pst, subFolder);
    }
}
```