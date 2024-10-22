---
title: "Creando y Guardando Notas de Outlook en Python"
url: /es/java/creando-y-guardando-notas-de-outlook-en-python/
weight: 20
type: docs
---

## **Aspose.Email - Creando y Guardando Notas de Outlook**
Para crear y guardar notas de Outlook utilizando **Aspose.Email Java para Python**, use el siguiente código.

**Código Python**

```python



note = self.MapiNote()

note.setSubject("Nota de color azul")

note.setBody("Esta es una nota de color azul")

noteColor = self.NoteColor

note.setColor(noteColor.Blue)

note.setHeight(500)

note.setWidth(500)

noteSaveFormat = self.NoteSaveFormat

note.save(self.dataDir + "MapiNote.msg", noteSaveFormat.Msg)

print "Nota de Outlook creada con éxito."

```
## **Descargar Código en Ejecución**
Descargue **Creando y Guardando Notas de Outlook (Aspose.Email)** desde cualquiera de los sitios de codificación social mencionados a continuación:

- [GitHub](https://github.com/aspose-email/Aspose.Email-for-Java/releases/tag/Aspose.Email_Java_for_Python-v1.0)
- [CodePlex](http://asposeemailjavapython.codeplex.com/releases/)