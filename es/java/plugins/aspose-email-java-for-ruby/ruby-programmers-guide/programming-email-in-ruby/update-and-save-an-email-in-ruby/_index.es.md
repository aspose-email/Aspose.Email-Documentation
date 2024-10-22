---
title: "Actualizar y guardar un correo electrónico en Ruby"
url: /es/java/update-and-save-an-email-in-ruby/
weight: 80
type: docs
---

## **Aspose.Email - Actualizar y guardar un correo electrónico**
Para actualizar y guardar un correo electrónico usando **Aspose.Email Java para Ruby**, simplemente invoca el módulo **UpdateEmail**. Aquí puedes ver un código de ejemplo.

**Código Ruby**

``` ruby

 data_dir = File.dirname(File.dirname(File.dirname(File.dirname(__FILE__)))) + '/data/'



\# Inicializar y cargar un archivo MSG existente especificando el formato de mensaje

email = Rjb::import('com.aspose.email.MailMessage').load(data_dir + "Message.msg")

\# Inicializar una variable String para obtener el asunto del correo electrónico

subject = email.getSubject()

\# Agregar más información al asunto

subject = subject + " Este texto se agrega al asunto existente"

\# Establecer el asunto del correo electrónico

email.setSubject(subject)

\# Inicializar una variable String para obtener el cuerpo HTML del correo electrónico

body = email.getHtmlBody()

\# Agregar más información a la variable Body

body = body + "<br> Este texto se agrega al cuerpo existente"

\# Establecer el cuerpo del correo electrónico

email.setHtmlBody(body)

\# Inicializar el objeto MailAddressCollection

contacts = Rjb::import('com.aspose.email.MailAddressCollection').new

\# Recuperar la lista TO del correo electrónico

contacts = email.getTo()

\# Agregar otra dirección de correo electrónico a la colección

contacts.add("to1@domain.com")

\# Establecer la colección como la lista TO del correo electrónico

email.setTo(contacts)

\# Inicializar MailAddressCollection

contacts = Rjb::import('com.aspose.email.MailAddressCollection').new

\# Recuperar la lista CC del correo electrónico

contacts = email.getCC()

\# Agregar otra dirección de correo electrónico a la colección

contacts.add("cc2@domain.com")

\# Establecer la colección como la lista CC del correo electrónico

email.setCC(contacts)

\# Guardar el mensaje de correo electrónico en disco especificando el formato de mensaje

email.save(data_dir + "UpdateMessage.msg", Rjb::import('com.aspose.email.MailMessageSaveType').getOutlookMessageFormat())

\# Mostrar estado

puts "Mensaje de correo electrónico actualizado con éxito."

```
## **Descargar código en ejecución**
Descarga **Actualizar y guardar un correo electrónico (Aspose.Email)** de cualquiera de los sitios de codificación social mencionados a continuación:

- [GitHub](https://github.com/aspose-email/Aspose.Email-for-Java/blob/master/Plugins/Aspose_Email_Java_for_Ruby/lib/asposeemailjava/Email/updateemail.rb)