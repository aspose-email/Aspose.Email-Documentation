---
title: "Leer archivo OLM de Outlook para Mac y obtener información de carpetas y subcarpetas"
url: /es/net/read-outlook-for-mac-olm-file-and-get-folders-and-subfolders-information/
weight: 120
type: docs
---

OLM es un formato de archivo específico utilizado por Microsoft Outlook para almacenar datos locales como correos electrónicos, archivos adjuntos, notas, datos de calendario, contactos, tareas, historial y más. Los archivos OLM son compatibles únicamente con Outlook para Mac y no pueden ser abiertos o accedidos por Outlook para Windows, que utiliza el formato de archivo PST en su lugar.

## **Apertura de archivos en formato OLM**

Los archivos en formato OLM se pueden abrir de dos maneras:

- utilizando el constructor
- utilizando el método estático FromFile

Existen diferencias en el comportamiento entre estos métodos. Consulte la sección a continuación.

### **Apertura de archivos por constructor**

Para abrir un archivo, llame al constructor de la clase [OlmStorage](https://reference.aspose.com/email/net/aspose.email.storage.olm/olmstorage/) y pase el nombre completo del archivo o el flujo como argumento:

```cs
var fileName = "MyStorage.olm";
var olm = new OlmStorage(fileName);
```

### **Apertura de archivos utilizando el método estático FromFile**

Para abrir un archivo, utilice el método estático [FromFile](https://reference.aspose.com/email/net/aspose.email.storage.olm/olmstorage/fromfile/) y pase el nombre completo del archivo o el flujo como argumento:

```cs
var fileName = "MyStorage.olm";
var olm = OlmStorage.FromFile(fileName);
```

## **Obtención de carpetas**

Para acceder a la estructura de directorios de un archivo OLM, cree una instancia de la clase [OlmStorage](https://reference.aspose.com/email/net/aspose.email.storage.olm/olmstorage/) usando su constructor y pase la ruta al archivo. Una vez que el archivo esté abierto, acceda a su estructura de directorios utilizando la propiedad [FolderHierarchy](https://reference.aspose.com/email/net/aspose.email.storage.olm/olmstorage/folderhierarchy/). Esta propiedad devuelve una lista de objetos [OlmFolder](https://reference.aspose.com/email/net/aspose.email.storage.olm/olmfolder/), cada uno representando un directorio en el archivo OLM. Para explorar aún más la estructura de directorios, acceda a la propiedad [SubFolders](https://reference.aspose.com/email/net/aspose.email.storage.olm/olmfolder/subfolders/) de cada objeto, que devuelve una lista de sus subdirectorios. Al utilizar estas propiedades, puede navegar a través de toda la jerarquía de directorios del archivo OLM y acceder a todos los directorios y subdirectorios que contiene.

El siguiente ejemplo muestra la lista de todas las carpetas en orden jerárquico:

```cs
using (var olm = new OlmStorage(fileName))
{
    PrintAllFolders(olm.FolderHierarchy, string.Empty);
}

private void PrintAllFolders(List<OlmFolder> folderHierarchy, string indent)
{
    foreach (var folder in folderHierarchy)
    {
        Console.WriteLine($"{indent}{folder.Name}");
        PrintAllFolders(folder.SubFolders, indent+"-");
    }
}
```

Al utilizar el método [FromFile](https://reference.aspose.com/email/net/aspose.email.storage.olm/olmstorage/fromfile/) para abrir un archivo OLM, la propiedad [FolderHierarchy](https://reference.aspose.com/email/net/aspose.email.storage.olm/olmstorage/folderhierarchy/) no se inicializará por defecto y devolverá null. En este caso, llame al método GetFolders explícitamente para inicializar la propiedad [FolderHierarchy](https://reference.aspose.com/email/net/aspose.email.storage.olm/olmstorage/folderhierarchy/) y recuperar la lista de directorios en el archivo OLM:

```cs
using (var olm = OlmStorage.FromFile(fileName))
{
    var folders = olm.GetFolders();
}
```

También es posible obtener cualquier carpeta por nombre:

1. Llame al método [GetFolder](https://reference.aspose.com/email/net/aspose.email.clients.graph/igraphclient/getfolder/).
2. Pase el nombre de la carpeta como el primer argumento y un valor que indique si se debe ignorar la distinción entre mayúsculas y minúsculas al buscar una carpeta, como segundo parámetro.

```cs
using (var olm = OlmStorage.FromFile(fileName))
{
    // obtener la carpeta de la bandeja de entrada por nombre
    OlmFolder folder = olm.GetFolder("Inbox", true);
}
```

## **Lista de correos electrónicos**

La clase [OlmFolder](https://reference.aspose.com/email/net/aspose.email.storage.olm/olmfolder/) que representa una carpeta tiene los siguientes métodos para obtener la lista de correos electrónicos:

- [EnumerateMessages](https://reference.aspose.com/email/net/aspose.email.storage.olm/olmfolder/enumeratemessages/) implementa la iteración de correos electrónicos en una carpeta. En este caso, cada iteración devuelve un objeto [OlmMessageInfo](https://reference.aspose.com/email/net/aspose.email.storage.olm/olmmessageinfo/) que proporciona información breve sobre el correo electrónico.
- [EnumerateMapiMessages](https://reference.aspose.com/email/net/aspose.email.storage.olm/olmfolder/enumeratemapimessages/), también implementa la iteración de correos electrónicos en una carpeta, pero en este caso, cada iteración devuelve un objeto [MapiMessage](https://reference.aspose.com/email/net/aspose.email.mapi/mapimessage/) que representa el correo electrónico en sí, con todas sus propiedades.

### **Usando el método EnumerateMessages**

```cs
using (var olm = OlmStorage.FromFile(fileName))
{
    var folder = olm.GetFolder("Inbox", true);
    foreach (var messageInfo in folder.EnumerateMessages())
    {
        Console.WriteLine(messageInfo.Subject);
    }
}
```

### **Usando el método EnumerateMapiMessages**

```cs
using (var olm = OlmStorage.FromFile(fileName))
{
    var folder = olm.GetFolder("Inbox", true);

    foreach (var msg in folder.EnumerateMapiMessages())
    {
        // guardar mensaje en formato MSG
        msg.Save($"{msg.Subject}.msg");
    }
}
```

### **Otras propiedades útiles**

Otras propiedades útiles de la clase OlmFolder son: [HasMessages](https://reference.aspose.com/email/net/aspose.email.storage.olm/olmfolder/hasmessages/) y [MessageCount](https://reference.aspose.com/email/net/aspose.email.storage.olm/olmfolder/messagecount/) que devuelven la existencia de mensajes en la carpeta y su cantidad.

```cs
using (var olm = OlmStorage.FromFile(fileName))
{
    var folder = olm.GetFolder("Inbox", true);

    if (folder.HasMessages)
    {
        Console.WriteLine($"Número de mensajes: {folder.MessageCount}");
    }
}
```
### **Obtener o establecer la fecha de modificación de un mensaje**

La fecha de modificación representa la fecha y hora en que se modificó por última vez el mensaje OLM. Puede usar la propiedad [OlmMessageInfo.ModifiedDate](https://reference.aspose.com/email/net/aspose.email.storage.olm/olmmessageinfo/modifieddate/) para recuperar o actualizar el valor de la fecha de modificación de un mensaje OLM.

Aquí hay un ejemplo que demuestra el uso de la propiedad:

```cs
foreach (OlmMessageInfo messageInfo in inboxFolder.EnumerateMessages())
{
   DateTime modifiedDate = messageInfo.ModifiedDate;
}
```
## **Extracción de correos electrónicos**

La clase [OlmStorage](https://reference.aspose.com/email/net/aspose.email.storage.olm/olmstorage/) tiene el método [ExtractMapiMessage](https://reference.aspose.com/email/net/aspose.email.storage.olm/olmstorage/extractmapimessage/) que permite extraer correos electrónicos. Este método recibe un objeto [OlmMessageInfo](https://reference.aspose.com/email/net/aspose.email.storage.olm/olmmessageinfo/).

```cs
using (var olm = OlmStorage.FromFile(fileName))
{
    var folder = olm.GetFolder("Inbox", true);

    foreach (var messageInfo in folder.EnumerateMessages())
    {
        if (messageInfo.Date == DateTime.Today)
        {
            // Extrae los mensajes de hoy de la bandeja de entrada
            var msg = olm.ExtractMapiMessage(messageInfo);
        }
    }
}
```
## **Extracción de todos los elementos de un correo electrónico utilizando la API de recorrido**

Puede extraer todos los elementos de un archivo OLM de Outlook tanto como sea posible, sin lanzar excepciones, incluso si algunos datos del archivo original están corruptos. Para realizar esto, utilice el constructor [OlmStorage(TraversalExceptionsCallback callback)](https://reference.aspose.com/email/net/aspose.email.storage.olm/olmstorage/#constructors) y el método [Load(string fileName)](https://reference.aspose.com/email/net/aspose.email.storage.olm/olmstorage/load/#load_1) en lugar del método FromFile. El constructor permite definir un método de retorno de llamada.

```cs
using (var olm = new OlmStorage((exception, id) => { /* Código de manejo de excepciones. */ }))
```
El método de retorno de llamada hace que las excepciones de carga y recorrido estén disponibles.

El método [Load](https://reference.aspose.com/email/net/aspose.email.storage.olm/olmstorage/load/#load_1) devuelve 'true' si el archivo se ha cargado con éxito y es posible un recorrido posterior. Si un archivo está dañado y no es posible un recorrido, se devuelve 'false'.

```cs
if (olm.Load(fileName))
```

El siguiente fragmento de código y los pasos muestran cómo usar esta API:

1. Cree una nueva instancia de la clase [OlmStorage](https://reference.aspose.com/email/net/aspose.email.storage.olm/olmstorage/), pasando un método de manejo de excepciones para manejar cualquier excepción que se encuentre durante el proceso.
2. Cargue el archivo OLM llamando al método [Load](https://reference.aspose.com/email/net/aspose.email.storage.olm/olmstorage/load/#load_1) de la instancia de OlmStorage.
3. Si el archivo OLM se carga con éxito, obtenga la jerarquía de carpetas llamando al método [GetFolders](https://reference.aspose.com/email/net/aspose.email.storage.olm/olmstorage/getfolders/) en la instancia de OlmStorage. Esto devuelve una lista de objetos OlmFolder.
4. Llame al método ExtractItems, pasando la instancia de OlmStorage y la lista de objetos OlmFolder.
5. En el método ExtractItems, itere a través de cada carpeta en la lista de carpetas.
6. Si la carpeta contiene mensajes (correos electrónicos), imprima el nombre de la carpeta en la consola usando Console.WriteLine(folder).
7. Itere a través de los mensajes en la carpeta actual llamando al método EnumerateMessages en la instancia de OlmStorage, pasando la carpeta actual como argumento.
8. Imprima el asunto de cada mensaje en la consola usando Console.WriteLine(msg.Subject).
9. Si la carpeta tiene subcarpetas, llame recursivamente al método ExtractItems nuevamente, pasando la instancia de OlmStorage y las subcarpetas de la carpeta actual.

```cs
using (var olm = new OlmStorage((exception, id) => { /* Código de manejo de excepciones. */ }))
{
    if (olm.Load(fileName))
    {
        var folderHierarchy = olm.GetFolders();
        ExtractItems(olm, folderHierarchy);
    }
}

private static void ExtractItems(OlmStorage olm, List<OlmFolder> folders)
{
    foreach (var folder in folders)
    {
        if (folder.HasMessages)
        {
            Console.WriteLine(folder);

            foreach (var msg in olm.EnumerateMessages(folder))
            {
                Console.WriteLine(msg.Subject);
            }
        }

        if (folder.SubFolders.Count > 0)
        {
            ExtractItems(olm, folder.SubFolders);
        }
    }
}
```
## **Extraer mensajes de OLM por identificadores**

El proceso de extracción de correos electrónicos se ha vuelto más fácil con la capacidad de extraer mensajes OLM seleccionados por identificadores. Es urgente para aplicaciones que almacenan identificadores en una base de datos. Extraer mensajes bajo demanda es la forma eficiente de evitar recorrer todo el almacenamiento cada vez para encontrar un mensaje específico para extraer. La propiedad [EntryId](https://reference.aspose.com/email/net/aspose.email.storage.olm/olmmessageinfo/entryid/) de la clase [OlmMessageInfo](https://reference.aspose.com/email/net/aspose.email.storage.olm/olmmessageinfo/#olmmessageinfo-class) obtiene el identificador de entrada del mensaje. El método [ExtractMapiMessage(string id)](https://reference.aspose.com/email/net/aspose.email.storage.olm/olmstorage/extractmapimessage/#extractmapimessage_1) sobrecargado de la clase [OlmStorage](https://reference.aspose.com/email/net/aspose.email.storage.olm/olmstorage/#olmstorage-class) obtiene el mensaje de OLM. El siguiente fragmento de código demuestra el uso de estas características:

```cs
foreach (OlmMessageInfo msgInfo in olmFolder.EnumerateMessages())
{
    MapiMessage msg = storage.ExtractMapiMessage(msgInfo.EntryId);
}
```

## **Obtener la ruta de la carpeta**

También puede obtener la ruta de las carpetas en el archivo OML. Aspose.Email proporciona la propiedad [OlmFolder.Path](https://reference.aspose.com/email/net/aspose.email.storage.olm/olmfolder/path/) que devuelve la ruta de la carpeta. El siguiente fragmento de código demuestra el uso de la propiedad [OlmFolder.Path](https://reference.aspose.com/email/net/aspose.email.storage.olm/olmfolder/path/) para obtener las rutas de las carpetas en el archivo OML.

```cs
var storage = new OlmStorage("SampleOLM.olm");
PrintPath(storage, storage.FolderHierarchy);

public static void PrintPath(OlmStorage storage, List<OlmFolder> folders)
{
    foreach (OlmFolder folder in folders)
    {
        // imprimir la ruta de la carpeta actual
        Console.WriteLine(folder.Path);

        if (folder.SubFolders.Count > 0)
        {
            PrintPath(storage, folder.SubFolders);
        }
    }
}
```

## **Contar el número de elementos en la carpeta**

También puede contar el número de elementos en la carpeta. Aspose.Email proporciona la propiedad [OlmFolder.MessageCount](https://reference.aspose.com/email/net/aspose.email.storage.olm/olmfolder/messagecount/) que devuelve el número de elementos en la carpeta. El siguiente fragmento de código demuestra el uso de la propiedad [OlmFolder.MessageCount](https://reference.aspose.com/email/net/aspose.email.storage.olm/olmfolder/messagecount/) para obtener el número de elementos en las carpetas del archivo OML.

```cs
var storage = new OlmStorage("SampleOLM.olm");
PrintMessageCount(storage.FolderHierarchy);

public static void PrintMessageCount(List<OlmFolder> folders)
{
    foreach (OlmFolder folder in folders)
    {
        Console.WriteLine("Número de mensajes [" + folder.Name + "]: " + folder.MessageCount);
    }
}
```

### **Obtener el número total de elementos de OlmStorage**

La clase [OlmStorage](https://reference.aspose.com/email/net/aspose.email.storage.olm/olmstorage/) también tiene el método [GetTotalItemsCount()](https://reference.aspose.com/email/net/aspose.email.storage.olm/olmstorage/gettotalitemscount/) que devuelve el número total de elementos de mensaje contenidos en el almacenamiento OLM.
  
```cs
using (var olm = new OlmStorage("storage.olm"))
{
    var count = olm.GetTotalItemsCount();
}
```

### **Extraer mensajes de OLM por identificadores**
  
A veces es necesario extraer mensajes seleccionados por identificadores. Por ejemplo, su aplicación almacena identificadores en una base de datos y extrae un mensaje bajo demanda. Esta es la forma eficiente de evitar recorrer todo el almacenamiento cada vez para encontrar un mensaje específico a extraer. Esta característica está disponible para los almacenes OLM.

El siguiente código muestra cómo extraer mensajes de OLM por identificadores.

El código realiza los siguientes pasos:

1. Inicia un bucle foreach para iterar a través de una lista de objetos [OlmMessageInfo](https://reference.aspose.com/email/net/aspose.email.storage.olm/olmmessageinfo/) . El bucle utiliza el método [EnumerateMessages](https://reference.aspose.com/email/net/aspose.email.storage.pst/folderinfo/enumeratemessages/) del objeto olmFolder para recuperar una lista de todos los mensajes en la carpeta actual que se está iterando.
2. El bucle extrae el objeto MapiMessage correspondiente del almacenamiento llamando al método [ExtractMapiMessage(string id)](https://reference.aspose.com/email/net/aspose.email.storage.olm/olmstorage/extractmapimessage/#extractmapimessage_1) de la clase [OlmStorage](https://reference.aspose.com/email/net/aspose.email.storage.olm/olmstorage/), pasando el [EntryId](https://reference.aspose.com/email/net/aspose.email.storage.olm/olmmessageinfo/entryid/) del mensaje actual como parámetro.

El objeto MapiMessage recuperado se puede utilizar para acceder y manipular el contenido del mensaje. El bucle continúa hasta que se han procesado todos los mensajes en la carpeta.

```cs
foreach (OlmMessageInfo msgInfo in olmFolder.EnumerateMessages())
{
    MapiMessage msg = storage.ExtractMapiMessage(msgInfo.EntryId);
}
```
## **Recuperación de colores de categorías de Outlook**

Para trabajar con colores de categorías o categorías de elementos de Outlook almacenados en archivos OLM, Aspose.Email ofrece las siguientes soluciones:

- La clase [OlmItemCategory](https://reference.aspose.com/email/net/aspose.email.storage.olm/olmitemcategory/#olmitemcategory-class) - representa categorías de elementos de Outlook que están disponibles por su nombre y colores asociados, representados en formato hexadecimal.
- El método [GetCategories()](https://reference.aspose.com/email/net/aspose.email.storage.olm/olmstorage/getcategories/) de la clase [OlmStorage](https://reference.aspose.com/email/net/aspose.email.storage.olm/olmstorage/#olmstorage-class) - recupera la lista de categorías.

El siguiente ejemplo de código demuestra cómo obtener todas las categorías utilizadas del almacenamiento OML:

```cs
using (var olm = OlmStorage.FromFile("storage.olm"))
{
    var categories = olm.GetCategories();
    
    foreach (var category in categories)
    {
        Console.WriteLine($"Nombre de la categoría: {category.Name}");
        
        //El color se representa como un valor hexadecimal: #rrggbb
        Console.WriteLine($"Color de la categoría: {category.Color}");
    }
}
```
El siguiente ejemplo de código muestra cómo obtener el color de categoría de un mensaje:

```cs
foreach (var msg in olm.EnumerateMessages(folder))
{
    if (msg.Categories != null)
    {
        foreach (var msgCategory in msg.Categories)
        {
            Console.WriteLine($"Nombre de la categoría: {msgCategory}");
            var categoryColor = cat.First(c => c.Name.Equals(msgCategory, StringComparison.OrdinalIgnoreCase)).Color;
            Console.WriteLine($"Color de la categoría: {categoryColor}");
        }
    }
}
```