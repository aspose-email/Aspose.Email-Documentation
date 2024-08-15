---
title: "Lea la información sobre archivos OLM de Outlook para Mac y obtenga carpetas y subcarpetas"
url: /es/net/read-outlook-for-mac-olm-file-and-get-folders-and-subfolders-information/
weight: 120
type: docs
---

OLM es un formato de archivo específico utilizado por Microsoft Outlook para almacenar datos locales como correos electrónicos, archivos adjuntos, notas, datos de calendario, contactos, tareas, historial y más. Los archivos OLM solo son compatibles con Outlook para Mac y Outlook para Windows no puede abrirlos ni acceder a ellos, ya que utiliza el formato de archivo PST en su lugar.

## **Apertura de archivos en formato OLM**

Los archivos en formato OLM se pueden abrir de dos maneras:

- uso del constructor
- uso del método estático FromFile

Hay diferencias de comportamiento entre estos métodos. Consulte la sección siguiente.

### **Apertura de archivos por constructor**

Para abrir un archivo, llame al constructor del [OlmStorage](https://reference.aspose.com/email/net/aspose.email.storage.olm/olmstorage/) clase y pasarle el nombre completo del archivo o la secuencia como argumento:

```cs
var fileName = "MyStorage.olm";
var olm = new OlmStorage(fileName);
```

### **Abrir archivos mediante el método estático fromFile**

Para abrir un archivo, utilice el método estático [FromFile](https://reference.aspose.com/email/net/aspose.email.storage.olm/olmstorage/fromfile/) y pásale el nombre completo del archivo o la secuencia como argumento:

```cs
var fileName = "MyStorage.olm";
var olm = OlmStorage.FromFile(fileName);
```

## **Obtención de carpetas**

Para acceder a la estructura de directorios de un archivo OLM, cree una instancia del [OlmStorage](https://reference.aspose.com/email/net/aspose.email.storage.olm/olmstorage/) clase usando su constructor y pasando la ruta al archivo.
Una vez abierto el archivo, acceda a su estructura de directorios mediante [FolderHierarchy](https://reference.aspose.com/email/net/aspose.email.storage.olm/olmstorage/folderhierarchy/) propiedad. Esta propiedad devuelve una lista de [OlmFolder](https://reference.aspose.com/email/net/aspose.email.storage.olm/olmfolder/) objetos, cada uno de los cuales representa un directorio del archivo OLM.
Para explorar más a fondo la estructura de directorios, acceda al [SubFolders](https://reference.aspose.com/email/net/aspose.email.storage.olm/olmfolder/subfolders/) propiedad de cada objeto, que devuelve una lista de sus subdirectorios. Al utilizar estas propiedades, puede navegar por toda la jerarquía de directorios del archivo OLM y acceder a todos los directorios y subdirectorios que contiene.

El ejemplo siguiente muestra la lista de todas las carpetas en orden jerárquico:

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

Al usar el [FromFile](https://reference.aspose.com/email/net/aspose.email.storage.olm/olmstorage/fromfile/) método para abrir un archivo OLM, el [FolderHierarchy](https://reference.aspose.com/email/net/aspose.email.storage.olm/olmstorage/folderhierarchy/) la propiedad no se inicializará de forma predeterminada y devolverá un valor nulo. En este caso, llame al método getFolders de forma explícita para inicializar el [FolderHierarchy](https://reference.aspose.com/email/net/aspose.email.storage.olm/olmstorage/folderhierarchy/) propiedad y recupere la lista de directorios del archivo OLM:

```cs
using (var olm = OlmStorage.FromFile(fileName))
{
    var folders = olm.GetFolders();
}
```

Además, es posible obtener cualquier carpeta por nombre:

1. Call [GetFolder](https://reference.aspose.com/email/net/aspose.email.clients.graph/igraphclient/getfolder/) method.
2. Pase el nombre de la carpeta como primer argumento y valor, que muestra si se debe ignorar la distinción entre mayúsculas y minúsculas al buscar una carpeta, como segundo parámetro.

```cs
using (var olm = OlmStorage.FromFile(fileName))
{
    // get inbox folder by name
    OlmFolder folder = olm.GetFolder("Inbox", true);
}
```

## **Lista de correos electrónicos**

[OlmFolder](https://reference.aspose.com/email/net/aspose.email.storage.olm/olmfolder/) class, que representa una carpeta, tiene los siguientes métodos para obtener la lista de correos electrónicos:

- [EnumerateMessages](https://reference.aspose.com/email/net/aspose.email.storage.olm/olmfolder/enumeratemessages/) implementa la iteración de correos electrónicos en una carpeta. En este caso, cada iteración devuelve [OlmMessageInfo](https://reference.aspose.com/email/net/aspose.email.storage.olm/olmmessageinfo/) objeto, que proporciona información breve sobre el correo electrónico.
- [EnumerateMapiMessages](https://reference.aspose.com/email/net/aspose.email.storage.olm/olmfolder/enumeratemapimessages/), también implementa la iteración de correos electrónicos en una carpeta, pero en este caso, cada iteración devuelve [MapiMessage](https://reference.aspose.com/email/net/aspose.email.mapi/mapimessage/) objeto, que representa el propio correo electrónico, con todas las propiedades.

### **Uso del método EnumerateMessages**

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

### **Uso del método EnumerateMapiMessages**

```cs
using (var olm = OlmStorage.FromFile(fileName))
{
    var folder = olm.GetFolder("Inbox", true);

    foreach (var msg in folder.EnumerateMapiMessages())
    {
        // save message in MSG format
        msg.Save($"{msg.Subject}.msg");
    }
}
```

### **Otras propiedades útiles**

Las otras propiedades útiles de la clase OLMFolder son: [HasMessages](https://reference.aspose.com/email/net/aspose.email.storage.olm/olmfolder/hasmessages/) and [MessageCount](https://reference.aspose.com/email/net/aspose.email.storage.olm/olmfolder/messagecount/) propiedades, que devuelven la presencia de los mensajes en la carpeta y su recuento.

```cs
using (var olm = OlmStorage.FromFile(fileName))
{
    var folder = olm.GetFolder("Inbox", true);

    if (folder.HasMessages)
    {
        Console.WriteLine($"Message count: {folder.MessageCount}");
    }
}
```
### **Obtener o establecer la fecha de modificación de un mensaje**

La fecha de modificación representa la fecha y la hora en que se modificó por última vez el mensaje de OLM. Puede utilizar el [OlmMessageInfo.ModifiedDate](https://reference.aspose.com/email/net/aspose.email.storage.olm/olmmessageinfo/modifieddate/) propiedad para recuperar o actualizar el valor de fecha de modificación de un mensaje de OLM.

Este es un ejemplo que demuestra el uso de la propiedad:

```cs
foreach (OlmMessageInfo messageInfo in inboxFolder.EnumerateMessages())
{
   DateTime modifiedDate = messageInfo.ModifiedDate;
}
```
## **Extracción de correos electrónicos**

[OlmStorage](https://reference.aspose.com/email/net/aspose.email.storage.olm/olmstorage/) la clase tiene [ExtractMapiMessage](https://reference.aspose.com/email/net/aspose.email.storage.olm/olmstorage/extractmapimessage/) método que permite extraer correos electrónicos. Este método recibe un [OlmMessageInfo](https://reference.aspose.com/email/net/aspose.email.storage.olm/olmmessageinfo/) object.

```cs
using (var olm = OlmStorage.FromFile(fileName))
{
    var folder = olm.GetFolder("Inbox", true);

    foreach (var messageInfo in folder.EnumerateMessages())
    {
        if (messageInfo.Date == DateTime.Today)
        {
            // Extracts today's messages form Inbox
            var msg = olm.ExtractMapiMessage(messageInfo);
        }
    }
}
```
## **Extraer todos los elementos de un correo electrónico mediante la API Traversal**

Puede extraer todos los elementos de un archivo OLM de Outlook en la medida de lo posible, sin descartar excepciones, incluso si algunos datos del archivo original están dañados. Para realizar esto, utilice [OLMStorage (devolución de llamada de TraversalExceptions)](https://reference.aspose.com/email/net/aspose.email.storage.olm/olmstorage/#constructors) constructor y [Cargar (cadena FileName)](https://reference.aspose.com/email/net/aspose.email.storage.olm/olmstorage/load/#load_1) método en lugar del método fromFile. El constructor permite definir un método de devolución de llamada.

```cs
using (var olm = new OlmStorage((exception, id) => { /* Exception handling  code. */ }))
```
El método de devolución de llamada hace que estén disponibles las excepciones de carga y recorrido.

The [Load](https://reference.aspose.com/email/net/aspose.email.storage.olm/olmstorage/load/#load_1) el método devuelve 'true' si el archivo se ha cargado correctamente y es posible recorrerlo más a fondo. Si un archivo está dañado y no es posible recorrerlo, se devuelve «falso».

```cs
if (olm.Load(fileName))
```

El siguiente fragmento de código y los pasos muestran cómo usar esta API:

1. Cree una nueva instancia del [OlmStorage](https://reference.aspose.com/email/net/aspose.email.storage.olm/olmstorage/) class, pasando una llamada de manejo de excepciones para gestionar cualquier excepción encontrada durante el proceso.
2. Cargue el archivo OLM llamando al [Load](https://reference.aspose.com/email/net/aspose.email.storage.olm/olmstorage/load/#load_1) método de la instancia de OLMStorage.
3. Si el archivo OLM se ha cargado correctamente, obtenga la jerarquía de carpetas llamando al [GetFolders](https://reference.aspose.com/email/net/aspose.email.storage.olm/olmstorage/getfolders/) método en la instancia de OLMStorage. Esto devuelve una lista de objetos OLMFolder.
4. Llame al método ExtractItems y pase la instancia de OLMStorage y la lista de objetos OLMFolder.
5. En el método ExtractItems, recorra en iteración cada carpeta de la lista de carpetas.
6. Si la carpeta contiene mensajes (correos electrónicos), imprima el nombre de la carpeta en la consola mediante Console.WriteLine (folder).
7. Revisa los mensajes de la carpeta actual llamando al método EnumerateMessages en la instancia de OLMStorage y pasando la carpeta actual como argumento.
8. Imprima el asunto de cada mensaje en la consola mediante Console.writeLine (msg.Subject).
9. Si la carpeta tiene subcarpetas, vuelva a llamar de forma recursiva al método ExtractItems y pase la instancia de OLMStorage y las subcarpetas de la carpeta actual.

```cs
using (var olm = new OlmStorage((exception, id) => { /* Exception handling  code. */ }))
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
## **Extraer mensajes de OLM mediante identificadores**

El proceso de extracción del correo electrónico se ha vuelto más sencillo con la posibilidad de extraer los mensajes OLM seleccionados mediante identificadores. Es urgente que las aplicaciones almacenen los identificadores en una base de datos. La extracción de mensajes a petición es la forma eficaz de evitar tener que recorrer todo el almacenamiento cada vez que se busca un mensaje específico para extraerlo. El [EntryId](https://reference.aspose.com/email/net/aspose.email.storage.olm/olmmessageinfo/entryid/) propiedad del [OlmMessageInfo](https://reference.aspose.com/email/net/aspose.email.storage.olm/olmmessageinfo/#olmmessageinfo-class) la clase obtiene el identificador de entrada del mensaje. El sobrecargado [extractMapiMessage (identificador de cadena)](https://reference.aspose.com/email/net/aspose.email.storage.olm/olmstorage/extractmapimessage/#extractmapimessage_1) método del [OlmStorage](https://reference.aspose.com/email/net/aspose.email.storage.olm/olmstorage/#olmstorage-class) la clase recibe el mensaje de OLM. El siguiente fragmento de código muestra el uso de estas funciones:

```cs
foreach (OlmMessageInfo msgInfo in olmFolder.EnumerateMessages())
{
    MapiMessage msg = storage.ExtractMapiMessage(msgInfo.EntryId);
}
```

## **Obtener la ruta de la carpeta**

También puede obtener la ruta de las carpetas del archivo OML. Aspose.Email proporciona [OlmFolder.Path](https://reference.aspose.com/email/net/aspose.email.storage.olm/olmfolder/path/) propiedad que devuelve la ruta de la carpeta. El siguiente fragmento de código demuestra el uso de [OlmFolder.Path](https://reference.aspose.com/email/net/aspose.email.storage.olm/olmfolder/path/) propiedad para obtener las rutas de las carpetas en el archivo OML.

```cs
var storage = new OlmStorage("SampleOLM.olm");
PrintPath(storage, storage.FolderHierarchy);

public static void PrintPath(OlmStorage storage, List<OlmFolder> folders)
{
    foreach (OlmFolder folder in folders)
    {
        // print the current folder path
        Console.WriteLine(folder.Path);

        if (folder.SubFolders.Count > 0)
        {
            PrintPath(storage, folder.SubFolders);
        }
    }
}
```

## **Cuente el número de elementos de la carpeta**

También puede contar el número de elementos de la carpeta. Aspose.Email proporciona [OlmFolder.MessageCount](https://reference.aspose.com/email/net/aspose.email.storage.olm/olmfolder/messagecount/) propiedad que devuelve el número de elementos de la carpeta. El siguiente fragmento de código demuestra el uso de [OlmFolder.MessageCount](https://reference.aspose.com/email/net/aspose.email.storage.olm/olmfolder/messagecount/) propiedad para obtener el número de elementos de las carpetas del archivo OML.

```cs
var storage = new OlmStorage("SampleOLM.olm");
PrintMessageCount(storage.FolderHierarchy);

public static void PrintMessageCount(List<OlmFolder> folders)
{
    foreach (OlmFolder folder in folders)
    {
        Console.WriteLine("Message Count [" + folder.Name + "]: " + folder.MessageCount);
    }
}
```

### **Obtenga el recuento total de artículos de OLMStorage**

[OlmStorage](https://reference.aspose.com/email/net/aspose.email.storage.olm/olmstorage/) la clase también tiene [GetTotalItemsCount()](https://reference.aspose.com/email/net/aspose.email.storage.olm/olmstorage/gettotalitemscount/) método que devuelve el número total de elementos de mensaje contenidos en el almacenamiento de OLM.
 
```cs
  using (var olm = new OlmStorage("storage.olm"))
  {
     var count = olm.GetTotalItemsCount();
  }
```

### **Extraer mensajes de OLM mediante identificadores**
 
A veces es necesario extraer los mensajes seleccionados por identificadores. Por ejemplo, su aplicación almacena los identificadores en una base de datos y extrae un mensaje cuando lo solicita. Esta es la forma eficaz de evitar tener que recorrer todo el almacenamiento cada vez para encontrar un mensaje específico que extraer. Esta función está disponible para los almacenamientos OLM.

El siguiente código muestra cómo extraer mensajes de OLM mediante identificadores.

El código lleva a cabo los siguientes pasos:

1. Inicia un bucle foreach para recorrer en iteración una lista de [OlmMessageInfo](https://reference.aspose.com/email/net/aspose.email.storage.olm/olmmessageinfo/) objetos. El bucle usa el [EnumerateMessages](https://reference.aspose.com/email/net/aspose.email.storage.pst/folderinfo/enumeratemessages/) método del objeto OLMFolder para recuperar una lista de todos los mensajes de la carpeta actual que se está iterando.
2. El bucle extrae el objeto MAPIMessage correspondiente del almacenamiento llamando al [extractMapiMessage (identificador de cadena)](https://reference.aspose.com/email/net/aspose.email.storage.olm/olmstorage/extractmapimessage/#extractmapimessage_1) método de [OlmStorage](https://reference.aspose.com/email/net/aspose.email.storage.olm/olmstorage/) clase, aprobando en el [EntryId](https://reference.aspose.com/email/net/aspose.email.storage.olm/olmmessageinfo/entryid/) del mensaje actual como parámetro.

El objeto MapiMessage recuperado se puede usar para acceder al contenido del mensaje y manipularlo. El bucle continúa hasta que se hayan procesado todos los mensajes de la carpeta.

```cs
  foreach (OlmMessageInfo msgInfo in olmFolder.EnumerateMessages())
  {
      MapiMessage msg = storage.ExtractMapiMessage(msgInfo.EntryId);
  }
```
## **Recuperación de colores de categorías de Outlook**

Para trabajar con colores de categoría o categorías de elementos de Outlook almacenadas en archivos OLM, Aspose.Email ofrece las siguientes soluciones:

- [OlmItemCategory](https://reference.aspose.com/email/net/aspose.email.storage.olm/olmitemcategory/#olmitemcategory-class) clase: representa las categorías de elementos de Outlook que están disponibles por su nombre y colores asociados, representados en formato hexadecimal.
- [GetCategories()](https://reference.aspose.com/email/net/aspose.email.storage.olm/olmstorage/getcategories/) método del [OlmStorage](https://reference.aspose.com/email/net/aspose.email.storage.olm/olmstorage/#olmstorage-class) clase: recupera la lista de categorías.

El siguiente ejemplo de código muestra cómo obtener todas las categorías usadas del almacenamiento OML:

```cs
using (var olm = OlmStorage.FromFile("storage.olm"))
{
    var categories = olm.GetCategories();
   
    foreach (var category in categories)
    {
        Console.WriteLine($"Category name: {category.Name}");
       
		//Color is represented as a hexadecimal value: #rrggbb
        Console.WriteLine($"Category color: {category.Color}");
    }
}
```
El ejemplo de código que aparece a continuación muestra cómo obtener el color de una categoría de mensaje:

```cs
foreach (var msg in olm.EnumerateMessages(folder))
{
    if (msg.Categories != null)
    {
        foreach (var msgCategory in msg.Categories)
        {
            Console.WriteLine($"Category name: {msgCategory}");
            var categoryColor = cat.First(c => c.Name.Equals(msgCategory, StringComparison.OrdinalIgnoreCase)).Color;
            Console.WriteLine($"Category color: {categoryColor}");
        }
    }
}
```
