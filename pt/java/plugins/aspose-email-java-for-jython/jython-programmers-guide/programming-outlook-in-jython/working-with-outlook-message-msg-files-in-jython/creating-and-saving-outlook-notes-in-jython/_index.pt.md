---
title: "Criando e Salvando Notas do Outlook em Jython"
url: /pt/java/criando-e-salvando-notas-do-outlook-em-jython/
weight: 20
type: docs
---

## **Aspose.Email - Criando e Salvando Notas do Outlook**
Para criar notas do Outlook usando **Aspose.Email Java para Jython**, basta invocar o módulo **CreateOutlookNote**. Aqui você pode ver um exemplo de código.

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

        note.setSubject("Nota de cor azul")

        note.setBody("Esta é uma nota de cor azul")

        noteColor = NoteColor

        note.setColor(noteColor.Blue)

        note.setHeight(500)

        note.setWidth(500)

        noteSaveFormat=NoteSaveFormat

        note.save(dataDir + "MapiNote.msg", noteSaveFormat.Msg)

        print "Nota do Outlook criada com sucesso."





if __name__ == '__main__':        

    CreateOutlookNote()

```
## **Baixar Código em Execução**
Baixe **Criando e Salvando Notas do Outlook (Aspose.Email)** de qualquer um dos sites de codificação social mencionados abaixo:

- [GitHub](https://github.com/aspose-email/Aspose.Email-for-Java/releases/tag/Aspose.Email_Java_for_Jython-v1.0)
- [CodePlex](https://archive.codeplex.com/?p=asposeemailjavajython)