---
title: "Trabajando con Elementos del Calendario en Archivo PST"
url: /es/java/working-with-calendar-items-in-pst-file/
weight: 50
type: docs
---

## **Agregar MapiCalendar a PST**

[Crear nuevo PST, agregar subcarpetas y mensajes](/email/java/create-new-pst-add-sub-folders-and-messages/) mostró cómo crear un archivo PST y agregarle una subcarpeta. Con Aspose.Email, puedes agregar [MapiCalendar](https://reference.aspose.com/email/java/com.aspose.email/mapicalendar/) a la subcarpeta del Calendario de un archivo PST que hayas creado o cargado.

A continuación se presentan los pasos para agregar [MapiCalendar](https://reference.aspose.com/email/java/com.aspose.email/mapicalendar/) a un PST:

1. Crear un objeto [MapiCalendar](https://reference.aspose.com/email/java/com.aspose.email/mapicalendar/).
1. Configurar las propiedades del [MapiCalendar](https://reference.aspose.com/email/java/com.aspose.email/mapicalendar/) utilizando un constructor y métodos.
1. Crear un PST usando el método [PersonalStorage.create()](https://reference.aspose.com/email/java/com.aspose.email/personalstorage/#create-java.lang.String-int-).
1. Crear una carpeta predefinida (Calendario) en la raíz del archivo PST accediendo a la carpeta raíz y luego llamando al método [addMapiMessageItem()](https://reference.aspose.com/email/java/com.aspose.email/folderinfo/#addMapiMessageItem-com.aspose.email.IMapiMessageItem-).

El código a continuación muestra cómo crear un [MapiCalendar](https://reference.aspose.com/email/java/com.aspose.email/mapicalendar/) y luego agregarlo a la carpeta del Calendario de un archivo PST recién creado.

{{< gist "aspose-com-gists" "709d733586ce50505c3bca3f6e8bd18d" "Examples-src-main-java-com-aspose-email-examples-outlook-pst-AddMapiCalendarToPST-.java" >}}

## **Guardar Elementos del Calendario desde Outlook PST en Disco en formato ICS**

Este artículo muestra cómo acceder a elementos del calendario desde un archivo PST de Outlook y guardar el calendario en el disco en formato ICS. Utiliza las clases [PersonalStorage](https://reference.aspose.com/email/java/com.aspose.email/personalstorage/) y [MapiCalendar](https://reference.aspose.com/email/java/com.aspose.email/mapicalendar/) para obtener la información del calendario.

A continuación se presentan los pasos para guardar los elementos del calendario:

1. Cargar el archivo PST en la clase [PersonalStorage](https://reference.aspose.com/email/java/com.aspose.email/personalstorage/).
1. Explorar la carpeta del Calendario.
1. Obtener el contenido de la carpeta del Calendario para obtener la colección de mensajes.
1. Recorrer la colección de mensajes.
1. Llamar al método [PersonalStorage.extractMessage()](https://reference.aspose.com/email/java/com.aspose.email/personalstorage/#extractMessage-com.aspose.email.MessageInfo-) para obtener la información del contacto en la clase [MapiCalendar](https://reference.aspose.com/email/java/com.aspose.email/mapicalendar/).
1. Llamar al método [MapiCalendar.save()](https://reference.aspose.com/email/java/com.aspose.email/mapicalendar/#save-java.io.OutputStream-) para guardar el elemento del calendario en disco en formato ICS.

El programa a continuación carga un archivo PST desde el disco y guarda todos los elementos del calendario en formato ICS. Los archivos ICS pueden ser utilizados en cualquier otro programa que pueda cargar el archivo de calendario estándar ICS. Si abres cualquier archivo ICS en Microsoft Outlook, se verá como el de la captura de pantalla a continuación.

|![todo:image_alt_text](https://i.imgur.com/OhnGEXj.png)|
| :- |
|**Figura: Elemento del calendario guardado con Aspose.Email**|
{{< gist "aspose-com-gists" "709d733586ce50505c3bca3f6e8bd18d" "Examples-src-main-java-com-aspose-email-examples-outlook-pst-SaveCalendarItemsFromOutlookPSTToDiskInICSFormat-.java" >}}

## **Extraer Elementos del Calendario de un Archivo PST**

La clase MapiCalendar representa un elemento del calendario en el formato MAPI de Microsoft Outlook. Extraer un mensaje de un archivo PST y convertirlo en un elemento de mensaje MAPI. El siguiente ejemplo de código extrae un elemento del calendario de un archivo PST y lo convierte en un objeto MapiCalendar para su manipulación o procesamiento:

```java
MapiCalendar cal = (MapiCalendar) pst.extractMessage(messageInfo).toMapiMessageItem();
```
## **Guardar Elementos del Calendario en formato ICS con Timestamp Original**

Utiliza el ejemplo de código anterior para extraer un elemento del calendario de un archivo PST y luego especificar opciones adicionales para guardarlo como ICS con el timestamp original utilizando el método [setKeepOriginalDateTimeStamp](https://reference.aspose.com/email/java/com.aspose.email/mapicalendaricssaveoptions/#setKeepOriginalDateTimeStamp-boolean-) de la clase [MapiCalendarIcsSaveOptions](https://reference.aspose.com/email/java/com.aspose.email/mapicalendaricssaveoptions/):

```java
MapiCalendar cal = (MapiCalendar) pst.extractMessage(messageInfo).toMapiMessageItem();

if (cal != null) {
    MapiCalendarIcsSaveOptions so = new MapiCalendarIcsSaveOptions();
    so.setKeepOriginalDateTimeStamp(true);
    cal.save("cal.ics", so);
}
```
## **Modificar/Eliminar Ocurrencias de Recurrencias**

{{< gist "aspose-com-gists" "709d733586ce50505c3bca3f6e8bd18d" "Examples-src-main-java-com-aspose-email-examples-outlook-pst-ModifyDeleteOccurrencesFromRecurrence-ModifyDeleteOccurrencesFromRecurrence.java" >}}