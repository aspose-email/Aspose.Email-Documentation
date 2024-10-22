---
title: Convirtiendo Mensajes de Correo Electrónico en PHP
type: docs
weight: 10
url: /java/convirtiendo-mensajes-de-correo-electronico-en-php/
---

## **Aspose.Email - Convirtiendo Mensajes de Correo Electrónico**

Para convertir mensajes de correo electrónico usando **Aspose.Email Java para PHP**, llama al método **convert_eml_to_msg** del módulo **Converter**. Aquí puedes ver un código de ejemplo.

**Código PHP**

```php

 public static function convert_eml_to_msg($dataDir=null){

\# Inicializar y cargar un archivo EML existente especificando el formato del mensaje

$mailMessage=new MailMessage();

$eml = $mailMessage->load($dataDir . "Message.eml");

\# Guardar el mensaje de correo electrónico en disco en formato Unicode

$saveOptions=new SaveOptions();

$eml->save($dataDir . "AnEmail.msg", $saveOptions->getDefaultMsgUnicode());

\# Mostrar estado

print "Correo convertido a msg exitosamente.".PHP_EOL;

}

```

## **Descargar Código en Ejecución**

Descarga **Convirtiendo Mensajes de Correo Electrónico (Aspose.Email)** de cualquiera de los sitios de codificación social mencionados a continuación:

-   [GitHub](https://github.com/aspose-email/Aspose.Email-for-Java/blob/master/Plugins/Aspose_Email_Java_for_PHP/src/aspose/email/ProgrammingEmail/Converter.php)
-   [CodePlex](https://archive.codeplex.com/?p=asposeemailjavaphp#src/aspose/email/ProgrammingEmail/Converter.php)

