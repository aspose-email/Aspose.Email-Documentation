---
title: "Работа с задачами Outlook"
url: /ru/python-net/working-with-outlook-tasks/
weight: 110
type: docs
---


## **Создание, сохранение и чтение заданий**
Aspose.Email для .NET позволяет создавать задачи Outlook и сохранять их в формате MSG. Класс MapiTask предоставляет ряд свойств, таких как Percentcomplete, Estimatedefort, ActualEffort, History, LastUpdate и другие, позволяющие разместить и настроить информацию, необходимую для выполнения задачи Outlook. В этой статье показано, как создать, сохранить и прочитать MapiTask с диска. Чтобы создать и сохранить задачу на диске, выполните следующие действия:

1. Создайте новый объект класса MapiContact.
1. Введите информацию о свойствах задачи.
1. Сохраните задачу на диске в формате MSG.

В следующем фрагменте кода показано, как создавать, сохранять и читать задачи.



{{< gist "aspose-email" "356f0e128b9d45a7ee779fc813eb87e5" "Examples-WorkingWithOutlookMSGs-CreatingAndSavingOutlookTask-CreatingAndSavingOutlookTask.py" >}}
### **Чтение задачи MapiTask**
Объект класса MapiContact используется для преобразования объекта MapiMessage, который загружает задачу с диска в формате MSG. В следующем фрагменте кода показано, как читать MapiTask.



{{< gist "aspose-email" "356f0e128b9d45a7ee779fc813eb87e5" "Examples-WorkingWithOutlookMSGs-LoadingContactFromMSG-LoadingContactFromMSG.py" >}}
### **Чтение задачи vTodo**
Задачи Google, экспортированные в формате iCalendar в виде событий vTodo, можно загрузить с помощью класса MapiTask, как показано в следующем примере кода. В следующем фрагменте кода показано, как читать задачу vTodo.

```py
import aspose.email as ae

data_dir = "path/to/data/directory"

task = ae.mapi.MapiTask.from_v_todo(data_dir + "VToDoTask.ics")
task.save(data_dir + "VToDo_out.msg", ae.TaskSaveFormat.Msg)
```
### **Добавление информации о напоминаниях в MapiTask**
Как и Microsoft Outlook, Aspose.Email может добавлять напоминания в MapiTask. В следующем фрагменте кода показано, как добавить напоминание в MapiTask.

{{< gist "aspose-email" "356f0e128b9d45a7ee779fc813eb87e5" "Examples-WorkingWithOutlookMSGs-AddReminderInformationToMapiTask-AddReminderInformationToMapiTask.py" >}}

### **Добавление вложений в MapiTask**

Используйте [Add](https://reference.aspose.com/email/net/aspose.email.mapi/mapiattachmentcollection/add/#add) метод [MapiAttachmentCollection](https://reference.aspose.com/email/net/aspose.email.mapi/mapiattachmentcollection/#mapiattachmentcollection-class) класс для добавления вложения в MapiTask. В этом вам поможет следующий пример кода:

```python
import aspose.email as ae
import datetime as dt

task = ae.mapi.MapiTask("Task with attacment", "Test body of task with attacment", dt.datetime.now(), dt.datetime.now());
task.attachments.add("Attachment.txt", str.encode("attachment data"))
task.save("AddAttachmentsToMapiTask_out", ae.mapi.TaskSaveFormat.MSG)
```

### **Добавление повторения в MapiTask**
Aspose.Email позволяет создавать повторяющиеся задачи, повторяющиеся ежедневно, еженедельно, ежемесячно или ежегодно. В следующем фрагменте кода показано, как создать задачу с различными типами повторения.

{{< gist "aspose-email" "356f0e128b9d45a7ee779fc813eb87e5" "Examples-WorkingWithOutlookMSGs-AddRecurrenceToMapiTask-AddRecurrenceToMapiTask.py" >}}

### **Преобразование задачи в MHT**

В следующем примере кода показано, как преобразовать задачу в формат MHT с указанием дополнительных опций для формата MHT при отображении специфичных для задачи полей (RENDER_TASK_FIELDS) и включении информации в заголовок (WRITE_HEADER). *mht_format_options* собственность [MhtSaveOptions](https://reference.aspose.com/email/python-net/aspose.email/mhtsaveoptions/#mhtsaveoptions-class) класс используется для определения дополнительных опций при сохранении в формате MHTML.

```python
import aspose.email as ae

msg = ae.mapi.MapiMessage.load("MapiTask.msg")

opt = ae.SaveOptions.default_mhtml
opt.mht_format_options = ae.MhtFormatOptions.RENDER_TASK_FIELDS | ae.MhtFormatOptions.WRITE_HEADER

msg.save("MapiTask_out.mht", opt)
```