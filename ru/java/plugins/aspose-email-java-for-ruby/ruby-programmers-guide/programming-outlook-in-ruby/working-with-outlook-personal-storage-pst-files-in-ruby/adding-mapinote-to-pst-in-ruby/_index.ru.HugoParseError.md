---
title: Добавление MapiNote в PST на Ruby
type: docs
weight: 50
url: /java/adding-mapinote-to-pst-in-ruby/
---

## **Aspose.Email - Добавление MapiNote в PST**
Чтобы добавить MapiNote в PST с помощью **Aspose.Email Java для Ruby**, просто вызовите модуль **AddMapiNoteToPST**. Здесь вы можете увидеть пример кода.

**Ruby Код**

``` ruby

 data_dir = File.dirname(File.dirname(File.dirname(File.dirname(__FILE__)))) + '/data/'

mess = Rjb::import('com.aspose.email.MapiMessage').fromFile(data_dir + "MapiNote.msg")

\# Заметка #1

note1 = mess.toMapiMessageItem()

note1.setSubject("Заметка желтого цвета")

note1.setBody("Это заметка желтого цвета")

\# Заметка #2

note2 = mess.toMapiMessageItem()

note2.setSubject("Заметка розового цвета")

note2.setBody("Это заметка розового цвета")

note2.setColor(Rjb::import('com.aspose.email.NoteColor').Pink)

\# Заметка #3

note3 = mess.toMapiMessageItem()

note2.setSubject("Заметка синего цвета")

note2.setBody("Это заметка синего цвета")

note2.setColor(Rjb::import('com.aspose.email.NoteColor').Blue)

note3.setHeight(500)

note3.setWidth(500)

pst = Rjb::import('com.aspose.email.PersonalStorage').create(data_dir + "MapiNoteToPST.pst", Rjb::import('com.aspose.email.FileFormatVersion').Unicode)

notes_folder = pst.createPredefinedFolder("Заметки", Rjb::import('com.aspose.email.StandardIpmFolder').Notes)

notes_folder.addMapiMessageItem(note1)

notes_folder.addMapiMessageItem(note2)

notes_folder.addMapiMessageItem(note3)

puts "Заметка MapiNote успешно добавлена."

```
## **Скачать рабочий код**
Скачайте **Добавление MapiNote в PST (Aspose.Email)** с любого из нижеупомянутых социальных кодировочных сайтов:

- [GitHub](https://github.com/aspose-email/Aspose.Email-for-Java/blob/master/Plugins/Aspose_Email_Java_for_Ruby/lib/asposeemailjava/Outlook/addmapinotetopst.rb)