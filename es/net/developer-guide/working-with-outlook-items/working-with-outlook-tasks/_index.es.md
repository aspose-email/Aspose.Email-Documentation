---
title: "Trabajando con tareas de Outlook"
url: /es/net/working-with-outlook-tasks/
weight: 100
type: docs
---


## **Creación, almacenamiento y lectura de tareas**

Aspose.Email para.NET permite crear tareas de Outlook y guardarlas en formato MSG. El [MapiTask](https://reference.aspose.com/email/net/aspose.email.mapi/mapitask/) la clase proporciona una serie de propiedades tales como [PercentComplete](https://reference.aspose.com/email/net/aspose.email.mapi/mapitask/percentcomplete/), [EstimatedEffort](https://reference.aspose.com/email/net/aspose.email.mapi/mapitask/estimatedeffort/), [ActualEffort](https://reference.aspose.com/email/net/aspose.email.mapi/mapitask/actualeffort/), [History](https://reference.aspose.com/email/net/aspose.email.mapi/mapitask/history/), [LastUpdate](https://reference.aspose.com/email/net/aspose.email.mapi/mapitask/lastupdate/)y otros, para incluir y configurar la información requerida para una tarea de Outlook. En este artículo se muestra cómo crear, guardar y leer un [MapiTask](https://reference.aspose.com/email/net/aspose.email.mapi/mapitask/) desde el disco. Para crear y guardar una tarea en el disco:

1. Crea una instancia de un nuevo objeto del [MapiContact](https://reference.aspose.com/email/net/aspose.email.mapi/mapicontact/) class.
1. Introduzca la información de las propiedades de la tarea.
1. Guarda la tarea en un disco en formato MSG.

El siguiente fragmento de código muestra cómo crear, guardar y leer tareas.

{{< gist "aspose-com-gists" "6e5185a63aec6fd70d83098e82b06a32" "Examples-CSharp-Outlook-CreatingAndSavingOutlookTasks-CreatingAndSavingOutlookTasks.cs" >}}

### **Lectura de un MapiTask**

The [MapiContact](https://reference.aspose.com/email/net/aspose.email.mapi/mapicontact/) el objeto de clase se usa para emitir el [MapiMessage](https://reference.aspose.com/email/net/aspose.email.mapi/mapimessage/) objeto que carga una tarea desde el disco en formato MSG. El siguiente fragmento de código muestra cómo leer un [MapiTask](https://reference.aspose.com/email/net/aspose.email.mapi/mapitask/).

{{< gist "aspose-com-gists" "6e5185a63aec6fd70d83098e82b06a32" "Examples-CSharp-Outlook-LoadingContactFromMSG-LoadingContactFromMSG.cs" >}}

### **Lectura de una tarea de vToDo**

Las tareas de Google exportadas en formato iCalendar como eventos de vTodo se pueden cargar mediante el [MapiTask](https://reference.aspose.com/email/net/aspose.email.mapi/mapitask/) clase como se muestra en el siguiente ejemplo de código. El siguiente fragmento de código muestra cómo leer una tarea de vTodo.

{{< gist "aspose-com-gists" "6e5185a63aec6fd70d83098e82b06a32" "Examples-CSharp-Outlook-ReadingVToDoTask-ReadingVToDoTask.cs" >}}

### **Agregar información de recordatorio a un MapiTask**

Al igual que Microsoft Outlook, Aspose.Email puede agregar información de recordatorio a un [MapiTask](https://reference.aspose.com/email/net/aspose.email.mapi/mapitask/). En el siguiente fragmento de código se muestra cómo añadir información de recordatorio a un [MapiTask](https://reference.aspose.com/email/net/aspose.email.mapi/mapitask/).

{{< gist "aspose-com-gists" "6e5185a63aec6fd70d83098e82b06a32" "Examples-CSharp-Outlook-AddReminderInformationToMapiTask-AddReminderInformationToMapiTask.cs" >}}

### **Agregar archivos adjuntos a un MapiTask**

En el siguiente fragmento de código se muestra cómo añadir archivos adjuntos a un [MapiTask](https://reference.aspose.com/email/net/aspose.email.mapi/mapitask/).

{{< gist "aspose-com-gists" "6e5185a63aec6fd70d83098e82b06a32" "Examples-CSharp-Outlook-AddAttachmentsToMapiTask-AddAttachmentsToMapiTask.cs" >}}

### **Agregar recurrencia a MapiTask**

Aspose.Email permite crear una tarea recurrente donde la recurrencia puede ser diaria, semanal, mensual o anual. En el siguiente fragmento de código, se muestra cómo crear una tarea con diferentes tipos de periodicidad.

{{< gist "aspose-com-gists" "6e5185a63aec6fd70d83098e82b06a32" "Examples-CSharp-Outlook-AddRecurrenceToMapiTask-AddRecurrenceToMapiTask.cs" >}}

### **Conversión de Task a MHT**

Aspose.Email puede generar [MailMessage](https://reference.aspose.com/email/net/aspose.email/mailmessage/) como salida durante la conversión de un [MapiTask](https://reference.aspose.com/email/net/aspose.email.mapi/mapitask/) a MHT.

{{< gist "aspose-com-gists" "6e5185a63aec6fd70d83098e82b06a32" "Examples-CSharp-Outlook-ConvertMapiTaskToMHT-ConvertMapiTaskToMHT.cs" >}}
