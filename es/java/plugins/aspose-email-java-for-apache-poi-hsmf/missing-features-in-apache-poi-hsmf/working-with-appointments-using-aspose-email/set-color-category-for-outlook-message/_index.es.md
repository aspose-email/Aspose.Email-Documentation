---
title: "Establecer la categoría de color para el mensaje de Outlook"
url: /es/java/set-color-category-for-outlook-message/
weight: 30
type: docs
---

## **Aspose.Email - Establecer la categoría de color para el mensaje de Outlook**
Microsoft Outlook permite a los usuarios asignar categorías de colores para diferenciar los correos electrónicos. Una categoría de color marca un correo electrónico como de algún tipo de importancia o categoría. Aspose.Email ofrece la misma función a través del [FollowUpManager](https://apireference.aspose.com/email/java/com.aspose.email/class-use/FollowUpManager) clase. Esta clase admite las siguientes funciones:

- AddCategory() takes [MapiMessage](https://apireference.aspose.com/email/java/com.aspose.email/mapimessage) y la cadena de la categoría de color como argumentos.
- removeCategory () toma como argumentos mapiMessage y la cadena de categoría de color que se va a eliminar del mensaje.
- clearCategories () se usa para eliminar todas las categorías de colores del mensaje.
- getCategories () se usa para recuperar todas las categorías de color de un mensaje en particular.

**Java**

``` java

 MapiMessage msg = MapiMessage.fromFile(dataDir + "message.msg");

// Add category

FollowUpManager.addCategory(msg, "Purple Category");

// Add another category

FollowUpManager.addCategory(msg, "Red Category");

// Retrieve the list of available categories

IList categories = FollowUpManager.getCategories(msg);

// Remove the specified category

FollowUpManager.removeCategory(msg, "Red Category");

// Clear all categories

//FollowUpManager.clearCategories(msg);

msg.save(dataDir + "AsposeCategories.msg");

```
## **Descargar Running Code**
- [CodePlex](https://asposeemailjavaapachepoi.codeplex.com/releases/view/618811)
- [GitHub](https://github.com/aspose-email/Aspose.Email-for-Java/releases/tag/Aspose.Email_Java_for_Apache_POI-v1.0.0)
## **Descargar código de muestra**
- [CodePlex](https://asposeemailjavaapachepoi.codeplex.com/SourceControl/latest#src/main/java/com/aspose/email/examples/asposefeatures/appointments/colorcategory/AsposeCategory.java)
- [GitHub](https://github.com/aspose-email/Aspose.Email-for-Java/tree/master/Plugins/Aspose_Email_for_Apache_POI/src/main/java/com/aspose/email/examples/asposefeatures/appointments/colorcategory/AsposeCategory.java)

{{% alert color="primary" %}}

Para obtener más información, visite [Configuración de la categoría de color para los archivos de mensajes de Outlook (MSG)](/email/java/managing-message-files-with-aspose-email-outlook/).

{{% /alert %}}
