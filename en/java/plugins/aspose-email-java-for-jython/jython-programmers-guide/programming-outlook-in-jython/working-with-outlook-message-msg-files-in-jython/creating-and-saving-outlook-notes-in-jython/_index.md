---
title: Creating and Saving Outlook Notes in Jython
type: docs
weight: 20
url: /java/creating-and-saving-outlook-notes-in-jython/
---

## **Aspose.Email - Creating and Saving Outlook Notes**
To Create Outlook Notes using **Aspose.Email Java for Jython**, simply invoke **CreateOutlookNote** module. Here you can see example code.

**Jython Code**

{{< highlight python >}}

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

{{< /highlight >}}
## **Download Running Code**
Download **Creating and Saving Outlook Notes (Aspose.Email)** from any of the below mentioned social coding sites:

- [GitHub](https://github.com/aspose-email/Aspose.Email-for-Java/releases/tag/Aspose.Email_Java_for_Jython-v1.0)
- [CodePlex](https://archive.codeplex.com/?p=asposeemailjavajython)
