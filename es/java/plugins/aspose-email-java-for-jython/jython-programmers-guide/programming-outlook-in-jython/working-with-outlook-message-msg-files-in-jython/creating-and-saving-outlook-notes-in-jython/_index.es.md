---
title: "Crear y guardar notas de Outlook en Jython"
url: /es/java/creating-and-saving-outlook-notes-in-jython/
weight: 20
type: docs
---

## **Aspose.Email - Creación y almacenamiento de notas de Outlook**
Para crear notas de Outlook usando **Aspose.Email Java para Jython**, simplemente invoca **CreateOutlookNote** módulo. Aquí puedes ver un ejemplo de código.

**Código Jython**

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
## **Descargar Running Code**
Download **Creación y almacenamiento de notas de Outlook (Aspose.Email)** desde cualquiera de los sitios de codificación social mencionados a continuación:

- [GitHub](https://github.com/aspose-email/Aspose.Email-for-Java/releases/tag/Aspose.Email_Java_for_Jython-v1.0)
- [CodePlex](https://archive.codeplex.com/?p=asposeemailjavajython)
