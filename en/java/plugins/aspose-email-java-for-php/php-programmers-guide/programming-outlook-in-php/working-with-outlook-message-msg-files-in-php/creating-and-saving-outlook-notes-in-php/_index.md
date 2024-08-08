---
title: Creating and Saving Outlook Notes in PHP
type: docs
weight: 20
url: /java/creating-and-saving-outlook-notes-in-php/
---

## **Aspose.Email - Creating and Saving Outlook Notes**
To Create Outlook Notes using **Aspose.Email Java for PHP**, simply invoke **CreateOutlookNote** module. Here you can see example code.

**PHP Code**

``` php

 $note = new MapiNote();

$note->setSubject("Blue color note");

$note->setBody("This is a blue color note");

$noteColor=new NoteColor();

$note->setColor($noteColor->Blue);

$note->setHeight(500);

$note->setWidth(500);

$noteSaveFormat=new NoteSaveFormat();

$note->save($dataDir . "MapiNote.msg", $noteSaveFormat->Msg);

print "Created outlook note successfully.".PHP_EOL;

```
## **Download Running Code**
Download **Creating and Saving Outlook Notes (Aspose.Email)** from any of the below mentioned social coding sites:

- [GitHub](https://github.com/aspose-email/Aspose.Email-for-Java/blob/master/Plugins/Aspose_Email_Java_for_PHP/src/aspose/email/ProgrammingOutlook/WorkingWithOutlookMessageFiles/CreateOutlookNote.php)
- [CodePlex](https://archive.codeplex.com/?p=asposeemailjavaphp#src/aspose/email/ProgrammingOutlook/WorkingWithOutlookMessageFiles/CreateOutlookNote.php)
