---
title: "Administrar Adjuntos en Mensajes de Correo en PHP"
url: /es/java/manage-attachments-in-email-message-in-php/
weight: 50
type: docs
---

## **Aspose.Email - Administrar Adjuntos en Mensajes de Correo**
Para agregar adjuntos a un nuevo mensaje de correo utilizando **Aspose.Email Java para PHP**, llama al método **add_attachments** del módulo **ManageAttachments**. Aquí puedes ver el código de ejemplo.

**Código PHP**

``` php

 public static function add_attachments($dataDir=null){

\# Crear una nueva instancia de la clase MailMessage

$message =new MailMessage();

\# Establecer el asunto del mensaje

$message->setSubject("Nuevo mensaje creado por Aspose.Email para Java");

$mail_address = new MailAddress();

\# Establecer cuerpo Html

$message->setHtmlBody("<b>Esta línea está en negrita.</b> <br/> <br/>" .

"<font color=blue>Esta línea está en color azul</font>");

\# Establecer información del remitente

$message->setFrom(new MailAddress("from@domain.com", "Nombre del Remitente", false));

\# Agregar destinatarios TO

$message->getTo()->add(new MailAddress("to1@domain.com", "Destinatario 1", false));

\# Agregando adjunto

\# Cargar un adjunto

$attachment = new Attachment($dataDir . "1.txt");

\# Agregar adjunto en la instancia de la clase MailMessage

$message->addAttachment($attachment);

\# Guardar mensaje en disco

$messageFormat=new MessageFormat();

$message->save($dataDir . "Add-Attachment.msg", $messageFormat->getMsg());

\# Mostrar Estado

print "Adjunto agregado con éxito.".PHP_EOL;

}

```
## **Descargar Código en Ejecución**
Descarga **Administrar Adjuntos en Mensajes de Correo (Aspose.Email)** de cualquiera de los sitios de codificación social mencionados a continuación:

- [GitHub](https://github.com/aspose-email/Aspose.Email-for-Java/blob/master/Plugins/Aspose_Email_Java_for_PHP/src/aspose/email/ProgrammingEmail/ManageAttachments.php)
- [CodePlex](https://asposeemailjavaphp.codeplex.com/SourceControl/latest#src/aspose/email/ProgrammingEmail/ManageAttachments.php)