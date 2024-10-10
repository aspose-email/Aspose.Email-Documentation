---
title: "Создание и сохранение заметок Outlook на Python"
url: /ru/java/creating-and-saving-outlook-notes-in-python/
weight: 20
type: docs
---

## **Aspose.Email - Создание и сохранение заметок Outlook**
Для создания и сохранения заметок Outlook с использованием **Aspose.Email Java для Python** используйте следующий код.

**Код на Python**

```python



note = self.MapiNote()

note.setSubject("Заметка синего цвета")

note.setBody("Это заметка синего цвета")

noteColor = self.NoteColor

note.setColor(noteColor.Blue)

note.setHeight(500)

note.setWidth(500)

noteSaveFormat = self.NoteSaveFormat

note.save(self.dataDir + "MapiNote.msg", noteSaveFormat.Msg)

print "Заметка Outlook успешно создана."

```
## **Скачать работающий код**
Скачайте **Создание и сохранение заметок Outlook (Aspose.Email)** с любого из нижеприведенных социальных сайтов программирования:

- [GitHub](https://github.com/aspose-email/Aspose.Email-for-Java/releases/tag/Aspose.Email_Java_for_Python-v1.0)
- [CodePlex](http://asposeemailjavapython.codeplex.com/releases/)