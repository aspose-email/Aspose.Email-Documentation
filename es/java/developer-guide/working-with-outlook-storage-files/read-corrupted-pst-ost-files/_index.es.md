---
title: "Leer archivos PST/OST corruptos"
url: /es/java/read-corrupted-pst-ost-files/
weight: 112
type: docs
---

## **Leer archivos PST/OST corruptos**

A veces puede no ser posible leer el PST/OST debido a algunos problemas. Por ejemplo, algunos bloques de datos pueden estar corruptos. En tales casos, generalmente ocurren excepciones al llamar a los métodos [EnumerateFolders](https://reference.aspose.com/email/java/com.aspose.email/folderinfo/#enumerateFolders--), [EnumerateMessages](https://reference.aspose.com/email/java/com.aspose.email/folderinfo/#enumerateMessages--), [GetContents](https://reference.aspose.com/email/java/com.aspose.email/folderinfo/#getContents--), [GetSubfolders](https://reference.aspose.com/email/java/com.aspose.email/folderinfo/#getSubFolders--), etc. Sin embargo, los mensajes o carpetas individuales pueden permanecer intactos en el almacenamiento.

Los usuarios de Aspose.Email pueden encontrar identificadores de elementos de manera jerárquica. A continuación, puedes extraer elementos por identificadores. Para este propósito, la biblioteca ofrece los siguientes métodos:

- [PersonalStorage.findMessages(String parentEntryId)](https://reference.aspose.com/email/java/com.aspose.email/personalstorage/#findMessages-java.lang.String-) - encuentra los identificadores de mensajes para la carpeta.
- [PersonalStorage.findSubfolders(String parentEntryId)](https://reference.aspose.com/email/java/com.aspose.email/personalstorage/#findSubfolders-java.lang.String-) - encuentra los identificadores de subcarpetas para la carpeta.

**Nota**, que a pesar de las ventajas, hay almacenes corruptos que no se pueden leer incluso usando estos métodos.

El siguiente fragmento de código demuestra el uso de estos métodos para leer archivos PST/OST corruptos:

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
            System.out.println("Error al leer el mensaje. ID de entrada: " + messageId);
        }
    }

    Iterable<String> folderIdList = pst.findSubfolders(rootFolderId);

    for (String subFolderId : folderIdList) {
        if (subFolderId != rootFolderId) {
            try {
                FolderInfo subfolder = pst.getFolderById(subFolderId);
                System.out.println(subfolder.getDisplayName());
            } catch (Exception e) {
                System.out.println("Error al leer el mensaje. ID de entrada: " + subFolderId);
            }

            exploreCorruptedPst(pst, subFolderId);
        }
    }
}
```
## **Extraer elementos PST de archivos corruptos**

La API de recorrido permite extraer todos los elementos PST en la medida de lo posible, sin lanzar excepciones, incluso si algunos datos del archivo original están corruptos.

Utiliza el constructor [PersonalStorage(TraversalExceptionsCallback callback)](https://reference.aspose.com/email/java/com.aspose.email/personalstorage/#PersonalStorage-com.aspose.email.TraversalExceptionsCallback-) y el método [load(String fileName)](https://reference.aspose.com/email/java/com.aspose.email/personalstorage/#load-java.lang.String-) en lugar del método [fromFile](https://reference.aspose.com/email/java/com.aspose.email/personalstorage/#fromFile-java.lang.String-).

El constructor permite definir un método de callback.

```java
TraversalExceptionsCallback exceptionsCallback = new TraversalExceptionsCallback() {
    @Override
    public void invoke(TraversalAsposeException exception, String itemId) {
        /* Código de manejo de excepciones. */
    }
};

try (PersonalStorage pst = new PersonalStorage(exceptionsCallback)) { }
```
Las excepciones de carga y recorrido estarán disponibles a través del método de callback.

El método load devuelve 'true' si el archivo se ha cargado correctamente y es posible un recorrido posterior. Si un archivo está corrupto y no se puede recorrer, se devuelve 'false'.

```java
if (currentPst.load(inputStream))
```
El siguiente fragmento de código muestra cómo implementar la API de recorrido de archivos PST en un proyecto:

```java
public static void main(String[] args) {
    TraversalExceptionsCallback exceptionsCallback = new TraversalExceptionsCallback() {
        @Override
        public void invoke(TraversalAsposeException exception, String itemId) {
            /* Código de manejo de excepciones. */
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