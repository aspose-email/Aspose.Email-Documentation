---
title: "Lea la información sobre archivos OLM de Outlook para Mac y obtenga carpetas y subcarpetas"
url: /es/python-net/read-outlook-for-mac-olm-file-and-get-folders-and-subfolders-information/
weight: 120
type: docs
---

OLM (Outlook for Mac Archive) es un formato de archivo asociado a Microsoft Outlook para Mac. Se utiliza para archivar y almacenar mensajes de correo electrónico, contactos, elementos del calendario, tareas y otros datos de Outlook en ordenadores Mac. Los archivos OLM sirven como formato de copia de seguridad o archivo, lo que permite a los usuarios guardar sus datos de Outlook para Mac para consultarlos o migrarlos en el futuro. Es importante tener en cuenta que los archivos OLM son específicos de Outlook para Mac y no son compatibles con el formato de archivo PST (tabla de almacenamiento personal) que utiliza Outlook en Windows. Si necesitas transferir datos de Outlook entre diferentes plataformas, las herramientas de conversión serán útiles. Aspose.Email ofrece este tipo de herramientas que incluyen la apertura, la lectura y otras funcionalidades para trabajar con archivos OLM.

## **Apertura de archivos en formato OLM**

Los archivos en formato OLM se pueden abrir de dos maneras:

- uso del constructor
- usando el método estático 'from_file'

### **Apertura de archivos por constructor**

