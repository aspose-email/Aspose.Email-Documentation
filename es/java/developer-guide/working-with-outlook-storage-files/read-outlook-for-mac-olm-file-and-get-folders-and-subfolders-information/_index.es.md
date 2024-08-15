---
title: "Lea el archivo OLM de Outlook para Mac y obtenga información sobre carpetas y subcarpetas"
url: /es/java/read-outlook-for-mac-olm-file-and-get-folders-and-subfolders-information/
weight: 130
type: docs
---

{{% alert color="primary" %}}

Aspose.Email para Java le permite leer los archivos OLM de Outlook para Mac. Puede cargar un archivo OLM desde el disco a una instancia del [OlmStorage](https://reference.aspose.com/email/java/com.aspose.email/olmstorage/) y obtenga la información sobre su contenido, por ejemplo, carpetas, subcarpetas y mensajes.

{{% /alert %}}

## **Abrir archivos en formato OLM**

Los archivos en formato OLM se pueden abrir de dos maneras:

- uso del constructor
- uso del método estático FromFile

Hay diferencias de comportamiento entre estos métodos. Consulte la sección siguiente.

### **Abrir archivos por constructor**

Para abrir un archivo, llame al constructor del [OlmStorage](https://reference.aspose.com/email/java/com.aspose.email/olmstorage/) clase y pasarle el nombre completo del archivo o la secuencia como argumento:

```java
OlmStorage olm = new OlmStorage("fileName");
```

### **Abrir archivos mediante el método estático fromFile**

Para abrir un archivo, utilice el método estático [fromFile](https://reference.aspose.com/email/java/com.aspose.email/olmstorage/#fromFile-java.lang.String-) y pasarle el nombre completo del archivo como argumento:

```java
OlmStorage olm = OlmStorage.fromFile("fileName");
```
### **Abrir archivos mediante el método estático fromStream**

Para abrir un archivo mediante un método estático [fromStream](https://reference.aspose.com/email/java/com.aspose.email/olmstorage/#fromStream-java.io.InputStream-), pásale el nombre de una secuencia como argumento:


## **Leer archivo OLM**

El siguiente fragmento de código muestra cómo cargar el archivo OLM y obtener su contenido.

{{< gist "aspose-com-gists" "709d733586ce50505c3bca3f6e8bd18d" "Examples-src-main-java-com-aspose-email-examples-outlook-olm-LoadAndReadOLMFile.java" >}}

## **Obtener carpetas**

Para recuperar carpetas de un archivo OLM (Outlook para Mac), cárguelo con el [OlmStorage](https://reference.aspose.com/email/java/com.aspose.email/olmstorage/) clase primero y, a continuación, utilice uno de los siguientes métodos según sus necesidades:

- [getFolder (nombre de cadena, booleano ignoreCase)](https://reference.aspose.com/email/java/com.aspose.email/olmstorage/#getFolder-java.lang.String-boolean-) - Obtiene la carpeta por su nombre.
- [getFolders()](https://reference.aspose.com/email/java/com.aspose.email/olmstorage/#getFolders--) - Obtiene la jerarquía de carpetas/colección de carpetas.
- [getFolderHierarchy()](https://reference.aspose.com/email/java/com.aspose.email/olmstorage/#getFolderHierarchy--) - Obtiene la jerarquía de carpetas.

El ejemplo de código siguiente le mostrará cómo obtener una carpeta de un archivo OLM:

```java
// Get the folder by name
OlmStorage olm = OlmStorage.fromFile("fileName");

try {

    OlmFolder inbox = olm.getFolder("inbox", true);

} finally {

    olm.dispose();

}
```
Al usar el [fromFile](https://reference.aspose.com/email/java/com.aspose.email/olmstorage/#fromFile-java.lang.String-) método para abrir un archivo OLM, el [getFolderHierarchy()](https://reference.aspose.com/email/java/com.aspose.email/olmstorage/#getFolderHierarchy--) devolverá un valor nulo. En este caso, llame al [getFolders()](https://reference.aspose.com/email/java/com.aspose.email/olmstorage/#getFolders--) método explícito para recuperar la lista de directorios del archivo OLM.


### **Obtener la ruta de la carpeta**

También puede obtener la ruta de las carpetas del archivo OML. Aspose.Email proporciona [OlmFolder.Path](https://reference.aspose.com/email/java/com.aspose.email/olmfolder/#getPath--) propiedad que devuelve la ruta de la carpeta. El siguiente fragmento de código demuestra el uso de [OlmFolder.Path](https://reference.aspose.com/email/java/com.aspose.email/olmfolder/#getPath--) propiedad para obtener las rutas de las carpetas en el archivo OML.

{{< gist "aspose-com-gists" "709d733586ce50505c3bca3f6e8bd18d" "Examples-src-main-java-com-aspose-email-examples-outlook-olm-GetFolderPathInOLM-1.java" >}}

### **Cuenta el número de elementos de la carpeta**

También puede contar el número de elementos de la carpeta. Aspose.Email proporciona [OlmFolder.MessageCount](https://reference.aspose.com/email/java/com.aspose.email/olmfolder/#getMessageCount--) propiedad que devuelve el número de elementos de la carpeta. El siguiente fragmento de código demuestra el uso de [OlmFolder.MessageCount](https://reference.aspose.com/email/java/com.aspose.email/olmfolder/#getMessageCount--) propiedad para obtener el número de elementos de las carpetas del archivo OML.

{{< gist "aspose-com-gists" "709d733586ce50505c3bca3f6e8bd18d" "Examples-src-main-java-com-aspose-email-examples-outlook-olm-CountItemsInOLMFolder-1.java" >}}

## **Enumerar los mensajes de una carpeta determinada**

Aspose.Email proporciona la API para trabajar con los almacenamientos de OLM y extraer mensajes de una carpeta determinada. El [OlmFolder](https://reference.aspose.com/email/java/com.aspose.email/olmfolder/) and [OlmMessageInfo](https://reference.aspose.com/email/java/com.aspose.email/olmmessageinfo/) las clases representan información breve sobre una carpeta y un mensaje en el almacenamiento, respectivamente. El [OlmFolder](https://reference.aspose.com/email/java/com.aspose.email/olmfolder/) La clase proporciona los siguientes métodos:

- **OlmFolder.getSubFolder**(String subfolderName, boolean ignoreCase): obtiene la subcarpeta por su nombre.

- **OlmFolder.enumerateMapiMessages()** - Expone el enumerador, que admite una iteración de mapiMessages en la carpeta actual.

- **OlmFolder.enumerateMessages()** - Expone el enumerador, que admite una iteración de OLMMessageInfo en la carpeta actual.

- **OlmFolder.enumerateMessages**(int startIndex, int count): expone el enumerador, que admite una iteración de olmMessageInfo dentro de un rango determinado.

- **OlmFolder.enumerateMessages**(consulta MailQuery): expone el enumerador, que admite una iteración de OLMMessageInfo según los criterios de búsqueda.

Los siguientes ejemplos de código demostrarán el uso de estos métodos:

```java
 // Enumerates all messages in a given folder

OlmStorage olm = OlmStorage.fromFile("fileName");

try {

    OlmFolder inbox = olm.getFolder("inbox", true);

   for (OlmMessageInfo messageInfo : inbox.enumerateMessages()) {

        System.out.println(messageInfo.getSubject());

   }

} finally {

    olm.dispose();

}

// Enumerates a range of messages in a given folder

OlmStorage olm = OlmStorage.fromFile("fileName");

try {

    OlmFolder inbox = olm.getFolder("inbox", true);

   int startIndex = 10;

   int count = 100;

   for (OlmMessageInfo messageInfo : inbox.enumerateMessages(startIndex, count)) {

        System.out.println(messageInfo.getSubject());

   }

} finally {

    olm.dispose();

}

// Enumerates messages by search criteria

OlmStorage olm = OlmStorage.fromFile("fileName");

try {

    OlmFolder inbox = olm.getFolder("inbox", true);

    MailQueryBuilder mailQueryBuilder = new MailQueryBuilder();

    mailQueryBuilder.getSubject().contains("invitation");

    mailQueryBuilder.getFrom().contains("Mark");

   for (OlmMessageInfo messageInfo : inbox.enumerateMessages(mailQueryBuilder.getQuery())) {

        System.out.println(messageInfo.getSubject());

   }

} finally {

    olm.dispose();

}

// Enumerates all messages and the extraction of some of them

OlmStorage olm = OlmStorage.fromFile("fileName");

try {

    OlmFolder inbox = olm.getFolder("inbox", true);

   for (OlmMessageInfo messageInfo : inbox.enumerateMessages()) {

       if (messageInfo.hasAttachments()) {

            MapiMessage msg = olm.extractMapiMessage(messageInfo);

       }

   }

} finally {

    olm.dispose();

}
```
## **Extraer mensajes de OLM mediante identificadores**

A veces es necesario extraer los mensajes seleccionados por identificadores. Por ejemplo, su aplicación almacena los identificadores en una base de datos y extrae un mensaje cuando lo solicita. Esta es la forma eficaz de evitar tener que recorrer todo el almacenamiento cada vez para encontrar un mensaje específico que extraer. Para implementar esta función en los archivos OLM, Aspose.Email proporciona los siguientes métodos y clases:

- [EntryId](https://reference.aspose.com/email/java/com.aspose.email/olmmessageinfo/#getEntryId--) propiedad del [OlmMessageInfo](https://reference.aspose.com/email/java/com.aspose.email/olmmessageinfo/) class: obtiene el identificador de entrada del mensaje.
- overloaded [ExtractMapiMessage (identificador de cadena)](https://reference.aspose.com/email/java/com.aspose.email/olmstorage/#extractMapiMessage-java.lang.String-) método del [OlmStorage]() class: obtiene el mensaje de OLM.

El ejemplo de código que aparece a continuación muestra cómo extraer mensajes de OLM mediante identificadores:

```java
for (OlmMessageInfo msgInfo : olmFolder.enumerateMessages()) {
    MapiMessage msg = storage.extractMapiMessage(msgInfo.getEntryId());
}
```
**Note:** El identificador del mensaje es único en el archivo de almacenamiento. Los ID los crea Aspose.Email y no se pueden usar en bibliotecas o aplicaciones de procesamiento de OLM de otros fabricantes.


## **Extraer elementos OLM de archivos corruptos**

Aspose.Email proporciona una API transversal que permite extraer todos los elementos de OLM en la medida de lo posible, sin descartar excepciones, incluso si algunos datos del archivo original están dañados.

Usa el [OLMStorage (devolución de llamada de TraversalExceptions)](https://reference.aspose.com/email/java/com.aspose.email/olmstorage/#OlmStorage-com.aspose.email.TraversalExceptionsCallback-) constructor y el [load (nombre de archivo de cadena)](https://reference.aspose.com/email/java/com.aspose.email/olmstorage/#load-java.lang.String-) método en lugar del [fromFile](https://reference.aspose.com/email/java/com.aspose.email/olmstorage/#fromFile-java.lang.String-) method.

El constructor permite definir un método de devolución de llamada.

```java
OlmStorage olm = new OlmStorage(new TraversalExceptionsCallback() {
    public void invoke(TraversalAsposeException exception, String itemId) {
        /* Exception handling  code. */
    }
});
```
Las excepciones de carga y recorrido estarán disponibles mediante el método de devolución de llamada.

El método load devuelve «true» si el archivo se ha cargado correctamente y es posible recorrerlo más a fondo. Si un archivo está dañado y no es posible recorrerlo, se devuelve un valor «falso».

```java
TraversalExceptionsCallback exceptionsCallback = new TraversalExceptionsCallback() {
    public void invoke(TraversalAsposeException exception, String itemId) {
        /* Exception handling  code. */
    }
};
try (OlmStorage olm = new OlmStorage(exceptionsCallback)) {
    if (olm.load(fileName)) {
        List<OlmFolder> folderHierarchy = olm.getFolders();
        extractItems(olm, folderHierarchy);
    }
}

private static void extractItems(OlmStorage olm, List<OlmFolder> folders) {
    for (OlmFolder folder : folders) {
        if (folder.hasMessages()) {
            System.out.println(folder);

            for (MapiMessage msg : olm.enumerateMessages(folder)) {
                System.out.println(msg.getSubject());
            }
        }

        if (folder.getSubFolders().size() > 0) {
            extractItems(olm, folder.getSubFolders());
        }
    }
}
```
## **Obtener la fecha de modificación del mensaje**

The [OlmMessageInfo.getModifiedDate](https://reference.aspose.com/email/java/com.aspose.email/olmmessageinfo/#getModifiedDate--) Esta propiedad le permite obtener la fecha de modificación del mensaje.

```java
for (OlmMessageInfo messageInfo : inboxFolder.enumerateMessages()) {
    Date modifiedDate = messageInfo.getModifiedDate();
}
```