---
title: "Создание и сохранение заметок Outlook в Jython"
url: /ru/java/creating-and-saving-outlook-notes-in-jython/
weight: 20
type: docs
---

## **Aspose.Email - создание и сохранение заметок Outlook**
Для создания заметок Outlook с помощью **Aspose.Электронная почта Java для Mython**, просто вызовите **CreateOutlookNote** модуль. Здесь вы можете увидеть пример кода.

**Код Митона**

```python

 from aspose-email import Settings

from com.aspose.email import MapiNote

from com.aspose.email import NoteColor

from com.aspose.email import NoteSaveFormat

class CreateOutlookNote:

    def __init__(self):



        dataDir = Settings.dataDir + 'ProgrammingOutlook/WorkingWithOutlookMessageFiles/CreateOutlookNote/'



        note = MapiNote()

        note.setSubject("Blue color note")

        note.setBody("This is a blue color note")

        noteColor = NoteColor

        note.setColor(noteColor.Blue)

        note.setHeight(500)

        note.setWidth(500)

        noteSaveFormat=NoteSaveFormat

        note.save(dataDir + "MapiNote.msg", noteSaveFormat.Msg)

        print "Created outlook note successfully."





if __name__ == '__main__':       

    CreateOutlookNote()

```
## **Загрузить рабочий код**
Download **Создание и сохранение заметок Outlook (Aspose.Email)** с любого из нижеперечисленных сайтов социального программирования:

- [GitHub](https://github.com/aspose-email/Aspose.Email-for-Java/releases/tag/Aspose.Email_Java_for_Jython-v1.0)
- [CodePlex](https://archive.codeplex.com/?p=asposeemailjavajython)
