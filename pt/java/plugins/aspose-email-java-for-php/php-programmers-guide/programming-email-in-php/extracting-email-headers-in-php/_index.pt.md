---
title: "Extraindo Cabeçalhos de Email em PHP"
url: /pt/java/extracting-email-headers-in-php/
weight: 40
type: docs
---

## **Aspose.Email - Extraindo Cabeçalhos de Email**
Para Extrair Cabeçalhos de Email usando **Aspose.Email Java for PHP**, basta invocar o módulo **ExtractEmailHeaders**. Aqui você pode ver um código de exemplo.

**Código PHP**

``` php

 # Inicializar e Carregar um arquivo EML existente especificando o MessageFormat

$mailMessage=new MailMessage();

$message = $mailMessage->load($dataDir . "Message.eml");

print "Imprimindo todos os Cabeçalhos:".PHP_EOL;

\# Imprimir todos os cabeçalhos

$i=0;

while ($i < sizeof($message->getHeaders()->getCount())) {

print $message.$message->getHeaders()->get($i);

$i += 1;

}

```
## **Baixar Código em Execução**
Baixe **Extraindo Cabeçalhos de Email (Aspose.Email)** de qualquer um dos sites de codificação social mencionados abaixo:

- [GitHub](https://github.com/aspose-email/Aspose.Email-for-Java/blob/master/Plugins/Aspose_Email_Java_for_PHP/src/aspose/email/ProgrammingEmail/ExtractEmailHeaders.php)
- [CodePlex](https://archive.codeplex.com/?p=asposeemailjavaphp#src/aspose/email/ProgrammingEmail/ExtractEmailHeaders.php)