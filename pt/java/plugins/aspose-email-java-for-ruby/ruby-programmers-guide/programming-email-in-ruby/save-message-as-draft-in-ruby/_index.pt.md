---
title: "Salvar Mensagem como Rascunho em Ruby"
url: /pt/java/save-message-as-draft-in-ruby/
weight: 70
type: docs
---

## **Aspose.Email - Salvar Mensagem como Rascunho**
Para Salvar Mensagem como Rascunho usando **Aspose.Email Java para Ruby**, basta invocar o módulo **SaveMessageAsDraft**. Aqui você pode ver um código de exemplo.

**Código Ruby**

``` ruby

 data_dir = File.dirname(File.dirname(File.dirname(File.dirname(__FILE__)))) + '/data/'



\# Crie uma nova instância da classe MailMessage

message = Rjb::import('com.aspose.email.MailMessage').new

\# Defina o assunto da mensagem

message.setSubject("Nova mensagem criada pelo Aspose.Email para Java")

mail_address = Rjb::import('com.aspose.email.MailAddress')

\# Defina o corpo Html

message.setHtmlBody("<b>Esta linha está em negrito.</b> <br/> <br/>" +

        "<font color=blue>Esta linha está em azul</font>")

\# Defina as informações do remetente

message.setFrom(mail_address.new("from@domain.com", "Nome do Remetente", false))

\# Adicione os destinatários TO

message.getTo().add(mail_address.new("to1@domain.com", "Destinatário 1", false))

message.getTo().add(mail_address.new("to2@domain.com", "Destinatário 2", false))

\# Crie uma instância de MapiMessage e carregue a instância MailMessage nela

mapi_msg = Rjb::import('com.aspose.email.MapiMessage').fromMailMessage(message)

\# Defina as MapiMessageFlags como UNSENT e FROMME

mapi_message_flags = Rjb::import('com.aspose.email.MapiMessageFlags')

mapi_msg.setMessageFlags(mapi_message_flags.MSGFLAG_UNSENT || mapi_message_flags.MSGFLAG_FROMME)

\# Salve o MapiMessage no disco

mapi_msg.save(data_dir + "Novo-Rascunho.msg")

\# Exiba o Status

puts "Rascunho salvo com sucesso."

```
## **Baixar Código em Execução**
Baixe **Salvar Mensagem como Rascunho (Aspose.Email)** de qualquer um dos sites de codificação social mencionados abaixo:

- [GitHub](https://github.com/aspose-email/Aspose.Email-for-Java/blob/master/Plugins/Aspose_Email_Java_for_Ruby/lib/asposeemailjava/Email/savemessageasdraft.rb)