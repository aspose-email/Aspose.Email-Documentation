---
title: "Convertir Mensajes de Correo en Ruby"
url: /es/java/converting-email-messages-in-ruby/
weight: 10
type: docs
---

## **Aspose.Email - Convertir Mensajes de Correo**
Para convertir mensajes de correo utilizando **Aspose.Email Java for Ruby**, llama al método **convert_eml_to_msg** del módulo **Converter**. Aquí puedes ver un código de ejemplo.

**Código Ruby**

``` ruby

 def convert_eml_to_msg()    

    data_dir = File.dirname(File.dirname(File.dirname(File.dirname(__FILE__)))) + '/data/'

    # Inicializa y carga un archivo EML existente especificando el MessageFormat

    eml = Rjb::import('com.aspose.email.MailMessage').load(data_dir + "Message.eml")

    # Guarda el mensaje de correo en disco en formato Unicode

    eml.save(data_dir + "AnEmail.msg", Rjb::import('com.aspose.email.SaveOptions').getDefaultMsgUnicode())

    # Mostrar estado

    puts "Convertido de eml a msg exitosamente."

end

```
## **Descargar Código en Ejecución**
Descarga **Convertir Mensajes de Correo (Aspose.Email)** de cualquiera de los sitios de codificación social mencionados a continuación:

- [GitHub](https://github.com/aspose-email/Aspose.Email-for-Java/blob/master/Plugins/Aspose_Email_Java_for_Ruby/lib/asposeemailjava/Email/converter.rb)