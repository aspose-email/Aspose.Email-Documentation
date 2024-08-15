---
title: "Lea el archivo PST de Outlook y obtenga información sobre carpetas y subcarpetas"
url: /es/java/read-outlook-pst-file-and-get-folders-and-subfolders-information/
weight: 110
type: docs
---

{{% alert color="primary" %}}

Aspose.Email para Java permite leer archivos PST de Microsoft Outlook. Puede cargar un archivo PST desde un disco o transmitirlo a una instancia del [PersonalStorage](https://reference.aspose.com/email/java/com.aspose.email/personalstorage/) y obtenga la información sobre su contenido, por ejemplo, carpetas, subcarpetas y mensajes.

{{% /alert %}}

## **Cargar un archivo PST**

Se puede cargar un archivo PST de Outlook en una instancia de [PersonalStorage](https://reference.aspose.com/email/java/com.aspose.email/personalstorage/) clase. A continuación se muestra un fragmento de código para cargar el archivo PST:

{{< gist "aspose-com-gists" "709d733586ce50505c3bca3f6e8bd18d" "Examples-src-main-java-com-aspose-email-examples-outlook-pst-ReadOutlookPSTFile-LoadAPSTFile.java" >}}

## **Visualización de la información de carpetas**

Tras cargar el archivo PST en [PersonalStorage](https://reference.aspose.com/email/java/com.aspose.email/personalstorage/) clase, puede obtener la información sobre el nombre para mostrar del archivo, la carpeta raíz, las subcarpetas y el recuento de mensajes. El siguiente fragmento de código muestra el nombre de un archivo PST, las carpetas y el número de mensajes de las carpetas:

{{< gist "aspose-com-gists" "709d733586ce50505c3bca3f6e8bd18d" "Examples-src-main-java-com-aspose-email-examples-outlook-pst-ReadOutlookPSTFile-DisplayFolderAndMessageInformationForPSTFile.java" >}}

## **Obtenga solo carpetas definidas por el usuario**

Los archivos PST/OST pueden contener carpetas creadas por el usuario. Aspose.Email ofrece la posibilidad de acceder únicamente a las carpetas definidas por el usuario mediante el [PersonalStorageQueryBuilder.OnlyFoldersCreatedByUser](https://reference.aspose.com/email/java/com.aspose.email/personalstoragequerybuilder/#getOnlyFoldersCreatedByUser--) propiedad. Puede configurar el [PersonalStorageQueryBuilder.OnlyFoldersCreatedByUser](https://reference.aspose.com/email/java/com.aspose.email/personalstoragequerybuilder/#getOnlyFoldersCreatedByUser--) propiedad a **true** para obtener solo las carpetas definidas por el usuario. El siguiente fragmento de código demuestra el uso de [PersonalStorageQueryBuilder.OnlyFoldersCreatedByUser](https://reference.aspose.com/email/java/com.aspose.email/personalstoragequerybuilder/#getOnlyFoldersCreatedByUser--) para obtener carpetas definidas por el usuario.

{{< gist "aspose-com-gists" "709d733586ce50505c3bca3f6e8bd18d" "Examples-src-main-java-com-aspose-email-examples-outlook-pst-GetFoldersCreatedByUserOnly-1.java" >}}

## **Comprobar si la carpeta está en una carpeta predefinida**

Al abrir e inspeccionar las carpetas de un archivo PST (tabla de almacenamiento personal), puede comprobar si cada carpeta es un tipo de carpeta predefinido o una subcarpeta de un tipo de carpeta predefinido y obtener la información sobre cada carpeta.

The [FolderInfo.getPredefinedType (booleano getForTopLevelParent)](https://reference.aspose.com/email/java/com.aspose.email/folderinfo/#getPredefinedType-boolean-) el método se usa para comprobar si la carpeta es de [StandardIpmFolder](https://reference.aspose.com/email/java/com.aspose.email/standardipmfolder/).

Si el parámetro 'getForTopLevelParent' es verdadero, el método devuelve un valor de enumeración StandardIPMFolder para la carpeta principal de nivel superior. Esto determina si la carpeta actual es una subcarpeta de una carpeta predefinida. Si el parámetro 'getForTopLevelParent' es falso, devuelve un valor de enumeración StandardIPMFolder para la carpeta actual.

```java
String fileName = "my.pst";

try (PersonalStorage pst = PersonalStorage.fromFile(fileName)) {
    checkFolders(pst.getRootFolder().getSubFolders());
}

private void checkFolders(FolderInfoCollection folders) {
    for (FolderInfo folder : folders) {
        System.out.println("Display Name: " + folder.getDisplayName());

        // Determines whether the current folder is a predefined folder
        int folderType = folder.getPredefinedType(false);
        String answer = folderType == StandardIpmFolder.Unspecified ? "No" : "Yes, " + folderType;
        System.out.println("Is StandardIpmFolder?: " + answer);

        // Determines whether the current folder is a subfolder of a predefined folder
        if (folderType == StandardIpmFolder.Unspecified) {
            folderType = folder.getPredefinedType(true);
            answer = folderType == StandardIpmFolder.Unspecified ? "No" : "Yes, " + folderType;
            System.out.println("Is subfolder from StandardIpmFolder parent?: " + answer);
        }

        System.out.println();

        checkFolders(folder.getSubFolders());
    }
}
```
## **Obtenga o agregue una carpeta de fuentes RSS estándar en un archivo PST**

Aspose.Email permite recuperar una referencia a la carpeta predefinida que contiene las fuentes RSS. Esto puede resultar útil si desea acceder mediante programación a las fuentes RSS almacenadas en un archivo PST de Outlook y manipularlas. Asigne el valor de las fuentes RSS a [StandardIpmFolder](https://reference.aspose.com/email/java/com.aspose.email/standardipmfolder/) enum.

El siguiente ejemplo de código muestra cómo obtener una carpeta de fuentes RSS:

```java
try (PersonalStorage pst = PersonalStorage.fromFile("my.pst", false)) {
    FolderInfo rssFolder = pst.getPredefinedFolder(StandardIpmFolder.RssFeeds);
}
```
Y el ejemplo de código que aparece a continuación muestra cómo añadir una carpeta de fuentes RSS:

```java
try (PersonalStorage pst = PersonalStorage.create("my.pst", FileFormatVersion.Unicode)) {
    FolderInfo rssFolder = pst.createPredefinedFolder("RSS Feeds", StandardIpmFolder.RssFeeds);
}
```

## **Analizar carpetas en las que se pueden buscar**

Un PST/OST puede contener carpetas con capacidad de búsqueda además del tipo normal de carpetas. Aspose.Email proporciona [FolderKind](https://reference.aspose.com/email/java/com.aspose.email/folderkind/) enumerador para especificar los mensajes de dichas carpetas de búsqueda con [EnumerateFolders](https://reference.aspose.com/email/java/com.aspose.email/folderinfo/#enumerateFolders--) and [GetSubFolders](https://reference.aspose.com/email/java/com.aspose.email/folderinfo/#getSubFolders--) methods.

{{< gist "aspose-com-gists" "709d733586ce50505c3bca3f6e8bd18d" "Examples-src-main-java-com-aspose-email-examples-outlook-pst-ReadOutlookPSTFile-ParseSearchableFolders.java" >}}

## **Recuperar la información de la carpeta principal de MessageInfo**

El siguiente fragmento de código muestra cómo recuperar la información de la carpeta principal de [MessageInfo](https://reference.aspose.com/email/java/com.aspose.email/messageinfo/).

{{< gist "aspose-com-gists" "709d733586ce50505c3bca3f6e8bd18d" "Examples-src-main-java-com-aspose-email-examples-outlook-pst-ReadOutlookPSTFile-RetrieParentFolderInformationFromMessageInfo.java" >}}

## **API de recorrido de archivos PST**

La API transversal permite extraer todos los elementos de PST en la medida de lo posible, sin descartar excepciones, incluso si algunos datos del archivo original están dañados.
Los pasos siguientes muestran cómo usar esta API.

Use [PersonalStorage](https://reference.aspose.com/email/java/com.aspose.email/personalstorage/) constructor y [load](https://reference.aspose.com/email/java/com.aspose.email/personalstorage/#load-java.io.InputStream-) método en lugar del método fromFile.

El constructor permite definir un método de devolución de llamada.

```java
try (PersonalStorage currentPst = new PersonalStorage(new TraversalExceptionsCallback() {
    public void invoke(TraversalAsposeException exception, String itemId) {
        // Exception handling code.
    }
})) {
    //
}
```

Las excepciones de carga y recorrido estarán disponibles mediante el método de devolución de llamada.

The [load](https://reference.aspose.com/email/java/com.aspose.email/personalstorage/#load-java.io.InputStream-) el método devuelve 'true' si el archivo se ha cargado correctamente y es posible recorrerlo más a fondo. Si un archivo está dañado y no es posible recorrerlo, se devuelve «falso».

```java
if (currentPst.load(inputStream))
```

Esto permite abrir y recorrer incluso archivos PST corruptos sin descartar excepciones. Tanto las excepciones como los elementos corruptos se gestionarán mediante el método de devolución de llamada.

```java
try (PersonalStorage pst = new PersonalStorage(new TraversalExceptionsCallback() {
    public void invoke(TraversalAsposeException exception, String itemId) {
        // Exception handling code.
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
