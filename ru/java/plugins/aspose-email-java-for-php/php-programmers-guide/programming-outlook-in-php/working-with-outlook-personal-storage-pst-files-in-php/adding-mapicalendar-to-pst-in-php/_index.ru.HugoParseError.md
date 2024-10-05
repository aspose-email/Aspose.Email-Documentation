---
title: Добавление MapiCalendar в PST на PHP
type: docs
weight: 20
url: /java/adding-mapicalendar-to-pst-in-php/
---

## **Aspose.Email - Добавление MapiCalendar в PST**
Чтобы добавить MapiCalendar в PST с использованием **Aspose.Email Java для PHP**, просто вызовите модуль **AddMapiCalendarToPST**. Здесь вы можете увидеть пример кода.

**PHP Код**

``` php

 # Создать встречу

$appointment =new MapiCalendar(

"LAKE ARGYLE WA 6743",

"Встреча",

"Это очень важная встреча :)",

new Date(2012, 10, 2),

new Date(2012, 10, 2, 14, 0, 0));

\# Создать совещание

$attendees = new MapiRecipientCollection();

$mapiRecipientType=new MapiRecipientType();

$attendees->add("ReneeAJones@armyspy.com", "Renee A. Jones", $mapiRecipientType->MAPI_TO);

$attendees->add("SzllsyLiza@dayrep.com", "Szollosy Liza", $mapiRecipientType->MAPI_TO);

$meeting = new MapiCalendar(

"Комната для совещаний 3 в главном офисе",

"Совещание",

"Пожалуйста, подтвердите вашу доступность.",

new Date(2012, 10, 2, 13, 0, 0),

new Date(2012, 10, 2, 14, 0, 0),

"CharlieKhan@dayrep.com",

$attendees

);

$personalStorage=new PersonalStorage();

$fileFormatVersion=new FileFormatVersion();

$standardIpmFolder=new StandardIpmFolder();

$pst = $personalStorage->create($dataDir . "MapiCalendarToPST1.pst", $fileFormatVersion->Unicode);

$calendar_folder = $pst->createPredefinedFolder("Календарь", $standardIpmFolder->Appointments);

print "MapiCalendar успешно добавлен.".PHP_EOL;

```
## **Скачать рабочий код**
Скачайте **Добавление MapiCalendar в PST (Aspose.Email)** с любого из нижеупомянутых сайтов социального программирования:

- [GitHub](https://github.com/aspose-email/Aspose.Email-for-Java/blob/master/Plugins/Aspose_Email_Java_for_PHP/src/aspose/email/ProgrammingOutlook/WorkingWithOutlookPersonalStorage/AddMapiCalendarToPST.php)
- [CodePlex](https://github.com/aspose-email/Aspose.Email-for-Java/blob/master/Plugins/Aspose.Email-for-Java_for_PHP/src/aspose/email/ProgrammingOutlook/WorkingWithOutlookPersonalStorage/AddMapiCalendarToPST.php)