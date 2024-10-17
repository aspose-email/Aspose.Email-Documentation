---
title: "Leer archivo OLM de Outlook para Mac y obtener información de carpetas y subcarpetas"
url: /es/java/read-outlook-for-mac-olm-file-and-get-folders-and-subfolders-information/
weight: 130
type: docs
---

{{% alert color="primary" %}} 

Aspose.Email para Java te permite leer archivos OLM de Outlook para Mac. Puedes cargar un archivo OLM desde el disco en una instancia de la clase [OlmStorage](https://reference.aspose.com/email/java/com.aspose.email/olmstorage/) y obtener información sobre su contenido, por ejemplo, carpetas, subcarpetas y mensajes.

{{% /alert %}} 

## **Abrir archivos en formato OLM**

Los archivos en formato OLM se pueden abrir de dos maneras:

- utilizando el constructor
- utilizando el método estático FromFile

Hay diferencias en el comportamiento entre estos métodos. Consulta la sección a continuación.

### **Abrir archivos por constructor**

Para abrir un archivo, llama al constructor de la clase [OlmStorage](https://reference.aspose.com/email/java/com.aspose.email/olmstorage/) y pasa el nombre completo del archivo o un flujo como argumento:

```java
OlmStorage olm = new OlmStorage("fileName");
```

### **Abrir archivos utilizando el método estático FromFile**

Para abrir un archivo, utiliza el método estático [fromFile](https://reference.aspose.com/email/java/com.aspose.email/olmstorage/#fromFile-java.lang.String-) y pasa el nombre completo del archivo como argumento:

```java
OlmStorage olm = OlmStorage.fromFile("fileName");
```
### **Abrir archivos utilizando el método estático FromStream**

Para abrir un archivo utilizando el método estático [fromStream](https://reference.aspose.com/email/java/com.aspose.email/olmstorage/#fromStream-java.io.InputStream-), pasa un nombre de flujo como argumento:

## **Leer archivo OLM**

El siguiente fragmento de código te muestra cómo cargar el archivo OLM y obtener su contenido.

{{< gist "aspose-com-gists" "709d733586ce50505c3bca3f6e8bd18d" "Examples-src-main-java-com-aspose-email-examples-outlook-olm-LoadAndReadOLMFile.java" >}}

## **Obtener carpetas**

Para recuperar carpetas de un archivo OLM (Outlook para Mac), primero cárgalo con la clase [OlmStorage](https://reference.aspose.com/email/java/com.aspose.email/olmstorage/) y luego utiliza uno de los siguientes métodos dependiendo de tus necesidades:

- [getFolder(String name, boolean ignoreCase)](https://reference.aspose.com/email/java/com.aspose.email/olmstorage/#getFolder-java.lang.String-boolean-) - Obtiene la carpeta por nombre.
- [getFolders()](https://reference.aspose.com/email/java/com.aspose.email/olmstorage/#getFolders--) - Obtiene la jerarquía de carpetas/colectión de carpetas.
- [getFolderHierarchy()](https://reference.aspose.com/email/java/com.aspose.email/olmstorage/#getFolderHierarchy--) - Obtiene la jerarquía de carpetas.

El siguiente ejemplo de código te mostrará cómo obtener una carpeta de un archivo OLM:

```java
// Obtener la carpeta por nombre
OlmStorage olm = OlmStorage.fromFile("fileName");

try {

    OlmFolder inbox = olm.getFolder("inbox", true);

} finally {

    olm.dispose();

}
```
Al usar el método [fromFile](https://reference.aspose.com/email/java/com.aspose.email/olmstorage/#fromFile-java.lang.String-) para abrir un archivo OLM, el método [getFolderHierarchy()](https://reference.aspose.com/email/java/com.aspose.email/olmstorage/#getFolderHierarchy--) devolverá null. En este caso, llama al método [getFolders()](https://reference.aspose.com/email/java/com.aspose.email/olmstorage/#getFolders--) explícitamente para recuperar la lista de directorios en el archivo OLM.

### **Obtener ruta de la carpeta**

También puedes obtener la ruta de la carpeta de las carpetas en el archivo OML. Aspose.Email proporciona la propiedad [OlmFolder.Path](https://reference.aspose.com/email/java/com.aspose.email/olmfolder/#getPath--) que devuelve la ruta de la carpeta. El siguiente fragmento de código demuestra el uso de la propiedad [OlmFolder.Path](https://reference.aspose.com/email/java/com.aspose.email/olmfolder/#getPath--) para obtener las rutas de las carpetas en el archivo OML.

{{< gist "aspose-com-gists" "709d733586ce50505c3bca3f6e8bd18d" "Examples-src-main-java-com-aspose-email-examples-outlook-olm-GetFolderPathInOLM-1.java" >}}

### **Contar el número de elementos en la carpeta**

También puedes contar el número de elementos en la carpeta. Aspose.Email proporciona la propiedad [OlmFolder.MessageCount](https://reference.aspose.com/email/java/com.aspose.email/olmfolder/#getMessageCount--) que devuelve el número de elementos en la carpeta. El siguiente fragmento de código demuestra el uso de la propiedad [OlmFolder.MessageCount](https://reference.aspose.com/email/java/com.aspose.email/olmfolder/#getMessageCount--) para obtener el número de elementos en las carpetas del archivo OML.

{{< gist "aspose-com-gists" "709d733586ce50505c3bca3f6e8bd18d" "Examples-src-main-java-com-aspose-email-examples-outlook-olm-CountItemsInOLMFolder-1.java" >}}

## **Enumerar mensajes desde una carpeta dada**

Aspose.Email proporciona la API para trabajar con almacenamientos OLM y extraer mensajes de una carpeta dada. Las clases [OlmFolder](https://reference.aspose.com/email/java/com.aspose.email/olmfolder/) y [OlmMessageInfo](https://reference.aspose.com/email/java/com.aspose.email/olmmessageinfo/) representan información breve sobre una carpeta y un mensaje en el almacenamiento, respectivamente. La clase [OlmFolder](https://reference.aspose.com/email/java/com.aspose.email/olmfolder/) proporciona los siguientes métodos:

- **OlmFolder.getSubFolder**(String subfolderName, boolean ignoreCase) - Obtiene la subcarpeta por nombre.

- **OlmFolder.enumerateMapiMessages()** - Expone el enumerador, que soporta la iteración de MapiMessages en la carpeta actual.

- **OlmFolder.enumerateMessages()** - Expone el enumerador, que soporta la iteración de OlmMessageInfo en la carpeta actual.

- **OlmFolder.enumerateMessages**(int startIndex, int count) - Expone el enumerador, que soporta la iteración de OlmMessageInfo dentro de un rango dado.

- **OlmFolder.enumerateMessages**(MailQuery query) - Expone el enumerador, que soporta la iteración de OlmMessageInfo por criterios de búsqueda.

Los ejemplos de código a continuación demostrarán el uso de estos métodos:

```java
 // Enumera todos los mensajes en una carpeta dada

OlmStorage olm = OlmStorage.fromFile("fileName");

try {

    OlmFolder inbox = olm.getFolder("inbox", true);

   for (OlmMessageInfo messageInfo : inbox.enumerateMessages()) {

        System.out.println(messageInfo.getSubject());

   }

} finally {

    olm.dispose();

}

// Enumera un rango de mensajes en una carpeta dada

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

// Enumera mensajes por criterios de búsqueda

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

// Enumera todos los mensajes y la extracción de algunos de ellos

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
## **Extraer mensajes de OLM por identificadores**

A veces es necesario extraer mensajes seleccionados por identificadores. Por ejemplo, tu aplicación almacena identificadores en una base de datos y extrae un mensaje a pedido. Esta es la forma eficiente de evitar recorrer todo el almacenamiento cada vez para encontrar un mensaje específico a extraer. Para implementar esta característica para archivos OLM, Aspose.Email proporciona los siguientes métodos y clases:

- La propiedad [EntryId](https://reference.aspose.com/email/java/com.aspose.email/olmmessageinfo/#getEntryId--) de la clase [OlmMessageInfo](https://reference.aspose.com/email/java/com.aspose.email/olmmessageinfo/) - Obtiene el identificador de entrada del mensaje.
- El método sobrecargado [extractMapiMessage(String id)](https://reference.aspose.com/email/java/com.aspose.email/olmstorage/#extractMapiMessage-java.lang.String-) de la clase [OlmStorage]() - Obtiene el mensaje de OLM.

El ejemplo de código a continuación demuestra cómo extraer mensajes de OLM por identificadores:

```java
for (OlmMessageInfo msgInfo : olmFolder.enumerateMessages()) {
    MapiMessage msg = storage.extractMapiMessage(msgInfo.getEntryId());
}
```
**Nota:** El ID del mensaje es único dentro del archivo de almacenamiento. Los IDs son creados por Aspose.Email y no pueden ser utilizados en otras bibliotecas o aplicaciones de procesamiento OLM de terceros.

## **Extraer elementos OLM de archivos corruptos**

Aspose.Email proporciona una API de recorrido que permite extraer todos los elementos OLM tanto como sea posible, sin lanzar excepciones, incluso si algunos datos del archivo original están corruptos.

Utiliza el constructor [OlmStorage(TraversalExceptionsCallback callback)](https://reference.aspose.com/email/java/com.aspose.email/olmstorage/#OlmStorage-com.aspose.email.TraversalExceptionsCallback-) y el método [load(String fileName)](https://reference.aspose.com/email/java/com.aspose.email/olmstorage/#load-java.lang.String-) en lugar del método [fromFile](https://reference.aspose.com/email/java/com.aspose.email/olmstorage/#fromFile-java.lang.String-).

El constructor permite definir un método de callback.

```java
OlmStorage olm = new OlmStorage(new TraversalExceptionsCallback() {
    public void invoke(TraversalAsposeException exception, String itemId) {
        /* Código de manejo de excepciones. */
    }
});
```
Las excepciones de carga y recorrido estarán disponibles a través del método de callback.

El método load devuelve 'true' si el archivo se ha cargado correctamente y es posible un recorrido más. Si un archivo está corrupto y no es posible el recorrido, se devuelve 'false'.

```java
TraversalExceptionsCallback exceptionsCallback = new TraversalExceptionsCallback() {
    public void invoke(TraversalAsposeException exception, String itemId) {
        /* Código de manejo de excepciones. */
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
## **Obtener fecha de modificación del mensaje**

La propiedad [OlmMessageInfo.getModifiedDate](https://reference.aspose.com/email/java/com.aspose.email/olmmessageinfo/#getModifiedDate--) te permite obtener la fecha de modificación del mensaje.

```java
for (OlmMessageInfo messageInfo : inboxFolder.enumerateMessages()) {
    Date modifiedDate = messageInfo.getModifiedDate();
}
```