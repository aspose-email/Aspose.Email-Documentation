---
title: "Convertendo Mensagens de Email em Python"
url: /pt/java/converting-email-messages-in-python/
weight: 10
type: docs
---

## **Aspose.Email - Convertendo Mensagens de Email**
Para converter mensagens de email usando **Aspose.Email Java para Python**, utilize o seguinte código.

**Código Python**

``` python

 # Inicializar e carregar um arquivo EML existente especificando o MessageFormat

mailMessage = self.MailMessage

eml = mailMessage.load(self.dataDir + "Message.eml")

\# Salvar a mensagem de email no disco em formato Unicode

saveOptions= self.SaveOptions

eml.save(self.dataDir + "AnEmail.msg", saveOptions.getDefaultMsgUnicode())

\# Exibir Status

print "Email convertido para msg com sucesso."

```
## **Baixar Código em Execução**
Baixe **Convertendo Mensagens de Email (Aspose.Email)** de qualquer um dos sites de codificação social mencionados abaixo:

- [GitHub](https://github.com/aspose-email/Aspose.Email-for-Java/releases/tag/Aspose.Email_Java_for_Python-v1.0)
- [CodePlex](http://asposeemailjavapython.codeplex.com/releases/)