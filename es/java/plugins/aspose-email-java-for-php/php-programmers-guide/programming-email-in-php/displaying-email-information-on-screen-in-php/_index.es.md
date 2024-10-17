---
title: "Mostrando Información del Correo Electrónico en Pantalla en PHP"
url: /es/java/mostrando-informacion-del-correo-electronico-en-pantalla-en-php/
weight: 30
type: docs
---

## **Aspose.Email - Mostrando Información del Correo Electrónico**
Para mostrar información del correo electrónico utilizando **Aspose.Email Java para PHP**, simplemente invoca el módulo **GetEmailInfo**. Aquí puedes ver el código de ejemplo.

**Código PHP**

``` php

 # Crear una instancia de MailMessage cargando un archivo Eml

$message_format = new MessageFormat();

$mailMessage=new MailMessage();

$message = $mailMessage->load($dataDir . "Message.eml");

print "De: " . (string)$message->getFrom();

print "Para: " . (string)$message->getTo();

print "Asunto: " . (string)$message->getSubject();

print "CuerpoHtml: " . (string)$message->getHtmlBody();

print "CuerpoTexto: " . (string)$message->getTextBody();

```
## **Descargar Código en Ejecución**
Descarga **Mostrando Información del Correo Electrónico (Aspose.Email)** de cualquiera de los siguientes sitios de codificación social mencionados:

- [GitHub](https://github.com/aspose-email/Aspose.Email-for-Java/blob/master/Plugins/Aspose_Email_Java_for_PHP/src/aspose/email/ProgrammingEmail/GetEmailInfo.php)
- [CodePlex](https://archive.codeplex.com/?p=asposeemailjavaphp#src/aspose/email/ProgrammingEmail/GetEmailInfo.php)