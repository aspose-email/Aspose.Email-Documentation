---
title: "Cargar Mensaje de Correo Electrónico usando Aspose.Email y Apache POI HSMF"
url: /es/java/load-email-message-using-aspose-email-and-apache-poi-hsmf/
weight: 40
type: docs
---

## **Aspose.Email - Cargar Mensajes de Correo Electrónico**
{{% alert color="primary" %}} 

El método **load** expuesto por la clase **MailMessage** puede ser llamado por los desarrolladores para cargar mensajes de correo electrónico.

{{% /alert %}} 

Cargar diferentes tipos de mensajes de correo electrónico

**Java**

```java

 //Crear una instancia de MailMessage cargando un archivo Eml/Msg/Emlx/Mht

MailMessage messageMSG 	= MailMessage.load(dataDir + "message.msg");

MailMessage messageEML 	= MailMessage.load(dataDir + "message.eml");

MailMessage messageEMLX = MailMessage.load(dataDir + "message.emlx");

MailMessage messageMHT 	= MailMessage.load(dataDir + "message.mht");

```
## **Apache POI HSMF - Cargar Mensajes de Correo Electrónico**
{{% alert color="primary" %}} 

Apache POI HSMF proporciona un constructor MAPIMessages que toma el nombre de archivo para cargar un nuevo MAPIMessage.

{{% /alert %}} 

**Java**

```java

 String filename = dataDir + "message.msg";

MAPIMessage msg = new MAPIMessage(filename);

```
## **Descargar Código en Ejecución**
- [CodePlex](https://archive.codeplex.com/?p=asposeemailjavaapachepoi)
- [GitHub](https://github.com/aspose-email/Aspose.Email-for-Java/releases/tag/Aspose.Email_Java_for_Apache_POI-v1.0.0)
## **Descargar Código de Ejemplo**
- [CodePlex](https://archive.codeplex.com/?p=asposeemailjavaapachepoi#src/main/java/com/aspose/email/examples/featurescomparison/loadnsave/)
- [GitHub](https://github.com/aspose-email/Aspose.Email-for-Java/tree/master/Plugins/Aspose_Email_for_Apache_POI/src/main/java/com/aspose/email/examples/featurescomparison/loadnsave)

{{% alert color="primary" %}} 

Para más detalles, visita [Actualizar y Guardar un Correo Electrónico](/email/java/loading-and-saving-message/).

{{% /alert %}}