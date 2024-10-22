---
title: "Leer archivo PST de Outlook y obtener información de carpetas y subcarpetas"
url: /es/python-net/read-outlook-pst-file-and-get-folders-and-subfolders-information/
weight: 30
type: docs
---

Aspose.Email para .NET proporciona una API para leer archivos PST de Microsoft Outlook. Puedes cargar un archivo PST desde el disco o transmitirlo a una instancia de la clase PersonalStorage y obtener información sobre su contenido, como carpetas, subcarpetas y mensajes. La API también proporciona la capacidad de incluir carpetas de búsqueda al recorrer los mensajes de las carpetas PST.
## **Cargando un archivo PST**
Un archivo PST de Outlook se puede cargar en una instancia de la clase PersonalStorage. El siguiente fragmento de código muestra cómo cargar el archivo PST.

```python
{{< gist "aspose-email" "356f0e128b9d45a7ee779fc813eb87e5" "Examples-WorkingWithOutlookStorageFiles-ReadingOSTFiles-ReadingOSTFiles.py" >}}
```
## **Mostrando información PST**
Después de cargar el archivo PST en la clase PersonalStorage, puedes obtener información sobre el nombre de visualización del archivo, la carpeta raíz, subcarpetas y el conteo de mensajes. El siguiente fragmento de código muestra cómo mostrar el nombre del archivo PST, las carpetas y el número de mensajes en las carpetas.

```python
{{< gist "aspose-email" "356f0e128b9d45a7ee779fc813eb87e5" "Examples-WorkingWithOutlookStorageFiles-DisplayInformationOfPSTFile-DisplayInformationOfPSTFile.py" >}}
```

## **Obtener solo carpetas creadas por el usuario**

