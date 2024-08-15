---
title: "Análisis de archivos de mensajes de Outlook en PHP"
url: /es/java/parsing-outlook-message-files-in-php/
weight: 30
type: docs
---

## **Aspose.Email - Análisis de archivos de mensajes de Outlook**
Para analizar el archivo de mensajes de Outlook usando **Aspose.Email Java para PHP**, simplemente invoca **ParseOutlookMessageFile** módulo. Aquí puedes ver un ejemplo de código.

**Código PHP**

``` php

 $mapiMessage=new MapiMessage();

$outlook_message_file = $mapiMessage->fromFile($dataDir . "Message.msg");

\# Display sender's name

print "Sender Name : " . $outlook_message_file->getSenderName();

#Display Subject

print "Subject : " . $outlook_message_file->getSubject();

\# Display Body

print "Body : " . $outlook_message_file->getBody();

```
## **Descargar Running Code**
Download **Análisis de archivos de mensajes de Outlook (Aspose.Email)** desde cualquiera de los sitios de codificación social mencionados a continuación:

- [GitHub](https://github.com/aspose-email/Aspose.Email-for-Java/blob/master/Plugins/Aspose_Email_Java_for_PHP/src/aspose/email/ProgrammingOutlook/WorkingWithOutlookMessageFiles/ParseOutlookMessageFile.php)
- [CodePlex](https://archive.codeplex.com/?p=asposeemailjavaphp#src/aspose/email/ProgrammingOutlook/WorkingWithOutlookMessageFiles/ParseOutlookMessageFile.php)
