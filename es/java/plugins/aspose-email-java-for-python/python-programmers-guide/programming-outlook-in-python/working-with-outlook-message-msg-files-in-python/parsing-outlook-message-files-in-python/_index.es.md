---
title: "Análisis de Archivos de Mensajes de Outlook en Python"
url: /es/java/parsing-outlook-message-files-in-python/
weight: 30
type: docs
---

## **Aspose.Email - Análisis de Archivos de Mensajes de Outlook**
Para analizar archivos de mensajes de Outlook utilizando **Aspose.Email Java para Python**, utiliza el siguiente código.

**Código en Python**

```python



mapiMessage = self.MapiMessage

outlook_message_file = mapiMessage.fromFile(self.dataDir + "Message.msg")

\# Mostrar el nombre del remitente

print "Nombre del remitente : " 

print outlook_message_file.getSenderName()

#Mostrar Asunto

print "Asunto : " 

print outlook_message_file.getSubject()

\# Mostrar Cuerpo

print "Cuerpo : " 

print outlook_message_file.getBody()

```
## **Descargar Código en Ejecución**
Descarga **Análisis de Archivos de Mensajes de Outlook (Aspose.Email)** desde cualquiera de los sitios de codificación social mencionados a continuación:

- [GitHub](https://github.com/aspose-email/Aspose.Email-for-Java/releases/tag/Aspose.Email_Java_for_Python-v1.0)
- [CodePlex](http://asposeemailjavapython.codeplex.com/releases/)