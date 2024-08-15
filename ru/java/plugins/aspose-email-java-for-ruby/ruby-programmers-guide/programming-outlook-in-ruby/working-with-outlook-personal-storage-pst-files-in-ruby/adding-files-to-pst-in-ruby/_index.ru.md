---
title: "Добавление файлов в PST в Ruby"
url: /ru/java/adding-files-to-pst-in-ruby/
weight: 10
type: docs
---

## **Aspose.Email - добавление файлов в PST**
Чтобы добавить файл в PST, используя **Aspose.Электронная почта Java для Ruby**, просто вызовите **AddFileToPST** модуль. Здесь вы можете увидеть пример кода.

**Код Ruby**

``` ruby

 data_dir = File.dirname(File.dirname(File.dirname(File.dirname(__FILE__)))) + '/data/'

pst = Rjb::import('com.aspose.email.PersonalStorage').create(data_dir + "AddFile.pst", Rjb::import('com.aspose.email.FileFormatVersion').Unicode)

fi = pst.createPredefinedFolder("Inbox", Rjb::import('com.aspose.email.StandardIpmFolder').Inbox)

fi.addFile(data_dir + "Report.xlsx", "IPM.Document.Excel.Sheet.8")

pst.dispose()

puts "Added file to PST"

```
## **Загрузить рабочий код**
Download **Добавление файлов в PST (Aspose.Email)** с любого из нижеперечисленных сайтов социального программирования:

- [GitHub](https://github.com/aspose-email/Aspose.Email-for-Java/blob/master/Plugins/Aspose_Email_Java_for_Ruby/lib/asposeemailjava/Outlook/addfiletopst.rb)
