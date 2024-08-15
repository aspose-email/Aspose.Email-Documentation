---
title: "Trabajando con elementos del calendario en un archivo PST"
url: /es/net/working-with-calendar-items-in-pst-file/
weight: 50
type: docs
---


## **Agregar MapiCalendar a PST**

[Crear un nuevo archivo PST y agregar subcarpetas](https://docs.aspose.com/email/es/net/create-new-pst-add-sub-folders-and-messages/#creating-a-new-pst-file-and-add-subfolders) mostró cómo crear un archivo PST y agregarle una subcarpeta. Con Aspose.Email puede agregar MapiCalendar a la subcarpeta Calendario de un archivo PST que haya creado o cargado. A continuación se detallan los pasos para agregar MapiCalendar a un PST:

1. Crea un [MapiCalendar](https://reference.aspose.com/email/net/aspose.email.mapi/mapicalendar/) object.
2. Configure el [MapiCalendar](https://reference.aspose.com/email/net/aspose.email.mapi/mapicalendar/) propiedades que utilizan un constructor y métodos.
3. Cree un PST con el [PersonalStorage.Create()](https://reference.aspose.com/email/net/aspose.email.storage.pst/personalstorage/create/#create/) method.
4. Cree una carpeta predefinida (Calendario) en la raíz del archivo PST. Para ello, acceda a la carpeta raíz y, a continuación, llame al [AddMapiMessageItem()](https://reference.aspose.com/email/net/aspose.email.storage.pst/folderinfo/addmapimessageitem/#addmapimessageitem) method.

El siguiente fragmento de código muestra cómo crear un [MapiCalendar](https://reference.aspose.com/email/net/aspose.email.mapi/mapicalendar/) y, a continuación, agréguelo a la carpeta de calendario de un archivo PST recién creado.

{{< gist "aspose-com-gists" "6e5185a63aec6fd70d83098e82b06a32" "Examples-CSharp-Outlook-AddMapiCalendarToPST-AddMapiCalendarToPST.cs" >}}

## **Guardar los elementos del calendario de PST en el disco en formato ICS**

Este artículo muestra cómo acceder a los elementos del calendario desde un archivo PST de Outlook y guardar el calendario en el disco en formato ICS. Utilice el [PersonalStorage](https://reference.aspose.com/email/net/aspose.email.storage.pst/personalstorage/) and [MapiCalendar](https://reference.aspose.com/email/net/aspose.email.mapi/mapicalendar/) clases para obtener la información del calendario. A continuación se indican los pasos para guardar los elementos del calendario:

1. Cargue el archivo PST en [PersonalStorage](https://reference.aspose.com/email/net/aspose.email.storage.pst/personalstorage/) class.
1. Navega por la carpeta Calendario.
1. Obtenga el contenido de la carpeta Calendario para obtener la colección de mensajes.
1. Recorre la colección de mensajes.
1. Call [PersonalStorage.ExtractMessage()](https://reference.aspose.com/email/net/aspose.email.storage.pst/personalstorage/extractmessage/#extractmessage/) método para obtener la información de contacto en el [MapiCalendar](https://reference.aspose.com/email/net/aspose.email.mapi/mapicalendar/) class.
1. Llame al [MapiCalendar.Save()](https://reference.aspose.com/email/net/aspose.email.mapi/mapicalendar/save/#save/) método para guardar el elemento del calendario en el disco en formato ICS.

El siguiente programa carga un archivo PST desde el disco y guarda todos los elementos del calendario en formato ICS. Los archivos ICS se pueden usar entonces en cualquier otro programa que pueda cargar el archivo de calendario ICS estándar. Abierto en Microsoft Outlook, un archivo ICS tiene el mismo aspecto que el de la siguiente captura de pantalla.

|![todo:image_alt_text](working-with-calendar-items-in-pst-file_1.png)|
|: - |
El siguiente fragmento de código muestra cómo exportar los elementos del calendario del formato PST de Outlook al formato ICS.

{{< gist "aspose-com-gists" "6e5185a63aec6fd70d83098e82b06a32" "Examples-CSharp-Outlook-SaveCalendarItems-SaveCalendarItems.cs" >}}

### **Guardar como ICS con marca de tiempo original**

Las siguientes funciones están disponibles para guardar los elementos del calendario como ICS conservando su información original de fecha y hora:

- [MapiCalendarIcsSaveOptions](https://reference.aspose.com/email/net/aspose.email.mapi/mapicalendaricssaveoptions/) - Permite especificar opciones adicionales al guardar MapiCalendar en formato Ics.

- [MapiCalendarIcsSaveOptions.KeepOriginalDateTimeStamp](https://reference.aspose.com/email/net/aspose.email.mapi/mapicalendaricssaveoptions/keeporiginaldatetimestamp/) - Permite mantener el valor original de DateTimeStamp en el archivo de salida.

Usa el ejemplo de código que aparece a continuación para implementar las funciones en tu proyecto:

```cs
var cal = pst.ExtractMessage(msgInfo).ToMapiMessageItem() as MapiCalendar;

if (cal != null)
{
  cal.Save("cal.ics", new MapiCalendarIcsSaveOptions() { KeepOriginalDateTimeStamp = true});
}
```

## **Modificar o eliminar las ocurrencias de las recurrencias**

Se pueden agregar excepciones a las recurrencias existentes mediante la API Aspose.Email for .NET. El siguiente ejemplo de código ilustra el uso de esta función.

{{< gist "aspose-com-gists" "6e5185a63aec6fd70d83098e82b06a32" "Examples-CSharp-Outlook-ModifyDeleteOccurrenceInRecurrence-ModifyDeleteOccurrenceInRecurrence.cs" >}}
