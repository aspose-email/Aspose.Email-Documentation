---
title: "Leer almacenamiento de Outlook PST"
url: /es/java/read-outlook-storage-pst/
weight: 30
type: docs
---

## **Aspose.Email - Leer almacenamiento de Outlook PST**
Un archivo PST de Outlook se puede cargar en una instancia de la clase [PersonalStorage](https://apireference.aspose.com/email/java/com.aspose.email.class-use/PersonalStorage).

**Java**

``` java

 // Cargar el archivo PST de Outlook

String pstFileName = dataDir + "archive.pst";

PersonalStorage pst = PersonalStorage.fromFile(pstFileName);

// Obtener el nombre para mostrar del archivo PST

System.out.println("Nombre para mostrar: " + pst.getDisplayName());


```
## **Descargar código en ejecución**
- [CodePlex](https://archive.codeplex.com/?p=asposeemailjavaapachepoi)
- [GitHub](https://github.com/aspose-email/Aspose.Email-for-Java/releases/tag/Aspose.Email_Java_for_Apache_POI-v1.0.0)
## **Descargar código de muestra**
- [CodePlex](https://archive.codeplex.com/?p=asposeemailjavaapachepoi#src/main/java/com/aspose/email/examples/asposefeatures/outlookstorage/readpst/AsposeReadOutlookPST.java)
- [GitHub](https://github.com/aspose-email/Aspose.Email-for-Java/blob/master/Plugins/Aspose_Email_for_Apache_POI/src/main/java/com/aspose/email/examples/asposefeatures/outlookstorage/readpst/AsposeReadOutlookPST.java)

{{% alert color="primary" %}} 

Para más detalles, visita [Leer archivo PST de Outlook y obtener información sobre carpetas y subcarpetas](/email/java/read-outlook-pst-file-and-get-folders-and-subfolders-information/).

{{% /alert %}}