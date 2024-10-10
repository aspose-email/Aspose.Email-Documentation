---
title: "Создание и сохранение заметок Outlook в PHP"
url: /ru/java/creating-and-saving-outlook-notes-in-php/
weight: 20
type: docs
---

## **Aspose.Email - Создание и сохранение заметок Outlook**
Чтобы создать заметки Outlook с помощью **Aspose.Email Java для PHP**, просто вызовите модуль **CreateOutlookNote**. Здесь вы можете увидеть пример кода.

**PHP Код**

``` php

 $note = new MapiNote();

$note->setSubject("Заметка синего цвета");

$note->setBody("Это заметка синего цвета");

$noteColor=new NoteColor();

$note->setColor($noteColor->Blue);

$note->setHeight(500);

$note->setWidth(500);

$noteSaveFormat=new NoteSaveFormat();

$note->save($dataDir . "MapiNote.msg", $noteSaveFormat->Msg);

print "Заметка Outlook успешно создана.".PHP_EOL;

```
## **Скачать рабочий код**
Скачайте **Создание и сохранение заметок Outlook (Aspose.Email)** с любого из ниже упомянутых социальных кодировочных сайтов:

- [GitHub](https://github.com/aspose-email/Aspose.Email-for-Java/blob/master/Plugins/Aspose_Email_Java_for_PHP/src/aspose/email/ProgrammingOutlook/WorkingWithOutlookMessageFiles/CreateOutlookNote.php)
- [CodePlex](https://archive.codeplex.com/?p=asposeemailjavaphp#src/aspose/email/ProgrammingOutlook/WorkingWithOutlookMessageFiles/CreateOutlookNote.php)