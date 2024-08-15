---
title: "Crear y guardar notas de Outlook en Python"
url: /es/java/creating-and-saving-outlook-notes-in-python/
weight: 20
type: docs
---

## **Aspose.Email - Creación y almacenamiento de notas de Outlook**
Para crear y guardar notas de Outlook usando **Aspose.Email Java para Python**, Usa el siguiente código.

**Código Python**

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
## **Descargar Running Code**
Download **Creación y almacenamiento de notas de Outlook (Aspose.Email)** desde cualquiera de los sitios de codificación social mencionados a continuación:

- [GitHub](https://github.com/aspose-email/Aspose.Email-for-Java/releases/tag/Aspose.Email_Java_for_Python-v1.0)
- [CodePlex](http://asposeemailjavapython.codeplex.com/releases/)
