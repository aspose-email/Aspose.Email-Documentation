---
title: "Criar Novo Email em Python"
url: /pt/java/criar-novo-email-em-python/
weight: 20
type: docs
---

## **Aspose.Email - Criar Novo Email**
Para criar um novo email usando **Aspose.Email Java para Python**, use o seguinte código.

**Código Python**

``` python



\# Criar uma instância da classe MailMessage

message = self.MailMessage()

\# Definir o assunto da mensagem

message.setSubject("Nova mensagem criada por Aspose.Email para Java")

mail_address = self.MailAddress

\# Definir corpo Html

message.setHtmlBody("<b>Esta linha está em negrito.</b> <br/> <br/>" +

   "<font color=blue>Esta linha está na cor azul</font>")

\# Definir informações do remetente

message.setFrom(self.MailAddress("from@domain.com", "Nome do Remetente", False))

\# Adicionar destinatários TO

message.getTo().addMailAddress(self.MailAddress("to1@domain.com", "Destinatário 1", False))

message.getTo().addMailAddress(self.MailAddress("to2@domain.com", "Destinatário 2", False))

\# Adicionar destinatários CC

message.getCC().addMailAddress(self.MailAddress("cc1@domain.com", "Destinatário 3", False))

message.getCC().addMailAddress(self.MailAddress("cc2@domain.com", "Destinatário 4", False))

\# Salvar mensagem nos formatos EML e MSG

mail_message_save_type = self.MailMessageSaveType

message.save(self.dataDir + "Message.eml", mail_message_save_type.getEmlFormat())

message.save(self.dataDir + "Message.msg", mail_message_save_type.getOutlookMessageFormat())

\# Exibir Status

print "Mensagens de email criadas com sucesso."

```
## **Baixar Código em Execução**
Baixe **Criar Novo Email (Aspose.Email)** de qualquer um dos sites de codificação social mencionados abaixo:

- [GitHub](https://github.com/aspose-email/Aspose.Email-for-Java/releases/tag/Aspose.Email_Java_for_Python-v1.0)
- [CodePlex](http://asposeemailjavapython.codeplex.com/releases/)