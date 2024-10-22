---
title: "Conversión de Mensajes de Correo Electrónico en Python"
url: /es/java/converting-email-messages-in-python/
weight: 10
type: docs
---

## **Aspose.Email - Conversión de Mensajes de Correo Electrónico**
Para convertir mensajes de correo electrónico utilizando **Aspose.Email Java para Python**, use el siguiente código.

**Código Python**

``` python

 # Inicializar y cargar un archivo EML existente especificando el formato del mensaje

mailMessage = self.MailMessage

eml = mailMessage.load(self.dataDir + "Message.eml")

\# Guardar el mensaje de correo electrónico en disco en formato Unicode

saveOptions= self.SaveOptions

eml.save(self.dataDir + "AnEmail.msg", saveOptions.getDefaultMsgUnicode())

\# Mostrar estado

print "Correo electrónico convertido a msg exitosamente."

```
## **Descargar Código en Ejecución**
Descargue **Conversión de Mensajes de Correo Electrónico (Aspose.Email)** de cualquiera de los sitios de codificación social mencionados a continuación:

- [GitHub](https://github.com/aspose-email/Aspose.Email-for-Java/releases/tag/Aspose.Email_Java_for_Python-v1.0)
- [CodePlex](http://asposeemailjavapython.codeplex.com/releases/)