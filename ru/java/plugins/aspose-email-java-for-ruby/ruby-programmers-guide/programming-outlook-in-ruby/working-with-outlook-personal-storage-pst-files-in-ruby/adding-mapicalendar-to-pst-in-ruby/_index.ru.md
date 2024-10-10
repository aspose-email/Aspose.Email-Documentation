---
title: "Добавление MapiCalendar в PST на Ruby"
url: /ru/java/adding-mapicalendar-to-pst-in-ruby/
weight: 20
type: docs
---

## **Aspose.Email - Добавление MapiCalendar в PST**
Чтобы добавить MapiCalendar в PST с использованием **Aspose.Email Java для Ruby**, просто вызовите модуль **AddMapiCalendarToPST**. Здесь вы можете видеть пример кода.

**Код на Ruby**

```ruby

 data_dir = File.dirname(File.dirname(File.dirname(File.dirname(__FILE__)))) + '/data/'

\# Создание встречи

appointment = Rjb::import('com.aspose.email.MapiCalendar').new(

    "LAKE ARGYLE WA 6743",

    "Appointment",

    "Это очень важная встреча :)",

    Rjb::import('java.util.Date').new(2012, 10, 2),

    Rjb::import('java.util.Date').new(2012, 10, 2, 14, 0, 0))

\# Создание собрания

attendees = Rjb::import('com.aspose.email.MapiRecipientCollection').new

attendees.add("ReneeAJones@armyspy.com", "Renee A. Jones", Rjb::import('com.aspose.email.MapiRecipientType').MAPI_TO)

attendees.add("SzllsyLiza@dayrep.com", "Szollosy Liza", Rjb::import('com.aspose.email.MapiRecipientType').MAPI_TO)

meeting = Rjb::import('com.aspose.email.MapiCalendar').new(

    "Meeting Room 3 at Office Headquarters",

    "Meeting",

    "Пожалуйста, подтвердите свою доступность.",

    Rjb::import('java.util.Date').new(2012, 10, 2, 13, 0, 0),

    Rjb::import('java.util.Date').new(2012, 10, 2, 14, 0, 0),

    "CharlieKhan@dayrep.com",

    attendees

    )

pst = Rjb::import('com.aspose.email.PersonalStorage').create(data_dir + "MapiCalendarToPST.pst", Rjb::import('com.aspose.email.FileFormatVersion').Unicode)

calendar_folder = pst.createPredefinedFolder("Календарь", Rjb::import('com.aspose.email.StandardIpmFolder').Appointments)

calendar_folder.addMapiMessageItem(appointment)

calendar_folder.addMapiMessageItem(meeting)

puts "MapiCalendar успешно добавлен."

```
## **Скачать работающий код**
Скачайте **Добавление MapiCalendar в PST (Aspose.Email)** с любых из нижеупомянутых социальных кодовых сайтов:

- [GitHub](https://github.com/aspose-email/Aspose.Email-for-Java/blob/master/Plugins/Aspose_Email_Java_for_Ruby/lib/asposeemailjava/Outlook/addmapicalendartopst.rb)