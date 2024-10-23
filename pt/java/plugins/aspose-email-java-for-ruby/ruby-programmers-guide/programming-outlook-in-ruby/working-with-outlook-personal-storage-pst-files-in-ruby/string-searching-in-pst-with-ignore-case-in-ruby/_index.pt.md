---
title: "Busca de String em PST Ignorando Maiúsculas e Minúsculas em Ruby"
url: /pt/java/string-searching-in-pst-with-ignore-case-in-ruby/
weight: 90
type: docs
---

## **Aspose.Email - Busca de String em PST Ignorando Maiúsculas e Minúsculas**
Para buscar Strings em PST ignorando maiúsculas e minúsculas usando **Aspose.Email Java para Ruby**, simplesmente invoque o módulo **StringSearchInPST**. Aqui você pode ver um código de exemplo.

**Código Ruby**

```ruby

 data_dir = File.dirname(File.dirname(File.dirname(File.dirname(__FILE__)))) + '/data/'

\# Carregar o arquivo PST do Outlook

pst = Rjb::import('com.aspose.email.PersonalStorage').create(data_dir + "search.pst", Rjb::import('com.aspose.email.FileFormatVersion').Unicode)

fi = pst.createPredefinedFolder("Inbox", Rjb::import('com.aspose.email.StandardIpmFolder').Inbox)

fi.addMessage(Rjb::import('com.aspose.email.MapiMessage').fromMailMessage(Rjb::import('com.aspose.email.MailMessage').load(data_dir + "search.pst")))

builder = Rjb::import('com.aspose.email.MailQueryBuilder').new

builder.getFrom().contains("automated", true)

query = builder.getQuery()

coll = fi.getContents(query)

puts "Total de Resultados:" + coll.size().to_s

```
## **Baixar Código para Execução**
Baixe **Busca de String em PST Ignorando Maiúsculas e Minúsculas (Aspose.Email)** de qualquer um dos sites de codificação social mencionados abaixo:

- [GitHub](https://github.com/aspose-email/Aspose.Email-for-Java/blob/master/Plugins/Aspose_Email_Java_for_Ruby/lib/asposeemailjava/Outlook/stringsearchinpst.rb)