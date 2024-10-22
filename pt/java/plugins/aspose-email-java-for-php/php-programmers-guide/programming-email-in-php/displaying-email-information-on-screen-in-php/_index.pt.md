---
title: "Exibindo Informações de Email na Tela em PHP"
url: /pt/java/exibindo-informacoes-de-email-na-tela-em-php/
weight: 30
type: docs
---

## **Aspose.Email - Exibindo Informações de Email**
Para exibir informações de email usando **Aspose.Email Java for PHP**, simplesmente invoque o módulo **GetEmailInfo**. Aqui você pode ver um exemplo de código.

**Código PHP**

``` php

 # Crie uma instância de MailMessage carregando um arquivo Eml

$message_format = new MessageFormat();

$mailMessage=new MailMessage();

$message = $mailMessage->load($dataDir . "Message.eml");

print "De: " . (string)$message->getFrom();

print "Para: " . (string)$message->getTo();

print "Assunto: " . (string)$message->getSubject();

print "HtmlBody: " . (string)$message->getHtmlBody();

print "TextBody: " . (string)$message->getTextBody();

```
## **Baixar Código em Execução**
Baixe **Exibindo Informações de Email (Aspose.Email)** de qualquer um dos sites de codificação social mencionados abaixo:

- [GitHub](https://github.com/aspose-email/Aspose.Email-for-Java/blob/master/Plugins/Aspose_Email_Java_for_PHP/src/aspose/email/ProgrammingEmail/GetEmailInfo.php)
- [CodePlex](https://archive.codeplex.com/?p=asposeemailjavaphp#src/aspose/email/ProgrammingEmail/GetEmailInfo.php)