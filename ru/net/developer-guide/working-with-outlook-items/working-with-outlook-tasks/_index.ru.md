---
title: "Работа с задачами Outlook"
url: /ru/net/working-with-outlook-tasks/
weight: 100
type: docs
---


## **Создание, сохранение и чтение задач**

Aspose.Email для .NET позволяет создавать задачи Outlook и сохранять их в формате MSG. Класс [MapiTask](https://reference.aspose.com/email/net/aspose.email.mapi/mapitask/) предоставляет ряд свойств, таких как [PercentComplete](https://reference.aspose.com/email/net/aspose.email.mapi/mapitask/percentcomplete/), [EstimatedEffort](https://reference.aspose.com/email/net/aspose.email.mapi/mapitask/estimatedeffort/), [ActualEffort](https://reference.aspose.com/email/net/aspose.email.mapi/mapitask/actualeffort/), [History](https://reference.aspose.com/email/net/aspose.email.mapi/mapitask/history/), [LastUpdate](https://reference.aspose.com/email/net/aspose.email.mapi/mapitask/lastupdate/) и другие, для хранения и установки информации, необходимой для задачи Outlook. Эта статья показывает, как создать, сохранить и прочитать [MapiTask](https://reference.aspose.com/email/net/aspose.email.mapi/mapitask/) с диска. Чтобы создать и сохранить задачу на диск:

1. Создайте новый объект класса [MapiContact](https://reference.aspose.com/email/net/aspose.email.mapi/mapicontact/).
1. Введите информацию о свойствах задачи.
1. Сохраните задачу на диск в формате MSG.

Следующий фрагмент кода показывает, как создать, сохранить и прочитать задачи.

{{< gist "aspose-com-gists" "6e5185a63aec6fd70d83098e82b06a32" "Examples-CSharp-Outlook-CreatingAndSavingOutlookTasks-CreatingAndSavingOutlookTasks.cs" >}}

### **Чтение MapiTask**

Объект класса [MapiContact](https://reference.aspose.com/email/net/aspose.email.mapi/mapicontact/) используется для приведения объекта [MapiMessage](https://reference.aspose.com/email/net/aspose.email.mapi/mapimessage/) к типу, который загружает задачу с диска в формате MSG. Следующий фрагмент кода показывает, как прочитать [MapiTask](https://reference.aspose.com/email/net/aspose.email.mapi/mapitask/).

{{< gist "aspose-com-gists" "6e5185a63aec6fd70d83098e82b06a32" "Examples-CSharp-Outlook-LoadingContactFromMSG-LoadingContactFromMSG.cs" >}}

### **Чтение задачи VToDo**

Задачи Google, экспортированные в формате iCalendar как события VToDo, могут быть загружены с использованием класса [MapiTask](https://reference.aspose.com/email/net/aspose.email.mapi/mapitask/), как показано в следующем примере кода. Следующий фрагмент кода показывает, как прочитать задачу VToDo.

{{< gist "aspose-com-gists" "6e5185a63aec6fd70d83098e82b06a32" "Examples-CSharp-Outlook-ReadingVToDoTask-ReadingVToDoTask.cs" >}}

### **Добавление информации о напоминании к MapiTask**

Подобно Microsoft Outlook, Aspose.Email может добавлять информацию о напоминании к [MapiTask](https://reference.aspose.com/email/net/aspose.email.mapi/mapitask/). Следующий фрагмент кода показывает, как добавить информацию о напоминании к [MapiTask](https://reference.aspose.com/email/net/aspose.email.mapi/mapitask/).

{{< gist "aspose-com-gists" "6e5185a63aec6fd70d83098e82b06a32" "Examples-CSharp-Outlook-AddReminderInformationToMapiTask-AddReminderInformationToMapiTask.cs" >}}

### **Добавление вложений к MapiTask**

Следующий фрагмент кода показывает, как добавить вложения к [MapiTask](https://reference.aspose.com/email/net/aspose.email.mapi/mapitask/).

{{< gist "aspose-com-gists" "6e5185a63aec6fd70d83098e82b06a32" "Examples-CSharp-Outlook-AddAttachmentsToMapiTask-AddAttachmentsToMapiTask.cs" >}}

### **Добавление повторений к MapiTask**

Aspose.Email позволяет создавать повторяющуюся задачу, где повторение может быть ежедневным, еженедельным, ежемесячным или ежегодным. Следующий фрагмент кода показывает, как создать задачу с различными типами повторений.

{{< gist "aspose-com-gists" "6e5185a63aec6fd70d83098e82b06a32" "Examples-CSharp-Outlook-AddRecurrenceToMapiTask-AddRecurrenceToMapiTask.cs" >}}

### **Конвертация задачи в MHT**

Aspose.Email может генерировать вывод в формате [MailMessage](https://reference.aspose.com/email/net/aspose.email/mailmessage/) во время конвертации [MapiTask](https://reference.aspose.com/email/net/aspose.email.mapi/mapitask/) в MHT.

{{< gist "aspose-com-gists" "6e5185a63aec6fd70d83098e82b06a32" "Examples-CSharp-Outlook-ConvertMapiTaskToMHT-ConvertMapiTaskToMHT.cs" >}}