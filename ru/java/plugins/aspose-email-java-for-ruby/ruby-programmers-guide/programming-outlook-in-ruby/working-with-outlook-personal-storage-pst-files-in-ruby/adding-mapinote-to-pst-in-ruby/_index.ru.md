---
title: "Добавление MapiNote в PST в Ruby"
url: /ru/java/adding-mapinote-to-pst-in-ruby/
weight: 50
type: docs
---

## **Aspose.Email - добавление MapiNote в PST**
Чтобы добавить MapiNote в PST, используя **Aspose.Электронная почта Java для Ruby**, просто вызовите **AddMapiNoteToPST** модуль. Здесь вы можете увидеть пример кода.

**Код Ruby**

``` ruby

 data_dir = File.dirname(File.dirname(File.dirname(File.dirname(__FILE__)))) + '/data/'

mess = Rjb::import('com.aspose.email.MapiMessage').fromFile(data_dir + "MapiNote.msg")

\# Note #1

note1 = mess.toMapiMessageItem()

note1.setSubject("Yellow color note")

note1.setBody("This is a yellow color note")

\# Note #2

note2 = mess.toMapiMessageItem()

note2.setSubject("Pink color note")

note2.setBody("This is a pink color note")

note2.setColor(Rjb::import('com.aspose.email.NoteColor').Pink)

\# Note #3

note3 = mess.toMapiMessageItem()

note2.setSubject("Blue color note")

note2.setBody("This is a blue color note")

note2.setColor(Rjb::import('com.aspose.email.NoteColor').Blue)

note3.setHeight(500)

note3.setWidth(500)

pst = Rjb::import('com.aspose.email.PersonalStorage').create(data_dir + "MapiNoteToPST.pst", Rjb::import('com.aspose.email.FileFormatVersion').Unicode)

notes_folder = pst.createPredefinedFolder("Notes", Rjb::import('com.aspose.email.StandardIpmFolder').Notes)

notes_folder.addMapiMessageItem(note1)

notes_folder.addMapiMessageItem(note2)

notes_folder.addMapiMessageItem(note3)

puts "Added MapiNote Successfully."

```
## **Загрузить рабочий код**
Download **Добавление MapiNote в PST (Aspose.Email)** с любого из нижеперечисленных сайтов социального программирования:

- [GitHub](https://github.com/aspose-email/Aspose.Email-for-Java/blob/master/Plugins/Aspose_Email_Java_for_Ruby/lib/asposeemailjava/Outlook/addmapinotetopst.rb)
