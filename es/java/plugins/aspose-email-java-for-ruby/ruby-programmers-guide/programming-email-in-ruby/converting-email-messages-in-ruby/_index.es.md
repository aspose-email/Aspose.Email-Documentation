---
title: "Conversión de mensajes de correo electrónico en Ruby"
url: /es/java/converting-email-messages-in-ruby/
weight: 10
type: docs
---

## **Aspose.Email - Conversión de mensajes de correo electrónico**
Para convertir mensajes de correo electrónico mediante **Aspose.Email Java para Ruby**, llama **convert_eml_to_msg** método de **Converter** módulo. Aquí puedes ver un ejemplo de código.

**Código Ruby**

``` ruby

 def convert_eml_to_msg()   

    data_dir = File.dirname(File.dirname(File.dirname(File.dirname(__FILE__)))) + '/data/'

    # Initialize and Load an existing EML file by specifying the MessageFormat

    eml = Rjb::import('com.aspose.email.MailMessage').load(data_dir + "Message.eml")

    # Save the Email message to disk in Unicode format

    eml.save(data_dir + "AnEmail.msg", Rjb::import('com.aspose.email.SaveOptions').getDefaultMsgUnicode())

    # Display Status

    puts "Converted eml to msg successfully."

end

```
## **Descargar Running Code**
Download **Conversión de mensajes de correo electrónico (Aspose.Email)** desde cualquiera de los sitios de codificación social mencionados a continuación:

- [GitHub](https://github.com/aspose-email/Aspose.Email-for-Java/blob/master/Plugins/Aspose_Email_Java_for_Ruby/lib/asposeemailjava/Email/converter.rb)
