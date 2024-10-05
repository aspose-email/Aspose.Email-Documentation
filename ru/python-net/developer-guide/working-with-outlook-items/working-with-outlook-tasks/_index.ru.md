---
title: "Работа с задачами Outlook"
url: /ru/python-net/working-with-outlook-tasks/
weight: 110
type: docs
---


## **Создание, сохранение и чтение задач**
Aspose.Email для .NET позволяет создавать задачи Outlook и сохранять их в формате MSG. Класс MapiTask предоставляет ряд свойств, таких как Percentcomplete, Estimatedeffort, ActualEffort, History, LastUpdate и другие, чтобы учитывать и устанавливать информацию, необходимую для задачи Outlook. Эта статья показывает, как создать, сохранить и прочитать MapiTask с диска. Чтобы создать и сохранить задачу на диск:

1. Создайте новый объект класса MapiContact.
1. Введите информацию о свойствах задачи.
1. Сохраните задачу на диск в формате MSG.

Следующий кодовый фрагмент показывает, как создать, сохранить и прочитать задачи.



{{< gist "aspose-email" "356f0e128b9d45a7ee779fc813eb87e5" "Examples-WorkingWithOutlookMSGs-CreatingAndSavingOutlookTask-CreatingAndSavingOutlookTask.py" >}}
### **Чтение MapiTask**
Объект класса MapiContact используется для преобразования объекта MapiMessage, который загружает задачу с диска в формате MSG. Следующий кодовый фрагмент показывает, как читать MapiTask.



{{< gist "aspose-email" "356f0e128b9d45a7ee779fc813eb87e5" "Examples-WorkingWithOutlookMSGs-LoadingContactFromMSG-LoadingContactFromMSG.py" >}}
### **Чтение задачи VToDo**
Задачи Google, экспортируемые в формате iCalendar как события VToDo, могут быть загружены с использованием класса MapiTask, как показано в следующем примере кода. Следующий кодовый фрагмент показывает, как читать задачу VToDo.

```py
import aspose.email as ae

data_dir = "path/to/data/directory"

task = ae.mapi.MapiTask.from_v_todo(data_dir + "VToDoTask.ics")
task.save(data_dir + "VToDo_out.msg", ae.TaskSaveFormat.Msg)
```
### **Добавление информации о напоминании к MapiTask**
Аналогично Microsoft Outlook, Aspose.Email может добавлять информацию о напоминании к MapiTask. Следующий кодовый фрагмент показывает, как добавить информацию о напоминании к MapiTask.

{{< gist "aspose-email" "356f0e128b9d45a7ee779fc813eb87e5" "Examples-WorkingWithOutlookMSGs-AddReminderInformationToMapiTask-AddReminderInformationToMapiTask.py" >}}

### **Добавление вложений к MapiTask**

Используйте метод [Add](https://reference.aspose.com/email/net/aspose.email.mapi/mapiattachmentcollection/add/#add) класса [MapiAttachmentCollection](https://reference.aspose.com/email/net/aspose.email.mapi/mapiattachmentcollection/#mapiattachmentcollection-class) для добавления вложения к MapiTask. Следующий пример кода поможет вам с этим:

```python
import aspose.email as ae
import datetime as dt

task = ae.mapi.MapiTask("Задача с вложением", "Текст задачи с вложением", dt.datetime.now(), dt.datetime.now());
task.attachments.add("Attachment.txt", str.encode("attachment data"))
task.save("AddAttachmentsToMapiTask_out", ae.mapi.TaskSaveFormat.MSG)
```

### **Добавление повторения к MapiTask**
Aspose.Email позволяет создавать повторяющуюся задачу, где частота может быть ежедневной, еженедельной, ежемесячной или ежегодной. Следующий кодовый фрагмент показывает, как создать задачу с различными типами повторений.

{{< gist "aspose-email" "356f0e128b9d45a7ee779fc813eb87e5" "Examples-WorkingWithOutlookMSGs-AddRecurrenceToMapiTask-AddRecurrenceToMapiTask.py" >}}

### **Преобразование задачи в MHT**

Следующий пример кода демонстрирует, как преобразовать задачу в формат MHT, указывая дополнительные параметры для формата MHT, когда специфические для задачи поля должны быть отображены (RENDER_TASK_FIELDS) и что информация заголовка должна быть включена (WRITE_HEADER). Свойство *mht_format_options* класса [MhtSaveOptions](https://reference.aspose.com/email/python-net/aspose.email/mhtsaveoptions/#mhtsaveoptions-class) используется для определения дополнительных опций при сохранении в формате MHTML.

```python
import aspose.email as ae

msg = ae.mapi.MapiMessage.load("MapiTask.msg")

opt = ae.SaveOptions.default_mhtml
opt.mht_format_options = ae.MhtFormatOptions.RENDER_TASK_FIELDS | ae.MhtFormatOptions.WRITE_HEADER

msg.save("MapiTask_out.mht", opt)
```