---
title: "Adicionando Arquivos ao PST em Ruby"
url: /pt/java/adding-files-to-pst-in-ruby/
weight: 10
type: docs
---

## **Aspose.Email - Adicionando Arquivos ao PST**
Para adicionar um arquivo ao PST usando **Aspose.Email Java para Ruby**, basta invocar o módulo **AddFileToPST**. Aqui você pode ver um exemplo de código.

**Código Ruby**

``` ruby

 data_dir = File.dirname(File.dirname(File.dirname(File.dirname(__FILE__)))) + '/data/'

pst = Rjb::import('com.aspose.email.PersonalStorage').create(data_dir + "AddFile.pst", Rjb::import('com.aspose.email.FileFormatVersion').Unicode)

fi = pst.createPredefinedFolder("Inbox", Rjb::import('com.aspose.email.StandardIpmFolder').Inbox)

fi.addFile(data_dir + "Report.xlsx", "IPM.Document.Excel.Sheet.8")

pst.dispose()

puts "Arquivo adicionado ao PST"

```
## **Baixar Código em Execução**
Baixe **Adicionando Arquivos ao PST (Aspose.Email)** de qualquer um dos sites de codificação social mencionados abaixo:

- [GitHub](https://github.com/aspose-email/Aspose.Email-for-Java/blob/master/Plugins/Aspose_Email_Java_for_Ruby/lib/asposeemailjava/Outlook/addfiletopst.rb)