---
title: "Exibindo Informações de Email na Tela em Ruby"
url: /pt/java/displaying-email-information-on-screen-in-ruby/
weight: 40
type: docs
---

## **Aspose.Email - Exibindo Informações de Email**
Para Exibir Informações de Email usando **Aspose.Email Java para Ruby**, basta invocar o módulo **GetEmailInfo**. Aqui você pode ver um exemplo de código.

**Código Ruby**

``` ruby

 data_dir = File.dirname(File.dirname(File.dirname(File.dirname(__FILE__)))) + '/data/'

\# Crie uma instância de MailMessage carregando um arquivo Eml

message_format = Rjb::import('com.aspose.email.MessageFormat')

message = Rjb::import('com.aspose.email.MailMessage').load(data_dir + "Message.eml")

puts "De: " + message.getFrom().to_string

puts "Para: " + message.getTo().to_string

puts "Assunto: " + message.getSubject().to_s

puts "HtmlBody: " + message.getHtmlBody().to_s

puts "TextBody: " + message.getTextBody().to_s

```
## **Baixar Código em Execução**
Baixe **Exibindo Informações de Email (Aspose.Email)** de qualquer um dos sites de codificação social mencionados abaixo:

- [GitHub](https://github.com/aspose-email/Aspose.Email-for-Java/blob/master/Plugins/Aspose_Email_Java_for_Ruby/lib/asposeemailjava/Email/getemailinfo.rb)