---
title: "Guardar Mensaje de Correo Electrónico utilizando Aspose.Email y Apache POI HSMF"
url: /es/java/save-email-message-using-aspose-email-and-apache-poi-hsmf/
weight: 50
type: docs
---

## **Aspose.Email - Guardar Mensaje de Correo Electrónico**
El método MailMessage.save está disponible para guardar mensajes de correo electrónico en varios formatos.

**Java**

```java

 MailMessage messageMSG 	= MailMessage.load(dataDir + "message.msg");

messageMSG.save(dataDir + "AsposeMessage.msg");

messageMSG.save(dataDir + "AsposeMessage.eml");

messageMSG.save(dataDir + "AsposeMessage.emlx");

messageMSG.save(dataDir + "AsposeMessage.mht");

```
## **Apache POI HSMF - Guardar Mensaje de Correo Electrónico**
El cuerpo del correo electrónico se puede extraer para crear un nuevo archivo.

**Java**

```java

 String filename = "message.msg";

MAPIMessage msg = new MAPIMessage(filename);

PrintWriter txtOut = new PrintWriter("ApacheMessage.txt");

txtOut.println("Cuerpo del Correo Electrónico: " + msg.getTextBody());

txtOut.close();

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