---
title: "Trabajando con elementos del calendario en un archivo PST"
url: /es/cpp/working-with-calendar-items-in-pst-file/
weight: 50
type: docs
---

## **Agregar MapiCalendar a PST**
Crear un nuevo archivo PST y agregar subcarpetas mostró cómo crear un archivo PST y agregarle una subcarpeta. Con Aspose.Email puede agregar MapiCalendar a la subcarpeta Calendario de un archivo PST que haya creado o cargado. A continuación se detallan los pasos para agregar MapiCalendar a un PST:

1. Cree un objeto MapiCalendar.
1. Establezca las propiedades de MapiCalendar mediante un constructor y métodos.
1. Cree un PST con el método PersonalStorage.create ().
1. Cree una carpeta predefinida (Calendario) en la raíz del archivo PST accediendo a la carpeta raíz y, a continuación, llamando al método addMapIMessageItem ().

El siguiente fragmento de código muestra cómo crear un MapiCalendar y, a continuación, añadirlo a la carpeta de calendario de un archivo PST recién creado.



{{< gist "aspose-email" "ef0db907527892c88c557bb418093cee" "Examples-EmailCPP-Outlook-AddMapiCalendarToPST-AddMapiCalendarToPST.cpp" >}}
## **Guardar los elementos del calendario de PST en el disco en formato ICS**
En este artículo se muestra cómo acceder a los elementos del calendario desde un archivo PST de Outlook y guardar el calendario en el disco en formato ICS. Utilice las clases PersonalStorage y MapiCalendar para obtener la información del calendario. A continuación se indican los pasos para guardar los elementos del calendario:

1. Cargue el archivo PST en la clase PersonalStorage.
1. Navega por la carpeta Calendario.
1. Obtenga el contenido de la carpeta Calendario para obtener la colección de mensajes.
1. Recorre la colección de mensajes.
1. Llama al método PersonalStorage.extractMessage () para obtener la información de contacto de la clase MapiCalendar.
1. Llame al método MapiCalendar.save () para guardar el elemento del calendario en el disco en formato ICS.

El siguiente programa carga un archivo PST desde el disco y guarda todos los elementos del calendario en formato ICS. Los archivos ICS se pueden usar entonces en cualquier otro programa que pueda cargar el archivo de calendario ICS estándar. Abierto en Microsoft Outlook, un archivo ICS tiene el mismo aspecto que el de la siguiente captura de pantalla.

|![todo:image_alt_text](working-with-calendar-items-in-pst-file_1.png)|
|: - |
El siguiente fragmento de código muestra cómo exportar los elementos del calendario del formato PST de Outlook al formato ICS.



{{< gist "aspose-email" "ef0db907527892c88c557bb418093cee" "Examples-EmailCPP-Outlook-SaveCalendarItems-SaveCalendarItems.cpp" >}}
