---
title: "Atualizar e Salvar um E-mail em Python"
url: /pt/java/update-and-save-an-email-in-python/
weight: 80
type: docs
---

## **Aspose.Email - Atualizar e Salvar um E-mail**
Para Atualizar e Salvar um E-mail usando **Aspose.Email Java for Python**, use o seguinte código.

**Código Python**

``` python



\# Inicializar e Carregar um arquivo MSG existente, especificando o MessageFormat

mailMessage = self.MailMessage

email = mailMessage.load(self.dataDir + "Message.msg")

\# Inicializar uma variável String para obter o Assunto do E-mail

subject = email.getSubject()

\# Adicionar mais informações ao Assunto

subject = subject + " Este texto foi adicionado ao assunto existente"

\# Definir o Assunto do E-mail

email.setSubject('Este texto foi adicionado ao assunto existente')

\# Inicializar uma variável String para obter o Corpo HTML do E-mail

body = email.getHtmlBody()

\# Adicionar mais informações à variável do Corpo

body = body + "<br> Este texto foi adicionado ao corpo existente"

\# Definir o Corpo do E-mail

email.setHtmlBody(body)

\# Inicializar objeto MailAddressCollection

contacts = self.MailAddressCollection()

\# Recuperar a lista TO do E-mail

contacts = email.getTo()

\# Adicionar outro endereço de e-mail à coleção

contacts.add("to1@domain.com")

\# Definir a coleção como a lista TO do E-mail

email.setTo(contacts)

\# Inicializar MailAddressCollection

contacts = self.MailAddressCollection()

\# Recuperar a lista CC do E-mail

contacts = email.getCC()

\# Adicionar outro endereço de e-mail à coleção

contacts.add("cc2@domain.com")

\# Definir a coleção como a lista CC do E-mail

email.setCC(contacts)

\# Salvar a mensagem de E-mail no disco, especificando o MessageFormat

mailMessageSaveType = self.MailMessageSaveType

email.save(self.dataDir + "UpdateMessage.msg", mailMessageSaveType.getOutlookMessageFormat())

\# Exibir Status

print "Mensagem de e-mail atualizada com sucesso."

```
## **Baixar Código em Execução**
Baixe **Atualizar e Salvar um E-mail (Aspose.Email)** de qualquer um dos sites de codificação social mencionados abaixo:

- [GitHub](https://github.com/aspose-email/Aspose.Email-for-Java/releases/tag/Aspose.Email_Java_for_Python-v1.0)
- [CodePlex](http://asposeemailjavapython.codeplex.com/releases/)