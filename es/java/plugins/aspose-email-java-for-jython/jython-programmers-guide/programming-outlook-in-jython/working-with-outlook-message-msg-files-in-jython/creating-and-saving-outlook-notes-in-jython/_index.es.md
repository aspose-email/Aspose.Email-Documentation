---
title: "Creando y Guardando Notas de Outlook en Jython"
url: /es/java/creating-and-saving-outlook-notes-in-jython/
weight: 20
type: docs
---

## **Aspose.Email - Creando y Guardando Notas de Outlook**
Para crear notas de Outlook utilizando **Aspose.Email Java para Jython**, simplemente invoca el módulo **CreateOutlookNote**. Aquí puedes ver un código de ejemplo.

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

        note.setSubject("Nota de color azul")

        note.setBody("Esta es una nota de color azul")

        noteColor = NoteColor

        note.setColor(noteColor.Blue)

        note.setHeight(500)

        note.setWidth(500)

        noteSaveFormat=NoteSaveFormat

        note.save(dataDir + "MapiNote.msg", noteSaveFormat.Msg)

        print "Nota de Outlook creada exitosamente."





if __name__ == '__main__':        

    CreateOutlookNote()

```
## **Descargar Código en Ejecución**
Descarga **Creando y Guardando Notas de Outlook (Aspose.Email)** de cualquiera de los sitios de codificación social mencionados a continuación:

- [GitHub](https://github.com/aspose-email/Aspose.Email-for-Java/releases/tag/Aspose.Email_Java_for_Jython-v1.0)
- [CodePlex](https://archive.codeplex.com/?p=asposeemailjavajython)