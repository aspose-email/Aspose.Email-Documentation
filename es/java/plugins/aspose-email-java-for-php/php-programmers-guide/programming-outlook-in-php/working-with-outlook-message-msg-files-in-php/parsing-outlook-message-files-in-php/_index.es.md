---
title: "Análisis de Archivos de Mensajes de Outlook en PHP"
url: /es/java/parsing-outlook-message-files-in-php/
weight: 30
type: docs
---

## **Aspose.Email - Análisis de Archivos de Mensajes de Outlook**
Para analizar un archivo de mensaje de Outlook usando **Aspose.Email Java para PHP**, simplemente invoca el módulo **ParseOutlookMessageFile**. Aquí puedes ver un código de ejemplo.

**Código PHP**

``` php

 $mapiMessage=new MapiMessage();

$outlook_message_file = $mapiMessage->fromFile($dataDir . "Message.msg");

\# Mostrar el nombre del remitente

print "Nombre del Remitente : " . $outlook_message_file->getSenderName();

#Mostrar Asunto

print "Asunto : " . $outlook_message_file->getSubject();

\# Mostrar Cuerpo

print "Cuerpo : " . $outlook_message_file->getBody();

```
## **Descargar Código en Ejecución**
Descarga **Análisis de Archivos de Mensajes de Outlook (Aspose.Email)** de cualquiera de los sitios de codificación social mencionados a continuación:

- [GitHub](https://github.com/aspose-email/Aspose.Email-for-Java/blob/master/Plugins/Aspose_Email_Java_for_PHP/src/aspose/email/ProgrammingOutlook/WorkingWithOutlookMessageFiles/ParseOutlookMessageFile.php)
- [CodePlex](https://archive.codeplex.com/?p=asposeemailjavaphp#src/aspose/email/ProgrammingOutlook/WorkingWithOutlookMessageFiles/ParseOutlookMessageFile.php)