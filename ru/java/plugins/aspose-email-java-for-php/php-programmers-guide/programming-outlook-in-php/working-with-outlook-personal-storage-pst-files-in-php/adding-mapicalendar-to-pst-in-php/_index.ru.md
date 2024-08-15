---
title: "Добавление MapicaLendar в PST на PHP"
url: /ru/java/adding-mapicalendar-to-pst-in-php/
weight: 20
type: docs
---

## **Aspose.Email - Добавление MapiCalendar в PST**
Чтобы добавить MapicaLendar в PST, используя **Aspose.Электронная почта Java для PHP**, просто вызовите **AddMapiCalendarToPST** модуль. Здесь вы можете увидеть пример кода.

**Код PHP**

``` php

 # Create the appointment

$appointment =new MapiCalendar(

"LAKE ARGYLE WA 6743",

"Appointment",

"This is a very important meeting :)",

new Date(2012, 10, 2),

new Date(2012, 10, 2, 14, 0, 0));

\# Create the meeting

$attendees = new MapiRecipientCollection();

$mapiRecipientType=new MapiRecipientType();

$attendees->add("ReneeAJones@armyspy.com", "Renee A. Jones", $mapiRecipientType->MAPI_TO);

$attendees->add("SzllsyLiza@dayrep.com", "Szollosy Liza", $mapiRecipientType->MAPI_TO);

$meeting = new MapiCalendar(

"Meeting Room 3 at Office Headquarters",

"Meeting",

"Please confirm your availability.",

new Date(2012, 10, 2, 13, 0, 0),

new Date(2012, 10, 2, 14, 0, 0),

"CharlieKhan@dayrep.com",

$attendees

);

$personalStorage=new PersonalStorage();

$fileFormatVersion=new FileFormatVersion();

$standardIpmFolder=new StandardIpmFolder();

$pst = $personalStorage->create($dataDir . "MapiCalendarToPST1.pst", $fileFormatVersion->Unicode);

$calendar_folder = $pst->createPredefinedFolder("Calendar", $standardIpmFolder->Appointments);

print "Added MapiCalendar Successfully.".PHP_EOL;

```
## **Загрузить рабочий код**
Download **Добавление MapicaLendar в PST (Aspose.Email)** с любого из нижеперечисленных сайтов социального программирования:

- [GitHub](https://github.com/aspose-email/Aspose.Email-for-Java/blob/master/Plugins/Aspose_Email_Java_for_PHP/src/aspose/email/ProgrammingOutlook/WorkingWithOutlookPersonalStorage/AddMapiCalendarToPST.php)
- [CodePlex](https://github.com/aspose-email/Aspose.Email-for-Java/blob/master/Plugins/Aspose.Email-for-Java_for_PHP/src/aspose/email/ProgrammingOutlook/WorkingWithOutlookPersonalStorage/AddMapiCalendarToPST.php)
