---
title: "Añadir archivos a PST en Ruby"
url: /es/java/adding-files-to-pst-in-ruby/
weight: 10
type: docs
---

## **Aspose.Email - Agregar archivos a PST**
Para agregar un archivo a PST usando **Aspose.Email Java para Ruby**, simplemente invoca **AddFileToPST** módulo. Aquí puedes ver un ejemplo de código.

**Código Ruby**

``` ruby

 data_dir = File.dirname(File.dirname(File.dirname(File.dirname(__FILE__)))) + '/data/'

pst = Rjb::import('com.aspose.email.PersonalStorage').create(data_dir + "AddFile.pst", Rjb::import('com.aspose.email.FileFormatVersion').Unicode)

fi = pst.createPredefinedFolder("Inbox", Rjb::import('com.aspose.email.StandardIpmFolder').Inbox)

fi.addFile(data_dir + "Report.xlsx", "IPM.Document.Excel.Sheet.8")

pst.dispose()

puts "Added file to PST"

```
## **Descargar Running Code**
Download **Agregar archivos a PST (Aspose.Email)** desde cualquiera de los sitios de codificación social mencionados a continuación:

- [GitHub](https://github.com/aspose-email/Aspose.Email-for-Java/blob/master/Plugins/Aspose_Email_Java_for_Ruby/lib/asposeemailjava/Outlook/addfiletopst.rb)
