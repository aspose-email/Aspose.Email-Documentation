---
title: "Establecer categoría de color para el mensaje de Outlook"
url: /es/java/set-color-category-for-outlook-message/
weight: 30
type: docs
---

## **Aspose.Email - Establecer categoría de color para el mensaje de Outlook**
Microsoft Outlook permite a los usuarios asignar categorías de color para diferenciar correos electrónicos. Una categoría de color marca un correo electrónico como de algún tipo de importancia o categoría. Aspose.Email proporciona la misma función a través de la clase [FollowUpManager](https://apireference.aspose.com/email/java/com.aspose.email/class-use/FollowUpManager). La siguiente funcionalidad es compatible a través de esta clase:

- AddCategory() toma [MapiMessage](https://apireference.aspose.com/email/java/com.aspose.email/mapimessage) y la cadena de categoría de color como argumentos.
- removeCategory() toma MapiMessage y la cadena de categoría de color que se desea eliminar del mensaje como argumentos.
- clearCategories() se utiliza para eliminar todas las categorías de color del mensaje.
- getCategories() se utiliza para recuperar todas las categorías de color de un mensaje en particular.

**Java**

``` java

 MapiMessage msg = MapiMessage.fromFile(dataDir + "message.msg");

// Agregar categoría

FollowUpManager.addCategory(msg, "Categoría Púrpura");

// Agregar otra categoría

FollowUpManager.addCategory(msg, "Categoría Roja");

// Recuperar la lista de categorías disponibles

IList categories = FollowUpManager.getCategories(msg);

// Eliminar la categoría especificada

FollowUpManager.removeCategory(msg, "Categoría Roja");

// Limpiar todas las categorías

//FollowUpManager.clearCategories(msg);

msg.save(dataDir + "AsposeCategories.msg");

```
## **Descargar código en ejecución**
- [CodePlex](https://asposeemailjavaapachepoi.codeplex.com/releases/view/618811)
- [GitHub](https://github.com/aspose-email/Aspose.Email-for-Java/releases/tag/Aspose.Email_Java_for_Apache_POI-v1.0.0)
## **Descargar código de muestra**
- [CodePlex](https://asposeemailjavaapachepoi.codeplex.com/SourceControl/latest#src/main/java/com/aspose/email/examples/asposefeatures/appointments/colorcategory/AsposeCategory.java)
- [GitHub](https://github.com/aspose-email/Aspose.Email-for-Java/tree/master/Plugins/Aspose_Email_for_Apache_POI/src/main/java/com/aspose/email/examples/asposefeatures/appointments/colorcategory/AsposeCategory.java)

{{% alert color="primary" %}} 

Para más detalles, visita [Configuración de la categoría de color para archivos de mensaje de Outlook (MSG)](/email/java/managing-message-files-with-aspose-email-outlook/).

{{% /alert %}}