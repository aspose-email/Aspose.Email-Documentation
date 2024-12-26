---
title: Creating and Saving Outlook Notes in Python
ArticleTitle: Creating and Saving Outlook Notes in Python
type: docs
weight: 20
url: /java/creating-and-saving-outlook-notes-in-python/
---

## **Aspose.Email - Creating and Saving Outlook Notes**
To Create and Save Outlook Notes using **Aspose.Email Java for Python**, Use following code.

**Python Code**

{{< highlight python >}}



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

{{< /highlight >}}
## **Download Running Code**
Download **Creating and Saving Outlook Notes (Aspose.Email)** from any of the below mentioned social coding sites:

- [GitHub](https://github.com/aspose-email/Aspose.Email-for-Java/releases/tag/Aspose.Email_Java_for_Python-v1.0)
- [CodePlex](http://asposeemailjavapython.codeplex.com/releases/)
