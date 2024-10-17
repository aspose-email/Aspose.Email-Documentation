---
title: "Leer archivos PST de Outlook y obtener información de carpetas y subcarpetas"
url: /es/java/read-outlook-pst-file-and-get-folders-and-subfolders-information/
weight: 110
type: docs
---

{{% alert color="primary" %}} 

Aspose.Email para Java permite leer archivos PST de Microsoft Outlook. Puedes cargar un archivo PST desde el disco o transmitirlo a una instancia de la clase [PersonalStorage](https://reference.aspose.com/email/java/com.aspose.email/personalstorage/) y obtener información sobre su contenido, por ejemplo, carpetas, subcarpetas y mensajes.

{{% /alert %}} 

## **Cargar un archivo PST**

Un archivo PST de Outlook puede ser cargado en una instancia de la clase [PersonalStorage](https://reference.aspose.com/email/java/com.aspose.email/personalstorage/). A continuación se muestra un fragmento de código para cargar el archivo PST:

{{< gist "aspose-com-gists" "709d733586ce50505c3bca3f6e8bd18d" "Examples-src-main-java-com-aspose-email-examples-outlook-pst-ReadOutlookPSTFile-LoadAPSTFile.java" >}}

## **Mostrar información de carpetas**

Después de cargar el archivo PST en la clase [PersonalStorage](https://reference.aspose.com/email/java/com.aspose.email/personalstorage/), puedes obtener información sobre el nombre para mostrar del archivo, la carpeta raíz, las subcarpetas y el recuento de mensajes. El siguiente fragmento de código muestra el nombre de un archivo PST, las carpetas y el número de mensajes en las carpetas:

{{< gist "aspose-com-gists" "709d733586ce50505c3bca3f6e8bd18d" "Examples-src-main-java-com-aspose-email-examples-outlook-pst-ReadOutlookPSTFile-DisplayFolderAndMessageInformationForPSTFile.java" >}}

## **Obtener solo carpetas definidas por el usuario**

Un archivo PST/OST puede contener carpetas que fueron creadas por el usuario. Aspose.Email proporciona la capacidad de acceder solo a carpetas definidas por el usuario utilizando la propiedad [PersonalStorageQueryBuilder.OnlyFoldersCreatedByUser](https://reference.aspose.com/email/java/com.aspose.email/personalstoragequerybuilder/#getOnlyFoldersCreatedByUser--). Puedes establecer la propiedad [PersonalStorageQueryBuilder.OnlyFoldersCreatedByUser](https://reference.aspose.com/email/java/com.aspose.email/personalstoragequerybuilder/#getOnlyFoldersCreatedByUser--) en **true** para obtener solo carpetas definidas por el usuario. El siguiente fragmento de código demuestra el uso de [PersonalStorageQueryBuilder.OnlyFoldersCreatedByUser](https://reference.aspose.com/email/java/com.aspose.email/personalstoragequerybuilder/#getOnlyFoldersCreatedByUser--) para obtener carpetas definidas por el usuario.

{{< gist "aspose-com-gists" "709d733586ce50505c3bca3f6e8bd18d" "Examples-src-main-java-com-aspose-email-examples-outlook-pst-GetFoldersCreatedByUserOnly-1.java" >}}

## **Comprobar si la carpeta está en una carpeta predefinida**

Al abrir e inspeccionar las carpetas dentro de un archivo PST (Tabla de Almacenamiento Personal), puedes verificar si cada carpeta es de un tipo de carpeta predefinida o una subcarpeta de un tipo de carpeta predefinida, y obtener información sobre cada carpeta.

El método [FolderInfo.getPredefinedType(boolean getForTopLevelParent)](https://reference.aspose.com/email/java/com.aspose.email/folderinfo/#getPredefinedType-boolean-) se utiliza para verificar si la carpeta es de [StandardIpmFolder](https://reference.aspose.com/email/java/com.aspose.email/standardipmfolder/). 

Si el parámetro 'getForTopLevelParent' es verdadero, el método devuelve un valor de enumeración StandardIpmFolder para la carpeta principal de nivel superior. Esto determina si la carpeta actual es una subcarpeta de una carpeta predefinida. Si el parámetro 'getForTopLevelParent' es falso, devuelve un valor de enumeración StandardIpmFolder para la carpeta actual.

```java
String fileName = "my.pst";

try (PersonalStorage pst = PersonalStorage.fromFile(fileName)) {
    checkFolders(pst.getRootFolder().getSubFolders());
}

private void checkFolders(FolderInfoCollection folders) {
    for (FolderInfo folder : folders) {
        System.out.println("Display Name: " + folder.getDisplayName());

        // Determina si la carpeta actual es una carpeta predefinida
        int folderType = folder.getPredefinedType(false);
        String answer = folderType == StandardIpmFolder.Unspecified ? "No" : "Sí, " + folderType;
        System.out.println("¿Es StandardIpmFolder?: " + answer);

        // Determina si la carpeta actual es una subcarpeta de una carpeta predefinida
        if (folderType == StandardIpmFolder.Unspecified) {
            folderType = folder.getPredefinedType(true);
            answer = folderType == StandardIpmFolder.Unspecified ? "No" : "Sí, " + folderType;
            System.out.println("¿Es subcarpeta de la carpeta padre StandardIpmFolder?: " + answer);
        }

        System.out.println();

        checkFolders(folder.getSubFolders());
    }
}
```
## **Obtener o agregar una carpeta estándar de fuentes RSS en un archivo PST**

Aspose.Email hace posible recuperar una referencia a la carpeta predefinida que contiene fuentes RSS. Esto puede ser útil si deseas acceder y manipular programáticamente las fuentes RSS almacenadas en un archivo PST de Outlook. Asigna el valor de RssFeeds a la enumeración [StandardIpmFolder](https://reference.aspose.com/email/java/com.aspose.email/standardipmfolder/).

El siguiente ejemplo de código muestra cómo obtener una carpeta de fuentes RSS:

```java
try (PersonalStorage pst = PersonalStorage.fromFile("my.pst", false)) {
    FolderInfo rssFolder = pst.getPredefinedFolder(StandardIpmFolder.RssFeeds);
}
```
Y la siguiente muestra de código demuestra cómo agregar una carpeta de fuentes RSS:

```java
try (PersonalStorage pst = PersonalStorage.create("my.pst", FileFormatVersion.Unicode)) {
    FolderInfo rssFolder = pst.createPredefinedFolder("RSS Feeds", StandardIpmFolder.RssFeeds);
}
```

## **Analizar carpetas buscables**

Un PST/OST puede contener carpetas buscables además del tipo normal de carpetas. Aspose.Email proporciona el enumerador [FolderKind](https://reference.aspose.com/email/java/com.aspose.email/folderkind/) para especificar los mensajes de tales carpetas de búsqueda con los métodos [EnumerateFolders](https://reference.aspose.com/email/java/com.aspose.email/folderinfo/#enumerateFolders--) y [GetSubFolders](https://reference.aspose.com/email/java/com.aspose.email/folderinfo/#getSubFolders--).

{{< gist "aspose-com-gists" "709d733586ce50505c3bca3f6e8bd18d" "Examples-src-main-java-com-aspose-email-examples-outlook-pst-ReadOutlookPSTFile-ParseSearchableFolders.java" >}}

## **Recuperar información de la carpeta principal desde MessageInfo**

El siguiente fragmento de código te muestra cómo recuperar información de la carpeta principal de [MessageInfo](https://reference.aspose.com/email/java/com.aspose.email/messageinfo/).

{{< gist "aspose-com-gists" "709d733586ce50505c3bca3f6e8bd18d" "Examples-src-main-java-com-aspose-email-examples-outlook-pst-ReadOutlookPSTFile-RetrieParentFolderInformationFromMessageInfo.java" >}}

## **API de recorrido de archivos PST**

La API de recorrido permite extraer todos los elementos de PST tanto como sea posible, sin lanzar excepciones, incluso si algunos datos del archivo original están corruptos.
Los siguientes pasos muestran cómo utilizar esta API.

Usa el constructor [PersonalStorage](https://reference.aspose.com/email/java/com.aspose.email/personalstorage/) y el método [load](https://reference.aspose.com/email/java/com.aspose.email/personalstorage/#load-java.io.InputStream-) en lugar del método fromFile.

El constructor permite definir un método de devolución de llamada.

```java
try (PersonalStorage currentPst = new PersonalStorage(new TraversalExceptionsCallback() {
    public void invoke(TraversalAsposeException exception, String itemId) {
        // Código de manejo de excepciones.
    }
})) {
    //
}
```

Las excepciones de carga y recorrido estarán disponibles a través del método de devolución de llamada.

El método [load](https://reference.aspose.com/email/java/com.aspose.email/personalstorage/#load-java.io.InputStream-) devuelve 'true' si el archivo se ha cargado correctamente y es posible un recorrido adicional. Si un archivo está corrupto y no es posible el recorrido, se devuelve 'false'.

```java
if (currentPst.load(inputStream))
```

Esto permite abrir y recorrer incluso archivos PST corruptos sin lanzar excepciones. Tanto las excepciones como los elementos corruptos serán manejados por el método de devolución de llamada.

```java
try (PersonalStorage pst = new PersonalStorage(new TraversalExceptionsCallback() {
    public void invoke(TraversalAsposeException exception, String itemId) {
        // Código de manejo de excepciones.
    }
})) {
    if (pst.load("test.pst")) {
        getAllMessages(pst, pst.getRootFolder());
    }
}

private static void getAllMessages(PersonalStorage pst, FolderInfo folder) {
    for (String messageEntryId : folder.enumerateMessagesEntryId()) {
        MapiMessage message = pst.extractMessage(messageEntryId);
    }
    for (FolderInfo subFolder : folder.getSubFolders()) {
        getAllMessages(pst, subFolder);
    }
}
```