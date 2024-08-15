---
title: "Lea el archivo PST de Outlook y obtenga información sobre carpetas y subcarpetas"
url: /es/python-net/read-outlook-pst-file-and-get-folders-and-subfolders-information/
weight: 30
type: docs
---


Aspose.Email para.NET proporciona una API para leer archivos PST de Microsoft Outlook. Puede cargar un archivo PST desde un disco o una transmisión a una instancia de la clase PersonalStorage y obtener la información sobre su contenido, por ejemplo, carpetas, subcarpetas y mensajes. La API también ofrece la capacidad de incluir carpetas de búsqueda al buscar los mensajes de las carpetas PST.
## **Carga de un archivo PST**
Se puede cargar un archivo PST de Outlook en una instancia de la clase PersonalStorage. El siguiente fragmento de código muestra cómo cargar el archivo PST.



{{< gist "aspose-email" "356f0e128b9d45a7ee779fc813eb87e5" "Examples-WorkingWithOutlookStorageFiles-ReadingOSTFiles-ReadingOSTFiles.py" >}}
## **Visualización de la información de PST**
Tras cargar el archivo PST en la clase PersonalStorage, puede obtener la información sobre el nombre para mostrar del archivo, la carpeta raíz, las subcarpetas y el recuento de mensajes. El siguiente fragmento de código muestra cómo mostrar el nombre del archivo PST, las carpetas y el número de mensajes de las carpetas.



{{< gist "aspose-email" "356f0e128b9d45a7ee779fc813eb87e5" "Examples-WorkingWithOutlookStorageFiles-DisplayInformationOfPSTFile-DisplayInformationOfPSTFile.py" >}}

## **Obtener solo las carpetas creadas por el usuario**