Para abrir un archivo, llame al constructor del [OlmStorage](https://reference.aspose.com/email/python-net/aspose.email.storage.olm/olmstorage/#olmstorage-class) clase y pasarle el nombre completo del archivo o la secuencia como argumento:

```py
import aspose.email as ae

fileName = "my.olm"
olm = ae.storage.olm.OlmStorage(fileName)
```

### **Abrir archivos mediante el método estático fromFile**

Para abrir un archivo, utilice el método estático 'from_file' del [OlmStorage](https://reference.aspose.com/email/python-net/aspose.email.storage.olm/olmstorage/#olmstorage-class) clase y pasarle el nombre completo del archivo o la secuencia como argumento:

```py
import aspose.email as ae

fileName = "my.olm"
olm = ae.storage.olm.OlmStorage.from_file(fileName)
```

## **Obtención de carpetas**

Puede visualizar y mostrar la jerarquía de carpetas recuperada de un archivo OLM mediante la función «print_all_folders». Toma la propiedad 'folder_hierarchy' de [OlmStorage](https://reference.aspose.com/email/python-net/aspose.email.storage.olm/olmstorage/#olmstorage-class) clase y un nivel de indentación como entrada, luego recorre recursivamente la jerarquía para imprimir el nombre de cada carpeta junto con la sangría correspondiente. El ejemplo de código que aparece a continuación muestra cómo utilizar esta función para mostrar la jerarquía de carpetas desde un archivo OLM. Muestra la lista de todas las carpetas en orden jerárquico:

```py
import aspose.email as ae


def print_all_folders(folder_hierarchy, indent):
    for folder in folder_hierarchy:
        print(f"{indent}{folder.name}")
        print_all_folders(folder.sub_folders, indent + "-")

fileName = "my.olm"
olm = ae.storage.olm.OlmStorage(fileName)
print_all_folders(olm.folder_hierarchy, "")
```

El ejemplo de código anterior pretende mostrar la jerarquía de carpetas del archivo OLM mediante una función recursiva en un formato más estructurado y legible. Aspose.Email también permite acceder directamente a la estructura de carpetas desde el archivo OLM mediante el método 'get_folders () 'del [OlmStorage](https://reference.aspose.com/email/python-net/aspose.email.storage.olm/olmstorage/#olmstorage-class) class.

```py
import aspose.email as ae

fileName = "my.olm"
olm = ae.storage.olm.OlmStorage.from_file(fileName)
folders = olm.get_folders()
```

Además, es posible obtener cualquier carpeta por nombre. El siguiente ejemplo de código utiliza el método 'get_folder (name, ignore_case) 'del [OlmStorage](https://reference.aspose.com/email/python-net/aspose.email.storage.olm/olmstorage/#olmstorage-class) clase pasando el nombre de la carpeta y la distinción entre mayúsculas y minúsculas como parámetros para recuperar la carpeta por su nombre:


```py
import aspose.email as ae

fileName = "my.olm"
olm = ae.storage.olm.OlmStorage.from_file(fileName)
folder = olm.get_folder("Inbox", True)
```

## **Lista de correos electrónicos**

Los fragmentos de código que aparecen a continuación muestran cómo usar la biblioteca Aspose.Email para leer y extraer los asuntos de los correos electrónicos de un archivo de Outlook para Mac (OLM). [OlmFolder](https://reference.aspose.com/email/python-net/aspose.email.storage.olm/olmfolder/#olmfolder-class) class, que representa una carpeta, tiene los siguientes métodos para obtener la lista de correos electrónicos:

- 'enumerate_messages () ': recorre en iteración cada mensaje de correo electrónico de la carpeta. Este método devuelve los mensajes como instancias del [OlmMessageInfo](https://reference.aspose.com/email/python-net/aspose.email.storage.olm/olmmessageinfo/#olmmessageinfo-class) clase que proporciona información básica sobre cada mensaje de correo electrónico, como el asunto, el remitente, la fecha, etc.
- 'enumerate_mapi_messages () ': también recorre en iteración cada mensaje de correo electrónico de una carpeta, pero en este caso, devuelve los mensajes como instancias del [MapiMessage](https://reference.aspose.com/email/python-net/aspose.email.mapi/mapimessage/#mapimessage-class) clase que representa un mensaje de correo electrónico de una manera más detallada y específica de MAPI. Proporciona acceso a una amplia gama de propiedades y detalles del mensaje de correo electrónico, lo que permite un procesamiento más avanzado y especializado.

### **Uso del método EnumerateMessages**

```py
import aspose.email as ae

fileName = "my.olm"
olm = ae.storage.olm.OlmStorage.from_file(fileName)
folder = olm.get_folder("Inbox", True)

for message_info in folder.enumerate_messages():
    print(message_info.subject)
```

### **Uso del método EnumerateMapiMessages**

```py
import aspose.email as ae

fileName = "my.olm"
olm = ae.storage.olm.OlmStorage.from_file(fileName)
folder = olm.get_folder("Inbox", True)

for msg in folder.enumerate_mapi_messages():
    msg.save(f"{msg.subject}.msg")
```

### **Otras propiedades útiles**

Las otras propiedades útiles del [OlmFolder](https://reference.aspose.com/email/python-net/aspose.email.storage.olm/olmfolder/#olmfolder-class) las clases son:

- 'has_messages': obtiene un valor que indica si la carpeta actual tiene mensajes.
- 'message_count': obtiene el recuento de mensajes.

```py
import aspose.email as ae

fileName = "my.olm"
olm = ae.storage.olm.OlmStorage.from_file(fileName)
folder = olm.get_folder("Inbox", True)

if folder.has_messages:
   print(f"Message count: {folder.message_count}")
```

### **Obtener o establecer la fecha de modificación de un mensaje**

Puede recuperar información sobre la hora de la última modificación de un mensaje de correo electrónico. La propiedad 'modified_date' de [OlmMessageInfo](https://reference.aspose.com/email/python-net/aspose.email.storage.olm/olmmessageinfo/#olmmessageinfo-class) La clase representa la fecha y la hora en que se modificó el mensaje por última vez.

Este es un ejemplo que demuestra el uso de la propiedad:

```py
import aspose.email as ae

fileName = "my.olm"
olm = ae.storage.olm.OlmStorage.from_file(fileName)
folder = olm.get_folder("Inbox", True)

for message_info in folder.enumerate_messages():
    modifiedDate = message_info.modified_date
```

## **Extracción de correos electrónicos**

Puede recuperar los datos reales del mensaje MAPI de un almacenamiento de correo electrónico.El método 'extract_mapi_message (message_info) 'del [OlmStorage](https://reference.aspose.com/email/python-net/aspose.email.storage.olm/olmstorage/#olmstorage-class) La clase se usa para extraer el mensaje MAPI del almacenamiento en función del message_info proporcionado. 

El ejemplo de código que aparece a continuación muestra cómo utilizar este método:

```py
import aspose.email as ae

fileName = "my.olm"
olm = ae.storage.olm.OlmStorage.from_file(fileName)
folder = olm.get_folder("Inbox", True)

for message_info in folder.enumerate_messages():
    msg = olm.extract_mapi_message(message_info)
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

Para acceder a los datos de los mensajes MAPI, puede usar la propiedad 'entry_id' para obtener el identificador único (ID de entrada) de un mensaje mediante el [OlmMessageInfo](https://reference.aspose.com/email/python-net/aspose.email.storage.olm/olmmessageinfo/#olmmessageinfo-class) clase. Luego, puede utilizar el método 'extract_mapi_message (id) 'del [OlmStorage](https://reference.aspose.com/email/python-net/aspose.email.storage.olm/olmstorage/#olmstorage-class) class, pasando el ID de entrada como parámetro para recuperar el mensaje MAPI asociado a ese ID de entrada en particular. El siguiente fragmento de código muestra el uso de estas funciones:

```py

import aspose.email as ae

fileName = "my.olm"
olm = ae.storage.olm.OlmStorage.from_file(fileName)
folder = olm.get_folder("Inbox", True)

for message_info in folder.enumerate_messages():
    msg = olm.extract_mapi_message(message_info.entry_id)
```

## **Obtener la ruta de la carpeta**

También puede obtener la ruta jerárquica o la ubicación de la carpeta dentro del archivo OLM de Outlook. Aspose.Email proporciona la propiedad «ruta» del [OlmFolder](https://reference.aspose.com/email/python-net/aspose.email.storage.olm/olmfolder/#olmfolder-class) clase que devuelve la ruta de la carpeta. El siguiente fragmento de código muestra el uso de esta propiedad:

```py
import aspose.email as ae


def print_path(storage, folders):
    for folder in folders:
        # print the current folder path
        print(folder.path)

        if folder.sub_folders:
            print_path(storage, folder.sub_folders)


fileName = "my.olm"
olm = ae.storage.olm.OlmStorage(fileName)
print_path(olm, olm.folder_hierarchy)
```

## **Cuente el número de elementos de la carpeta**

Aspose.Email ofrece la posibilidad de contar el número total de mensajes de correo electrónico contenidos en la carpeta específica de un archivo OLM de Outlook. La propiedad 'message_count' de [OlmFolder](https://reference.aspose.com/email/python-net/aspose.email.storage.olm/olmfolder/#olmfolder-class) la clase devuelve el recuento total de elementos (mensajes de correo electrónico) almacenados en una carpeta específica del archivo OLM. El siguiente fragmento de código muestra el uso de esta propiedad:

```py
import aspose.email as ae


def print_message_count(folders):
    for folder in folders:
        print(f"Message Count [{folder.name}]: {folder.message_count}")


fileName = "my.olm"
olm = ae.storage.olm.OlmStorage(fileName)
print_message_count(olm.folder_hierarchy)
```

### **Obtenga el recuento total de artículos de OLMStorage**

El método 'get_total_items_count () 'del [OlmStorage](https://reference.aspose.com/email/python-net/aspose.email.storage.olm/olmstorage/#olmstorage-class) la clase devuelve el número total de elementos de mensaje contenidos en el almacenamiento de OLM.
 
```py
import aspose.email as ae

fileName = "my.olm"
olm = ae.storage.olm.OlmStorage(fileName)
count = olm.get_total_items_count()
```

## **Recuperar los colores de las categorías de Outlook**

Con Aspose.Email, puede recuperar y utilizar fácilmente los colores de categoría asociados a las categorías de elementos de Outlook almacenadas en archivos OLM. El [OlmItemCategory](https://reference.aspose.com/email/python-net/aspose.email.storage.olm/olmitemcategory/) La clase le permite acceder a los nombres de las categorías y sus respectivos colores representados en formato hexadecimal. El [OlmStorage](https://reference.aspose.com/email/python-net/aspose.email.storage.olm/olmstorage/#olmstorage-class) La clase presenta el método 'getCategories () 'para recuperar una lista de categorías del almacenamiento de OLM. Al implementar el siguiente ejemplo de código, puedes recuperar sin esfuerzo todas las categorías usadas de un archivo de almacenamiento OML y acceder al nombre de la categoría junto con su color.

```py
with OlmStorage.FromFile("storage.olm") as olm:
    categories = olm.GetCategories()
   
    for category in categories:
        print(f"Category name: {category.Name}")
       
        # Color is represented as a hexadecimal value: #rrggbb
        print(f"Category color: {category.Color}")
```

Además, puede recuperar el color de la categoría asociado a mensajes específicos recorriendo los mensajes de una carpeta y accediendo al color de la categoría correspondiente según el nombre de la categoría.

```py
for msg in olm.EnumerateMessages(folder):
    if msg.Categories is not None:
        for msgCategory in msg.Categories:
            print(f"Category name: {msgCategory}")
            categoryColor = next((c.Color for c in categories if c.Name.lower() == msgCategory.lower()), None)
            if categoryColor is not None:
                print(f"Category color: {categoryColor}")
```