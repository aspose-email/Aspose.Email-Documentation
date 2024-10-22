---
title: "Guardar mensaje como borrador en Ruby"
url: /es/java/save-message-as-draft-in-ruby/
weight: 70
type: docs
---

## **Aspose.Email - Guardar mensaje como borrador**
Para guardar un mensaje como borrador utilizando **Aspose.Email Java para Ruby**, simplemente invoca el módulo **SaveMessageAsDraft**. Aquí puedes ver un código de ejemplo.

**Código Ruby**

``` ruby

 data_dir = File.dirname(File.dirname(File.dirname(File.dirname(__FILE__)))) + '/data/'



\# Crear una nueva instancia de la clase MailMessage

message = Rjb::import('com.aspose.email.MailMessage').new

\# Establecer el asunto del mensaje

message.setSubject("Nuevo mensaje creado por Aspose.Email para Java")

mail_address = Rjb::import('com.aspose.email.MailAddress')

\# Establecer el cuerpo en Html

message.setHtmlBody("<b>Esta línea está en negrita.</b> <br/> <br/>" +

        "<font color=blue>Esta línea está en color azul</font>")

\# Establecer información del remitente

message.setFrom(mail_address.new("from@domain.com", "Nombre del Remitente", false))

\# Agregar destinatarios a TO

message.getTo().add(mail_address.new("to1@domain.com", "Destinatario 1", false))

message.getTo().add(mail_address.new("to2@domain.com", "Destinatario 2", false))

\# Crear una instancia de MapiMessage y cargar la instancia de MailMessage en ella

mapi_msg = Rjb::import('com.aspose.email.MapiMessage').fromMailMessage(message)

\# Establecer los MapiMessageFlags como UNSENT y FROMME

mapi_message_flags = Rjb::import('com.aspose.email.MapiMessageFlags')

mapi_msg.setMessageFlags(mapi_message_flags.MSGFLAG_UNSENT || mapi_message_flags.MSGFLAG_FROMME)

\# Guardar el MapiMessage en disco

mapi_msg.save(data_dir + "Nuevo-Borrador.msg")

\# Mostrar estado

puts "Borrador guardado con éxito."

```
## **Descargar código en ejecución**
Descarga **Guardar mensaje como borrador (Aspose.Email)** de cualquiera de los sitios de codificación social mencionados a continuación:

- [GitHub](https://github.com/aspose-email/Aspose.Email-for-Java/blob/master/Plugins/Aspose_Email_Java_for_Ruby/lib/asposeemailjava/Email/savemessageasdraft.rb)