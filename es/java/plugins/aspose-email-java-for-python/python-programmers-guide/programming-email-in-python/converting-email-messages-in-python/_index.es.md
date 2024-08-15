---
title: "Conversión de mensajes de correo electrónico en Python"
url: /es/java/converting-email-messages-in-python/
weight: 10
type: docs
---

## **Aspose.Email - Conversión de mensajes de correo electrónico**
Para convertir mensajes de correo electrónico mediante **Aspose.Email Java para Python**, Usa el siguiente código.

**Código Python**

``` python

 # Initialize and Load an existing EML file by specifying the MessageFormat

mailMessage = self.MailMessage

eml = mailMessage.load(self.dataDir + "Message.eml")

\# Save the Email message to disk in Unicode format

saveOptions= self.SaveOptions

eml.save(self.dataDir + "AnEmail.msg", saveOptions.getDefaultMsgUnicode())

\# Display Status

print "Converted email to msg successfully."

```
## **Descargar Running Code**
Download **Conversión de mensajes de correo electrónico (Aspose.Email)** desde cualquiera de los sitios de codificación social mencionados a continuación:

- [GitHub](https://github.com/aspose-email/Aspose.Email-for-Java/releases/tag/Aspose.Email_Java_for_Python-v1.0)
- [CodePlex](http://asposeemailjavapython.codeplex.com/releases/)
