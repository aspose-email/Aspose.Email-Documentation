---
title: "Trabajando con Elementos del Calendario en Archivos PST"
url: /es/cpp/working-with-calendar-items-in-pst-file/
weight: 50
type: docs
---

## **Agregar MapiCalendar a PST**
Crear un Nuevo Archivo PST y Agregar Subcarpetas mostró cómo crear un archivo PST y agregar una subcarpeta a él. Con Aspose.Email puedes agregar MapiCalendar a la subcarpeta del Calendario de un archivo PST que hayas creado o cargado. A continuación se muestran los pasos para agregar MapiCalendar a un PST:

1. Crear un objeto MapiCalendar.
1. Establecer las propiedades de MapiCalendar utilizando un constructor y métodos.
1. Crear un PST utilizando el método PersonalStorage.Create().
1. Crear una carpeta predefinida (Calendario) en la raíz del archivo PST accediendo a la carpeta raíz y luego llamando al método AddMapiMessageItem().

El siguiente fragmento de código muestra cómo crear un MapiCalendar y luego agregarlo a la carpeta del calendario de un archivo PST recién creado.



{{< gist "aspose-email" "ef0db907527892c88c557bb418093cee" "Examples-EmailCPP-Outlook-AddMapiCalendarToPST-AddMapiCalendarToPST.cpp" >}}
## **Guardar Elementos del Calendario desde PST en Disco en Formato ICS**
Este artículo muestra cómo acceder a los elementos del calendario desde un archivo PST de Outlook y guardar el calendario en disco en formato ICS. Usa las clases PersonalStorage y MapiCalendar para obtener la información del calendario. A continuación se muestran los pasos para guardar elementos del calendario:

1. Cargar el archivo PST en la clase PersonalStorage.
1. Navegar por la carpeta del Calendario.
1. Obtener el contenido de la carpeta del Calendario para obtener la colección de mensajes.
1. Recorrer la colección de mensajes.
1. Llamar al método PersonalStorage.ExtractMessage() para obtener la información de contacto en la clase MapiCalendar.
1. Llamar al método MapiCalendar.Save() para guardar el elemento del calendario en disco en formato ICS.

El programa a continuación carga un archivo PST desde el disco y guarda todos los elementos del calendario en formato ICS. Los archivos ICS pueden ser utilizados en cualquier otro programa que pueda cargar el archivo de calendario ICS estándar. Abierto en Microsoft Outlook, un archivo ICS se ve como el de la captura de pantalla a continuación.

|![todo:image_alt_text](working-with-calendar-items-in-pst-file_1.png)|
| :- |
El siguiente fragmento de código muestra cómo exportar los elementos del calendario desde Outlook PST a formato ICS.



{{< gist "aspose-email" "ef0db907527892c88c557bb418093cee" "Examples-EmailCPP-Outlook-SaveCalendarItems-SaveCalendarItems.cpp" >}}