---
title: "Personalizando Encabezados de Correo Electrónico en Python"
url: /es/java/personalizando-encabezados-de-correo-electronico-en-python/
weight: 30
type: docs
---

## **Aspose.Email - Personalizando Encabezados de Correo Electrónico**
Para personalizar los encabezados de correo electrónico usando **Aspose.Email Java for Python**, usa el siguiente código.

**Código en Python**

``` python



\# Crear una instancia de la clase MailMessage

message = self.MailMessage()

    # Establecer el asunto del mensaje

message.setSubject("Nuevo mensaje creado por Aspose.Email para Java")

\# Establecer el cuerpo Html

message.setHtmlBody("<b>Esta línea está en negrita.</b> <br/> <br/>" +

    "<font color=blue>Esta línea está en color azul</font>")

\# Establecer la información del remitente

message.setFrom(self.MailAddress("from@domain.com", "Nombre del Remitente", False))

\# Agregar destinatarios TO

message.getTo().addMailAddress(self.MailAddress("to@domain.com", "Destinatario 1", False))

\# Asunto del mensaje

message.setSubject("Personalizando Encabezados de Correo Electrónico")

\# Especificar la fecha

timeZone = self.TimeZone

calendar = self.Calendar

calendar = calendar.getInstance(timeZone.getTimeZone("GMT"))

date = calendar.getTime()

message.setDate(date)

\# Especificar XMailer

message.setXMailer("Aspose.Email")

\# Especificar Encabezado Secreto

message.getHeaders().add("secret-header", "mystery")

\# Guardar mensaje en disco

messageFormat= self.MessageFormat

message.save(self.dataDir + "MsgHeaders.msg", messageFormat.getMsg())

\# Mostrar Estado

print "Encabezados de mensaje personalizados con éxito."

```
## **Descargar Código en Ejecución**
Descarga **Personalizando Encabezados de Correo Electrónico (Aspose.Email)** de cualquiera de los sitios de codificación social mencionados a continuación:

- [GitHub](https://github.com/aspose-email/Aspose.Email-for-Java/releases/tag/Aspose.Email_Java_for_Python-v1.0)
- [CodePlex](http://asposeemailjavapython.codeplex.com/releases/)