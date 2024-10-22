---
title: "Leer el archivo OLM de Outlook para Mac y obtener información de carpetas y subcarpetas"
url: /es/python-net/read-outlook-for-mac-olm-file-and-get-folders-and-subfolders-information/
weight: 120
type: docs
---

OLM (Archivo de Outlook para Mac) es un formato de archivo asociado con Microsoft Outlook para Mac. Se utiliza para archivar y almacenar mensajes de correo electrónico, contactos, elementos de calendario, tareas y otros datos de Outlook en computadoras Mac. Los archivos OLM sirven como formato de respaldo o archivo, permitiendo a los usuarios guardar sus datos de Outlook para Mac para referencia futura o migración. Es importante señalar que los archivos OLM son específicos de Outlook para Mac y no son compatibles con el formato de archivo PST (Tabla de Almacenamiento Personal) utilizado por Outlook en Windows. Si necesita transferir datos de Outlook entre diferentes plataformas, las herramientas de conversión serán útiles. Aspose.Email ofrece tales herramientas, incluyendo abrir, leer y otras funcionalidades para trabajar con archivos OLM.

## **Apertura de archivos en formato OLM**

Los archivos en formato OLM se pueden abrir de dos maneras:

- utilizando el constructor
- utilizando el método estático 'from_file'

### **Apertura de archivos por constructor**

