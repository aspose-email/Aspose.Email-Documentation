---
title: "Crear nuevo correo electrónico en Ruby"
url: /es/java/create-new-email-in-ruby/
weight: 20
type: docs
---

## **Aspose.Email - Crear nuevo correo electrónico**
Para crear un nuevo correo electrónico utilizando **Aspose.Email Java para Ruby**, simplemente invoca el módulo **CreateNewEmail**. Aquí puedes ver un código de ejemplo.

**Código Ruby**

``` ruby

 data_dir = File.dirname(File.dirname(File.dirname(File.dirname(__FILE__)))) + '/data/'



\# Crear una nueva instancia de la clase MailMessage

message = Rjb::import('com.aspose.email.MailMessage').new

\# Establecer el asunto del mensaje

message.setSubject("Nuevo mensaje creado por Aspose.Email para Java")

mail_address = Rjb::import('com.aspose.email.MailAddress')

\# Establecer cuerpo en Html

message.setHtmlBody("<b>Esta línea está en negrita.</b> <br/> <br/>" +

        "<font color=blue>Esta línea está en color azul</font>")

\# Establecer información del remitente

message.setFrom(mail_address.new("from@domain.com", "Nombre del Remitente", false))

\# Agregar destinatarios TO

message.getTo().add(mail_address.new("to1@domain.com", "Destinatario 1", false))

message.getTo().add(mail_address.new("to2@domain.com", "Destinatario 2", false))

\# Agregar destinatarios CC

message.getCC().add(mail_address.new("cc1@domain.com", "Destinatario 3", false))

message.getCC().add(mail_address.new("cc2@domain.com", "Destinatario 4", false))

\# Guardar el mensaje en formatos EML y MSG

mail_message_save_type = Rjb::import('com.aspose.email.MailMessageSaveType')

message.save(data_dir + "Message.eml", mail_message_save_type.getEmlFormat())

message.save(data_dir + "Message.msg", mail_message_save_type.getOutlookMessageFormat())

\# Mostrar estado

puts "Correos electrónicos creados con éxito."

```
## **Descargar código en ejecución**
Descarga **Crear nuevo correo electrónico (Aspose.Email)** de cualquiera de los sitios de codificación social mencionados a continuación:

- [GitHub](https://github.com/aspose-email/Aspose.Email-for-Java/blob/master/Plugins/Aspose_Email_Java_for_Ruby/lib/asposeemailjava/Email/createnewemail.rb)