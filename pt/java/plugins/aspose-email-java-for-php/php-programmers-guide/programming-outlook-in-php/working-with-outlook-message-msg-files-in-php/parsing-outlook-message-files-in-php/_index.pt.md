---
title: "Analisando Arquivos de Mensagem do Outlook em PHP"
url: /pt/java/analisando-arquivos-de-mensagem-do-outlook-em-php/
weight: 30
type: docs
---

## **Aspose.Email - Analisando Arquivos de Mensagem do Outlook**
Para analisar o arquivo de mensagem do Outlook usando **Aspose.Email Java para PHP**, basta invocar o módulo **ParseOutlookMessageFile**. Aqui você pode ver um exemplo de código.

**Código PHP**

``` php

 $mapiMessage=new MapiMessage();

$outlook_message_file = $mapiMessage->fromFile($dataDir . "Message.msg");

\# Exibir nome do remetente

print "Nome do Remetente : " . $outlook_message_file->getSenderName();

#Exibir Assunto

print "Assunto : " . $outlook_message_file->getSubject();

\# Exibir Corpo

print "Corpo : " . $outlook_message_file->getBody();

```
## **Baixar Código em Execução**
Baixe **Analisando Arquivos de Mensagem do Outlook (Aspose.Email)** de qualquer um dos sites de codificação social mencionados abaixo:

- [GitHub](https://github.com/aspose-email/Aspose.Email-for-Java/blob/master/Plugins/Aspose_Email_Java_for_PHP/src/aspose/email/ProgrammingOutlook/WorkingWithOutlookMessageFiles/ParseOutlookMessageFile.php)
- [CodePlex](https://archive.codeplex.com/?p=asposeemailjavaphp#src/aspose/email/ProgrammingOutlook/WorkingWithOutlookMessageFiles/ParseOutlookMessageFile.php)