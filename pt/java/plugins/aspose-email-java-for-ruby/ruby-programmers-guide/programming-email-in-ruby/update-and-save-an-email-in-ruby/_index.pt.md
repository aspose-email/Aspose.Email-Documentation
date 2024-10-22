---
title: "Atualizar e Salvar um Email em Ruby"
url: /pt/java/update-and-save-an-email-in-ruby/
weight: 80
type: docs
---

## **Aspose.Email - Atualizar e Salvar um Email**
Para Atualizar e Salvar um Email usando **Aspose.Email Java para Ruby**, simplesmente invoque o módulo **UpdateEmail**. Aqui você pode ver um exemplo de código.

**Código Ruby**

``` ruby

 data_dir = File.dirname(File.dirname(File.dirname(File.dirname(__FILE__)))) + '/data/'



\# Inicializar e Carregar um arquivo MSG existente especificando o MessageFormat

email = Rjb::import('com.aspose.email.MailMessage').load(data_dir + "Message.msg")

\# Inicializar uma variável String para obter o Assunto do Email

subject = email.getSubject()

\# Adicionar mais informações ao Assunto

subject = subject + " Este texto é adicionado ao assunto existente"

\# Definir o Assunto do Email

email.setSubject(subject)

\# Inicializar uma variável String para obter o Corpo HTML do Email

body = email.getHtmlBody()

\# Adicionar mais informações à variável Corpo

body = body + "<br> Este texto é adicionado ao corpo existente"

\# Definir o Corpo do Email

email.setHtmlBody(body)

\# Inicializar objeto MailAddressCollection

contacts = Rjb::import('com.aspose.email.MailAddressCollection').new

\# Recuperar a lista TO do Email

contacts = email.getTo()

\# Adicionar outro endereço de email à coleção

contacts.add("to1@domain.com")

\# Definir a coleção como a lista TO do Email

email.setTo(contacts)

\# Inicializar MailAddressCollection

contacts = Rjb::import('com.aspose.email.MailAddressCollection').new

\# Recuperar a lista CC do Email

contacts = email.getCC()

\# Adicionar outro endereço de email à coleção

contacts.add("cc2@domain.com")

\# Definir a coleção como a lista CC do Email

email.setCC(contacts)

\# Salvar a mensagem de Email no disco especificando o MessageFormat

email.save(data_dir + "UpdateMessage.msg", Rjb::import('com.aspose.email.MailMessageSaveType').getOutlookMessageFormat())

\# Exibir Status

puts "Mensagem de email atualizada com sucesso."

```
## **Baixar Código em Execução**
Baixe **Atualizar e Salvar um Email (Aspose.Email)** de qualquer um dos sites de codificação social mencionados abaixo:

- [GitHub](https://github.com/aspose-email/Aspose.Email-for-Java/blob/master/Plugins/Aspose_Email_Java_for_Ruby/lib/asposeemailjava/Email/updateemail.rb)