---
title: "Creación y Guardado de Notas de Outlook en PHP"
url: /es/java/creacion-y-guardado-de-notas-de-outlook-en-php/
weight: 20
type: docs
---

## **Aspose.Email - Creación y Guardado de Notas de Outlook**
Para crear notas de Outlook utilizando **Aspose.Email Java para PHP**, simplemente invoca el módulo **CreateOutlookNote**. Aquí puedes ver un código de ejemplo.

**Código PHP**

``` php

 $note = new MapiNote();

$note->setSubject("Nota de color azul");

$note->setBody("Esta es una nota de color azul");

$noteColor=new NoteColor();

$note->setColor($noteColor->Blue);

$note->setHeight(500);

$note->setWidth(500);

$noteSaveFormat=new NoteSaveFormat();

$note->save($dataDir . "MapiNote.msg", $noteSaveFormat->Msg);

print "Nota de Outlook creada exitosamente.".PHP_EOL;

```
## **Descargar Código en Ejecución**
Descarga **Creación y Guardado de Notas de Outlook (Aspose.Email)** de cualquiera de los sitios de codificación social mencionados a continuación:

- [GitHub](https://github.com/aspose-email/Aspose.Email-for-Java/blob/master/Plugins/Aspose_Email_Java_for_PHP/src/aspose/email/ProgrammingOutlook/WorkingWithOutlookMessageFiles/CreateOutlookNote.php)
- [CodePlex](https://archive.codeplex.com/?p=asposeemailjavaphp#src/aspose/email/ProgrammingOutlook/WorkingWithOutlookMessageFiles/CreateOutlookNote.php)