---
title: "Personalizando Encabezados de Correo Electrónico en Ruby"
url: /es/java/personalizando-encabezados-de-correo-electronico-en-ruby/
weight: 30
type: docs
---

## **Aspose.Email - Personalizando Encabezados de Correo Electrónico**
Para personalizar encabezados de correo electrónico usando **Aspose.Email Java para Ruby**, simplemente invoca el módulo **CustomizeEmailHeaders**. Aquí puedes ver un ejemplo de código.

**Código Ruby**

``` ruby

 data_dir = File.dirname(File.dirname(File.dirname(File.dirname(__FILE__)))) + '/data/'



\# Crear una nueva instancia de la clase MailMessage

message = Rjb::import('com.aspose.email.MailMessage').new

\# Establecer el asunto del mensaje

message.setSubject("Nuevo mensaje creado por Aspose.Email para Java")

\# Establecer el cuerpo Html

message.setHtmlBody("<b>Esta línea está en negrita.</b> <br/> <br/>" +

        "<font color=blue>Esta línea está en color azul</font>")

\# Establecer información del remitente

message.setFrom(Rjb::import('com.aspose.email.MailAddress').new("from@domain.com", "Nombre del Remitente", false))

\# Agregar destinatarios TO

message.getTo().add(Rjb::import('com.aspose.email.MailAddress').new("to@domain.com", "Destinatario 1", false))

\# Asunto del mensaje

message.setSubject("Personalizando Encabezados de Correo Electrónico")

\# Especificar la Fecha

calendar = Rjb::import('java.util.Calendar').getInstance(Rjb::import('java.util.TimeZone').getTimeZone("GMT"))

date = calendar.getTime()

message.setDate(date)

\# Especificar XMailer

message.setXMailer("Aspose.Email")

\# Especificar Encabezado Secreto

message.getHeaders().add("secret-header", "misterio")

\# Guardar mensaje en disco

message.save(data_dir + "MsgHeaders.msg", Rjb::import('com.aspose.email.MessageFormat').getMsg())

\# Mostrar Estado

puts "Encabezados de mensaje personalizados con éxito."

```
## **Descargar Código en Ejecución**
Descarga **Personalizando Encabezados de Correo Electrónico (Aspose.Email)** de cualquiera de los siguientes sitios de codificación social:

- [GitHub](https://github.com/aspose-email/Aspose.Email-for-Java/blob/master/Plugins/Aspose_Email_Java_for_Ruby/lib/asposeemailjava/Email/customizeemailheaders.rb)