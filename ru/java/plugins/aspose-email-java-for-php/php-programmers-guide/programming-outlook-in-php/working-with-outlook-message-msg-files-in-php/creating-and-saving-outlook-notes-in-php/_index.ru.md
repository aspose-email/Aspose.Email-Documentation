---
title: "Создание и сохранение заметок Outlook в PHP"
url: /ru/java/creating-and-saving-outlook-notes-in-php/
weight: 20
type: docs
---

## **Aspose.Email - создание и сохранение заметок Outlook**
Для создания заметок Outlook с помощью **Aspose.Электронная почта Java для PHP**, просто вызовите **CreateOutlookNote** модуль. Здесь вы можете увидеть пример кода.

**Код PHP**

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
## **Загрузить рабочий код**
Download **Создание и сохранение заметок Outlook (Aspose.Email)** с любого из нижеперечисленных сайтов социального программирования:

- [GitHub](https://github.com/aspose-email/Aspose.Email-for-Java/blob/master/Plugins/Aspose_Email_Java_for_PHP/src/aspose/email/ProgrammingOutlook/WorkingWithOutlookMessageFiles/CreateOutlookNote.php)
- [CodePlex](https://archive.codeplex.com/?p=asposeemailjavaphp#src/aspose/email/ProgrammingOutlook/WorkingWithOutlookMessageFiles/CreateOutlookNote.php)
