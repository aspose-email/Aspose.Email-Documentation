---
title: "Actualizar y Guardar un Correo Electrónico en Python"
url: /es/java/update-and-save-an-email-in-python/
weight: 80
type: docs
---

## **Aspose.Email - Actualizar y Guardar un Correo Electrónico**
Para actualizar y guardar un correo electrónico usando **Aspose.Email Java para Python**, utiliza el siguiente código.

**Código Python**

``` python



\# Inicializar y cargar un archivo MSG existente especificando el MessageFormat

mailMessage = self.MailMessage

email = mailMessage.load(self.dataDir + "Message.msg")

\# Inicializar una variable String para obtener el Asunto del Correo Electrónico

subject = email.getSubject()

\# Agregar más información al Asunto

subject = subject + " Este texto se añade al asunto existente"

\# Establecer el Asunto del Correo Electrónico

email.setSubject('Este texto se añade al asunto existente')

\# Inicializar una variable String para obtener el Cuerpo HTML del Correo Electrónico

body = email.getHtmlBody()

\# Agregar más información a la variable Body

body = body + "<br> Este texto se añade al cuerpo existente"

\# Establecer el Cuerpo del Correo Electrónico

email.setHtmlBody(body)

\# Inicializar el objeto MailAddressCollection

contacts = self.MailAddressCollection()

\# Recuperar la lista TO del Correo Electrónico

contacts = email.getTo()

\# Agregar otra dirección de correo electrónico a la colección

contacts.add("to1@domain.com")

\# Establecer la colección como la lista TO del Correo Electrónico

email.setTo(contacts)

\# Inicializar MailAddressCollection

contacts = self.MailAddressCollection()

\# Recuperar la lista CC del Correo Electrónico

contacts = email.getCC()

\# Agregar otra dirección de correo electrónico a la colección

contacts.add("cc2@domain.com")

\# Establecer la colección como la lista CC del Correo Electrónico

email.setCC(contacts)

\# Guardar el mensaje de correo electrónico en disco especificando el MessageFormat

mailMessageSaveType = self.MailMessageSaveType

email.save(self.dataDir + "UpdateMessage.msg", mailMessageSaveType.getOutlookMessageFormat())

\# Mostrar Estado

print "Mensaje de correo electrónico actualizado con éxito."

```
## **Descargar Código en Ejecución**
Descarga **Actualizar y Guardar un Correo Electrónico (Aspose.Email)** desde cualquiera de los sitios de codificación social mencionados a continuación:

- [GitHub](https://github.com/aspose-email/Aspose.Email-for-Java/releases/tag/Aspose.Email_Java_for_Python-v1.0)
- [CodePlex](http://asposeemailjavapython.codeplex.com/releases/)