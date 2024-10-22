---
title: "Administrar Adjuntos en Mensajes de Correo en Ruby"
url: /es/java/manage-attachments-in-email-message-in-ruby/
weight: 60
type: docs
---

## **Aspose.Email - Administrar Adjuntos en Mensajes de Correo**
Para agregar adjuntos a un nuevo mensaje de correo utilizando **Aspose.Email Java para Ruby**, llama al método **add_attachments** del módulo **ManageAttachments**. Aquí puedes ver el código de ejemplo.

**Código Ruby**

``` ruby

 def add_attachments()

    data_dir = File.dirname(File.dirname(File.dirname(File.dirname(__FILE__)))) + '/data/'

    # Crear una nueva instancia de la clase MailMessage

    message = Rjb::import('com.aspose.email.MailMessage').new

    # Establecer el tema del mensaje

    message.setSubject("Nuevo mensaje creado por Aspose.Email para Java")

    mail_address = Rjb::import('com.aspose.email.MailAddress')

    # Establecer el cuerpo HTML

    message.setHtmlBody("<b>Esta línea está en negrita.</b> <br/> <br/>" +

            "<font color=blue>Esta línea está en color azul</font>")

    # Establecer la información del remitente

    message.setFrom(mail_address.new("from@domain.com", "Nombre del Remitente", false))

    # Agregar destinatarios a

    message.getTo().add(mail_address.new("to1@domain.com", "Destinatario 1", false))

    # Agregando adjunto

    # Cargar un adjunto

    attachment = Rjb::import('com.aspose.email.Attachment').new(data_dir + "attachment.txt")

    # Agregar el adjunto en la instancia de la clase MailMessage

    message.addAttachment(attachment)

    # Guardar el mensaje en el disco

    message.save(data_dir + "Add-Attachment.msg", Rjb::import('com.aspose.email.MessageFormat').getMsg())

    # Mostrar Estado

    puts "Adjunto agregado exitosamente."

end

```
## **Descargar Código en Ejecución**
Descargar **Administrar Adjuntos en Mensajes de Correo (Aspose.Email)** de cualquiera de los sitios de codificación social mencionados a continuación:

- [GitHub](https://github.com/aspose-email/Aspose.Email-for-Java/blob/master/Plugins/Aspose_Email_Java_for_Ruby/lib/asposeemailjava/Email/manageattachments.rb)