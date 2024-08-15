---
title: "Creación y almacenamiento de notas de Outlook en PHP"
url: /es/java/creating-and-saving-outlook-notes-in-php/
weight: 20
type: docs
---

## **Aspose.Email - Creación y almacenamiento de notas de Outlook**
Para crear notas de Outlook usando **Aspose.Email Java para PHP**, simplemente invoca **CreateOutlookNote** módulo. Aquí puedes ver un ejemplo de código.

**Código PHP**

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
## **Descargar Running Code**
Download **Creación y almacenamiento de notas de Outlook (Aspose.Email)** desde cualquiera de los sitios de codificación social mencionados a continuación:

- [GitHub](https://github.com/aspose-email/Aspose.Email-for-Java/blob/master/Plugins/Aspose_Email_Java_for_PHP/src/aspose/email/ProgrammingOutlook/WorkingWithOutlookMessageFiles/CreateOutlookNote.php)
- [CodePlex](https://archive.codeplex.com/?p=asposeemailjavaphp#src/aspose/email/ProgrammingOutlook/WorkingWithOutlookMessageFiles/CreateOutlookNote.php)
