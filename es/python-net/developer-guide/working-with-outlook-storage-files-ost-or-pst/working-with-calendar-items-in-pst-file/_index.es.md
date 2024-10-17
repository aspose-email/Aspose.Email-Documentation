---
title: "Trabajando con elementos del calendario en archivos PST"
url: /es/python-net/working-with-calendar-items-in-pst-file/
weight: 50
type: docs
---

## **Agregar MapiCalendar a PST**
Crear un nuevo archivo PST y agregar subcarpetas mostró cómo crear un archivo PST y agregarle una subcarpeta. Con Aspose.Email, puedes agregar MapiCalendar a la subcarpeta Calendario de un archivo PST que has creado o cargado. A continuación se presentan los pasos para agregar MapiCalendar a un PST:

1. Crea un objeto MapiCalendar.
1. Establece las propiedades de MapiCalendar usando un constructor y métodos.
1. Crea un PST utilizando el método PersonalStorage.create().
1. Crea una carpeta predefinida (Calendario) en la raíz del archivo PST accediendo a la carpeta raíz y luego llamando al método add_mapi_message_item().

El siguiente fragmento de código te muestra cómo crear un MapiCalendar y luego agregarlo a la carpeta de calendario de un archivo PST recién creado.

{{< gist "aspose-email" "356f0e128b9d45a7ee779fc813eb87e5" "Examples-WorkingWithOutlookStorageFiles-AddMapiCalendarToPST-AddMapiCalendarToPST.py" >}}
## **Guardar elementos del calendario de PST en disco en formato ICS**
Este artículo muestra cómo acceder a elementos del calendario desde un archivo PST de Outlook y guardar el calendario en disco en formato ICS. Usa las clases PersonalStorage y MapiCalendar para obtener la información del calendario. A continuación se presentan los pasos para guardar elementos del calendario:

1. Carga el archivo PST en la clase PersonalStorage.
1. Revisa la carpeta Calendario.
1. Obtén el contenido de la carpeta Calendario para obtener la colección de mensajes.
1. Recorre la colección de mensajes.
1. Llama al método PersonalStorage.extract_message() para obtener la información del contacto en la clase MapiCalendar.
1. Llama al método MapiCalendar.save() para guardar el elemento del calendario en disco en formato ICS.

El programa a continuación carga un archivo PST desde el disco y guarda todos los elementos del calendario en formato ICS. Los archivos ICS pueden ser utilizados después en cualquier otro programa que pueda cargar el archivo estándar de calendario ICS. Abierto en Microsoft Outlook, un archivo ICS se ve como el de la siguiente captura de pantalla.

|![todo:image_alt_text](working-with-calendar-items-in-pst-file_1.png)|
| :- |
El siguiente fragmento de código te muestra cómo exportar los elementos del calendario desde PST de Outlook a formato ICS.

{{< gist "aspose-email" "356f0e128b9d45a7ee779fc813eb87e5" "Examples-WorkingWithOutlookStorageFiles-SaveCalendarItems-SaveCalendarItems.py" >}}

### **Guardar como ICS con marca de tiempo original**

El método *keep_original_date_time_stamp* de la clase [MapiCalendarIcsSaveOptions](https://reference.aspose.com/email/python-net/aspose.email.mapi/mapicalendaricssaveoptions/#mapicalendaricssaveoptions-class) permite preservar las marcas de fecha y hora originales de los elementos del calendario al guardarlos como un archivo ICS (iCalendar). El siguiente ejemplo de código demuestra la implementación de este método:

```python
import aspose.email as ae

pst = ae.storage.pst.PersonalStorage.from_file("my.pst")

calendar_folder = pst.get_predefined_folder(ae.storage.pst.StandardIpmFolder.APPOINTMENTS)

for msg_info in calendar_folder.enumerate_messages():
    cal = pst.extract_message(msg_info).to_mapi_message_item()

    save_options = ae.mapi.MapiCalendarIcsSaveOptions()
    save_options.keep_original_date_time_stamp = True

    if not (cal is None):
      cal.save("cal.ics", save_options)
```
## **Modificar/Eliminar ocurrencias de recurrencias**

Se pueden agregar excepciones a las recurrencias existentes utilizando la API Aspose.Email para .NET. El siguiente ejemplo de código ilustra el uso de esta función.

```py
from datetime import datetime, timedelta
from aspose.email.storage.pst import PersonalStorage, StandardIpmFolder, FileFormatVersion
from aspose.email.mapi import MapiCalendar, MapiCalendarEventRecurrence, \
    MapiCalendarDailyRecurrencePattern, MapiCalendarRecurrenceEndType, \
    MapiCalendarExceptionInfo, MapiCalendarRecurrencePatternType, \
    MapiRecipientCollection, MapiRecipientType

start_date = datetime.now().date()

recurrence = MapiCalendarEventRecurrence()
pattern = MapiCalendarDailyRecurrencePattern()
pattern.pattern_type = MapiCalendarRecurrencePatternType.DAY
pattern.period = 1
pattern.end_type = MapiCalendarRecurrenceEndType.NEVER_END
recurrence.recurrence_pattern = pattern

exception_date = start_date + timedelta(days=1)

# agregando una excepción
exception_info = MapiCalendarExceptionInfo()
exception_info.location = "Londres"
exception_info.subject = "Subj"
exception_info.original_start_date = exception_date
exception_info.start_date_time = exception_date
exception_info.end_date_time = exception_date + timedelta(hours=5)
pattern.exceptions.append(exception_info)
pattern.modified_instance_dates.append(exception_date)
# cada instancia modificada también debe tener una entrada en el campo DeletedInstanceDates con la fecha de instancia original.
pattern.deleted_instance_dates.append(exception_date)

# agregando una instancia eliminada
pattern.deleted_instance_dates.append(exception_date + timedelta(days=2))

rec_coll = MapiRecipientCollection()
rec_coll.add("receiver@domain.com", "receiver", MapiRecipientType.TO)
new_cal = MapiCalendar(
    "Esta es la ubicación",
    "Este es el resumen",
    "Esta es una prueba de recurrencia",
    start_date,
    start_date + timedelta(hours=3),
    "organizer@domain.com",
    rec_coll
)
new_cal.recurrence = recurrence

with PersonalStorage.create("output.pst", FileFormatVersion.UNICODE) as pst:
    calendar_folder = pst.create_predefined_folder("Calendario", StandardIpmFolder.APPOINTMENTS)
    calendar_folder.add_message(new_cal)
```