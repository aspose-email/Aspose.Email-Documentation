---
title: "Trabajando con tareas de Outlook"
url: /es/cpp/working-with-outlook-tasks/
weight: 110
type: docs
---

## **Creación, almacenamiento y lectura de tareas**
Aspose.Email para C++ te permite crear tareas de Outlook y guardarlas en formato MSG. La clase MapiTask proporciona varias propiedades, como Percentcomplete, Estimatedeffort, ActualEffort, History, LastUpdate y otras, para incluir y establecer la información necesaria para una tarea de Outlook. En este artículo se muestra cómo crear, guardar y leer un MapiTask desde un disco. Para crear y guardar una tarea en un disco:

1. Crea una instancia de un nuevo objeto de la clase MapiTask.
1. Introduzca la información de las propiedades de la tarea.
1. Guarda la tarea en un disco en formato MSG.

El siguiente fragmento de código muestra cómo crear, guardar y leer tareas.



{{< gist "aspose-email" "ef0db907527892c88c557bb418093cee" "Examples-EmailCPP-Outlook-CreatingAndSavingOutlookTasks-CreatingAndSavingOutlookTasks.cpp" >}}
### **Lectura de un MapiTask**
El objeto de clase MapiTask se usa para convertir el objeto MapiMessage que carga una tarea desde un disco en formato MSG. El siguiente fragmento de código muestra cómo leer un MapiTask.



{{< gist "aspose-email" "ef0db907527892c88c557bb418093cee" "Examples-EmailCPP-Outlook-LoadingContactFromMSG-LoadingContactFromMSG.cpp" >}}
### **Lectura de una tarea de vToDo**
Las tareas de Google exportadas en formato iCalendar como eventos vTodo se pueden cargar con la clase MapiTask, como se muestra en el siguiente ejemplo de código. En el siguiente fragmento de código, se muestra cómo leer una tarea de vTodo.



{{< gist "aspose-email" "ef0db907527892c88c557bb418093cee" "Examples-EmailCPP-Outlook-ReadingVToDoTask-ReadingVToDoTask.cpp" >}}
### **Agregar información de recordatorio a un MapiTask**
Al igual que Microsoft Outlook, Aspose.Email puede agregar información de recordatorio a un MapiTask. El siguiente fragmento de código muestra cómo agregar información de recordatorio a un MapiTask.



{{< gist "aspose-email" "ef0db907527892c88c557bb418093cee" "Examples-EmailCPP-Outlook-AddReminderInformationToMapiTask-AddReminderInformationToMapiTask.cpp" >}}
### **Agregar archivos adjuntos a un MapiTask**
El siguiente fragmento de código muestra cómo agregar archivos adjuntos a un MapiTask.



{{< gist "aspose-email" "ef0db907527892c88c557bb418093cee" "Examples-EmailCPP-Outlook-AddAttachmentsToMapiTask-AddAttachmentsToMapiTask.cpp" >}}
### **Agregar recurrencia a MapiTask**
Aspose.Email permite crear una tarea recurrente donde la recurrencia puede ser diaria, semanal, mensual o anual. En el siguiente fragmento de código, se muestra cómo crear una tarea con diferentes tipos de recurrencia.



{{< gist "aspose-email" "ef0db907527892c88c557bb418093cee" "Examples-EmailCPP-Outlook-AddRecurrenceToMapiTask-AddRecurrenceToMapiTask.cpp" >}}
