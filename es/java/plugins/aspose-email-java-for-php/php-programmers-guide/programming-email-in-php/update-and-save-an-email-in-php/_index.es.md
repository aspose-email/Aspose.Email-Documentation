---
title: "Actualizar y Guardar un Correo Electrónico en PHP"
url: /es/java/update-and-save-an-email-in-php/
weight: 70
type: docs
---

## **Aspose.Email - Actualizar y Guardar un Correo Electrónico**
Para actualizar y guardar un correo electrónico utilizando **Aspose.Email Java para PHP**, simplemente invoca el módulo **UpdateEmail**. Aquí puedes ver un ejemplo de código.

**Código PHP**

``` php

 # Inicializar y cargar un archivo MSG existente especificando el MessageFormat

$mailMessage=new MailMessage();

$email = $mailMessage->load($dataDir . "Message.msg");

\# Inicializar una variable String para obtener el Asunto del Correo Electrónico

$subject = $email->getSubject();

\# Establecer el Asunto del Correo Electrónico

$email->setSubject('Este texto se añade al asunto existente');

\# Inicializar una variable String para obtener el Cuerpo HTML del Correo Electrónico

$body = $email->getHtmlBody();

\# Agregar más información a la variable Body

$body = $body . "<br> Este texto se añade al cuerpo existente".PHP_EOL;

\# Establecer el Cuerpo del Correo Electrónico

$email->setHtmlBody($body);

\# Inicializar el objeto MailAddressCollection

$contacts = new MailAddressCollection();

\# Recuperar la lista TO del Correo Electrónico

$contacts = $email->getTo();

\# Agregar otra dirección de correo electrónico a la colección

$contacts->add("to1@domain.com");

\# Establecer la colección como la lista TO del Correo Electrónico

$email->setTo($contacts);

\# Inicializar MailAddressCollection

$contacts = new MailAddressCollection();

\# Recuperar la lista CC del Correo Electrónico

$contacts = $email->getCC();

\# Agregar otra dirección de correo electrónico a la colección

$contacts->add("cc2@domain.com");

\# Establecer la colección como la lista CC del Correo Electrónico

$email->setCC($contacts);

\# Guardar el mensaje de correo electrónico en disco especificando el MessageFormat

$mailMessageSaveType=new MailMessageSaveType();

$email->save($dataDir . "UpdateMessage.msg", $mailMessageSaveType->getOutlookMessageFormat());

\# Mostrar Estado

print "Mensaje de correo electrónico actualizado con éxito.".PHP_EOL;

```
## **Descargar Código en Ejecución**
Descarga **Actualizar y Guardar un Correo Electrónico (Aspose.Email)** desde cualquiera de los sitios de codificación social mencionados a continuación:

- [GitHub](https://github.com/aspose-email/Aspose.Email-for-Java/blob/master/Plugins/Aspose_Email_Java_for_PHP/src/aspose/email/ProgrammingEmail/UpdateEmail.php)
- [CodePlex](https://archive.codeplex.com/?p=asposeemailjavaphp#src/aspose/email/ProgrammingEmail/UpdateEmail.php)