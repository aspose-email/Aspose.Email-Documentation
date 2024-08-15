---
title: "Trabajando con elementos del calendario en un archivo PST"
url: /es/python-net/working-with-calendar-items-in-pst-file/
weight: 50
type: docs
---


## **Agregar MapiCalendar a PST**
Crear un nuevo archivo PST y agregar subcarpetas mostró cómo crear un archivo PST y agregarle una subcarpeta. Con Aspose.Email puede agregar MapiCalendar a la subcarpeta Calendario de un archivo PST que haya creado o cargado. A continuación se detallan los pasos para agregar MapiCalendar a un PST:

1. Cree un objeto MapiCalendar.
1. Establezca las propiedades de MapiCalendar mediante un constructor y métodos.
1. Cree un PST con el método PersonalStorage.create ().
1. Cree una carpeta predefinida (Calendario) en la raíz del archivo PST accediendo a la carpeta raíz y, a continuación, llamando al método add_mapi_message_item ().

El siguiente fragmento de código muestra cómo crear un MapiCalendar y, a continuación, añadirlo a la carpeta de calendario de un archivo PST recién creado.

{{< gist "aspose-email" "356f0e128b9d45a7ee779fc813eb87e5" "Examples-WorkingWithOutlookStorageFiles-AddMapiCalendarToPST-AddMapiCalendarToPST.py" >}}
## **Guardar los elementos del calendario de PST en el disco en formato ICS**
En este artículo se muestra cómo acceder a los elementos del calendario desde un archivo PST de Outlook y guardar el calendario en el disco en formato ICS. Utilice las clases PersonalStorage y MapiCalendar para obtener la información del calendario. A continuación se indican los pasos para guardar los elementos del calendario:

1. Cargue el archivo PST en la clase PersonalStorage.
1. Navega por la carpeta Calendario.
1. Obtenga el contenido de la carpeta Calendario para obtener la colección de mensajes.
1. Recorre la colección de mensajes.
1. Llama al método PersonalStorage.extract_message () para obtener la información de contacto de la clase MapiCalendar.
1. Llame al método MapiCalendar.save () para guardar el elemento del calendario en el disco en formato ICS.

El siguiente programa carga un archivo PST desde el disco y guarda todos los elementos del calendario en formato ICS. Los archivos ICS se pueden usar entonces en cualquier otro programa que pueda cargar el archivo de calendario ICS estándar. Abierto en Microsoft Outlook, un archivo ICS tiene el mismo aspecto que el de la siguiente captura de pantalla.

|![todo:image_alt_text](working-with-calendar-items-in-pst-file_1.png)|
|: - |
El siguiente fragmento de código muestra cómo exportar los elementos del calendario del formato PST de Outlook al formato ICS.



{{< gist "aspose-email" "356f0e128b9d45a7ee779fc813eb87e5" "Examples-WorkingWithOutlookStorageFiles-SaveCalendarItems-SaveCalendarItems.py" >}}

### **Guardar como ICS con marca de tiempo original**

The *keep_original_date_time_stamp* método del [MapiCalendarIcsSaveOptions](https://reference.aspose.com/email/python-net/aspose.email.mapi/mapicalendaricssaveoptions/#mapicalendaricssaveoptions-class) La clase permite conservar las marcas de fecha y hora originales de los elementos del calendario al guardarlos como un archivo ICS (iCalendar). El siguiente ejemplo de código demuestra la implementación de este método:

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
## **Modificar o eliminar las ocurrencias de las recurrencias**

Se pueden agregar excepciones a las recurrencias existentes mediante la API Aspose.Email for .NET. El siguiente ejemplo de código ilustra el uso de esta función. 

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

# adding one exception
exception_info = MapiCalendarExceptionInfo()
exception_info.location = "London"
exception_info.subject = "Subj"
exception_info.original_start_date = exception_date
exception_info.start_date_time = exception_date
exception_info.end_date_time = exception_date + timedelta(hours=5)
pattern.exceptions.append(exception_info)
pattern.modified_instance_dates.append(exception_date)
# every modified instance also has to have an entry in the DeletedInstanceDates field with the original instance date.
pattern.deleted_instance_dates.append(exception_date)

# adding one deleted instance
pattern.deleted_instance_dates.append(exception_date + timedelta(days=2))

rec_coll = MapiRecipientCollection()
rec_coll.add("receiver@domain.com", "receiver", MapiRecipientType.TO)
new_cal = MapiCalendar(
    "This is Location",
    "This is Summary",
    "This is recurrence test",
    start_date,
    start_date + timedelta(hours=3),
    "organizer@domain.com",
    rec_coll
)
new_cal.recurrence = recurrence

with PersonalStorage.create("output.pst", FileFormatVersion.UNICODE) as pst:
    calendar_folder = pst.create_predefined_folder("Calendar", StandardIpmFolder.APPOINTMENTS)
    calendar_folder.add_message(new_cal)
```
