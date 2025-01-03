---
title: "Adicionando MapiJournal ao PST em Ruby"
url: /pt/java/adding-mapijournal-to-pst-in-ruby/
weight: 40
type: docs
---
  
## **Aspose.Email - Adicionando MapiJournal ao PST**  
Para adicionar MapiJournal ao PST usando **Aspose.Email Java para Ruby**, basta invocar o módulo **AddMapiJournalToPST**. Aqui você pode ver um exemplo de código.  
  
**Código Ruby**  
  
```ruby  
  
 data_dir = File.dirname(File.dirname(File.dirname(File.dirname(__FILE__)))) + '/data/'  
  
d1 = Rjb::import('java.util.Date').new  
  
cl = Rjb::import('java.util.Calendar').getInstance()  
  
cl.setTime(d1)  
  
cl.add(Rjb::import('java.util.Calendar').HOUR, 1)  
  
d2 = cl.getTime()  
  
journal = Rjb::import('com.aspose.email.MapiJournal').new("registro diário", "chamado no escuro", "Chamada telefônica", "Chamada telefônica")  
  
journal.setStartTime(d1)  
  
journal.setEndTime(d2)  
  
pst = Rjb::import('com.aspose.email.PersonalStorage').create(data_dir + "JournalPST.pst", Rjb::import('com.aspose.email.FileFormatVersion').Unicode)  
  
journal_folder = pst.createPredefinedFolder("Journal", Rjb::import('com.aspose.email.StandardIpmFolder').Journal)  
  
journal_folder.addMapiMessageItem(journal)  
  
puts "MapiJournal adicionado com sucesso."  
  
```  
## **Baixar Código em Execução**  
Baixe **Adicionando MapiJournal ao PST (Aspose.Email)** de qualquer um dos sites de codificação social mencionados abaixo:  
  
- [GitHub](https://github.com/aspose-email/Aspose.Email-for-Java/blob/master/Plugins/Aspose_Email_Java_for_Ruby/lib/asposeemailjava/Outlook/addmapijournaltopst.rb)  