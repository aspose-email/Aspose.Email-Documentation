---
title: "Comprobar la Protección por Contraseña de PST"
url: /es/java/check-pst-password-protection/
weight: 10
type: docs
---

## **Aspose.Email - Comprobar la Protección por Contraseña de PST**
Microsoft Outlook permite a los usuarios proteger con contraseña los archivos PST para restringir el acceso a ellos. Aspose.Email puede detectar la protección por contraseña en un archivo PST. Esta página muestra cómo comprobar un PST para una contraseña y también cómo comprobar si la contraseña aplicada en él es correcta.

**Java**

``` java

 if (pst.getMessageStoreProperties().contains(MapiPropertyTag.PR_PST_PASSWORD))

{

    long passwordHash = pst.getMessageStoreProperties().get_Item(MapiPropertyTag.PR_PST_PASSWORD).getLong();

    return passwordHash != 0;

}

```
## **Descargar Código en Ejecución**
- [CodePlex](https://archive.codeplex.com/?p=asposeemailjavaapachepoi)
- [GitHub](https://github.com/aspose-email/Aspose.Email-for-Java/releases/tag/Aspose.Email_Java_for_Apache_POI-v1.0.0)
## **Descargar Código de Ejemplo**
- [CodePlex](https://archive.codeplex.com/?p=asposeemailjavaapachepoi#src/main/java/com/aspose/email/examples/asposefeatures/outlookstorage/checkprotection/AsposeCheckProtection.java)
- [GitHub](https://github.com/aspose-email/Aspose.Email-for-Java/blob/master/Plugins/Aspose_Email_for_Apache_POI/src/main/java/com/aspose/email/examples/asposefeatures/outlookstorage/checkprotection/AsposeCheckProtection.java)

{{% alert color="primary" %}} 

Para más detalles, visita [Trabajando con las Propiedades de Protección por Contraseña de PST](/email/java/working-with-calendar-items-in-pst-file/).

{{% /alert %}}