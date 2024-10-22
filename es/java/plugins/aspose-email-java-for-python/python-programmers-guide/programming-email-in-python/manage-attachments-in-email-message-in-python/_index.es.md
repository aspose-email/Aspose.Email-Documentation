---
title: "Gestionar Archivos Adjuntos en Mensajes de Correo Electrónico en Python"
url: /es/java/manage-attachments-in-email-message-in-python/
weight: 60
type: docs
---

## **Aspose.Email - Gestionar Archivos Adjuntos en Correo Electrónico**
Para gestionar archivos adjuntos en correo electrónico utilizando **Aspose.Email Java para Python**, usa el siguiente código.

**Código Python**

``` python



\# Crear una instancia de la clase MailMessage

message = self.MailMessage()

\# Establecer el asunto del mensaje

message.setSubject("Nuevo mensaje creado por Aspose.Email para Java")

mail_address = self.MailAddress

\# Establecer el cuerpo HTML

message.setHtmlBody("<b>Esta línea está en negrita.</b> <br/> <br/>" +

    "<font color=blue>Esta línea está en color azul</font>")

\# Establecer la información del remitente

message.setFrom(self.MailAddress("from@domain.com", "Nombre del Remitente", False))

\# Agregar destinatarios TO

message.getTo().addMailAddress(self.MailAddress("to1@domain.com", "Destinatario 1", False))

\# Agregar archivo adjunto

\# Cargar un archivo adjunto

attachment = self.Attachment(self.dataDir + "1.txt")

\# Añadir el archivo adjunto en la instancia de la clase MailMessage

message.addAttachment(attachment)

\# Guardar mensaje en disco

messageFormat = self.MessageFormat

message.save(self.dataDir + "Add-Attachment.msg", messageFormat.getMsg())

\# Mostrar estado

print "Archivo adjunto añadido con éxito."

```
## **Descargar Código Ejecutable**
Descarga **Gestionar Archivos Adjuntos en Mensajes de Correo Electrónico (Aspose.Email)** de cualquiera de los sitios de codificación social mencionados a continuación:

- [GitHub](https://github.com/aspose-email/Aspose.Email-for-Java/releases/tag/Aspose.Email_Java_for_Python-v1.0)
- [CodePlex](http://asposeemailjavapython.codeplex.com/releases/)