Los archivos PST/OST pueden contener carpetas que fueron creadas por un usuario, es decir, excluyendo todas las carpetas IPM estándar. Aspose.Email proporciona la capacidad de acceder solo a las carpetas creadas por el usuario utilizando la propiedad *only_folders_created_by_user* de la clase [PersonalStorageQueryBuilder](https://reference.aspose.com/email/python-net/aspose.email.storage.pst/personalstoragequerybuilder/#personalstoragequerybuilder-class). Puedes establecer la propiedad *only_folders_created_by_user* en True para obtener solo carpetas creadas por el usuario. El siguiente fragmento de código demuestra cómo puedes usar la propiedad *only_folders_created_by_user* en tu proyecto:

```python
import aspose.email as ae

pst = ae.storage.pst.PersonalStorage.from_file("my.pst")

query_builder = ae.storage.pst.PersonalStorageQueryBuilder()
query_builder.only_folders_created_by_user.equals(True)

folders = pst.root_folder.get_sub_folders(query_builder.get_query())

for folder in folders:
    print(f"Carpeta: {folder.display_name}")
```

## **Comprobando si la carpeta está en una carpeta predefinida**

El método "get_predefined_type" de la clase [FolderInfo](https://reference.aspose.com/email/python-net/aspose.email.storage.pst/folderinfo/#folderinfo-class) te permite averiguar si una carpeta dentro de un archivo PST es una carpeta estándar. Las carpetas estándar (o predefinidas), a diferencia de las creadas por el usuario, son carpetas que son creadas por Outlook cuando agregas una cuenta de correo electrónico, como Bandeja de entrada, Elementos enviados, Borradores, Elementos eliminados, Calendario, Tareas, Notas, etc.

El siguiente ejemplo de código demuestra cómo usar este método en un proyecto. Si se establece en True, devuelve el tipo predefinido para la carpeta principal de nivel superior. Esto determina si la carpeta actual es una subcarpeta de una carpeta predefinida. Si se establece en False, devuelve el tipo predefinido para la carpeta actual.

```python
import aspose.email as ae

pst = ae.storage.pst.PersonalStorage.from_file("my.pst")

folders = pst.root_folder.get_sub_folders()

for folder in folders:
    print(f"Carpeta: {folder.display_name}")
    print(f"Es predefinida: {folder.get_predefined_type(False) != ae.storage.pst.StandardIpmFolder.UNSPECIFIED}")
    print("-----------------------------------")
```
## **Obteniendo y añadiendo una carpeta estándar de RSS Feeds en PersonalStorage**

Aspose.Email proporciona funcionalidad para recuperar una referencia a una carpeta predefinida de RSS Feeds, permitiendo a los desarrolladores acceder y manipular programáticamente los feeds RSS almacenados en un archivo PST de Outlook. Al obtener una referencia a la "carpeta de RSS Feeds", los desarrolladores pueden trabajar con los datos del feed RSS, lo que puede incluir suscribirse a nuevos feeds, actualizar feeds existentes o extraer información de los feeds.

El valor de RssFeeds en el enum StandardIpmFolder típicamente representaría el tipo de carpeta predefinido diseñado específicamente para almacenar feeds RSS dentro de un archivo PST de Outlook. Usando este valor de enum, los desarrolladores pueden apuntar e interactuar programáticamente con la "carpeta de RSS Feeds". Los siguientes ejemplos de código demostrarán cómo implementar esta función en tu proyecto:

```python
import aspose.email as ae

pst = ae.storage.pst.PersonalStorage.from_file("my.pst")

rss_folder = pst.get_predefined_folder(ae.storage.pst.StandardIpmFolder.RSS_FEEDS)
```
Para agregar una carpeta de RSS Feeds, utiliza el siguiente fragmento de código:

```python
import aspose.email as ae

pst = ae.storage.pst.PersonalStorage.from_file("my.pst")

rss_folder = pst.create_predefined_folder("RSS Feeds", ae.storage.pst.StandardIpmFolder.RSS_FEEDS)
```

## **Analizando Carpetas Buscables**

Aspose.Email proporciona una enumeración [FolderKind](https://reference.aspose.com/email/python-net/aspose.email.storage.pst/folderkind/#folderkind-enumeration) para trabajar con diferentes tipos de carpetas PST. Además de las carpetas NORMALES, funciona con carpetas de BÚSQUEDA. Una carpeta de BÚSQUEDA es una carpeta virtual que proporciona una vista de todos los elementos de correo electrónico que coinciden con criterios de búsqueda específicos. Para analizar carpetas de BÚSQUEDA, utiliza el siguiente fragmento de código:

```python
import aspose.email as ae

pst = ae.storage.pst.PersonalStorage.from_file("my.pst")

folders = pst.root_folder.get_sub_folders(ae.storage.pst.FolderKind.SEARCH | ae.storage.pst.FolderKind.NORMAL)

# Recorre cada carpeta para mostrar el nombre de la carpeta y el número de mensajes
for folder in folders:
    print(f"Carpeta: {folder.display_name}")
    sub_folders = folder.get_sub_folders(ae.storage.pst.FolderKind.SEARCH | ae.storage.pst.FolderKind.NORMAL)
    for sub_folder in sub_folders:
        print(f"Sub-carpeta: {folder.display_name}")
```

## **Recuperando información de la carpeta padre desde MessageInfo**
El siguiente fragmento de código muestra cómo recuperar información de la carpeta padre desde MessageInfo.

```python
{{< gist "aspose-email" "356f0e128b9d45a7ee779fc813eb87e5" "Examples-WorkingWithOutlookStorageFiles-RetrievingParentFolderInformationFromMessageInfo-RetrievingParentFolderInformationFromMessageInfo.py" >}}
```

## **Recuperando una subcarpeta PST por ruta**

Para recuperar una subcarpeta PST por ruta, utiliza el método *get_sub_folder* de la clase [FolderInfo](https://reference.aspose.com/email/python-net/aspose.email.storage.pst/folderinfo/#folderinfo-class). Recupera una subcarpeta específica dentro de un directorio o sistema de archivos.

El método toma los siguientes parámetros:

- **name** - representa el nombre de la subcarpeta que necesita ser recuperada. Se utiliza para especificar el nombre o identificador de la subcarpeta que el método debería buscar.

- **ignore_case** - es un valor booleano que determina si el método debería ignorar la sensibilidad a mayúsculas y minúsculas al comparar el nombre de la subcarpeta. Si se establece en True, el método considerará que los nombres coinciden sin tener en cuenta el caso (por ejemplo, "carpeta" y "Carpeta" se tratarán como lo mismo). Si se establece en False, el método realizará una comparación sensible a mayúsculas y minúsculas.

- **handle_path_separator** - es un valor booleano que especifica si el método debe manejar el separador de ruta al buscar la subcarpeta. Los separadores de ruta son caracteres utilizados para separar carpetas en una ruta de directorio (por ejemplo, `\` en Windows o `/` en Unix). Si se establece en True, el método manejará automáticamente el separador de ruta, asegurando una coincidencia correcta de carpetas. Si se establece en False, tratará el separador de ruta como parte del nombre de la subcarpeta, lo que resultará en un comportamiento de búsqueda diferente.

El siguiente ejemplo de código muestra cómo recuperar una subcarpeta PST por ruta:

```python
import aspose.email as ae

pst = ae.storage.pst.PersonalStorage.from_file("my.pst")

# En este ejemplo, el método devolverá una carpeta nombrada 'Ene'
# que se encuentra en la ruta Inbox\Reports\
# relativa a la carpeta raíz.
folder = pst.root_folder.get_sub_folder("Inbox\Reports\Jan", True, True)
```