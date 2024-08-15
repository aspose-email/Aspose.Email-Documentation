---
title: "Extraiga los encabezados de los mensajes con Aspose.Email y Apache POI HSMF"
url: /es/java/extract-message-headers-using-aspose-email-and-apache-poi-hsmf/
weight: 30
type: docs
---

## **Aspose.Email - Extraer los encabezados de los mensajes**
El encabezado del correo electrónico representa un conjunto estándar de campos de encabezado definido por Internet y RFC que se incluye en los mensajes de correo electrónico de Internet. Se puede especificar un encabezado de correo electrónico mediante la clase MailMessage. Los tipos de encabezados comunes se definen en la clase HeaderType. Es una clase sellada que funciona como una enumeración normal.

**Java**

```java

 //Gets Email Headers

System.out.println("From: " 	+ message.getFrom());

System.out.println("To: " 	+ message.getTo());

System.out.println("CC: " 	+ message.getCC());

System.out.println("Bcc: " 	+ message.getBcc());

System.out.println("Subject: " 	+ message.getSubject());

```
## **Apache POI HSMF - Extraer encabezados de mensajes**
La clase MapiMessage proporciona los métodos para acceder a los encabezados de los mensajes de correo electrónico.

**Java**

```java

 MAPIMessage msg = new MAPIMessage(dataDir + "message.msg");

System.out.println("From: " + msg.getDisplayFrom());

System.out.println("To: " + msg.getDisplayTo());

System.out.println("CC: " + msg.getDisplayCC());

System.out.println("BCC: " + msg.getDisplayBCC());

System.out.println("Subject: " + msg.getSubject());

```
## **Descargar Running Code**
- [CodePlex](https://asposeemailjavaapachepoi.codeplex.com/releases/view/618811)
- [GitHub](https://github.com/aspose-email/Aspose.Email-for-Java/releases/tag/Aspose.Email_Java_for_Apache_POI-v1.0.0)
## **Descargar código de muestra**
- [CodePlex](https://asposeemailjavaapachepoi.codeplex.com/SourceControl/latest#src/main/java/com/aspose/email/examples/featurescomparison/extractor/)
- [GitHub](https://github.com/aspose-email/Aspose.Email-for-Java/tree/master/Plugins/Aspose_Email_for_Apache_POI/src/main/java/com/aspose/email/examples/featurescomparison/extractor)

{{% alert color="primary" %}}

Para obtener más información, visite [Extracción de encabezados de correo electrónico](/email/java/extracting-message-contents-from-emails/).

{{% /alert %}}
