---
title: "Personalizando Cabeçalhos de Email em Ruby"
url: /pt/java/personalizando-cabecalhos-de-email-em-ruby/
weight: 30
type: docs
---

## **Aspose.Email - Personalizando Cabeçalhos de Email**
Para Personalizar Cabeçalhos de Email usando **Aspose.Email Java para Ruby**, simplesmente invoque o módulo **CustomizeEmailHeaders**. Aqui você pode ver um exemplo de código.

**Código Ruby**

``` ruby

 data_dir = File.dirname(File.dirname(File.dirname(File.dirname(__FILE__)))) + '/data/'



\# Criar uma nova instância da classe MailMessage

message = Rjb::import('com.aspose.email.MailMessage').new

\# Definir o assunto da mensagem

message.setSubject("Nova mensagem criada pelo Aspose.Email para Java")

\# Definir corpo Html

message.setHtmlBody("<b>Esta linha está em negrito.</b> <br/> <br/>" +

        "<font color=blue>Esta linha está em azul</font>")

\# Definir informações do remetente

message.setFrom(Rjb::import('com.aspose.email.MailAddress').new("from@domain.com", "Nome do Remetente", false))

\# Adicionar destinatários TO

message.getTo().add(Rjb::import('com.aspose.email.MailAddress').new("to@domain.com", "Destinatário 1", false))

\# Assunto da mensagem

message.setSubject("Personalizando Cabeçalhos de Email")

\# Especificar Data

calendar = Rjb::import('java.util.Calendar').getInstance(Rjb::import('java.util.TimeZone').getTimeZone("GMT"))

date = calendar.getTime()

message.setDate(date)

\# Especificar XMailer

message.setXMailer("Aspose.Email")

\# Especificar Cabeçalho Secreto

message.getHeaders().add("secret-header", "mystery")

\# Salvar mensagem no disco

message.save(data_dir + "MsgHeaders.msg", Rjb::import('com.aspose.email.MessageFormat').getMsg())

\# Exibir Status

puts "Cabeçalhos de mensagem personalizados com sucesso."

```
## **Baixar Código em Execução**
Baixe **Personalizando Cabeçalhos de Email (Aspose.Email)** de qualquer um dos sites de codificação social mencionados abaixo:

- [GitHub](https://github.com/aspose-email/Aspose.Email-for-Java/blob/master/Plugins/Aspose_Email_Java_for_Ruby/lib/asposeemailjava/Email/customizeemailheaders.rb)