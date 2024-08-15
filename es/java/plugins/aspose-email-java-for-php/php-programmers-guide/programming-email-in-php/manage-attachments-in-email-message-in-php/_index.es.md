---
title: "Administrar archivos adjuntos en mensajes de correo electrónico en PHP"
url: /es/java/manage-attachments-in-email-message-in-php/
weight: 50
type: docs
---

## **Aspose.Email - Administrar los archivos adjuntos en un mensaje de correo electrónico**
Para agregar archivos adjuntos a un nuevo mensaje de correo electrónico mediante **Aspose.Email Java para PHP**, llama **add_attachments** método de **ManageAttachments** módulo. Aquí puedes ver un ejemplo de código.

**Código PHP**

``` php

 public static function add_attachments($dataDir=null){

\# Create a new instance of MailMessage class

$message =new MailMessage();

\# Set subject of the message

$message->setSubject("New message created by Aspose.Email for Java");

$mail_address = new MailAddress();

\# Set Html body

$message->setHtmlBody("<b>This line is in bold.</b> <br/> <br/>" .

"<font color=blue>This line is in blue color</font>");

\# Set sender information

$message->setFrom(new MailAddress("from@domain.com", "Sender Name", false));

\# Add TO recipients

$message->getTo()->add(new MailAddress("to1@domain.com", "Recipient 1", false));

\# Adding attachment

\# Load an attachment

$attachment = new Attachment($dataDir . "1.txt");

\# Add attachment in instance of MailMessage class

$message->addAttachment($attachment);

\# Save message to disc

$messageFormat=new MessageFormat();

$message->save($dataDir . "Add-Attachment.msg", $messageFormat->getMsg());

\# Display Status

print "Added attachment successfully.".PHP_EOL;

}

```
## **Descargar Running Code**
Download **Administrar los archivos adjuntos en un mensaje de correo electrónico (Aspose.Email)** desde cualquiera de los sitios de codificación social mencionados a continuación:

- [GitHub](https://github.com/aspose-email/Aspose.Email-for-Java/blob/master/Plugins/Aspose_Email_Java_for_PHP/src/aspose/email/ProgrammingEmail/ManageAttachments.php)
- [CodePlex](https://asposeemailjavaphp.codeplex.com/SourceControl/latest#src/aspose/email/ProgrammingEmail/ManageAttachments.php)