Para abrir un archivo, llame al constructor de la clase [OlmStorage](https://reference.aspose.com/email/python-net/aspose.email.storage.olm/olmstorage/#olmstorage-class) y pase el nombre completo del archivo o el flujo como argumento:

```py
import aspose.email as ae

fileName = "my.olm"
olm = ae.storage.olm.OlmStorage(fileName)
```

### **Apertura de archivos usando el método estático FromFile**

Para abrir un archivo, use el método estático 'from_file' de la clase [OlmStorage](https://reference.aspose.com/email/python-net/aspose.email.storage.olm/olmstorage/#olmstorage-class) y pase el nombre completo del archivo o el flujo como argumento:

```py
import aspose.email as ae

fileName = "my.olm"
olm = ae.storage.olm.OlmStorage.from_file(fileName)
```

## **Obteniendo carpetas**

Puede visualizar y mostrar la jerarquía de carpetas recuperada de un archivo OLM utilizando la función 'print_all_folders'. Esta toma la propiedad 'folder_hierarchy' de la clase [OlmStorage](https://reference.aspose.com/email/python-net/aspose.email.storage.olm/olmstorage/#olmstorage-class) y un nivel de sangrado como entrada, luego recorre recursivamente la jerarquía para imprimir el nombre de cada carpeta junto con la sangría apropiada. El siguiente ejemplo de código demuestra cómo usar esta función para mostrar la jerarquía de carpetas de un archivo OLM. Muestra la lista de todas las carpetas en orden jerárquico:

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

El ejemplo de código anterior está destinado a mostrar la jerarquía de carpetas del archivo OLM a través de una función recursiva en un formato más estructurado y legible. Aspose.Email también hace posible acceder directamente a la estructura de carpetas del archivo OLM utilizando el método 'get_folders()' de la clase [OlmStorage](https://reference.aspose.com/email/python-net/aspose.email.storage.olm/olmstorage/#olmstorage-class).

```py
import aspose.email as ae

fileName = "my.olm"
olm = ae.storage.olm.OlmStorage.from_file(fileName)
folders = olm.get_folders()
```

Además, es posible obtener cualquier carpeta por nombre. El siguiente ejemplo de código utiliza el método 'get_folder(name, ignore_case)' de la clase [OlmStorage](https://reference.aspose.com/email/python-net/aspose.email.storage.olm/olmstorage/#olmstorage-class) pasando el nombre de la carpeta y la sensibilidad de mayúsculas como parámetros para recuperar la carpeta por su nombre:


```py
import aspose.email as ae

fileName = "my.olm"
olm = ae.storage.olm.OlmStorage.from_file(fileName)
folder = olm.get_folder("Inbox", True)
```

## **Lista de correos electrónicos**

Los fragmentos de código a continuación demuestran cómo usar la biblioteca Aspose.Email para leer y extraer los asuntos de los correos electrónicos de un archivo de Outlook para Mac (OLM). La clase [OlmFolder](https://reference.aspose.com/email/python-net/aspose.email.storage.olm/olmfolder/#olmfolder-class), que representa una carpeta, tiene los siguientes métodos para obtener la lista de correos electrónicos:

- 'enumerate_messages()' - Itera a través de cada mensaje de correo electrónico en la carpeta. Este método devuelve mensajes como instancias de la clase [OlmMessageInfo](https://reference.aspose.com/email/python-net/aspose.email.storage.olm/olmmessageinfo/#olmmessageinfo-class) que proporciona información básica sobre cada mensaje de correo, como asunto, remitente, fecha, etc.
- 'enumerate_mapi_messages()' - También itera a través de cada mensaje de correo electrónico en una carpeta, pero en este caso, devuelve mensajes como instancias de la clase [MapiMessage](https://reference.aspose.com/email/python-net/aspose.email.mapi/mapimessage/#mapimessage-class) que representa un mensaje de correo de manera más detallada y específica de MAPI. Proporciona acceso a una amplia gama de propiedades y detalles del mensaje de correo, permitiendo un procesamiento más avanzado y especializado.

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

Las otras propiedades útiles de la clase [OlmFolder](https://reference.aspose.com/email/python-net/aspose.email.storage.olm/olmfolder/#olmfolder-class) son: 

- 'has_messages' - Obtiene un valor que indica si la carpeta actual tiene mensajes.
- 'message_count' - Obtiene el conteo de mensajes.

```py
import aspose.email as ae

fileName = "my.olm"
olm = ae.storage.olm.OlmStorage.from_file(fileName)
folder = olm.get_folder("Inbox", True)

if folder.has_messages:
   print(f"Conteo de mensajes: {folder.message_count}")
```

### **Obtener o establecer la fecha de modificación de un mensaje**

Puede recuperar información sobre la hora de la última modificación de un mensaje de correo electrónico. La propiedad 'modified_date' de la clase [OlmMessageInfo](https://reference.aspose.com/email/python-net/aspose.email.storage.olm/olmmessageinfo/#olmmessageinfo-class) representa la fecha y hora en que se modificó por última vez el mensaje. 

Aquí hay un ejemplo que demuestra el uso de la propiedad:

```py
import aspose.email as ae

fileName = "my.olm"
olm = ae.storage.olm.OlmStorage.from_file(fileName)
folder = olm.get_folder("Inbox", True)

for message_info in folder.enumerate_messages():
    modifiedDate = message_info.modified_date
```

## **Extracción de correos electrónicos**

Puede recuperar los datos reales del mensaje MAPI de un almacenamiento de correos electrónicos. El método 'extract_mapi_message(message_info)' de la clase [OlmStorage](https://reference.aspose.com/email/python-net/aspose.email.storage.olm/olmstorage/#olmstorage-class) se utiliza para extraer el mensaje MAPI del almacenamiento según la información del mensaje proporcionada.  

El siguiente ejemplo de código demuestra cómo usar este método:

```py
import aspose.email as ae

fileName = "my.olm"
olm = ae.storage.olm.OlmStorage.from_file(fileName)
folder = olm.get_folder("Inbox", True)

for message_info in folder.enumerate_messages():
    msg = olm.extract_mapi_message(message_info)
```

## **Extracción de todos los ítems de un correo electrónico utilizando la API de recorrido**

Puede extraer todos los ítems de un archivo OLM de Outlook tanto como sea posible, sin lanzar excepciones, incluso si algunos datos del archivo original están corruptos. Para realizar esto, use el constructor [OlmStorage(TraversalExceptionsCallback callback)](https://reference.aspose.com/email/net/aspose.email.storage.olm/olmstorage/#constructors) y el método [Load(string fileName)](https://reference.aspose.com/email/net/aspose.email.storage.olm/olmstorage/load/#load_1) en lugar del método FromFile. El constructor permite definir un método de devolución de llamada.

```cs
using (var olm = new OlmStorage((exception, id) => { /* Código de manejo de excepciones. */ }))
```
El método de devolución de llamada hace que las excepciones de carga y recorrido estén disponibles.

El método [Load](https://reference.aspose.com/email/net/aspose.email.storage.olm/olmstorage/load/#load_1) devuelve 'true' si el archivo se ha cargado correctamente y se puede realizar un recorrido adicional. Si un archivo está dañado y no se puede realizar un recorrido, se devuelve 'false'.

```cs
if (olm.Load(fileName))
```

El siguiente fragmento de código y los pasos muestran cómo usar esta API:

1. Cree una nueva instancia de la clase [OlmStorage](https://reference.aspose.com/email/net/aspose.email.storage.olm/olmstorage/), pasando un callback de manejo de excepciones para manejar cualquier excepción encontrada durante el proceso.
2. Cargue el archivo OLM llamando al método [Load](https://reference.aspose.com/email/net/aspose.email.storage.olm/olmstorage/load/#load_1) de la instancia de OlmStorage. 
3. Si el archivo OLM se carga correctamente, obtenga la jerarquía de carpetas llamando al método [GetFolders](https://reference.aspose.com/email/net/aspose.email.storage.olm/olmstorage/getfolders/) en la instancia de OlmStorage. Esto devuelve una lista de objetos OlmFolder.
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

Para acceder a los datos del mensaje MAPI, puede usar la propiedad 'entry_id' para obtener el identificador único (Entry ID) de un mensaje utilizando la clase [OlmMessageInfo](https://reference.aspose.com/email/python-net/aspose.email.storage.olm/olmmessageinfo/#olmmessageinfo-class). Luego, puede utilizar el método 'extract_mapi_message(id)' de la clase [OlmStorage](https://reference.aspose.com/email/python-net/aspose.email.storage.olm/olmstorage/#olmstorage-class), pasando el Entry ID como parámetro para recuperar el mensaje MAPI asociado con ese Entry ID particular. El siguiente fragmento de código demuestra el uso de estas características:

```py

import aspose.email as ae

fileName = "my.olm"
olm = ae.storage.olm.OlmStorage.from_file(fileName)
folder = olm.get_folder("Inbox", True)

for message_info in folder.enumerate_messages():
    msg = olm.extract_mapi_message(message_info.entry_id)
```

## **Obtener la ruta de la carpeta**

También puede obtener la ruta jerárquica o ubicación de la carpeta dentro del archivo OLM de Outlook. Aspose.Email proporciona la propiedad 'path' de la clase [OlmFolder](https://reference.aspose.com/email/python-net/aspose.email.storage.olm/olmfolder/#olmfolder-class) que devuelve la ruta de la carpeta. El siguiente fragmento de código demuestra el uso de esta propiedad:

```py
import aspose.email as ae


def print_path(storage, folders):
    for folder in folders:
        # imprime la ruta de la carpeta actual
        print(folder.path)

        if folder.sub_folders:
            print_path(storage, folder.sub_folders)


fileName = "my.olm"
olm = ae.storage.olm.OlmStorage(fileName)
print_path(olm, olm.folder_hierarchy)
```

## **Contar el número de ítems en la carpeta**

Aspose.Email proporciona la capacidad de contar el número total de mensajes de correo electrónico contenidos dentro de una carpeta específica de un archivo OLM de Outlook. La propiedad 'message_count' de la clase [OlmFolder](https://reference.aspose.com/email/python-net/aspose.email.storage.olm/olmfolder/#olmfolder-class) devuelve el conteo total de ítems (mensajes de correo electrónico) almacenados dentro de una carpeta específica en el archivo OLM. El siguiente fragmento de código demuestra el uso de esta propiedad:

```py
import aspose.email as ae


def print_message_count(folders):
    for folder in folders:
        print(f"Conteo de mensajes [{folder.name}]: {folder.message_count}")


fileName = "my.olm"
olm = ae.storage.olm.OlmStorage(fileName)
print_message_count(olm.folder_hierarchy)
```

### **Obtener el conteo total de ítems de OlmStorage**

El método 'get_total_items_count()' de la clase [OlmStorage](https://reference.aspose.com/email/python-net/aspose.email.storage.olm/olmstorage/#olmstorage-class) devuelve el número total de ítems de mensajes contenidos en el almacenamiento OLM.
  
```py
import aspose.email as ae

fileName = "my.olm"
olm = ae.storage.olm.OlmStorage(fileName)
count = olm.get_total_items_count()
```

## **Recuperar colores de categorías de Outlook**

Con Aspose.Email, puede recuperar y utilizar fácilmente los colores de las categorías asociadas con elementos de categoría de Outlook almacenados en archivos OLM. La clase [OlmItemCategory](https://reference.aspose.com/email/python-net/aspose.email.storage.olm/olmitemcategory/) le permite acceder a los nombres de categoría y sus respectivos colores representados en formato hexadecimal. La clase [OlmStorage](https://reference.aspose.com/email/python-net/aspose.email.storage.olm/olmstorage/#olmstorage-class) presenta el método 'GetCategories()' para recuperar una lista de categorías del almacenamiento OLM. Al implementar el siguiente fragmento de código, puede recuperar fácilmente todas las categorías utilizadas de un archivo de almacenamiento OML y acceder al nombre de la categoría junto con su color. 

```py
with OlmStorage.FromFile("storage.olm") as olm:
    categories = olm.GetCategories()
    
    for category in categories:
        print(f"Nombre de la categoría: {category.Name}")
        
        # El color se representa como un valor hexadecimal: #rrggbb
        print(f"Color de la categoría: {category.Color}")
```

Además, puede recuperar el color de la categoría asociado con mensajes específicos iterando a través de los mensajes en una carpeta y accediendo al color de la categoría correspondiente según el nombre de la categoría.

```py
for msg in olm.EnumerateMessages(folder):
    if msg.Categories is not None:
        for msgCategory in msg.Categories:
            print(f"Nombre de la categoría: {msgCategory}")
            categoryColor = next((c.Color for c in categories if c.Name.lower() == msgCategory.lower()), None)
            if categoryColor is not None:
                print(f"Color de la categoría: {categoryColor}")
```