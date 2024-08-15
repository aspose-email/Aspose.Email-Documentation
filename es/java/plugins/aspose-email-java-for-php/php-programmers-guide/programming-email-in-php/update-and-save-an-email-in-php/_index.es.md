---
title: "Actualizar y guardar un correo electrónico en PHP"
url: /es/java/update-and-save-an-email-in-php/
weight: 70
type: docs
---

## **Aspose.Email - Actualizar y guardar un correo electrónico**
Para actualizar y guardar un correo electrónico usando **Aspose.Email Java para PHP**, simplemente invoca **UpdateEmail** módulo. Aquí puedes ver un ejemplo de código.

**Código PHP**

``` php

 # Initialize and Load an existing MSG file by specifying the MessageFormat

$mailMessage=new MailMessage();

$email = $mailMessage->load($dataDir . "Message.msg");

\# Initialize a String variable to get the Email Subject

$subject = $email->getSubject();

\# Set the Email Subject

$email->setSubject('This text is added to the existing subject');

\# Initialize a String variable to get the Email's HTML Body

$body = $email->getHtmlBody();

\# Apppend some more information to the Body variable

$body = $body . "<br> This text is added to the existing body".PHP_EOL;

\# Set the Email Body

$email->setHtmlBody($body);

\# Initialize MailAddressCollection object

$contacts = new MailAddressCollection();

\# Retrieve Email's TO list

$contacts = $email->getTo();

\# Add another email address to collection

$contacts->add("to1@domain.com");

\# Set the collection as Email's TO list

$email->setTo($contacts);

\# Initialize MailAddressCollection

$contacts = new MailAddressCollection();

\# Retrieve Email's CC list

$contacts = $email->getCC();

\# Add another email address to collection

$contacts->add("cc2@domain.com");

\# Set the collection as Email's CC list

$email->setCC($contacts);

\# Save the Email message to disk by specifying the MessageFormat

$mailMessageSaveType=new MailMessageSaveType();

$email->save($dataDir . "UpdateMessage.msg", $mailMessageSaveType->getOutlookMessageFormat());

\# Display Status

print "Updated email message Successfully.".PHP_EOL;

```
## **Descargar Running Code**
Download **Actualizar y guardar un correo electrónico (Aspose.Email)** desde cualquiera de los sitios de codificación social mencionados a continuación:

- [GitHub](https://github.com/aspose-email/Aspose.Email-for-Java/blob/master/Plugins/Aspose_Email_Java_for_PHP/src/aspose/email/ProgrammingEmail/UpdateEmail.php)
- [CodePlex](https://archive.codeplex.com/?p=asposeemailjavaphp#src/aspose/email/ProgrammingEmail/UpdateEmail.php)
