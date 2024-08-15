---
title: "Trabajando con tareas de Outlook"
url: /es/java/working-with-outlook-tasks/
weight: 90
type: docs
---

## **Crear, guardar y leer tareas de Outlook**

Aspose.Email para Java permite a los desarrolladores crear tareas de Outlook y guardarlas en formato MSG. El [MapiTask](https://reference.aspose.com/email/java/com.aspose.email/mapitask/) la clase proporciona una serie de propiedades tales como [PercentComplete](https://reference.aspose.com/email/java/com.aspose.email/mapitask/#getPercentComplete--), [EstimatedEffort](https://reference.aspose.com/email/java/com.aspose.email/mapitask/#getEstimatedEffort--), [ActualEffort](https://reference.aspose.com/email/java/com.aspose.email/mapitask/#getActualEffort--), [History](https://reference.aspose.com/email/java/com.aspose.email/mapitask/#getHistory--), [LastUpdate](https://reference.aspose.com/email/java/com.aspose.email/mapitask/#getLastUpdate--), etc., para incluir y configurar la información requerida para una tarea de Outlook. Este artículo muestra cómo crear, guardar y leer un [MapiTask](https://reference.aspose.com/email/java/com.aspose.email/mapitask/) desde el disco.

### **Crear y guardar una MapiTask**

Los pasos siguientes se pueden usar para crear y guardar una tarea en el disco.

1. Crea una instancia de un nuevo objeto del [MapiTask](https://reference.aspose.com/email/java/com.aspose.email/mapitask/) class.
1. Introduzca la información de las distintas propiedades de la tarea.
1. Guarde la tarea en el disco en formato MSG.

{{< gist "aspose-com-gists" "709d733586ce50505c3bca3f6e8bd18d" "Examples-src-main-java-com-aspose-email-examples-outlook-msg-OutlookTasks-CreateAndSaveMapiTask.java" >}}

#### **Leer un MapiTask**

The [MapiTask](https://reference.aspose.com/email/java/com.aspose.email/mapitask/) el objeto de clase se usa para emitir el [MapiMessage](https://reference.aspose.com/email/java/com.aspose.email/mapimessage/) objeto que carga una tarea desde el disco en formato MSG.

{{< gist "aspose-com-gists" "709d733586ce50505c3bca3f6e8bd18d" "Examples-src-main-java-com-aspose-email-examples-outlook-msg-OutlookTasks-ReadingAMapiTask.java" >}}

#### **Leer una tarea de vToDo**

Las tareas de Google exportadas en formato iCalendar como eventos de vTodo se pueden cargar mediante el [MapiTask](https://reference.aspose.com/email/java/com.aspose.email/mapitask/) clase como se muestra en el siguiente ejemplo de código.

{{< gist "aspose-com-gists" "709d733586ce50505c3bca3f6e8bd18d" "Examples-src-main-java-com-aspose-email-examples-outlook-msg-OutlookTasks-ReadingAVToDoTask.java" >}}

### **Agregar información de recordatorio a un MapiTask**

Al igual que Microsoft Outlook, Aspose.Email puede agregar información de recordatorio a un [MapiTask](https://reference.aspose.com/email/java/com.aspose.email/mapitask/). En el siguiente fragmento de código se muestra cómo añadir información de recordatorio a un [MapiTask](https://reference.aspose.com/email/java/com.aspose.email/mapitask/).

{{< gist "aspose-com-gists" "709d733586ce50505c3bca3f6e8bd18d" "Examples-src-main-java-com-aspose-email-examples-outlook-msg-OutlookTasks-AddReminderInformationToAMapiTask.java" >}}

### **Agregar un archivo adjunto a un MapiTask**

En el siguiente fragmento de código se muestra cómo añadir archivos adjuntos a un [MapiTask](https://reference.aspose.com/email/java/com.aspose.email/mapitask/).

{{< gist "aspose-com-gists" "709d733586ce50505c3bca3f6e8bd18d" "Examples-src-main-java-com-aspose-email-examples-outlook-msg-OutlookTasks-AddingAttachmentToAMapiTask.java" >}}

### **Conversión de la tarea de Outlook a MHT**

Aspose.Email puede generar [MapiMessage](https://reference.aspose.com/email/java/com.aspose.email/mapimessage/) como salida durante la conversión de un [MapiTask](https://reference.aspose.com/email/java/com.aspose.email/mapitask/) a MHT.

{{< gist "aspose-com-gists" "709d733586ce50505c3bca3f6e8bd18d" "Examples-src-main-java-com-aspose-email-examples-outlook-msg-ConvertMapiTaskToMHT-convertMapiTaskToMHT.java" >}}
