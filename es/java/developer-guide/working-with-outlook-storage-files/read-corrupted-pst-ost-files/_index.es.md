---
title: "Leer archivos PST/OST corruptos"
url: /es/java/read-corrupted-pst-ost-files/
weight: 112
type: docs
---

## **Leer archivos PST/OST corruptos**

A veces puede que no sea posible leer el PST/OST debido a algunos problemas. Por ejemplo, algunos bloques de datos pueden estar dañados. En tales casos, suelen surgir excepciones al llamar al [EnumerateFolders](https://reference.aspose.com/email/java/com.aspose.email/folderinfo/#enumerateFolders--), [EnumerateMessages](https://reference.aspose.com/email/java/com.aspose.email/folderinfo/#enumerateMessages--), [GetContents](https://reference.aspose.com/email/java/com.aspose.email/folderinfo/#getContents--), [GetSubfolders](https://reference.aspose.com/email/java/com.aspose.email/folderinfo/#getSubFolders--), etc. métodos. Sin embargo, es posible que los mensajes o carpetas individuales permanezcan intactos en el almacenamiento.

Los usuarios de Aspose.Email pueden encontrar los identificadores de los artículos de forma jerárquica. Además, puede extraer los elementos por identificadores. Para ello, la biblioteca ofrece los siguientes métodos:

- [PersonalStorage.findMessages (cadena ParentEntryID)](https://reference.aspose.com/email/java/com.aspose.email/personalstorage/#findMessages-java.lang.String-) - busca los identificadores de los mensajes de la carpeta.
- [PersonalStorage.findSubfolders (cadena ParentEntryID)](https://reference.aspose.com/email/java/com.aspose.email/personalstorage/#findSubfolders-java.lang.String-) - busca los identificadores de las subcarpetas de la carpeta.

**Note**, que a pesar de las ventajas, hay almacenamientos corruptos que no se pueden leer ni siquiera con estos métodos.

El siguiente fragmento de código muestra el uso de estos métodos para leer archivos PST/OST dañados:

```java
try (PersonalStorage pst = PersonalStorage.fromFile(fileName)) {
    exploreCorruptedPst(pst, pst.getRootFolder().getEntryIdString());
}

public static void exploreCorruptedPst(PersonalStorage pst, String rootFolderId) {
    Iterable<String> messageIdList = pst.findMessages(rootFolderId);

    for (String messageId : messageIdList) {
        try {
            MapiMessage msg = pst.extractMessage(messageId);
            System.out.println("- " + msg.getSubject());
        } catch (Exception e) {
            System.out.println("Message reading error. Entry id: " + messageId);
        }
    }

    Iterable<String> folderIdList = pst.findSubfolders(rootFolderId);

    for (String subFolderId : folderIdList) {
        if (subFolderId != rootFolderId) {
            try {
                FolderInfo subfolder = pst.getFolderById(subFolderId);
                System.out.println(subfolder.getDisplayName());
            } catch (Exception e) {
                System.out.println("Message reading error. Entry id: " + subFolderId);
            }

            exploreCorruptedPst(pst, subFolderId);
        }
    }
}
```
## **Extraer elementos PST de archivos corruptos**

La API transversal permite extraer todos los elementos de PST en la medida de lo posible, sin descartar excepciones, incluso si algunos datos del archivo original están dañados.

Usa el [Almacenamiento personal (devolución de llamada de Traversal Exceptions)](https://reference.aspose.com/email/java/com.aspose.email/personalstorage/#PersonalStorage-com.aspose.email.TraversalExceptionsCallback-) constructor y el [load (nombre de archivo de cadena)](https://reference.aspose.com/email/java/com.aspose.email/personalstorage/#load-java.lang.String-) método en lugar del [fromFile](https://reference.aspose.com/email/java/com.aspose.email/personalstorage/#fromFile-java.lang.String-) method.

El constructor permite definir un método de devolución de llamada.

```java
TraversalExceptionsCallback exceptionsCallback = new TraversalExceptionsCallback() {
    @Override
    public void invoke(TraversalAsposeException exception, String itemId) {
        /* Exception handling  code. */
    }
};

try (PersonalStorage pst = new PersonalStorage(exceptionsCallback)) { }
```
Las excepciones de carga y recorrido estarán disponibles mediante el método de devolución de llamada.

El método load devuelve «true» si el archivo se ha cargado correctamente y es posible recorrerlo más a fondo. Si un archivo está dañado y no es posible recorrerlo, se devuelve un valor «falso».

```java
if (currentPst.load(inputStream))
```
El siguiente ejemplo de código muestra cómo implementar la API de recorrido de archivos PST en un proyecto:

```java
public static void main(String[] args) {
    TraversalExceptionsCallback exceptionsCallback = new TraversalExceptionsCallback() {
        @Override
        public void invoke(TraversalAsposeException exception, String itemId) {
            /* Exception handling  code. */
        }
    };

    try (PersonalStorage pst = new PersonalStorage(exceptionsCallback)) {
        if (pst.load("test.pst")) {
            getAllMessages(pst, pst.getRootFolder());
        }
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