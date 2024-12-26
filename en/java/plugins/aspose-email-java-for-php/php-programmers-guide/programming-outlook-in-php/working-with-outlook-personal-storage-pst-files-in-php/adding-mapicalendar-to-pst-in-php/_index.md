---
title: Adding MapiCalendar to PST in PHP
ArticleTitle: Adding MapiCalendar to PST in PHP
type: docs
weight: 20
url: /java/adding-mapicalendar-to-pst-in-php/
---

## **Aspose.Email - Adding MapiCalendar to PST**
To Add MapiCalendar to PST using **Aspose.Email Java for PHP**, simply invoke **AddMapiCalendarToPST** module. Here you can see example code.

**PHP Code**

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
## **Download Running Code**
Download **Adding MapiCalendar to PST (Aspose.Email)** from any of the below mentioned social coding sites:

- [GitHub](https://github.com/aspose-email/Aspose.Email-for-Java/blob/master/Plugins/Aspose_Email_Java_for_PHP/src/aspose/email/ProgrammingOutlook/WorkingWithOutlookPersonalStorage/AddMapiCalendarToPST.php)
- [CodePlex](https://github.com/aspose-email/Aspose.Email-for-Java/blob/master/Plugins/Aspose.Email-for-Java_for_PHP/src/aspose/email/ProgrammingOutlook/WorkingWithOutlookPersonalStorage/AddMapiCalendarToPST.php)
