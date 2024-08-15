---
title: "Lea el archivo PST de Outlook y obtenga información sobre carpetas y subcarpetas"
url: /es/net/read-outlook-pst-file-and-get-folders-and-subfolders-information/
weight: 110
type: docs
---


Aspose.Email para.NET proporciona una API para leer archivos PST de Microsoft Outlook. Puede cargar un archivo PST desde un disco o transmitirlo a una instancia del [PersonalStorage](https://reference.aspose.com/email/net/aspose.email.storage.pst/personalstorage/) y obtenga la información sobre su contenido, por ejemplo, carpetas, subcarpetas y mensajes. La API también ofrece la capacidad de incluir carpetas de búsqueda mientras busca los mensajes de las carpetas PST.

## **Carga de un archivo PST**

Se puede cargar un archivo PST de Outlook en una instancia de [PersonalStorage](https://reference.aspose.com/email/net/aspose.email.storage.pst/personalstorage/) clase. El siguiente fragmento de código muestra cómo cargar el archivo PST.

{{< gist "aspose-com-gists" "6e5185a63aec6fd70d83098e82b06a32" "Examples-CSharp-Outlook-PST-LoadingPSTFile-LoadingPSTFile.cs" >}}

## **Visualización de la información de carpetas**

Tras cargar el archivo PST en [PersonalStorage](https://reference.aspose.com/email/net/aspose.email.storage.pst/personalstorage/) clase, puede obtener la información sobre el nombre para mostrar del archivo, la carpeta raíz, las subcarpetas y el recuento de mensajes. El siguiente fragmento de código muestra cómo mostrar el nombre del archivo PST, las carpetas y el número de mensajes de las carpetas.

{{< gist "aspose-com-gists" "6e5185a63aec6fd70d83098e82b06a32" "Examples-CSharp-Outlook-PST-DisplayInformationOfPSTFile-DisplayInformationOfPSTFile.cs" >}}

## **Obtenga solo carpetas definidas por el usuario**

Los archivos PST/OST pueden contener carpetas creadas por un usuario. Aspose.Email ofrece la posibilidad de acceder únicamente a las carpetas definidas por el usuario mediante el [PersonalStorageQueryBuilder.OnlyFoldersCreatedByUser](https://reference.aspose.com/email/net/aspose.email.storage.pst/personalstoragequerybuilder/onlyfolderscreatedbyuser/) propiedad. Puede configurar el [PersonalStorageQueryBuilder.OnlyFoldersCreatedByUser](https://reference.aspose.com/email/net/aspose.email.storage.pst/personalstoragequerybuilder/onlyfolderscreatedbyuser/) propiedad a **true** para obtener solo las carpetas definidas por el usuario. El siguiente fragmento de código demuestra el uso de [PersonalStorageQueryBuilder.OnlyFoldersCreatedByUser](https://reference.aspose.com/email/net/aspose.email.storage.pst/personalstoragequerybuilder/onlyfolderscreatedbyuser/) para obtener carpetas definidas por el usuario.

{{< gist "aspose-com-gists" "522d47278b8ca448dc1d7eb97193322c" "Examples-CSharp-Outlook-PST-GetFoldersCreatedByUserOnly-1.cs" >}}

## **Comprobar si la carpeta está en una carpeta predefinida**

Al abrir e inspeccionar las carpetas de un archivo PST (tabla de almacenamiento personal), puede comprobar si cada carpeta es un tipo de carpeta predefinido o una subcarpeta de un tipo de carpeta predefinido y obtener la información sobre cada carpeta.

The [FolderInfo.GetPredefinedType](https://reference.aspose.com/email/net/aspose.email.storage.pst/folderinfo/getpredefinedtype/#folderinfogetpredefinedtype-method)El método (bool getForTopLevelParent) permite comprobar si una carpeta es de [StandardIpmFolder](https://reference.aspose.com/email/net/aspose.email.storage.pst/standardipmfolder/). Si *getForTopLevelParent* el parámetro es verdadero, el método devuelve un [StandardIpmFolder](https://reference.aspose.com/email/net/aspose.email.storage.pst/standardipmfolder/) valor de enumeración para la carpeta principal de nivel superior. Esto determina si la carpeta actual es una subcarpeta de una carpeta predefinida. Si *getForTopLevelParent* el parámetro es falso, devuelve un [StandardIpmFolder](https://reference.aspose.com/email/net/aspose.email.storage.pst/standardipmfolder/) valor de enumeración de la carpeta actual.

El siguiente ejemplo de código muestra cómo implementar esta función en tu proyecto:

```cs
PersonalStorage.FromFile("my.pst"))
        {
            FolderInfoCollection folders = pst.RootFolder.GetSubFolders();

            foreach (FolderInfo folder in folders)
            {
                Console.WriteLine($"Folder: {folder.DisplayName}");
                Console.WriteLine($"Is predefined: {folder.GetPredefinedType(false) != StandardIpmFolder.Unspecified}");
                Console.WriteLine("-----------------------------------");
            }
        }
    }
```
## **Obtener y agregar una carpeta de fuentes RSS estándar en PersonalStorage**

Aspose.Email permite recuperar una referencia a la carpeta predefinida que contiene las fuentes RSS. Esto puede resultar útil si desea acceder mediante programación a las fuentes RSS almacenadas en un archivo PST de Outlook y manipularlas.
Asigne el valor de las fuentes RSS a [StandardIpmFolder](https://reference.aspose.com/email/net/aspose.email.storage.pst/standardipmfolder/#standardipmfolder-enumeration) enum.  

El siguiente ejemplo de código muestra cómo obtener una carpeta de fuentes RSS.

```cs
using (var pst = PersonalStorage.FromFile("my.pst", false))
{
    var rssFolder = pst.GetPredefinedFolder(StandardIpmFolder.RssFeeds);
}
```

Para agregar una carpeta de fuentes RSS, usa el siguiente fragmento de código:

```cs
using (var pst = PersonalStorage.Create("my.pst", FileFormatVersion.Unicode))
{
    var rssFolder = pst.CreatePredefinedFolder("RSS Feeds", StandardIpmFolder.RssFeeds);
}
```

## **Análisis de carpetas en las que se pueden buscar**

Un PST/OST puede contener carpetas con capacidad de búsqueda además del tipo normal de carpetas. Aspose.Email proporciona [FolderKind](https://reference.aspose.com/email/net/aspose.email.storage.pst/folderkind/) enumerador para especificar los mensajes de dichas carpetas de búsqueda con [EnumerateFolders](https://reference.aspose.com/email/net/aspose.email.storage.pst/folderinfo/enumeratefolders/#enumeratefolders/) and [GetSubFolders](https://reference.aspose.com/email/net/aspose.email.storage.pst/folderinfo/getsubfolders/#getsubfolders/) métodos. El siguiente fragmento de código muestra cómo analizar las carpetas en las que se pueden buscar.

```cs
using (PersonalStorage pst = PersonalStorage.FromFile("my.pst"))
        {
            FolderInfoCollection folders = pst.RootFolder.GetSubFolders(FolderKind.Search | FolderKind.Normal);

            // Browse through each folder to display folder name and number of messages
            foreach (FolderInfo folder in folders)
            {
                Console.WriteLine($"Folder: {folder.DisplayName}");

                FolderInfoCollection subFolders = folder.GetSubFolders(FolderKind.Search | FolderKind.Normal);
                foreach (FolderInfo subFolder in subFolders)
                {
                    Console.WriteLine($"Sub-folder: {subFolder.DisplayName}");
                }
            }
        }
```

## **Recuperar la información de la carpeta principal de MessageInfo**

El siguiente fragmento de código muestra cómo recuperar la información de la carpeta principal de [MessageInfo](https://reference.aspose.com/email/net/aspose.email.storage.pst/messageinfo/).

{{< gist "aspose-com-gists" "6e5185a63aec6fd70d83098e82b06a32" "Examples-CSharp-PST-RetreivingParentFolderInformationFromMessageInfo-RetreivingParentFolderInformationFromMessageInfo.cs" >}}

## **Recuperar una subcarpeta PST por ruta**

The [FolderInfo.getSubfolder (nombre de cadena, bool ignoreCase, bool handlePathSeparator)](https://reference.aspose.com/email/net/aspose.email.storage.pst/folderinfo/getsubfolder/#getsubfolder_2) la sobrecarga de métodos le permitirá recuperar una subcarpeta con el nombre especificado de la carpeta PST actual.

El método toma los siguientes parámetros:

- **name** - especifica el nombre de la subcarpeta que se va a recuperar.
- **ignoreCase** - determina si la búsqueda del nombre de la subcarpeta debe distinguir entre mayúsculas y minúsculas o no. Si se establece en *true*, la búsqueda no distinguirá entre mayúsculas y minúsculas; de lo contrario, distinguirá entre mayúsculas y minúsculas.
- **handlePathSeparator** - especifica si el nombre de la carpeta especificada debe tratarse como una ruta si contiene barras invertidas. Si se establece en *true*, el método interpretará el nombre de la carpeta como una ruta e intentará navegar a la subcarpeta utilizando la ruta. Si se establece en *false*, el método tratará el nombre de la carpeta como un nombre simple y buscará una subcarpeta con un nombre exacto.
 
El siguiente ejemplo de código demuestra cómo implementar este método en tu proyecto:

```cs
var folder = pst.RootFolder.GetSubFolder(@"Inbox\Reports\Jan", true, true);
In this sample, the method will return a ‘Jan’ named folder that is located at the Inbox\Reports\ path relative to the root folder.
```

## **API de recorrido de archivos PST**

La API transversal permite extraer todos los elementos de PST en la medida de lo posible, sin descartar excepciones, incluso si algunos datos del archivo original están dañados.
Los pasos siguientes muestran cómo usar esta API.

Use [PersonalStorage](https://reference.aspose.com/email/net/aspose.email.storage.pst/personalstorage/) constructor y [Load](https://reference.aspose.com/email/net/aspose.email.storage.pst/personalstorage/load/) método en lugar del método fromFile.

El constructor permite definir un método de devolución de llamada.

```csharp
using (var currentPst = new PersonalStorage((exception, itemId) => { /* Exception handling  code. */ }))
```

Las excepciones de carga y recorrido estarán disponibles mediante el método de devolución de llamada.

The [Load](https://reference.aspose.com/email/net/aspose.email.storage.pst/personalstorage/load/) el método devuelve 'true' si el archivo se ha cargado correctamente y es posible recorrerlo más a fondo. Si un archivo está dañado y no es posible recorrerlo, se devuelve «falso».

```csharp
if (currentPst.Load(inputStream))
```

Esto permite abrir y recorrer incluso archivos PST corruptos sin descartar excepciones. Además, las excepciones y los elementos corruptos se gestionarán mediante el método de devolución de llamadas.

```csharp
using (PersonalStorage pst = new PersonalStorage((exception, itemId) => { /* Exception handling  code. */ }))
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
