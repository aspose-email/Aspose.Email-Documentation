---
title: "Analisando Arquivos de Mensagem do Outlook em Ruby"
url: /pt/java/analisando-arquivos-de-mensagem-do-outlook-em-ruby/
weight: 40
type: docs
---

## **Aspose.Email - Analisando Arquivos de Mensagem do Outlook**
Para analisar um arquivo de mensagem do Outlook usando **Aspose.Email Java for Ruby**, simplesmente invoque o módulo **ParseOutlookMessageFile**. Aqui você pode ver um código de exemplo.

**Código Ruby**

``` ruby

 data_dir = File.dirname(File.dirname(File.dirname(File.dirname(__FILE__)))) + '/data/'

outlook_message_file = Rjb::import('com.aspose.email.MapiMessage').fromFile(data_dir + "Message.msg")

\# Exibir o nome do remetente

puts "Nome do Remetente : " + outlook_message_file.getSenderName().to_s

#Exibir Assunto

puts "Assunto : " + outlook_message_file.getSubject().to_s

\# Exibir Corpo

puts "Corpo : " + outlook_message_file.getBody().to_s

```
## **Baixar Código em Execução**
Baixe **Analisando Arquivos de Mensagem do Outlook (Aspose.Email)** de qualquer um dos sites de codificação social mencionados abaixo:

- [GitHub](https://github.com/aspose-email/Aspose.Email-for-Java/blob/master/Plugins/Aspose_Email_Java_for_Ruby/lib/asposeemailjava/Outlook/parseoutlookmessagefile.rb)