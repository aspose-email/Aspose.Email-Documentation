---
title: "Exibindo Informações de Email na Tela em Python"
url: /pt/java/exibindo-informacoes-de-email-na-tela-em-python/
weight: 40
type: docs
---

## **Aspose.Email - Exibindo Informações de Email**
Para exibir informações de email usando **Aspose.Email Java para Python**, use o seguinte código.

**Código Python**

``` python



\# Criar uma instância MailMessage carregando um arquivo Eml

message_format = self.MessageFormat

mailMessage = self.MailMessage

message = mailMessage.load(self.dataDir + "Message.eml")

print "De: " 

print message.getFrom()

print "Para: " 

print message.getTo()

print "Assunto: " 

print message.getSubject()

print "HtmlBody: " 

print message.getHtmlBody()

print "TextBody: " 

print message.getTextBody()

```
## **Baixar Código em Execução**
Baixe **Exibindo Informações de Email (Aspose.Email)** de qualquer um dos sites de codificação social mencionados abaixo:

- [GitHub](https://github.com/aspose-email/Aspose.Email-for-Java/releases/tag/Aspose.Email_Java_for_Python-v1.0)
- [CodePlex](http://asposeemailjavapython.codeplex.com/releases/)