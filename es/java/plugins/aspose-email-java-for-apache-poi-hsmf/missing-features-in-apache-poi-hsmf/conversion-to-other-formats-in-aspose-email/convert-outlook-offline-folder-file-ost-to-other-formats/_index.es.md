---
title: "Convierta el archivo de carpetas sin conexión de Outlook (OST) a otros formatos"
url: /es/java/convert-outlook-offline-folder-file-ost-to-other-formats/
weight: 20
type: docs
---

## **Aspose.Email - Convierte OST a otros formatos**
{{% alert color="primary" %}}

Microsoft Outlook crea un archivo PST para el almacenamiento del correo electrónico cuando utiliza servidores de correo POP3 o IMAP para descargar mensajes. Crea un archivo OST cuando usas Microsoft Exchange como servidor de correo. OST admite archivos de mayor tamaño en comparación con PST.

{{% /alert %}}

Aspose.Email permite convertir un archivo OST a PST con una sola línea de código. Del mismo modo, el archivo OST se puede crear a partir de un archivo PST utilizando la misma línea de código con el enumerador FileFormat.

**Java**

```java

 PersonalStorage ost = PersonalStorage.fromFile(dataDir + "outlook.ost");

ost.saveAs(dataDir + "AsposeOST-PST.pst", FileFormat.Pst);

```
## **Descargar Running Code**
- [CodePlex](https://archive.codeplex.com/?p=asposeemailjavaapachepoi)
- [GitHub](https://github.com/aspose-email/Aspose.Email-for-Java/releases/tag/Aspose.Email_Java_for_Apache_POI-v1.0.0)
## **Descargar código de muestra**
- [CodePlex](https://archive.codeplex.com/?p=asposeemailjavaapachepoi#src/main/java/com/aspose/email/examples/asposefeatures/conversion/osttopst/AsposeOSTtoPST.java)
- [GitHub](https://github.com/aspose-email/Aspose.Email-for-Java/blob/master/Plugins/Aspose_Email_for_Apache_POI/src/main/java/com/aspose/email/examples/asposefeatures/conversion/osttopst/AsposeOSTtoPST.java)
