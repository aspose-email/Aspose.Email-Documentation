---
title: "Mostrando Información de Correo Electrónico en Pantalla en Python"
url: /es/java/mostrando-informacion-de-correo-electronico-en-pantalla-en-python/
weight: 40
type: docs
---

## **Aspose.Email - Mostrando Información de Correo Electrónico**
Para mostrar información de correo electrónico usando **Aspose.Email Java para Python**, utilice el siguiente código.

**Código en Python**

``` python



\# Crear instancia de MailMessage cargando un archivo Eml

message_format = self.MessageFormat

mailMessage = self.MailMessage

message = mailMessage.load(self.dataDir + "Message.eml")

print "De: " 

print message.getFrom()

print "Para: " 

print message.getTo()

print "Asunto: " 

print message.getSubject()

print "CuerpoHtml: " 

print message.getHtmlBody()

print "CuerpoTexto: " 

print message.getTextBody()

```
## **Descargar Código en Ejecución**
Descargue **Mostrando Información de Correo Electrónico (Aspose.Email)** de cualquiera de los sitios de codificación social mencionados a continuación:

- [GitHub](https://github.com/aspose-email/Aspose.Email-for-Java/releases/tag/Aspose.Email_Java_for_Python-v1.0)
- [CodePlex](http://asposeemailjavapython.codeplex.com/releases/)