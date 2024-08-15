---
title: "Análisis de archivos de mensajes de Outlook en Python"
url: /es/java/parsing-outlook-message-files-in-python/
weight: 30
type: docs
---

## **Aspose.Email - Análisis de archivos de mensajes de Outlook**
Para analizar los archivos de mensajes de Outlook usando **Aspose.Email Java para Python**, Usa el siguiente código.

**Código Python**

```python



mapiMessage = self.MapiMessage

outlook_message_file = mapiMessage.fromFile(self.dataDir + "Message.msg")

\# Display sender's name

print "Sender Name : "

print outlook_message_file.getSenderName()

#Display Subject

print "Subject : "

print outlook_message_file.getSubject()

\# Display Body

print "Body : "

print outlook_message_file.getBody()

```
## **Descargar Running Code**
Download **Análisis de archivos de mensajes de Outlook (Aspose.Email)** desde cualquiera de los sitios de codificación social mencionados a continuación:

- [GitHub](https://github.com/aspose-email/Aspose.Email-for-Java/releases/tag/Aspose.Email_Java_for_Python-v1.0)
- [CodePlex](http://asposeemailjavapython.codeplex.com/releases/)
