---
title: "Trabajando con tareas de Outlook"
url: /es/python-net/working-with-outlook-tasks/
weight: 110
type: docs
---


## **Creación, almacenamiento y lectura de tareas**
Aspose.Email para.NET permite crear tareas de Outlook y guardarlas en formato MSG. La clase MapiTask proporciona varias propiedades, como Percentcomplete, Estimatedeffort, ActualEffort, History, LastUpdate y otras, para incluir y establecer la información necesaria para una tarea de Outlook. En este artículo se muestra cómo crear, guardar y leer un MapiTask desde un disco. Para crear y guardar una tarea en un disco:

1. Cree una instancia de un objeto nuevo de la clase MapiContact.
1. Introduzca la información de las propiedades de la tarea.
1. Guarda la tarea en un disco en formato MSG.

El siguiente fragmento de código muestra cómo crear, guardar y leer tareas.



{{< gist "aspose-email" "356f0e128b9d45a7ee779fc813eb87e5" "Examples-WorkingWithOutlookMSGs-CreatingAndSavingOutlookTask-CreatingAndSavingOutlookTask.py" >}}
### **Lectura de un MapiTask**
El objeto de clase MapiContact se usa para convertir el objeto MapiMessage que carga una tarea desde un disco en formato MSG. El siguiente fragmento de código muestra cómo leer un MapiTask.



{{< gist "aspose-email" "356f0e128b9d45a7ee779fc813eb87e5" "Examples-WorkingWithOutlookMSGs-LoadingContactFromMSG-LoadingContactFromMSG.py" >}}
### **Lectura de una tarea de vToDo**
Las tareas de Google exportadas en formato iCalendar como eventos vTodo se pueden cargar con la clase MapiTask, como se muestra en el siguiente ejemplo de código. En el siguiente fragmento de código, se muestra cómo leer una tarea de vTodo.

```py
import aspose.email as ae

data_dir = "path/to/data/directory"

task = ae.mapi.MapiTask.from_v_todo(data_dir + "VToDoTask.ics")
task.save(data_dir + "VToDo_out.msg", ae.TaskSaveFormat.Msg)
```
### **Agregar información de recordatorio a un MapiTask**
Al igual que Microsoft Outlook, Aspose.Email puede agregar información de recordatorio a un MapiTask. El siguiente fragmento de código muestra cómo agregar información de recordatorio a un MapiTask.

{{< gist "aspose-email" "356f0e128b9d45a7ee779fc813eb87e5" "Examples-WorkingWithOutlookMSGs-AddReminderInformationToMapiTask-AddReminderInformationToMapiTask.py" >}}

### **Agregar archivos adjuntos a un MapiTask**

Usa el [Add](https://reference.aspose.com/email/net/aspose.email.mapi/mapiattachmentcollection/add/#add) método del [MapiAttachmentCollection](https://reference.aspose.com/email/net/aspose.email.mapi/mapiattachmentcollection/#mapiattachmentcollection-class) clase para agregar un archivo adjunto a un MapiTask. El siguiente ejemplo de código le ayudará con eso:

```python
import aspose.email as ae
import datetime as dt

task = ae.mapi.MapiTask("Task with attacment", "Test body of task with attacment", dt.datetime.now(), dt.datetime.now());
task.attachments.add("Attachment.txt", str.encode("attachment data"))
task.save("AddAttachmentsToMapiTask_out", ae.mapi.TaskSaveFormat.MSG)
```

### **Agregar recurrencia a MapiTask**
Aspose.Email permite crear una tarea recurrente donde la recurrencia puede ser diaria, semanal, mensual o anual. En el siguiente fragmento de código, se muestra cómo crear una tarea con diferentes tipos de recurrencia.

{{< gist "aspose-email" "356f0e128b9d45a7ee779fc813eb87e5" "Examples-WorkingWithOutlookMSGs-AddRecurrenceToMapiTask-AddRecurrenceToMapiTask.py" >}}

### **Conversión de una tarea a MHT**

El siguiente ejemplo de código muestra cómo convertir una tarea al formato MHT especificando opciones adicionales para el formato MHT cuando se deben representar los campos específicos de la tarea (RENDER_TASK_FIELDS) y se debe incluir la información del encabezado (WRITE_HEADER). El *mht_format_options* propiedad del [MhtSaveOptions](https://reference.aspose.com/email/python-net/aspose.email/mhtsaveoptions/#mhtsaveoptions-class) La clase se usa para definir opciones adicionales al guardar en formato MHTML.

```python
import aspose.email as ae

msg = ae.mapi.MapiMessage.load("MapiTask.msg")

opt = ae.SaveOptions.default_mhtml
opt.mht_format_options = ae.MhtFormatOptions.RENDER_TASK_FIELDS | ae.MhtFormatOptions.WRITE_HEADER

msg.save("MapiTask_out.mht", opt)
```