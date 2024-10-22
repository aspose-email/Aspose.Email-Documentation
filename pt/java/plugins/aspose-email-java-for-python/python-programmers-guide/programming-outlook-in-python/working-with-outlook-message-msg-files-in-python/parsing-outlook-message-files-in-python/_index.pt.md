---
title: "Analisando Arquivos de Mensagens do Outlook em Python"
url: /pt/java/analisando-arquivos-de-mensagens-do-outlook-em-python/
weight: 30
type: docs
---

## **Aspose.Email - Analisando Arquivos de Mensagens do Outlook**
Para analisar Arquivos de Mensagens do Outlook usando **Aspose.Email Java para Python**, use o código a seguir.

**Código Python**

```python



mapiMessage = self.MapiMessage

outlook_message_file = mapiMessage.fromFile(self.dataDir + "Message.msg")

\# Exibir o nome do remetente

print "Nome do Remetente : " 

print outlook_message_file.getSenderName()

#Exibir Assunto

print "Assunto : " 

print outlook_message_file.getSubject()

\# Exibir Corpo

print "Corpo : " 

print outlook_message_file.getBody()

```
## **Baixar Código em Execução**
Baixe **Analisando Arquivos de Mensagens do Outlook (Aspose.Email)** de qualquer um dos sites de codificação social mencionados abaixo:

- [GitHub](https://github.com/aspose-email/Aspose.Email-for-Java/releases/tag/Aspose.Email_Java_for_Python-v1.0)
- [CodePlex](http://asposeemailjavapython.codeplex.com/releases/)