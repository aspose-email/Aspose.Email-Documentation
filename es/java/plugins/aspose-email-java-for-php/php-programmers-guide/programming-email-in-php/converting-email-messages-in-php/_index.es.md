---
title: "Conversión de mensajes de correo electrónico en PHP"
url: /es/java/converting-email-messages-in-php/
weight: 10
type: docs
---

## **Aspose.Email - Conversión de mensajes de correo electrónico**
Para convertir mensajes de correo electrónico mediante **Aspose.Email Java para PHP**, llama **convert_eml_to_msg** método de **Converter** módulo. Aquí puedes ver un ejemplo de código.

**Código PHP**

``` php

 public static function convert_eml_to_msg($dataDir=null){

\# Initialize and Load an existing EML file by specifying the MessageFormat

$mailMessage=new MailMessage();

$eml = $mailMessage->load($dataDir . "Message.eml");

\# Save the Email message to disk in Unicode format

$saveOptions=new SaveOptions();

$eml->save($dataDir . "AnEmail.msg", $saveOptions->getDefaultMsgUnicode());

\# Display Status

print "Converted email to msg successfully.".PHP_EOL;

}

```
## **Descargar Running Code**
Download **Conversión de mensajes de correo electrónico (Aspose.Email)** desde cualquiera de los sitios de codificación social mencionados a continuación:

- [GitHub](https://github.com/aspose-email/Aspose.Email-for-Java/blob/master/Plugins/Aspose_Email_Java_for_PHP/src/aspose/email/ProgrammingEmail/Converter.php)
- [CodePlex](https://archive.codeplex.com/?p=asposeemailjavaphp#src/aspose/email/ProgrammingEmail/Converter.php)
