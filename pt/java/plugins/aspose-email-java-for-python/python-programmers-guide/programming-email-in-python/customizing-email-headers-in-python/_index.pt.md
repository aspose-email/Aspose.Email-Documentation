---
title: "Personalizando Cabeçalhos de Email em Python"
url: /pt/java/customizando-email-headers-in-python/
weight: 30
type: docs
---

## **Aspose.Email - Personalizando Cabeçalhos de Email**
Para Personalizar Cabeçalhos de Email usando **Aspose.Email Java for Python**, use o seguinte código.

**Código Python**

``` python



\# Crie uma instância da classe MailMessage

message = self.MailMessage()

    # Defina o assunto da mensagem

message.setSubject("Nova mensagem criada pelo Aspose.Email para Java")

\# Defina o corpo em Html

message.setHtmlBody("<b>Esta linha está em negrito.</b> <br/> <br/>" +

    "<font color=blue>Esta linha está em azul</font>")

\# Defina as informações do remetente

message.setFrom(self.MailAddress("from@domain.com", "Nome do Remetente", False))

\# Adicione destinatários TO

message.getTo().addMailAddress(self.MailAddress("to@domain.com", "Destinatário 1", False))

\# Assunto da mensagem

message.setSubject("Personalizando Cabeçalhos de Email")

\# Especifique a Data

timeZone = self.TimeZone

calendar = self.Calendar

calendar = calendar.getInstance(timeZone.getTimeZone("GMT"))

date = calendar.getTime()

message.setDate(date)

\# Especifique XMailer

message.setXMailer("Aspose.Email")

\# Especifique Cabeçalho Secreto

message.getHeaders().add("secret-header", "mystery")

\# Salve a mensagem no disco

messageFormat= self.MessageFormat

message.save(self.dataDir + "MsgHeaders.msg", messageFormat.getMsg())

\# Exiba o Status

print "Cabeçalhos da mensagem personalizados com sucesso."

```
## **Baixar Código em Execução**
Baixe **Personalizando Cabeçalhos de Email (Aspose.Email)** de qualquer um dos sites de codificação social mencionados abaixo:

- [GitHub](https://github.com/aspose-email/Aspose.Email-for-Java/releases/tag/Aspose.Email_Java_for_Python-v1.0)
- [CodePlex](http://asposeemailjavapython.codeplex.com/releases/)