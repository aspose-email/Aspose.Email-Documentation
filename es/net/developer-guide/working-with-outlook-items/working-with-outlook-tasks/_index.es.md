---
title: "Trabajando con Tareas de Outlook"
url: /es/net/working-with-outlook-tasks/
weight: 100
type: docs
---

## **Crear, Guardar y Leer Tareas**

Aspose.Email para .NET te permite crear tareas de Outlook y guardarlas en formato MSG. La clase [MapiTask](https://reference.aspose.com/email/net/aspose.email.mapi/mapitask/) proporciona una serie de propiedades como [PercentComplete](https://reference.aspose.com/email/net/aspose.email.mapi/mapitask/percentcomplete/), [EstimatedEffort](https://reference.aspose.com/email/net/aspose.email.mapi/mapitask/estimatedeffort/), [ActualEffort](https://reference.aspose.com/email/net/aspose.email.mapi/mapitask/actualeffort/), [History](https://reference.aspose.com/email/net/aspose.email.mapi/mapitask/history/), [LastUpdate](https://reference.aspose.com/email/net/aspose.email.mapi/mapitask/lastupdate/), y otras, para acomodar y establecer la información requerida para una tarea de Outlook. Este artículo muestra cómo crear, guardar y leer un [MapiTask](https://reference.aspose.com/email/net/aspose.email.mapi/mapitask/) desde el disco. Para crear y guardar una tarea en el disco:

1. Instancia un nuevo objeto de la clase [MapiContact](https://reference.aspose.com/email/net/aspose.email.mapi/mapicontact/).
1. Ingresa la información de las propiedades de la tarea.
1. Guarda la tarea en disco en formato MSG.

El siguiente fragmento de código te muestra cómo crear, guardar y leer Tareas.

{{< gist "aspose-com-gists" "6e5185a63aec6fd70d83098e82b06a32" "Examples-CSharp-Outlook-CreatingAndSavingOutlookTasks-CreatingAndSavingOutlookTasks.cs" >}}

### **Leer un MapiTask**

El objeto de la clase [MapiContact](https://reference.aspose.com/email/net/aspose.email.mapi/mapicontact/) se utiliza para convertir el objeto [MapiMessage](https://reference.aspose.com/email/net/aspose.email.mapi/mapimessage/) que carga una tarea desde el disco en formato MSG. El siguiente fragmento de código te muestra cómo leer un [MapiTask](https://reference.aspose.com/email/net/aspose.email.mapi/mapitask/).

{{< gist "aspose-com-gists" "6e5185a63aec6fd70d83098e82b06a32" "Examples-CSharp-Outlook-LoadingContactFromMSG-LoadingContactFromMSG.cs" >}}

### **Leer una Tarea VToDo**

Las tareas de Google exportadas en formato iCalendar como eventos VToDo pueden ser cargadas utilizando la clase [MapiTask](https://reference.aspose.com/email/net/aspose.email.mapi/mapitask/) como se muestra en el siguiente ejemplo de código. El siguiente fragmento de código te muestra cómo leer una Tarea VToDo.

{{< gist "aspose-com-gists" "6e5185a63aec6fd70d83098e82b06a32" "Examples-CSharp-Outlook-ReadingVToDoTask-ReadingVToDoTask.cs" >}}

### **Agregar Información de Recordatorio a un MapiTask**

Similar a Microsoft Outlook, Aspose.Email puede agregar información de recordatorio a un [MapiTask](https://reference.aspose.com/email/net/aspose.email.mapi/mapitask/). El siguiente fragmento de código te muestra cómo agregar información de recordatorio a un [MapiTask](https://reference.aspose.com/email/net/aspose.email.mapi/mapitask/).

{{< gist "aspose-com-gists" "6e5185a63aec6fd70d83098e82b06a32" "Examples-CSharp-Outlook-AddReminderInformationToMapiTask-AddReminderInformationToMapiTask.cs" >}}

### **Agregar Archivos Adjuntos a un MapiTask**

El siguiente fragmento de código te muestra cómo agregar archivos adjuntos a un [MapiTask](https://reference.aspose.com/email/net/aspose.email.mapi/mapitask/).

{{< gist "aspose-com-gists" "6e5185a63aec6fd70d83098e82b06a32" "Examples-CSharp-Outlook-AddAttachmentsToMapiTask-AddAttachmentsToMapiTask.cs" >}}

### **Agregar Recurrencia a MapiTask**

Aspose.Email permite crear una tarea recurrente donde la recurrencia puede ser diaria, semanal, mensual o anual. El siguiente fragmento de código te muestra cómo crear una tarea con diferentes tipos de recurrencia.

{{< gist "aspose-com-gists" "6e5185a63aec6fd70d83098e82b06a32" "Examples-CSharp-Outlook-AddRecurrenceToMapiTask-AddRecurrenceToMapiTask.cs" >}}

### **Convertir Tarea a MHT**

Aspose.Email puede generar una salida similar a [MailMessage](https://reference.aspose.com/email/net/aspose.email/mailmessage/) durante la conversión de un [MapiTask](https://reference.aspose.com/email/net/aspose.email.mapi/mapitask/) a MHT.

{{< gist "aspose-com-gists" "6e5185a63aec6fd70d83098e82b06a32" "Examples-CSharp-Outlook-ConvertMapiTaskToMHT-ConvertMapiTaskToMHT.cs" >}}