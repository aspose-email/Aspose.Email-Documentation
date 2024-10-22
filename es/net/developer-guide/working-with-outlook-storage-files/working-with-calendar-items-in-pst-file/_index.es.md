---
title: "Trabajando con elementos de calendario en archivo PST"
url: /es/net/working-with-calendar-items-in-pst-file/
weight: 50
type: docs
---


## **Agregar MapiCalendar a PST**

[Crear un nuevo archivo PST y agregar subcarpetas](https://docs.aspose.com/email/es/net/create-new-pst-add-sub-folders-and-messages/#creating-a-new-pst-file-and-add-subfolders) mostró cómo crear un archivo PST y agregarle una subcarpeta. Con Aspose.Email puedes agregar MapiCalendar a la subcarpeta de Calendario de un archivo PST que has creado o cargado. A continuación se detallan los pasos para agregar MapiCalendar a un PST:

1. Crear un [MapiCalendar](https://reference.aspose.com/email/net/aspose.email.mapi/mapicalendar/) objeto.
2. Establecer las propiedades de [MapiCalendar](https://reference.aspose.com/email/net/aspose.email.mapi/mapicalendar/) utilizando un constructor y métodos.
3. Crear un PST usando el método [PersonalStorage.Create()](https://reference.aspose.com/email/net/aspose.email.storage.pst/personalstorage/create/#create/).
4. Crear una carpeta predefinida (Calendario) en la raíz del archivo PST accediendo a la carpeta raíz y luego llamando al método [AddMapiMessageItem()](https://reference.aspose.com/email/net/aspose.email.storage.pst/folderinfo/addmapimessageitem/#addmapimessageitem).

El siguiente fragmento de código te muestra cómo crear un [MapiCalendar](https://reference.aspose.com/email/net/aspose.email.mapi/mapicalendar/) y luego agregarlo a la carpeta de calendario de un archivo PST recién creado.

{{< gist "aspose-com-gists" "6e5185a63aec6fd70d83098e82b06a32" "Examples-CSharp-Outlook-AddMapiCalendarToPST-AddMapiCalendarToPST.cs" >}}

## **Guardar elementos de calendario de PST en disco en formato ICS**

Este artículo muestra cómo acceder a elementos de calendario de un archivo PST de Outlook y guardar el calendario en disco en formato ICS. Usa las clases [PersonalStorage](https://reference.aspose.com/email/net/aspose.email.storage.pst/personalstorage/) y [MapiCalendar](https://reference.aspose.com/email/net/aspose.email.mapi/mapicalendar/) para obtener la información del calendario. A continuación se detallan los pasos para guardar elementos de calendario:

1. Cargar el archivo PST en la clase [PersonalStorage](https://reference.aspose.com/email/net/aspose.email.storage.pst/personalstorage/).
2. Navegar a la carpeta de Calendario.
3. Obtener el contenido de la carpeta de Calendario para obtener la colección de mensajes.
4. Recorrer la colección de mensajes.
5. Llamar al método [PersonalStorage.ExtractMessage()](https://reference.aspose.com/email/net/aspose.email.storage.pst/personalstorage/extractmessage/#extractmessage/) para obtener la información de contacto en la clase [MapiCalendar](https://reference.aspose.com/email/net/aspose.email.mapi/mapicalendar/).
6. Llamar al método [MapiCalendar.Save()](https://reference.aspose.com/email/net/aspose.email.mapi/mapicalendar/save/#save/) para guardar el elemento del calendario en disco en formato ICS.

El programa a continuación carga un archivo PST desde el disco y guarda todos los elementos del calendario en formato ICS. Los archivos ICS pueden luego ser utilizados en cualquier otro programa que pueda cargar el archivo estándar de calendario ICS. Abierto en Microsoft Outlook, un archivo ICS se ve como el de la captura de pantalla a continuación.

|![todo:image_alt_text](working-with-calendar-items-in-pst-file_1.png)|
| :- |
El siguiente fragmento de código te muestra cómo exportar los elementos del calendario de PST de Outlook a formato ICS.

{{< gist "aspose-com-gists" "6e5185a63aec6fd70d83098e82b06a32" "Examples-CSharp-Outlook-SaveCalendarItems-SaveCalendarItems.cs" >}}

### **Guardar como ICS con la marca de tiempo original**

Las siguientes funciones están disponibles para guardar elementos de calendario como ICS preservando su información original de fecha y hora:

- [MapiCalendarIcsSaveOptions](https://reference.aspose.com/email/net/aspose.email.mapi/mapicalendaricssaveoptions/) - Permite especificar opciones adicionales al guardar MapiCalendar en formato Ics.

- [MapiCalendarIcsSaveOptions.KeepOriginalDateTimeStamp](https://reference.aspose.com/email/net/aspose.email.mapi/mapicalendaricssaveoptions/keeporiginaldatetimestamp/) - Permite mantener el valor original de DateTimeStamp en el archivo de salida.

Utiliza el siguiente ejemplo de código para implementar las funciones en tu proyecto:

```cs
var cal = pst.ExtractMessage(msgInfo).ToMapiMessageItem() as MapiCalendar;

if (cal != null)
{
  cal.Save("cal.ics", new MapiCalendarIcsSaveOptions() { KeepOriginalDateTimeStamp = true});
}
```

## **Modificar/Eliminar ocurrencias de recurrencias**

Las excepciones pueden ser añadidas a recurrencias existentes utilizando el API Aspose.Email para .NET. El siguiente ejemplo de código ilustra el uso de esta función.

{{< gist "aspose-com-gists" "6e5185a63aec6fd70d83098e82b06a32" "Examples-CSharp-Outlook-ModifyDeleteOccurrenceInRecurrence-ModifyDeleteOccurrenceInRecurrence.cs" >}}