---
title: "Trabajando con Tareas de Outlook"
url: /es/cpp/working-with-outlook-tasks/
weight: 110
type: docs
---

## **Crear, Guardar y Leer Tareas**
Aspose.Email para C++ te permite crear tareas de Outlook y guardarlas en formato MSG. La clase MapiTask proporciona una serie de propiedades como Percentcomplete, Estimatedeffort, ActualEffort, History, LastUpdate y otras, para acomodar y establecer la información requerida para una tarea de Outlook. Este artículo muestra cómo crear, guardar y leer un MapiTask desde el disco. Para crear y guardar una tarea en el disco:

1. Instanciar un nuevo objeto de la clase MapiTask.
1. Ingresar la información de las propiedades de la tarea.
1. Guardar la tarea en el disco en formato MSG.

El siguiente fragmento de código te muestra cómo crear, guardar y leer Tareas.



{{< gist "aspose-email" "ef0db907527892c88c557bb418093cee" "Examples-EmailCPP-Outlook-CreatingAndSavingOutlookTasks-CreatingAndSavingOutlookTasks.cpp" >}}
### **Leer un MapiTask**
El objeto de la clase MapiTask se utiliza para transformar el objeto MapiMessage que carga una tarea desde el disco en formato MSG. El siguiente fragmento de código te muestra cómo leer un MapiTask.



{{< gist "aspose-email" "ef0db907527892c88c557bb418093cee" "Examples-EmailCPP-Outlook-LoadingContactFromMSG-LoadingContactFromMSG.cpp" >}}
### **Leer una Tarea VToDo**
Las tareas de Google exportadas en formato iCalendar como eventos VToDo se pueden cargar utilizando la clase MapiTask como se muestra en el siguiente ejemplo de código. El siguiente fragmento de código te muestra cómo leer una Tarea VToDo.



{{< gist "aspose-email" "ef0db907527892c88c557bb418093cee" "Examples-EmailCPP-Outlook-ReadingVToDoTask-ReadingVToDoTask.cpp" >}}
### **Agregar Información de Recordatorio a un MapiTask**
Similar a Microsoft Outlook, Aspose.Email puede agregar información de recordatorio a un MapiTask. El siguiente fragmento de código te muestra cómo agregar información de recordatorio a un MapiTask.



{{< gist "aspose-email" "ef0db907527892c88c557bb418093cee" "Examples-EmailCPP-Outlook-AddReminderInformationToMapiTask-AddReminderInformationToMapiTask.cpp" >}}
### **Agregar Adjuntos a un MapiTask**
El siguiente fragmento de código te muestra cómo agregar adjuntos a un MapiTask.



{{< gist "aspose-email" "ef0db907527892c88c557bb418093cee" "Examples-EmailCPP-Outlook-AddAttachmentsToMapiTask-AddAttachmentsToMapiTask.cpp" >}}
### **Agregar Recurrencia a MapiTask**
Aspose.Email permite crear una tarea recurrente donde la recurrencia puede ser diaria, semanal, mensual o anual. El siguiente fragmento de código te muestra cómo crear una tarea con diferentes tipos de recurrencia.



{{< gist "aspose-email" "ef0db907527892c88c557bb418093cee" "Examples-EmailCPP-Outlook-AddRecurrenceToMapiTask-AddRecurrenceToMapiTask.cpp" >}}