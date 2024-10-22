---
title: "Agregar MapiCalendar a PST en Ruby"
url: /es/java/adding-mapicalendar-to-pst-in-ruby/
weight: 20
type: docs
---

## **Aspose.Email - Agregar MapiCalendar a PST**
Para agregar MapiCalendar a PST utilizando **Aspose.Email Java for Ruby**, simplemente invoca el módulo **AddMapiCalendarToPST**. Aquí puedes ver un código de ejemplo.

**Código Ruby**

```ruby

 data_dir = File.dirname(File.dirname(File.dirname(File.dirname(__FILE__)))) + '/data/'

\# Crear la cita

appointment = Rjb::import('com.aspose.email.MapiCalendar').new(

    "LAKE ARGYLE WA 6743",

    "Cita",

    "Esta es una reunión muy importante :)",

    Rjb::import('java.util.Date').new(2012, 10, 2),

    Rjb::import('java.util.Date').new(2012, 10, 2, 14, 0, 0))

\# Crear la reunión

attendees = Rjb::import('com.aspose.email.MapiRecipientCollection').new

attendees.add("ReneeAJones@armyspy.com", "Renee A. Jones", Rjb::import('com.aspose.email.MapiRecipientType').MAPI_TO)

attendees.add("SzllsyLiza@dayrep.com", "Szollosy Liza", Rjb::import('com.aspose.email.MapiRecipientType').MAPI_TO)

meeting = Rjb::import('com.aspose.email.MapiCalendar').new(

    "Sala de Reuniones 3 en Sede Central",

    "Reunión",

    "Por favor confirma tu disponibilidad.",

    Rjb::import('java.util.Date').new(2012, 10, 2, 13, 0, 0),

    Rjb::import('java.util.Date').new(2012, 10, 2, 14, 0, 0),

    "CharlieKhan@dayrep.com",

    attendees

    )

pst = Rjb::import('com.aspose.email.PersonalStorage').create(data_dir + "MapiCalendarToPST.pst", Rjb::import('com.aspose.email.FileFormatVersion').Unicode)

calendar_folder = pst.createPredefinedFolder("Calendario", Rjb::import('com.aspose.email.StandardIpmFolder').Appointments)

calendar_folder.addMapiMessageItem(appointment)

calendar_folder.addMapiMessageItem(meeting)

puts "MapiCalendar agregado con éxito."

```
## **Descargar Código en Ejecución**
Descarga **Agregar MapiCalendar a PST (Aspose.Email)** de cualquiera de los sitios de codificación social mencionados a continuación:

- [GitHub](https://github.com/aspose-email/Aspose.Email-for-Java/blob/master/Plugins/Aspose_Email_Java_for_Ruby/lib/asposeemailjava/Outlook/addmapicalendartopst.rb)