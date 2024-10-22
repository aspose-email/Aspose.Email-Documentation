---
title: "Pesquisar Mensagens e Pastas em um PST por Alguns Critérios em Ruby"
url: /pt/java/search-messages-and-folders-in-a-pst-by-some-criteria-in-ruby/
weight: 80
type: docs
---

## **Aspose.Email - Pesquisar Mensagens e Pastas em um PST**
Para pesquisar mensagens e pastas em um PST usando **Aspose.Email Java para Ruby**, basta invocar o módulo **SearchMessagesAndFoldersInPST**. Aqui você pode ver um código de exemplo.

**Código Ruby**

```ruby

 data_dir = File.dirname(File.dirname(File.dirname(File.dirname(__FILE__)))) + '/data/'

\# Carregar o arquivo PST do Outlook

pst = Rjb::import('com.aspose.email.PersonalStorage').fromFile(data_dir + "sample.pst")

folder = pst.getRootFolder().getSubFolder("myInbox")

builder = Rjb::import('com.aspose.email.PersonalStorageQueryBuilder').new

\# Mensagens de alta importância

builder.getImportance().equals(Rjb::import('com.aspose.email.MapiImportance').High)

messages = folder.getContents(builder.getQuery())

puts "Mensagens com Alta Imp:" + messages.size().to_s

#builder = new PersonalStorageQueryBuilder();

builder.getMessageClass().equals("IPM.Note")

messages = folder.getContents(builder.getQuery())

puts "Mensagens com IPM.Note:" + messages.size().to_s

\# Mensagens com anexos E alta importância

builder.getImportance().equals(Rjb::import('com.aspose.email.MapiImportance').High)

builder.hasFlags(Rjb::import('com.aspose.email.MapiMessageFlags').MSGFLAG_HASATTACH)

messages = folder.getContents(builder.getQuery())

puts "Mensagens com anexos: " + messages.size().to_s

\# Mensagens com tamanho > 15 KB

builder.getMessageSize().greater(15000)

messages = folder.getContents(builder.getQuery())

puts "mensagens tamanho > 15Kb:" + messages.size().to_s

\# Mensagens não lidas

builder.hasNoFlags(Rjb::import('com.aspose.email.MapiMessageFlags').MSGFLAG_READ)

messages = folder.getContents(builder.getQuery())

puts "Não lidas:" + messages.size().to_s

\# Mensagens não lidas com anexos

builder.hasNoFlags(Rjb::import('com.aspose.email.MapiMessageFlags').MSGFLAG_READ)

builder.hasFlags(Rjb::import('com.aspose.email.MapiMessageFlags').MSGFLAG_HASATTACH)

messages = folder.getContents(builder.getQuery())

puts "Mensagens não lidas com anexos: " + messages.size().to_s

```
## **Baixar Código em Execução**
Baixe **Pesquisar Mensagens e Pastas em um PST (Aspose.Email)** de qualquer um dos sites de codificação social mencionados abaixo:

- [GitHub](https://github.com/aspose-email/Aspose.Email-for-Java/blob/master/Plugins/Aspose_Email_Java_for_Ruby/lib/asposeemailjava/Outlook/searchmessagesandfoldersinpst.rb)