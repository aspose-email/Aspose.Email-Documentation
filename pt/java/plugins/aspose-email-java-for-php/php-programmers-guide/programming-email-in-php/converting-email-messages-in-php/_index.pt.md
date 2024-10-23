---
title: "Convertendo Mensagens de Email em PHP"
url: /pt/java/converting-email-messages-in-php/
weight: 10
type: docs
---

## **Aspose.Email - Convertendo Mensagens de Email**
Para converter mensagens de email usando **Aspose.Email Java for PHP**, chame o método **convert_eml_to_msg** do módulo **Converter**. Aqui você pode ver um exemplo de código.

**Código PHP**

``` php

 public static function convert_eml_to_msg($dataDir=null){

\# Inicializar e carregar um arquivo EML existente especificando o formato da mensagem

$mailMessage=new MailMessage();

$eml = $mailMessage->load($dataDir . "Message.eml");

\# Salvar a mensagem de email no disco em formato Unicode

$saveOptions=new SaveOptions();

$eml->save($dataDir . "AnEmail.msg", $saveOptions->getDefaultMsgUnicode());

\# Exibir Status

print "Email convertido para msg com sucesso.".PHP_EOL;

}

```
## **Baixar Código em Execução**
Baixe **Convertendo Mensagens de Email (Aspose.Email)** de qualquer um dos sites de codificação social mencionados abaixo:

- [GitHub](https://github.com/aspose-email/Aspose.Email-for-Java/blob/master/Plugins/Aspose_Email_Java_for_PHP/src/aspose/email/ProgrammingEmail/Converter.php)
- [CodePlex](https://archive.codeplex.com/?p=asposeemailjavaphp#src/aspose/email/ProgrammingEmail/Converter.php)