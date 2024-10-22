---
title: "Guardar mensaje como borrador en PHP"
url: /es/java/save-message-as-draft-in-php/
weight: 60
type: docs
---

## **Aspose.Email - Guardar mensaje como borrador**
Para guardar un mensaje como borrador utilizando **Aspose.Email Java para PHP**, simplemente invoque el módulo **SaveMessageAsDraft**. Aquí puede ver un código de ejemplo.

**Código PHP**

``` php

 # Crear una nueva instancia de la clase MailMessage

$message = new MailMessage();

\# Establecer el asunto del mensaje

$message->setSubject("Nuevo mensaje creado por Aspose.Email para Java");

$mail_address = new MailAddress();

\# Establecer el cuerpo Html

$message->setHtmlBody("<b>Esta línea está en negrita.</b> <br/> <br/>" .

"<font color=blue>Esta línea está en color azul</font>");

\# Establecer la información del remitente

$message->setFrom(new MailAddress("from@domain.com", "Nombre del Remitente", false));

\# Agregar destinatarios TO

$message->getTo()->add(new MailAddress("to1@domain.com", "Destinatario 1", false));

$message->getTo()->add(new MailAddress("to2@domain.com", "Destinatario 2", false));

\# Crear una instancia de MapiMessage y cargar la instancia de MailMessage en ella

$mapiMessage=new MapiMessage();

$mapi_msg = $mapiMessage->fromMailMessage($message);

\# Establecer las MapiMessageFlags como UNSENT y FROMME

$mapi_message_flags = new MapiMessageFlags();

\# Guardar el MapiMessage en el disco

$mapi_msg->save($dataDir . "New-Draft.msg");

\# Mostrar Estado

print "Borrador guardado con éxito.".PHP_EOL;

```
## **Descargar Código en Ejecución**
Descargue **Guardar mensaje como borrador (Aspose.Email)** desde cualquiera de los sitios de codificación social mencionados a continuación:

- [GitHub](https://github.com/aspose-email/Aspose.Email-for-Java/blob/master/Plugins/Aspose_Email_Java_for_PHP/src/aspose/email/ProgrammingEmail/SaveMessageAsDraft.php)
- [CodePlex](https://archive.codeplex.com/?p=asposeemailjavaphp#src/aspose/email/ProgrammingEmail/SaveMessageAsDraft.php)