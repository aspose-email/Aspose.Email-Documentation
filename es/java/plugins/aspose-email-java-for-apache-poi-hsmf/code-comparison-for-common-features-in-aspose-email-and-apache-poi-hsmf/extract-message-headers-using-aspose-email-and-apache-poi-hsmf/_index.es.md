---
title: "Extraer Encabezados de Mensajes utilizando Aspose.Email y Apache POI HSMF"
url: /es/java/extract-message-headers-using-aspose-email-and-apache-poi-hsmf/
weight: 30
type: docs
---

## **Aspose.Email - Extraer Encabezados de Mensajes**
El encabezado de correo electrónico representa un conjunto estándar de campos de encabezado definidos por Internet y RFC incluidos en mensajes de correo electrónico de Internet. Un encabezado de correo electrónico puede ser especificado usando la clase MailMessage. Los tipos de encabezados comunes están definidos en la clase HeaderType. Es una clase sellada que funciona como una enumeración normal.

**Java**

```java

 //Obtiene los Encabezados de Email

System.out.println("De: " 	+ message.getFrom());

System.out.println("Para: " 	+ message.getTo());

System.out.println("CC: " 	+ message.getCC());

System.out.println("Cco: " 	+ message.getBcc());

System.out.println("Asunto: " 	+ message.getSubject());

```
## **Apache POI HSMF - Extraer Encabezados de Mensajes**
La clase MAPIMessage proporciona los métodos para acceder a los encabezados de los mensajes de correo electrónico.

**Java**

```java

 MAPIMessage msg = new MAPIMessage(dataDir + "message.msg");

System.out.println("De: " + msg.getDisplayFrom());

System.out.println("Para: " + msg.getDisplayTo());

System.out.println("CC: " + msg.getDisplayCC());

System.out.println("CCO: " + msg.getDisplayBCC());

System.out.println("Asunto: " + msg.getSubject());

```
## **Descargar Código en Ejecución**
- [CodePlex](https://asposeemailjavaapachepoi.codeplex.com/releases/view/618811)
- [GitHub](https://github.com/aspose-email/Aspose.Email-for-Java/releases/tag/Aspose.Email_Java_for_Apache_POI-v1.0.0)
## **Descargar Código de Ejemplo**
- [CodePlex](https://asposeemailjavaapachepoi.codeplex.com/SourceControl/latest#src/main/java/com/aspose/email/examples/featurescomparison/extractor/)
- [GitHub](https://github.com/aspose-email/Aspose.Email-for-Java/tree/master/Plugins/Aspose_Email_for_Apache_POI/src/main/java/com/aspose/email/examples/featurescomparison/extractor)

{{% alert color="primary" %}} 

Para más detalles, visita [Extracción de Encabezados de Email](/email/java/extracting-message-contents-from-emails/).

{{% /alert %}}