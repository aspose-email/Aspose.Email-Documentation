---
title: "Работа с задачами Outlook"
url: /ru/net/working-with-outlook-tasks/
weight: 100
type: docs
---


## **Создание, сохранение и чтение заданий**

Aspose.Email для .NET позволяет создавать задачи Outlook и сохранять их в формате MSG. [MapiTask](https://reference.aspose.com/email/net/aspose.email.mapi/mapitask/) класс предоставляет ряд свойств, таких как [PercentComplete](https://reference.aspose.com/email/net/aspose.email.mapi/mapitask/percentcomplete/), [EstimatedEffort](https://reference.aspose.com/email/net/aspose.email.mapi/mapitask/estimatedeffort/), [ActualEffort](https://reference.aspose.com/email/net/aspose.email.mapi/mapitask/actualeffort/), [History](https://reference.aspose.com/email/net/aspose.email.mapi/mapitask/history/), [LastUpdate](https://reference.aspose.com/email/net/aspose.email.mapi/mapitask/lastupdate/)и другие для сбора и настройки информации, необходимой для выполнения задачи Outlook. В этой статье показано, как создать, сохранить и прочитать [MapiTask](https://reference.aspose.com/email/net/aspose.email.mapi/mapitask/) с диска. Чтобы создать и сохранить задачу на диске, выполните следующие действия:

1. Создайте новый объект из [MapiContact](https://reference.aspose.com/email/net/aspose.email.mapi/mapicontact/) class.
1. Введите информацию о свойствах задачи.
1. Сохраните задачу на диске в формате MSG.

В следующем фрагменте кода показано, как создавать, сохранять и читать задачи.

{{< gist "aspose-com-gists" "6e5185a63aec6fd70d83098e82b06a32" "Examples-CSharp-Outlook-CreatingAndSavingOutlookTasks-CreatingAndSavingOutlookTasks.cs" >}}

### **Чтение задачи MapiTask**

The [MapiContact](https://reference.aspose.com/email/net/aspose.email.mapi/mapicontact/) объект класса используется для создания [MapiMessage](https://reference.aspose.com/email/net/aspose.email.mapi/mapimessage/) объект, который загружает задачу с диска в формате MSG. В следующем фрагменте кода показано, как читать [MapiTask](https://reference.aspose.com/email/net/aspose.email.mapi/mapitask/).

{{< gist "aspose-com-gists" "6e5185a63aec6fd70d83098e82b06a32" "Examples-CSharp-Outlook-LoadingContactFromMSG-LoadingContactFromMSG.cs" >}}

### **Чтение задачи vTodo**

Задачи Google, экспортированные в формате iCalendar в виде событий vTodo, можно загрузить с помощью [MapiTask](https://reference.aspose.com/email/net/aspose.email.mapi/mapitask/) класс, как показано в следующем примере кода. В следующем фрагменте кода показано, как читать задачу vTodo.

{{< gist "aspose-com-gists" "6e5185a63aec6fd70d83098e82b06a32" "Examples-CSharp-Outlook-ReadingVToDoTask-ReadingVToDoTask.cs" >}}

### **Добавление информации о напоминаниях в MapiTask**

Как и Microsoft Outlook, Aspose.Email может добавлять информацию о напоминаниях в [MapiTask](https://reference.aspose.com/email/net/aspose.email.mapi/mapitask/). В следующем фрагменте кода показано, как добавить в файл напоминания [MapiTask](https://reference.aspose.com/email/net/aspose.email.mapi/mapitask/).

{{< gist "aspose-com-gists" "6e5185a63aec6fd70d83098e82b06a32" "Examples-CSharp-Outlook-AddReminderInformationToMapiTask-AddReminderInformationToMapiTask.cs" >}}

### **Добавление вложений в MapiTask**

В следующем фрагменте кода показано, как добавлять вложения в [MapiTask](https://reference.aspose.com/email/net/aspose.email.mapi/mapitask/).

{{< gist "aspose-com-gists" "6e5185a63aec6fd70d83098e82b06a32" "Examples-CSharp-Outlook-AddAttachmentsToMapiTask-AddAttachmentsToMapiTask.cs" >}}

### **Добавление повторения в MapiTask**

Aspose.Email позволяет создавать повторяющиеся задачи, повторяющиеся ежедневно, еженедельно, ежемесячно или ежегодно. В следующем фрагменте кода показано, как создать задачу с различными типами повторения.

{{< gist "aspose-com-gists" "6e5185a63aec6fd70d83098e82b06a32" "Examples-CSharp-Outlook-AddRecurrenceToMapiTask-AddRecurrenceToMapiTask.cs" >}}

### **Преобразование задачи в MHT**

Aspose.Email может генерировать [MailMessage](https://reference.aspose.com/email/net/aspose.email/mailmessage/) например, вывод во время преобразования [MapiTask](https://reference.aspose.com/email/net/aspose.email.mapi/mapitask/) в MHT.

{{< gist "aspose-com-gists" "6e5185a63aec6fd70d83098e82b06a32" "Examples-CSharp-Outlook-ConvertMapiTaskToMHT-ConvertMapiTaskToMHT.cs" >}}
