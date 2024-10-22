---
title: "Extraer el Cuerpo del Mensaje usando Aspose.Email y Apache POI HSMF"
url: /es/java/extract-message-body-using-aspose-email-and-apache-poi-hsmf/
weight: 20
type: docs
---

## **Aspose.Email - Extraer el Cuerpo del Mensaje**
El MailMessage representa un mensaje de correo electrónico y permite a los desarrolladores acceder a las propiedades del mensaje de correo electrónico. La información del encabezado (discutida en [Extracción de Encabezados de Correo Electrónico](http://www.aspose.com/docs/display/emailjava/Extracting+Email+Headers)) puede ser extraída y manipulada de diferentes maneras.

**Java**

```java

 MailMessage msg = MailMessage.load(dataDir + "message.msg");

System.out.println("Cuerpo:"+ msg.getBody());

System.out.println("Cuerpo de Texto:"+ msg.getTextBody());

System.out.println("Cuerpo de Texto HTML:"+ msg.getHtmlBody());

```
## **Apache POI HSMF - Extraer el Cuerpo del Mensaje**
MAPIMessage puede acceder al cuerpo del mensaje de correo electrónico.

**Java**

```java

 MAPIMessage msg = new MAPIMessage(dataDir + "message.msg");

System.out.println("Cuerpo de Texto:"+ msg.getTextBody());

```
## **Descargar Código en Ejecución**
- [CodePlex](https://archive.codeplex.com/?p=asposeemailjavaapachepoi)
- [GitHub](https://github.com/aspose-email/Aspose.Email-for-Java/releases/tag/Aspose.Email_Java_for_Apache_POI-v1.0.0)
## **Descargar Código de Ejemplo**
- [CodePlex](https://archive.codeplex.com/?p=asposeemailjavaapachepoi#src/main/java/com/aspose/email/examples/featurescomparison/extractor/)
- [GitHub](https://github.com/aspose-email/Aspose.Email-for-Java/tree/master/Plugins/Aspose_Email_for_Apache_POI/src/main/java/com/aspose/email/examples/featurescomparison/extractor)

{{% alert color="primary" %}} 

Para más detalles, visita [Mostrando Información del Correo Electrónico en Pantalla](/email/java/display-information-in-custom-order-in-mhtml-files/).

{{% /alert %}}