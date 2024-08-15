---
title: "Trabajando con elementos del calendario en un archivo PST"
url: /es/java/working-with-calendar-items-in-pst-file/
weight: 50
type: docs
---

## **Agregar MapiCalendar a PST**

[Crear un nuevo PST, agregar subcarpetas y mensajes](/email/java/create-new-pst-add-sub-folders-and-messages/) mostró cómo crear un archivo PST y agregarle una subcarpeta. Con Aspose.Email puedes agregar [MapiCalendar](https://reference.aspose.com/email/java/com.aspose.email/mapicalendar/) a la subcarpeta Calendario de un archivo PST que haya creado o cargado.

A continuación se muestran los pasos para agregar [MapiCalendar](https://reference.aspose.com/email/java/com.aspose.email/mapicalendar/) a un PST:

1. Crea un [MapiCalendar](https://reference.aspose.com/email/java/com.aspose.email/mapicalendar/) object.
1. Configure el [MapiCalendar](https://reference.aspose.com/email/java/com.aspose.email/mapicalendar/) propiedades que utilizan un constructor y métodos.
1. Cree un PST con el [PersonalStorage.create()](https://reference.aspose.com/email/java/com.aspose.email/personalstorage/#create-java.lang.String-int-) method.
1. Cree una carpeta predefinida (Calendario) en la raíz del archivo PST. Para ello, acceda a la carpeta raíz y, a continuación, llame al [addMapiMessageItem()](https://reference.aspose.com/email/java/com.aspose.email/folderinfo/#addMapiMessageItem-com.aspose.email.IMapiMessageItem-) method.

El siguiente fragmento de código muestra cómo crear un [MapiCalendar](https://reference.aspose.com/email/java/com.aspose.email/mapicalendar/) y, a continuación, agréguelo a la carpeta Calendario de un archivo PST recién creado.

{{< gist "aspose-com-gists" "709d733586ce50505c3bca3f6e8bd18d" "Examples-src-main-java-com-aspose-email-examples-outlook-pst-AddMapiCalendarToPST-.java" >}}

## **Guarde los elementos del calendario de Outlook PST en el disco en formato ICS**

Este artículo muestra cómo acceder a los elementos del calendario desde un archivo PST de Outlook y guardar el calendario en el disco en formato ICS. Utiliza el [PersonalStorage](https://reference.aspose.com/email/java/com.aspose.email/personalstorage/) and [MapiCalendar](https://reference.aspose.com/email/java/com.aspose.email/mapicalendar/) clases para obtener la información del calendario.

A continuación se indican los pasos para guardar los elementos del calendario:

1. Cargue el archivo PST en [PersonalStorage](https://reference.aspose.com/email/java/com.aspose.email/personalstorage/) class.
1. Navega por la carpeta Calendario.
1. Obtenga el contenido de la carpeta Calendario para obtener la colección de mensajes.
1. Recorre la colección de mensajes.
1. Llame al [PersonalStorage.extractMessage()](https://reference.aspose.com/email/java/com.aspose.email/personalstorage/#extractMessage-com.aspose.email.MessageInfo-) método para obtener la información de contacto en el [MapiCalendar](https://reference.aspose.com/email/java/com.aspose.email/mapicalendar/) class.
1. Llame al [MapiCalendar.save()](https://reference.aspose.com/email/java/com.aspose.email/mapicalendar/#save-java.io.OutputStream-) método para guardar el elemento del calendario en el disco en formato ICS.

El siguiente programa carga un archivo PST desde el disco y guarda todos los elementos del calendario en formato ICS. Los archivos ICS se pueden usar entonces en cualquier otro programa que pueda cargar el archivo de calendario ICS estándar. Si abres cualquier archivo ICS en Microsoft Outlook, tendrá el mismo aspecto que el de la siguiente captura de pantalla.

|![todo:image_alt_text](https://i.imgur.com/OhnGEXj.png)|
|: - |
|**Figura: Elemento de calendario guardado con Aspose.Email**|
{{< gist "aspose-com-gists" "709d733586ce50505c3bca3f6e8bd18d" "Examples-src-main-java-com-aspose-email-examples-outlook-pst-SaveCalendarItemsFromOutlookPSTToDiskInICSFormat-.java" >}}

## **Extraer elementos del calendario de un archivo PST**

La clase MapiCalendar representa un elemento del calendario en el formato MAPI de Microsoft Outlook. Extraiga un mensaje de un archivo PST y conviértalo en un elemento de mensaje MAPI. El siguiente ejemplo de código extrae un elemento de calendario de un archivo PST y lo convierte en un objeto MAPICalendar para su posterior manipulación o procesamiento:

```java
MapiCalendar cal = (MapiCalendar) pst.extractMessage(messageInfo).toMapiMessageItem();
```
## **Guarde los elementos del calendario en formato ICS con la marca de tiempo original**

Utilice el ejemplo de código anterior para extraer un elemento del calendario de un archivo PST y, a continuación, especifique opciones adicionales para guardarlo como ICS con la marca de hora original mediante el [setKeepOriginalDateTimeStamp](https://reference.aspose.com/email/java/com.aspose.email/mapicalendaricssaveoptions/#setKeepOriginalDateTimeStamp-boolean-) método del [MapiCalendarIcsSaveOptions](https://reference.aspose.com/email/java/com.aspose.email/mapicalendaricssaveoptions/) class:

```java
MapiCalendar cal = (MapiCalendar) pst.extractMessage(messageInfo).toMapiMessageItem();

if (cal != null) {
    MapiCalendarIcsSaveOptions so = new MapiCalendarIcsSaveOptions();
    so.setKeepOriginalDateTimeStamp(true);
    cal.save("cal.ics", so);
}
```
## **Modificar o eliminar las ocurrencias de las recurrencias**

{{< gist "aspose-com-gists" "709d733586ce50505c3bca3f6e8bd18d" "Examples-src-main-java-com-aspose-email-examples-outlook-pst-ModifyDeleteOccurrencesFromRecurrence-ModifyDeleteOccurrencesFromRecurrence.java" >}}
