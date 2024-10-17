---
title: "Crear nuevo correo electrónico en Python"
url: /es/java/crear-nuevo-correo-electronico-en-python/
weight: 20
type: docs
---

## **Aspose.Email - Crear nuevo correo electrónico**
Para crear un nuevo correo electrónico utilizando **Aspose.Email Java para Python**, utiliza el siguiente código.

**Código en Python**

``` python



\# Crear una instancia de la clase MailMessage

message = self.MailMessage()

\# Establecer el asunto del mensaje

message.setSubject("Nuevo mensaje creado por Aspose.Email para Java")

mail_address = self.MailAddress

\# Establecer cuerpo HTML

message.setHtmlBody("<b>Esta línea está en negrita.</b> <br/> <br/>" +

   "<font color=blue>Esta línea está en color azul</font>")

\# Establecer información del remitente

message.setFrom(self.MailAddress("from@domain.com", "Nombre del remitente", False))

\# Agregar destinatarios TO

message.getTo().addMailAddress(self.MailAddress("to1@domain.com", "Destinatario 1", False))

message.getTo().addMailAddress(self.MailAddress("to2@domain.com", "Destinatario 2", False))

\# Agregar destinatarios CC

message.getCC().addMailAddress(self.MailAddress("cc1@domain.com", "Destinatario 3", False))

message.getCC().addMailAddress(self.MailAddress("cc2@domain.com", "Destinatario 4", False))

\# Guardar el mensaje en formatos EML y MSG

mail_message_save_type = self.MailMessageSaveType

message.save(self.dataDir + "Message.eml", mail_message_save_type.getEmlFormat())

message.save(self.dataDir + "Message.msg", mail_message_save_type.getOutlookMessageFormat())

\# Mostrar estado

print "Correo electrónico creado con éxito."

```
## **Descargar código en ejecución**
Descarga **Crear nuevo correo electrónico (Aspose.Email)** de cualquiera de los sitios de codificación social mencionados a continuación:

- [GitHub](https://github.com/aspose-email/Aspose.Email-for-Java/releases/tag/Aspose.Email_Java_for_Python-v1.0)
- [CodePlex](http://asposeemailjavapython.codeplex.com/releases/)