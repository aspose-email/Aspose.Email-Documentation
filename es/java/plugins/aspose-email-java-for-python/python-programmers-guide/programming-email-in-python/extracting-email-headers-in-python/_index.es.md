---
title: "Extracción de Encabezados de Correo Electrónico en Python"
url: /es/java/extracting-email-headers-in-python/
weight: 50
type: docs
---

## **Aspose.Email - Extracción de Encabezados de Correo Electrónico**
Para extraer encabezados de correo electrónico utilizando **Aspose.Email Java para Python**, use el siguiente código.

**Código Python**

``` python



\# Inicializar y cargar un archivo EML existente especificando el formato del mensaje

mailMessage = self.MailMessage

message = mailMessage.load(self.dataDir + "Message.eml")

print "Imprimiendo todos los encabezados:"

\# Imprimir todos los encabezados

i=0

while (i < message.getHeaders().getCount()):

    print message.getHeaders().get(i)

    i += 1

```
## **Descargar Código en Ejecución**
Descargue **Extracción de Encabezados de Correo Electrónico (Aspose.Email)** de cualquiera de los sitios de codificación social mencionados a continuación:

- [GitHub](https://github.com/aspose-email/Aspose.Email-for-Java/releases/tag/Aspose.Email_Java_for_Python-v1.0)
- [CodePlex](http://asposeemailjavapython.codeplex.com/releases/)