---
title: "Extracción de encabezados de correo electrónico en PHP"
url: /es/java/extracting-email-headers-in-php/
weight: 40
type: docs
---

## **Aspose.Email - Extracción de encabezados de correo electrónico**
Para extraer encabezados de correo electrónico usando **Aspose.Email Java para PHP**, simplemente invoca **ExtractEmailHeaders** módulo. Aquí puedes ver un ejemplo de código.

**Código PHP**

``` php

 # Initialize and Load an existing EML file by specifying the MessageFormat

$mailMessage=new MailMessage();

$message = $mailMessage->load($dataDir . "Message.eml");

print "Printing all Headers:".PHP_EOL;

\# Print out all the headers

$i=0;

while ($i < sizeof($message->getHeaders()->getCount())) {

print $message.$message->getHeaders()->get($i);

$i += 1;

}

```
## **Descargar Running Code**
Download **Extracción de encabezados de correo electrónico (Aspose.Email)** desde cualquiera de los sitios de codificación social mencionados a continuación:

- [GitHub](https://github.com/aspose-email/Aspose.Email-for-Java/blob/master/Plugins/Aspose_Email_Java_for_PHP/src/aspose/email/ProgrammingEmail/ExtractEmailHeaders.php)
- [CodePlex](https://archive.codeplex.com/?p=asposeemailjavaphp#src/aspose/email/ProgrammingEmail/ExtractEmailHeaders.php)