Los archivos PST/OST pueden contener carpetas creadas por un usuario, es decir, excluyendo todas las carpetas IPM estándar. Aspose.Email ofrece la posibilidad de acceder únicamente a las carpetas creadas por el usuario mediante el *only_folders_created_by_user* propiedad del [PersonalStorageQueryBuilder](https://reference.aspose.com/email/python-net/aspose.email.storage.pst/personalstoragequerybuilder/#personalstoragequerybuilder-class) clase. Puede configurar el *only_folders_created_by_user* propiedad en True para obtener solo las carpetas creadas por el usuario. En el siguiente fragmento de código se muestra cómo se puede utilizar *only_folders_created_by_user* propiedad en su proyecto:

```python
import aspose.email as ae

pst = ae.storage.pst.PersonalStorage.from_file("my.pst")

query_builder = ae.storage.pst.PersonalStorageQueryBuilder()
query_builder.only_folders_created_by_user.equals(True)

folders = pst.root_folder.get_sub_folders(query_builder.get_query())

for folder in folders:
    print(f"Folder: {folder.display_name}")
```

## **Comprobar si la carpeta está en una carpeta predefinida**

El método «get_predefined_type» del [FolderInfo](https://reference.aspose.com/email/python-net/aspose.email.storage.pst/folderinfo/#folderinfo-class) La clase le permite averiguar si una carpeta dentro de un archivo PST es una carpeta estándar. Las carpetas estándar (o predefinidas), a diferencia de las carpetas creadas por el usuario, son carpetas que Outlook crea al agregar una cuenta de correo electrónico, como la bandeja de entrada, los elementos enviados, los borradores, los elementos eliminados, el calendario, las tareas, las notas, etc.

El ejemplo de código siguiente muestra cómo usar este método en un proyecto. Si se establece en True, devuelve el tipo predefinido para la carpeta principal de nivel superior. Esto determina si la carpeta actual es una subcarpeta de una carpeta predefinida. Si se establece en False, devuelve el tipo predefinido para la carpeta actual.


```python
import aspose.email as ae

pst = ae.storage.pst.PersonalStorage.from_file("my.pst")

folders = pst.root_folder.get_sub_folders()

for folder in folders:
    print(f"Folder: {folder.display_name}")
    print(f"Is predefined: {folder.get_predefined_type(False) != ae.storage.pst.StandardIpmFolder.UNSPECIFIED}")
    print("-----------------------------------")
```
## **Obtener y agregar una carpeta de fuentes RSS estándar en PersonalStorage**

Aspose.Email proporciona la funcionalidad para recuperar una referencia a una carpeta predefinida de fuentes RSS, lo que permite a los desarrolladores acceder y manipular mediante programación las fuentes RSS almacenadas en un archivo PST de Outlook. Al obtener una referencia a la «carpeta de fuentes RSS», los desarrolladores pueden trabajar con los datos de las fuentes RSS, lo que puede incluir la suscripción a nuevas fuentes, la actualización de las fuentes existentes o la extracción de información de las fuentes.

El valor de RSSFeeds en la enumeración StandardIPMFolder normalmente representa el tipo de carpeta predefinido diseñado específicamente para almacenar fuentes RSS en un archivo PST de Outlook. Con este valor de enumeración, los desarrolladores pueden seleccionar la «carpeta de fuentes RSS» e interactuar con ella mediante programación. Los siguientes ejemplos de código mostrarán cómo implementar esta función en su proyecto:

```python
import aspose.email as ae

pst = ae.storage.pst.PersonalStorage.from_file("my.pst")

rss_folder = pst.get_predefined_folder(ae.storage.pst.StandardIpmFolder.RSS_FEEDS)
```
Para agregar una carpeta de fuentes RSS, usa el siguiente fragmento de código:

```python
import aspose.email as ae

pst = ae.storage.pst.PersonalStorage.from_file("my.pst")

rss_folder = pst.create_predefined_folder("RSS Feeds", ae.storage.pst.StandardIpmFolder.RSS_FEEDS)
```

## **Análisis de carpetas en las que se pueden buscar**

Aspose.Email proporciona un [FolderKind](https://reference.aspose.com/email/python-net/aspose.email.storage.pst/folderkind/#folderkind-enumeration) enumeración para trabajar con diferentes tipos de carpetas PST. Además de las carpetas NORMALES, funciona con las carpetas SEARCH. Una carpeta SEARCH es una carpeta virtual que proporciona una vista de todos los elementos de correo electrónico que coinciden con criterios de búsqueda específicos. Para analizar las carpetas SEARCH, utilice el siguiente fragmento de código:

```python
import aspose.email as ae

pst = ae.storage.pst.PersonalStorage.from_file("my.pst")

folders = pst.root_folder.get_sub_folders(ae.storage.pst.FolderKind.SEARCH | ae.storage.pst.FolderKind.NORMAL)

# Browse through each folder to display folder name and number of messages
for folder in folders:
    print(f"Folder: {folder.display_name}")
    sub_folders = folder.get_sub_folders(ae.storage.pst.FolderKind.SEARCH | ae.storage.pst.FolderKind.NORMAL)
    for sub_folder in sub_folders:
        print(f"Sub-folder: {folder.display_name}")
```

## **Recuperar la información de la carpeta principal de MessageInfo**
En el siguiente fragmento de código, se muestra cómo recuperar la información de la carpeta principal de MessageInfo.



{{< gist "aspose-email" "356f0e128b9d45a7ee779fc813eb87e5" "Examples-WorkingWithOutlookStorageFiles-RetrievingParentFolderInformationFromMessageInfo-RetrievingParentFolderInformationFromMessageInfo.py" >}}

## **Recuperar una subcarpeta PST por ruta**

Para recuperar una subcarpeta PST por ruta, utilice *get_sub_folder* método del [FolderInfo](https://reference.aspose.com/email/python-net/aspose.email.storage.pst/folderinfo/#folderinfo-class) clase. Recupera una subcarpeta específica dentro de un directorio o sistema de archivos.

El método toma los siguientes parámetros:

- **name** - representa el nombre de la subcarpeta que se debe recuperar. Se usa para especificar el nombre o el identificador de la subcarpeta que debe buscar el método.

- **ignore_case** - es un valor booleano que determina si el método debe ignorar la distinción entre mayúsculas y minúsculas al comparar el nombre de la subcarpeta. Si se establece en True, el método considerará que el nombre coincide sin tener en cuenta las mayúsculas y minúsculas (por ejemplo, «carpeta» y «carpeta» se tratarán de la misma manera). Si se establece en False, el método realizará una comparación que distingue entre mayúsculas y minúsculas.

- **handle_path_separator** - es un valor booleano que especifica si el método debe gestionar el separador de rutas al buscar la subcarpeta. Los separadores de rutas son caracteres que se utilizan para separar las carpetas de una ruta de directorio (p. ej., `\` en Windows o `/` en Unix). Si se establece en True, el método gestionará el separador de rutas automáticamente, garantizando la correcta coincidencia de carpetas. Si se establece en False, tratará el separador de rutas como parte del nombre de la subcarpeta, lo que provocará un comportamiento de búsqueda diferente.

El siguiente ejemplo de código muestra cómo recuperar una subcarpeta PST por ruta:

```python
import aspose.email as ae

pst = ae.storage.pst.PersonalStorage.from_file("my.pst")

# In this sample, the method will return a ‘Jan’ named folder
# that is located at the Inbox\Reports\ path
# relative to the root folder.
folder = pst.root_folder.get_sub_folder("Inbox\Reports\Jan", True, True)
```
