---
title: "Добавление файлов в PST на Ruby"
url: /ru/java/adding-files-to-pst-in-ruby/
weight: 10
type: docs
---

## **Aspose.Email - Добавление файлов в PST**
Чтобы добавить файл в PST с помощью **Aspose.Email Java для Ruby**, просто вызовите модуль **AddFileToPST**. Здесь вы можете видеть пример кода.

**Ruby код**

``` ruby

 data_dir = File.dirname(File.dirname(File.dirname(File.dirname(__FILE__)))) + '/data/'

pst = Rjb::import('com.aspose.email.PersonalStorage').create(data_dir + "AddFile.pst", Rjb::import('com.aspose.email.FileFormatVersion').Unicode)

fi = pst.createPredefinedFolder("Inbox", Rjb::import('com.aspose.email.StandardIpmFolder').Inbox)

fi.addFile(data_dir + "Report.xlsx", "IPM.Document.Excel.Sheet.8")

pst.dispose()

puts "Добавлен файл в PST"

```
## **Скачать работающий код**
Скачайте **Добавление файлов в PST (Aspose.Email)** с любого из нижеупомянутых сайтов для социального кодирования:

- [GitHub](https://github.com/aspose-email/Aspose.Email-for-Java/blob/master/Plugins/Aspose_Email_Java_for_Ruby/lib/asposeemailjava/Outlook/addfiletopst.rb)