---
title: "Cargue un mensaje de correo electrónico con Aspose.Email y Apache POI HSMF"
url: /es/java/load-email-message-using-aspose-email-and-apache-poi-hsmf/
weight: 40
type: docs
---

## **Aspose.Email - Cargar mensajes de correo electrónico**
{{% alert color="primary" %}}

The **load** método expuesto por **MailMessage** Los desarrolladores pueden llamar a la clase para cargar mensajes de correo electrónico.

{{% /alert %}}

Cargar diferentes tipos de mensajes de correo electrónico

**Java**

```java

 //Create MailMessage instance by loading an Eml/Msg/Emlx/Mht file

MailMessage messageMSG 	= MailMessage.load(dataDir + "message.msg");

MailMessage messageEML 	= MailMessage.load(dataDir + "message.eml");

MailMessage messageEMLX = MailMessage.load(dataDir + "message.emlx");

MailMessage messageMHT 	= MailMessage.load(dataDir + "message.mht");

```
## **Apache POI HSMF - Carga mensajes de correo electrónico**
{{% alert color="primary" %}}

Apache POI HSMF proporciona el constructor MapiMessages que toma el nombre del archivo para cargar un nuevo MAPIMessage.

{{% /alert %}}

**Java**

```java

 String filename = dataDir + "message.msg";

MAPIMessage msg = new MAPIMessage(filename);

```
## **Descargar Running Code**
- [CodePlex](https://archive.codeplex.com/?p=asposeemailjavaapachepoi)
- [GitHub](https://github.com/aspose-email/Aspose.Email-for-Java/releases/tag/Aspose.Email_Java_for_Apache_POI-v1.0.0)
## **Descargar código de muestra**
- [CodePlex](https://archive.codeplex.com/?p=asposeemailjavaapachepoi#src/main/java/com/aspose/email/examples/featurescomparison/loadnsave/)
- [GitHub](https://github.com/aspose-email/Aspose.Email-for-Java/tree/master/Plugins/Aspose_Email_for_Apache_POI/src/main/java/com/aspose/email/examples/featurescomparison/loadnsave)

{{% alert color="primary" %}}

Para obtener más información, visite [Actualizar y guardar un correo electrónico](/email/java/loading-and-saving-message/).

{{% /alert %}}
