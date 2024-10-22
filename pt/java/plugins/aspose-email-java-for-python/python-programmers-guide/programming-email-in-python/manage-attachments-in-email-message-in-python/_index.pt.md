---
title: "Gerenciar Anexos em Mensagens de Email em Python"
url: /pt/java/manage-attachments-in-email-message-in-python/
weight: 60
type: docs
---

## **Aspose.Email - Gerenciar Anexos em Email**
Para gerenciar anexos em email usando **Aspose.Email Java for Python**, use o seguinte código.

**Código Python**

``` python



\# Criar uma instância da classe MailMessage

message = self.MailMessage()

\# Definir o assunto da mensagem

message.setSubject("Nova mensagem criada pelo Aspose.Email para Java")

mail_address = self.MailAddress

\# Definir corpo HTML

message.setHtmlBody("<b>Esta linha está em negrito.</b> <br/> <br/>" +

    "<font color=blue>Esta linha está em azul</font>")

\# Definir informações do remetente

message.setFrom(self.MailAddress("from@domain.com", "Nome do Remetente", False))

\# Adicionar destinatários TO

message.getTo().addMailAddress(self.MailAddress("to1@domain.com", "Destinatário 1", False))

\# Adicionando anexo

\# Carregar um anexo

attachment = self.Attachment(self.dataDir + "1.txt")

\# Adicionar anexo na instância da classe MailMessage

message.addAttachment(attachment)

\# Salvar mensagem no disco

messageFormat = self.MessageFormat

message.save(self.dataDir + "Add-Attachment.msg", messageFormat.getMsg())

\# Exibir Status

print "Anexo adicionado com sucesso."

```
## **Baixar Código em Execução**
Baixe **Gerenciar Anexos em Mensagens de Email (Aspose.Email)** de qualquer um dos sites de codificação social mencionados abaixo:

- [GitHub](https://github.com/aspose-email/Aspose.Email-for-Java/releases/tag/Aspose.Email_Java_for_Python-v1.0)
- [CodePlex](http://asposeemailjavapython.codeplex.com/releases/)