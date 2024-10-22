---
title: "Salvar Mensagem como Rascunho em Python"
url: /pt/java/save-message-as-draft-in-python/
weight: 70
type: docs
---

## **Aspose.Email - Salvar Mensagem como Rascunho**
Para salvar uma mensagem como rascunho usando **Aspose.Email Java para Python**, use o seguinte código.

**Código Python**

``` python



\# Criar uma instância da classe MailMessage

message = self.MailMessage()

\# Definir o assunto da mensagem

message.setSubject("Nova mensagem criada pelo Aspose.Email para Java")

mail_address = self.MailAddress

\# Definir corpo Html

message.setHtmlBody("<b>Esta linha está em negrito.</b> <br/> <br/>" +

    "<font color=blue>Esta linha está em azul</font>")

\# Definir informações do remetente

message.setFrom(self.MailAddress("from@domain.com", "Nome do Remetente", False))

\# Adicionar destinatários TO

message.getTo().addMailAddress(self.MailAddress("to1@domain.com", "Destinatário 1", False))

message.getTo().addMailAddress(self.MailAddress("to2@domain.com", "Destinatário 2", False))

\# Criar uma instância de MapiMessage e carregar a instância MailMessage nela

mapiMessage = self.MapiMessage

mapi_msg = mapiMessage.fromMailMessage(message)

\# Definir os MapiMessageFlags como UNSENT e FROMME

mapi_message_flags = self.MapiMessageFlags

\# Salvar o MapiMessage no disco

mapi_msg.save(self.dataDir + "New-Draft.msg")

\# Exibir Status

print "Rascunho salvo com sucesso."

```
## **Baixar Código em Execução**
Baixe **Salvar Mensagem como Rascunho (Aspose.Email)** de qualquer um dos sites de codificação social mencionados abaixo:

- [GitHub](https://github.com/aspose-email/Aspose.Email-for-Java/releases/tag/Aspose.Email_Java_for_Python-v1.0)
- [CodePlex](http://asposeemailjavapython.codeplex.com/releases/)