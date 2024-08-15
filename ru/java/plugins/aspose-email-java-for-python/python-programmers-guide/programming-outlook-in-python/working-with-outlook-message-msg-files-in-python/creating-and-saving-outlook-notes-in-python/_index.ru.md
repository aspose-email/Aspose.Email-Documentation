---
title: "Создание и сохранение заметок Outlook в Python"
url: /ru/java/creating-and-saving-outlook-notes-in-python/
weight: 20
type: docs
---

## **Aspose.Email - создание и сохранение заметок Outlook**
Создание и сохранение заметок Outlook с помощью **Aspose.Электронная почта Java для Python**, Используйте следующий код.

**Код Python**

```python



note = self.MapiNote()

note.setSubject("Blue color note")

note.setBody("This is a blue color note")

noteColor = self.NoteColor

note.setColor(noteColor.Blue)

note.setHeight(500)

note.setWidth(500)

noteSaveFormat = self.NoteSaveFormat

note.save(self.dataDir + "MapiNote.msg", noteSaveFormat.Msg)

print "Created outlook note successfully."

```
## **Загрузить рабочий код**
Download **Создание и сохранение заметок Outlook (Aspose.Email)** с любого из нижеперечисленных сайтов социального программирования:

- [GitHub](https://github.com/aspose-email/Aspose.Email-for-Java/releases/tag/Aspose.Email_Java_for_Python-v1.0)
- [CodePlex](http://asposeemailjavapython.codeplex.com/releases/)
