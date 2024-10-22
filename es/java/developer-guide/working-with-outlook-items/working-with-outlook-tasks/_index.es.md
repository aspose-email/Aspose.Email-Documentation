---
title: "Trabajando con Tareas de Outlook"
url: /es/java/working-with-outlook-tasks/
weight: 90
type: docs
---

## **Crear, Guardar y Leer Tareas de Outlook**

Aspose.Email para Java permite a los desarrolladores crear tareas de Outlook y guardarlas en formato MSG. La clase [MapiTask](https://reference.aspose.com/email/java/com.aspose.email/mapitask/) proporciona una serie de propiedades como [PercentComplete](https://reference.aspose.com/email/java/com.aspose.email/mapitask/#getPercentComplete--), [EstimatedEffort](https://reference.aspose.com/email/java/com.aspose.email/mapitask/#getEstimatedEffort--), [ActualEffort](https://reference.aspose.com/email/java/com.aspose.email/mapitask/#getActualEffort--), [History](https://reference.aspose.com/email/java/com.aspose.email/mapitask/#getHistory--), [LastUpdate](https://reference.aspose.com/email/java/com.aspose.email/mapitask/#getLastUpdate--), etc., para acomodar y establecer la información requerida para una tarea de Outlook. Este artículo muestra cómo crear, guardar y leer un [MapiTask](https://reference.aspose.com/email/java/com.aspose.email/mapitask/) desde el disco.

### **Crear y Guardar un MapiTask**

Los siguientes pasos pueden ser utilizados para crear y guardar una tarea en el disco.

1. Instanciar un nuevo objeto de la clase [MapiTask](https://reference.aspose.com/email/java/com.aspose.email/mapitask/).
1. Ingresar información para las diversas propiedades de la tarea.
1. Guardar la tarea en el disco en formato MSG.

{{< gist "aspose-com-gists" "709d733586ce50505c3bca3f6e8bd18d" "Examples-src-main-java-com-aspose-email-examples-outlook-msg-OutlookTasks-CreateAndSaveMapiTask.java" >}}

#### **Leer un MapiTask**

El objeto de la clase [MapiTask](https://reference.aspose.com/email/java/com.aspose.email/mapitask/) se utiliza para convertir el objeto [MapiMessage](https://reference.aspose.com/email/java/com.aspose.email/mapimessage/) que carga una tarea del disco en formato MSG.

{{< gist "aspose-com-gists" "709d733586ce50505c3bca3f6e8bd18d" "Examples-src-main-java-com-aspose-email-examples-outlook-msg-OutlookTasks-ReadingAMapiTask.java" >}}

#### **Leer una Tarea VToDo**

Las tareas de Google exportadas en formato iCalendar como eventos VToDo pueden ser cargadas usando la clase [MapiTask](https://reference.aspose.com/email/java/com.aspose.email/mapitask/) como se muestra en el siguiente ejemplo de código.

{{< gist "aspose-com-gists" "709d733586ce50505c3bca3f6e8bd18d" "Examples-src-main-java-com-aspose-email-examples-outlook-msg-OutlookTasks-ReadingAVToDoTask.java" >}}

### **Agregar Información de Recordatorio a un MapiTask**

Similar a Microsoft Outlook, Aspose.Email puede agregar información de recordatorio a un [MapiTask](https://reference.aspose.com/email/java/com.aspose.email/mapitask/). El siguiente fragmento de código muestra cómo agregar información de recordatorio a un [MapiTask](https://reference.aspose.com/email/java/com.aspose.email/mapitask/).

{{< gist "aspose-com-gists" "709d733586ce50505c3bca3f6e8bd18d" "Examples-src-main-java-com-aspose-email-examples-outlook-msg-OutlookTasks-AddReminderInformationToAMapiTask.java" >}}

### **Agregar Adjunto a un MapiTask**

El siguiente fragmento de código muestra cómo agregar adjuntos a un [MapiTask](https://reference.aspose.com/email/java/com.aspose.email/mapitask/).

{{< gist "aspose-com-gists" "709d733586ce50505c3bca3f6e8bd18d" "Examples-src-main-java-com-aspose-email-examples-outlook-msg-OutlookTasks-AddingAttachmentToAMapiTask.java" >}}

### **Convertir Tarea de Outlook a MHT**

Aspose.Email puede generar una salida similar a [MapiMessage](https://reference.aspose.com/email/java/com.aspose.email/mapimessage/) durante la conversión de un [MapiTask](https://reference.aspose.com/email/java/com.aspose.email/mapitask/) a MHT.

{{< gist "aspose-com-gists" "709d733586ce50505c3bca3f6e8bd18d" "Examples-src-main-java-com-aspose-email-examples-outlook-msg-ConvertMapiTaskToMHT-convertMapiTaskToMHT.java" >}}