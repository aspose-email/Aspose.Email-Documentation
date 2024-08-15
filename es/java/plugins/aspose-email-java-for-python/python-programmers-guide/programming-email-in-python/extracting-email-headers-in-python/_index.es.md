---
title: "Extracción de encabezados de correo electrónico en Python"
url: /es/java/extracting-email-headers-in-python/
weight: 50
type: docs
---

## **Aspose.Email - Extracción de encabezados de correo electrónico**
Para extraer encabezados de correo electrónico usando **Aspose.Email Java para Python**, Usa el siguiente código.

**Código Python**

``` python



\# Initialize and Load an existing EML file by specifying the MessageFormat

mailMessage = self.MailMessage

message = mailMessage.load(self.dataDir + "Message.eml")

print "Printing all Headers:"

\# Print out all the headers

i=0

while (i < message.getHeaders().getCount()):

    print message.getHeaders().get(i)

    i += 1

```
## **Descargar Running Code**
Download **Extracción de encabezados de correo electrónico (Aspose.Email)** desde cualquiera de los sitios de codificación social mencionados a continuación:

- [GitHub](https://github.com/aspose-email/Aspose.Email-for-Java/releases/tag/Aspose.Email_Java_for_Python-v1.0)
- [CodePlex](http://asposeemailjavapython.codeplex.com/releases/)
