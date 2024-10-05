---
title: "Создание и сохранение заметок Outlook в Jython"
url: /ru/java/creating-and-saving-outlook-notes-in-jython/
weight: 20
type: docs
---

## **Aspose.Email - Создание и сохранение заметок Outlook**
Для создания заметок Outlook с помощью **Aspose.Email Java для Jython** просто вызовите модуль **CreateOutlookNote**. Здесь вы можете увидеть пример кода.

**Jython код**

```python

 from aspose-email import Settings

from com.aspose.email import MapiNote

from com.aspose.email import NoteColor

from com.aspose.email import NoteSaveFormat

class CreateOutlookNote:

    def __init__(self):



        dataDir = Settings.dataDir + 'ProgrammingOutlook/WorkingWithOutlookMessageFiles/CreateOutlookNote/'



        note = MapiNote()

        note.setSubject("Записка синего цвета")

        note.setBody("Это записка синего цвета")

        noteColor = NoteColor

        note.setColor(noteColor.Blue)

        note.setHeight(500)

        note.setWidth(500)

        noteSaveFormat=NoteSaveFormat

        note.save(dataDir + "MapiNote.msg", noteSaveFormat.Msg)

        print "Записка Outlook успешно создана."





if __name__ == '__main__':        

    CreateOutlookNote()

```
## **Скачать рабочий код**
Скачайте **Создание и сохранение заметок Outlook (Aspose.Email)** с любого из упомянутых ниже сайтов для совместной разработки:

- [GitHub](https://github.com/aspose-email/Aspose.Email-for-Java/releases/tag/Aspose.Email_Java_for_Jython-v1.0)
- [CodePlex](https://archive.codeplex.com/?p=asposeemailjavajython)