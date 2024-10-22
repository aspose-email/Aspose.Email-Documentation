---
title: "Extracción de Encabezados de Correo Electrónico en PHP"
url: /es/java/extracting-email-headers-in-php/
weight: 40
type: docs
---

## **Aspose.Email - Extracción de Encabezados de Correo Electrónico**
Para extraer encabezados de correo electrónico utilizando **Aspose.Email Java para PHP**, simplemente invoca el módulo **ExtractEmailHeaders**. Aquí puedes ver un código de ejemplo.

**Código PHP**

``` php

 # Inicializar y cargar un archivo EML existente especificando el formato del mensaje

$mailMessage=new MailMessage();

$message = $mailMessage->load($dataDir . "Message.eml");

print "Imprimiendo todos los encabezados:".PHP_EOL;

\# Imprimir todos los encabezados

$i=0;

while ($i < sizeof($message->getHeaders()->getCount())) {

print $message.$message->getHeaders()->get($i);

$i += 1;

}

```
## **Descargar Código en Ejecución**
Descarga **Extracción de Encabezados de Correo Electrónico (Aspose.Email)** de cualquiera de los sitios de codificación social mencionados a continuación:

- [GitHub](https://github.com/aspose-email/Aspose.Email-for-Java/blob/master/Plugins/Aspose_Email_Java_for_PHP/src/aspose/email/ProgrammingEmail/ExtractEmailHeaders.php)
- [CodePlex](https://archive.codeplex.com/?p=asposeemailjavaphp#src/aspose/email/ProgrammingEmail/ExtractEmailHeaders.php)