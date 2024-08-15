---
title: "Extraiga el cuerpo del mensaje con Aspose.Email y Apache POI HSMF"
url: /es/java/extract-message-body-using-aspose-email-and-apache-poi-hsmf/
weight: 20
type: docs
---

## **Aspose.Email - Extraer el cuerpo del mensaje**
El MailMessage representa un mensaje de correo electrónico y permite a los desarrolladores acceder a las propiedades del mensaje de correo electrónico. La información del encabezado (que se explica en [Extracción de encabezados de correo electrónico](http://www.aspose.com/docs/display/emailjava/Extracting+Email+Headers)) pueden extraerse y manipularse de diferentes maneras.

**Java**

```java

 MailMessage msg = MailMessage.load(dataDir + "message.msg");

System.out.println("Body:"+ msg.getBody());

System.out.println("Text Body:"+ msg.getTextBody());

System.out.println("Text Body HTML:"+ msg.getHtmlBody());

```
## **Apache POI HSMF - Extraer el cuerpo del mensaje**
MapiMessage puede acceder al cuerpo del mensaje de correo electrónico.

**Java**

```java

 MAPIMessage msg = new MAPIMessage(dataDir + "message.msg");

System.out.println("Text Body:"+ msg.getTextBody());

```
## **Descargar Running Code**
- [CodePlex](https://archive.codeplex.com/?p=asposeemailjavaapachepoi)
- [GitHub](https://github.com/aspose-email/Aspose.Email-for-Java/releases/tag/Aspose.Email_Java_for_Apache_POI-v1.0.0)
## **Descargar código de muestra**
- [CodePlex](https://archive.codeplex.com/?p=asposeemailjavaapachepoi#src/main/java/com/aspose/email/examples/featurescomparison/extractor/)
- [GitHub](https://github.com/aspose-email/Aspose.Email-for-Java/tree/master/Plugins/Aspose_Email_for_Apache_POI/src/main/java/com/aspose/email/examples/featurescomparison/extractor)

{{% alert color="primary" %}}

Para obtener más información, visite [Mostrar información de correo electrónico en la pantalla](/email/java/display-information-in-custom-order-in-mhtml-files/).

{{% /alert %}}
