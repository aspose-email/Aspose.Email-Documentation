---
title: "Guardar mensaje como borrador en Python"
url: /es/java/save-message-as-draft-in-python/
weight: 70
type: docs
---

## **Aspose.Email - Guardar mensaje como borrador**
Para guardar un mensaje como borrador utilizando **Aspose.Email Java para Python**, utiliza el siguiente código.

**Código Python**

``` python



\# Crear una instancia de la clase MailMessage

message = self.MailMessage()

\# Establecer el asunto del mensaje

message.setSubject("Nuevo mensaje creado por Aspose.Email para Java")

mail_address = self.MailAddress

\# Establecer cuerpo Html

message.setHtmlBody("<b>Esta línea está en negrita.</b> <br/> <br/>" +

    "<font color=blue>Esta línea está en color azul</font>")

\# Establecer información del remitente

message.setFrom(self.MailAddress("from@domain.com", "Nombre del Remitente", False))

\# Agregar destinatarios a TO

message.getTo().addMailAddress(self.MailAddress("to1@domain.com", "Destinatario 1", False))

message.getTo().addMailAddress(self.MailAddress("to2@domain.com", "Destinatario 2", False))

\# Crear una instancia de MapiMessage y cargar la instancia de MailMessage en ella

mapiMessage = self.MapiMessage

mapi_msg = mapiMessage.fromMailMessage(message)

\# Establecer los MapiMessageFlags como UNSENT y FROMME

mapi_message_flags = self.MapiMessageFlags

\# Guardar el MapiMessage en el disco

mapi_msg.save(self.dataDir + "Nuevo-Borrador.msg")

\# Mostrar estado

print "Borrador guardado exitosamente."

```
## **Descargar código en ejecución**
Descarga **Guardar mensaje como borrador (Aspose.Email)** de cualquiera de los sitios de codificación social mencionados a continuación:

- [GitHub](https://github.com/aspose-email/Aspose.Email-for-Java/releases/tag/Aspose.Email_Java_for_Python-v1.0)
- [CodePlex](http://asposeemailjavapython.codeplex.com/releases/)