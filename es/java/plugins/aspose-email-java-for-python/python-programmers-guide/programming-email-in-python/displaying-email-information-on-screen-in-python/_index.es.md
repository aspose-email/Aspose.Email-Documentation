---
title: "Mostrar información de correo electrónico en la pantalla en Python"
url: /es/java/displaying-email-information-on-screen-in-python/
weight: 40
type: docs
---

## **Aspose.Email - Mostrar información de correo electrónico**
Para mostrar información de correo electrónico mediante **Aspose.Email Java para Python**, Usa el siguiente código.

**Código Python**

``` python



\# Create MailMessage instance by loading an Eml file

message_format = self.MessageFormat

mailMessage = self.MailMessage

message = mailMessage.load(self.dataDir + "Message.eml")

print "From: "

print message.getFrom()

print "To: "

print message.getTo()

print "Subject: "

print message.getSubject()

print "HtmlBody: "

print message.getHtmlBody()

print "TextBody: "

print message.getTextBody()

```
## **Descargar Running Code**
Download **Mostrar información de correo electrónico (Aspose.Email)** desde cualquiera de los sitios de codificación social mencionados a continuación:

- [GitHub](https://github.com/aspose-email/Aspose.Email-for-Java/releases/tag/Aspose.Email_Java_for_Python-v1.0)
- [CodePlex](http://asposeemailjavapython.codeplex.com/releases/)
