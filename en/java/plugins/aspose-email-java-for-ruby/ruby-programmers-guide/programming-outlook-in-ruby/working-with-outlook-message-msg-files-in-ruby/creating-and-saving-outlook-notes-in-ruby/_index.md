---
title: Creating and Saving Outlook Notes in Ruby
type: docs
weight: 20
url: /java/creating-and-saving-outlook-notes-in-ruby/
---

## **Aspose.Email - Creating and Saving Outlook Notes**
To Create Outlook Notes using **Aspose.Email Java for Ruby**, simply invoke **CreateOutlookNote** module. Here you can see example code.

**Ruby Code**

``` ruby

 data_dir = File.dirname(File.dirname(File.dirname(File.dirname(__FILE__)))) + '/data/'

note = Rjb::import('com.aspose.email.MapiNote').new

note.setSubject("Blue color note")

note.setBody("This is a blue color note")

note.setColor(Rjb::import('com.aspose.email.NoteColor').Blue)

note.setHeight(500)

note.setWidth(500)

note.save(data_dir + "MapiNote.msg", Rjb::import('com.aspose.email.NoteSaveFormat').Msg)

puts "Created outlook note successfully."

```
## **Download Running Code**
Download **Creating and Saving Outlook Notes (Aspose.Email)** from any of the below mentioned social coding sites:

- [GitHub](https://github.com/aspose-email/Aspose.Email-for-Java/blob/master/Plugins/Aspose_Email_Java_for_Ruby/lib/asposeemailjava/Outlook/createoutlooknote.rb)
