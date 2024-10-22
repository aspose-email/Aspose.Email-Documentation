---
title: "Trabajando con Tareas de Outlook"
url: /es/python-net/working-with-outlook-tasks/
weight: 110
type: docs
---

## **Creación, Guardado y Lectura de Tareas**
Aspose.Email para .NET te permite crear tareas de Outlook y guardarlas en formato MSG. La clase MapiTask proporciona una serie de propiedades como Percentcomplete, Estimatedeffort, ActualEffort, History, LastUpdate y otras, para acomodar y establecer la información requerida para una tarea de Outlook. Este artículo muestra cómo crear, guardar y leer un MapiTask desde el disco. Para crear y guardar una tarea en disco:

1. Instanciar un nuevo objeto de la clase MapiContact.
1. Ingresar la información de las propiedades de la tarea.
1. Guardar la tarea en disco en formato MSG.

El siguiente fragmento de código te muestra cómo crear, guardar y leer Tareas.

{{< gist "aspose-email" "356f0e128b9d45a7ee779fc813eb87e5" "Examples-WorkingWithOutlookMSGs-CreatingAndSavingOutlookTask-CreatingAndSavingOutlookTask.py" >}}
### **Leyendo un MapiTask**
El objeto de la clase MapiContact se utiliza para convertir el objeto MapiMessage que carga una tarea desde el disco en formato MSG. El siguiente fragmento de código te muestra cómo leer un MapiTask.

{{< gist "aspose-email" "356f0e128b9d45a7ee779fc813eb87e5" "Examples-WorkingWithOutlookMSGs-LoadingContactFromMSG-LoadingContactFromMSG.py" >}}
### **Leyendo una Tarea VToDo**
Las Tareas de Google exportadas en formato iCalendar como eventos VToDo pueden ser cargadas utilizando la clase MapiTask, como se muestra en el siguiente ejemplo de código. El siguiente fragmento de código te muestra cómo leer una Tarea VToDo.

```py
import aspose.email as ae

data_dir = "path/to/data/directory"

task = ae.mapi.MapiTask.from_v_todo(data_dir + "VToDoTask.ics")
task.save(data_dir + "VToDo_out.msg", ae.TaskSaveFormat.Msg)
```
### **Agregando Información de Recordatorio a un MapiTask**
Similar a Microsoft Outlook, Aspose.Email puede agregar información de recordatorio a un MapiTask. El siguiente fragmento de código te muestra cómo agregar información de recordatorio a un MapiTask.

{{< gist "aspose-email" "356f0e128b9d45a7ee779fc813eb87e5" "Examples-WorkingWithOutlookMSGs-AddReminderInformationToMapiTask-AddReminderInformationToMapiTask.py" >}}

### **Agregando Adjuntos a un MapiTask**

Usa el [Add](https://reference.aspose.com/email/net/aspose.email.mapi/mapiattachmentcollection/add/#add) método de la clase [MapiAttachmentCollection](https://reference.aspose.com/email/net/aspose.email.mapi/mapiattachmentcollection/#mapiattachmentcollection-class) para agregar un adjunto a un MapiTask. El siguiente ejemplo de código te ayudará con eso:

```python
import aspose.email as ae
import datetime as dt

task = ae.mapi.MapiTask("Tarea con adjunto", "Cuerpo de prueba de tarea con adjunto", dt.datetime.now(), dt.datetime.now());
task.attachments.add("Attachment.txt", str.encode("datos del adjunto"))
task.save("AddAttachmentsToMapiTask_out", ae.mapi.TaskSaveFormat.MSG)
```

### **Agregando Recurrencia a un MapiTask**
Aspose.Email permite crear una tarea recurrente donde la recurrencia puede ser diaria, semanal, mensual o anual. El siguiente fragmento de código te muestra cómo crear una tarea con diferentes tipos de recurrencia.

{{< gist "aspose-email" "356f0e128b9d45a7ee779fc813eb87e5" "Examples-WorkingWithOutlookMSGs-AddRecurrenceToMapiTask-AddRecurrenceToMapiTask.py" >}}

### **Convirtiendo una Tarea a MHT**

El siguiente ejemplo de código demuestra cómo convertir una tarea a formato MHT especificando opciones adicionales para el formato MHT cuando los campos específicos de la tarea deben ser renderizados (RENDER_TASK_FIELDS) y que la información del encabezado debe ser incluida (WRITE_HEADER). La propiedad *mht_format_options* de la clase [MhtSaveOptions](https://reference.aspose.com/email/python-net/aspose.email/mhtsaveoptions/#mhtsaveoptions-class) se utiliza para definir opciones adicionales al guardar en formato MHTML.

```python
import aspose.email as ae

msg = ae.mapi.MapiMessage.load("MapiTask.msg")

opt = ae.SaveOptions.default_mhtml
opt.mht_format_options = ae.MhtFormatOptions.RENDER_TASK_FIELDS | ae.MhtFormatOptions.WRITE_HEADER

msg.save("MapiTask_out.mht", opt)
```