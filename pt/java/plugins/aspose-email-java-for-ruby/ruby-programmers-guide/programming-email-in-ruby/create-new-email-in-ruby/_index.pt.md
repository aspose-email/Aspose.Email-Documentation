---
title: "Criar Novo Email em Ruby"
url: /pt/java/create-new-email-in-ruby/
weight: 20
type: docs
---

## **Aspose.Email - Criar Novo Email**
Para criar um novo email usando **Aspose.Email Java para Ruby**, basta invocar o módulo **CreateNewEmail**. Aqui você pode ver um exemplo de código.

**Código Ruby**

``` ruby

 data_dir = File.dirname(File.dirname(File.dirname(File.dirname(__FILE__)))) + '/data/'



\# Criar uma nova instância da classe MailMessage

message = Rjb::import('com.aspose.email.MailMessage').new

\# Definir o assunto da mensagem

message.setSubject("Nova mensagem criada pelo Aspose.Email para Java")

mail_address = Rjb::import('com.aspose.email.MailAddress')

\# Definir corpo em Html

message.setHtmlBody("<b>Esta linha está em negrito.</b> <br/> <br/>" +

        "<font color=blue>Esta linha está na cor azul</font>")

\# Definir informações do remetente

message.setFrom(mail_address.new("from@domain.com", "Nome do Remetente", false))

\# Adicionar destinatários TO

message.getTo().add(mail_address.new("to1@domain.com", "Destinatário 1", false))

message.getTo().add(mail_address.new("to2@domain.com", "Destinatário 2", false))

\# Adicionar destinatários CC

message.getCC().add(mail_address.new("cc1@domain.com", "Destinatário 3", false))

message.getCC().add(mail_address.new("cc2@domain.com", "Destinatário 4", false))

\# Salvar mensagem nos formatos EML e MSG

mail_message_save_type = Rjb::import('com.aspose.email.MailMessageSaveType')

message.save(data_dir + "Message.eml", mail_message_save_type.getEmlFormat())

message.save(data_dir + "Message.msg", mail_message_save_type.getOutlookMessageFormat())

\# Exibir Status

puts "Mensagens de email criadas com sucesso."

```
## **Baixar Código em Execução**
Baixe **Criar Novo Email (Aspose.Email)** de qualquer um dos sites de codificação social mencionados abaixo:

- [GitHub](https://github.com/aspose-email/Aspose.Email-for-Java/blob/master/Plugins/Aspose_Email_Java_for_Ruby/lib/asposeemailjava/Email/createnewemail.rb)