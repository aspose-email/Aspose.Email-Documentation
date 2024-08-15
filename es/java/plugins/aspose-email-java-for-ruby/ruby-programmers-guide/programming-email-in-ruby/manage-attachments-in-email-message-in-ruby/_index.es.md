---
title: "Administrar archivos adjuntos en mensajes de correo electrónico en Ruby"
url: /es/java/manage-attachments-in-email-message-in-ruby/
weight: 60
type: docs
---

## **Aspose.Email - Administrar los archivos adjuntos en un mensaje de correo electrónico**
Para agregar archivos adjuntos a un nuevo mensaje de correo electrónico mediante **Aspose.Email Java para Ruby**, llama **add_attachments** método de **ManageAttachments** módulo. Aquí puedes ver un ejemplo de código.

**Código Ruby**

``` ruby

 def add_attachments()

    data_dir = File.dirname(File.dirname(File.dirname(File.dirname(__FILE__)))) + '/data/'

    # Create a new instance of MailMessage class

    message = Rjb::import('com.aspose.email.MailMessage').new

    # Set subject of the message

    message.setSubject("New message created by Aspose.Email for Java")

    mail_address = Rjb::import('com.aspose.email.MailAddress')

    # Set Html body

    message.setHtmlBody("<b>This line is in bold.</b> <br/> <br/>" +

            "<font color=blue>This line is in blue color</font>")

    # Set sender information

    message.setFrom(mail_address.new("from@domain.com", "Sender Name", false))

    # Add TO recipients

    message.getTo().add(mail_address.new("to1@domain.com", "Recipient 1", false))

    # Adding attachment

    # Load an attachment

    attachment = Rjb::import('com.aspose.email.Attachment').new(data_dir + "attachment.txt")

    # Add attachment in instance of MailMessage class

    message.addAttachment(attachment)

    # Save message to disc

    message.save(data_dir + "Add-Attachment.msg", Rjb::import('com.aspose.email.MessageFormat').getMsg())

    # Display Status

    puts "Added attachment successfully."

end

```
## **Descargar Running Code**
Download **Administrar los archivos adjuntos en un mensaje de correo electrónico (Aspose.Email)** desde cualquiera de los sitios de codificación social mencionados a continuación:

- [GitHub](https://github.com/aspose-email/Aspose.Email-for-Java/blob/master/Plugins/Aspose_Email_Java_for_Ruby/lib/asposeemailjava/Email/manageattachments.rb)
