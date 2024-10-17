---
title: "Trabajando con Notas de Outlook"
url: /es/java/working-with-outlook-notes/
weight: 100
type: docs
---

## **Crear, Guardar y Leer Notas de Outlook**

Aspose.Email proporciona la funcionalidad para crear notas de Outlook y guardarlas en el disco en formato MSG. La clase [MapiNote](https://reference.aspose.com/email/java/com.aspose.email/mapinote/) ofrece propiedades y métodos para establecer la información deseada para una nota. Este artículo muestra cómo crear, guardar y leer una [MapiNote](https://reference.aspose.com/email/java/com.aspose.email/mapinote/) desde el disco.

### **Crear y Guardar Nota de Outlook**

Los siguientes pasos se pueden utilizar para crear y guardar una nota en el disco.

1. Instanciar un objeto de la clase [MapiNote](https://reference.aspose.com/email/java/com.aspose.email/mapinote/).
1. Establecer varias propiedades según se desee.
1. Guardar la nota en el disco como un archivo MSG.
 
{{< gist "aspose-com-gists" "709d733586ce50505c3bca3f6e8bd18d" "Examples-src-main-java-com-aspose-email-examples-outlook-msg-OutlookNotes-CreateAndSaveOutlookNote.java" >}}

### **Leer un MapiNote**

El objeto de la clase [MapiNote](https://reference.aspose.com/email/java/com.aspose.email/mapinote/) se utiliza para convertir el objeto [MapiMessage](https://reference.aspose.com/email/java/com.aspose.email/mapimessage/) que carga una nota desde el disco en formato MSG.

{{< gist "aspose-com-gists" "709d733586ce50505c3bca3f6e8bd18d" "Examples-src-main-java-com-aspose-email-examples-outlook-msg-OutlookNotes-ReadAMapiNote.java" >}}