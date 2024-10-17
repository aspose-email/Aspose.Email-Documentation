---
title: "Crear un nuevo correo electrónico en PHP"
url: /es/java/crear-nuevo-correo-electronico-en-php/
weight: 20
type: docs
---

## **Aspose.Email - Crear nuevo correo electrónico**
Para crear un nuevo correo electrónico utilizando **Aspose.Email Java para PHP**, simplemente invoca el módulo **CreateNewEmail**. Aquí puedes ver un código de ejemplo.

**Código PHP**

``` php

 # Crear una nueva instancia de la clase MailMessage

$message = new MailMessage();

\# Establecer el asunto del mensaje

$message->setSubject("Nuevo mensaje creado por Aspose.Email para Java");

$mail_address = new MailAddress();

\# Establecer el cuerpo en Html

$message->setHtmlBody("<b>Esta línea está en negrita.</b> <br/> <br/>" .

"<font color=blue>Esta línea está en color azul</font>");

\# Establecer información del remitente

$message->setFrom(new MailAddress("from@domain.com", "Nombre del Remitente", false));

\# Agregar destinatarios TO

$message->getTo()->add(new MailAddress("to1@domain.com", "Destinatario 1", false));

$message->getTo()->add(new MailAddress("to2@domain.com", "Destinatario 2", false));

\# Agregar destinatarios CC

$message->getCC()->add(new MailAddress("cc1@domain.com", "Destinatario 3", false));

$message->getCC()->add(new MailAddress("cc2@domain.com", "Destinatario 4", false));

\# Guardar el mensaje en formatos EML y MSG

$mail_message_save_type = new MailMessageSaveType();

$message->save($dataDir . "Mensaje.eml", $mail_message_save_type->getEmlFormat());

$message->save($dataDir . "Mensaje.msg", $mail_message_save_type->getOutlookMessageFormat());

\# Mostrar Estado

print "Mensajes de correo electrónico creados con éxito.".PHP_EOL;


```
## **Descargar código en ejecución**
Descarga **Crear nuevo correo electrónico (Aspose.Email)** de cualquiera de los sitios de codificación social mencionados a continuación:

- [GitHub](https://github.com/aspose-email/Aspose.Email-for-Java/blob/master/Plugins/Aspose_Email_Java_for_PHP/src/aspose/email/ProgrammingEmail/CreateNewEmail.php)
- [CodePlex](https://asposeemailjavaphp.codeplex.com/SourceControl/latest#src/aspose/email/ProgrammingEmail/CreateNewEmail.php)