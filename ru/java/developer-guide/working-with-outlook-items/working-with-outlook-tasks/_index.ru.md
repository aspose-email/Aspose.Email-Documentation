---
title: "Работа с задачами Outlook"
url: /ru/java/working-with-outlook-tasks/
weight: 90
type: docs
---

## **Создание, сохранение и чтение задач Outlook**

Aspose.Email для Java позволяет разработчикам создавать задачи Outlook и сохранять их в формате MSG. [MapiTask](https://reference.aspose.com/email/java/com.aspose.email/mapitask/) класс предоставляет ряд свойств, таких как [PercentComplete](https://reference.aspose.com/email/java/com.aspose.email/mapitask/#getPercentComplete--), [EstimatedEffort](https://reference.aspose.com/email/java/com.aspose.email/mapitask/#getEstimatedEffort--), [ActualEffort](https://reference.aspose.com/email/java/com.aspose.email/mapitask/#getActualEffort--), [History](https://reference.aspose.com/email/java/com.aspose.email/mapitask/#getHistory--), [LastUpdate](https://reference.aspose.com/email/java/com.aspose.email/mapitask/#getLastUpdate--)и т. д. для размещения и настройки информации, необходимой для выполнения задачи Outlook. В этой статье показано, как создать, сохранить и прочитать [MapiTask](https://reference.aspose.com/email/java/com.aspose.email/mapitask/) с диска.

### **Создайте и сохраните MapiTask**

Следующие шаги можно использовать для создания и сохранения задачи на диске.

1. Создайте новый объект из [MapiTask](https://reference.aspose.com/email/java/com.aspose.email/mapitask/) class.
1. Введите информацию о различных свойствах задачи.
1. Сохраните задачу на диске в формате MSG.

{{< gist "aspose-com-gists" "709d733586ce50505c3bca3f6e8bd18d" "Examples-src-main-java-com-aspose-email-examples-outlook-msg-OutlookTasks-CreateAndSaveMapiTask.java" >}}

#### **Прочитайте задачу MapiTask**

The [MapiTask](https://reference.aspose.com/email/java/com.aspose.email/mapitask/) объект класса используется для создания [MapiMessage](https://reference.aspose.com/email/java/com.aspose.email/mapimessage/) объект, который загружает задачу с диска в формате MSG.

{{< gist "aspose-com-gists" "709d733586ce50505c3bca3f6e8bd18d" "Examples-src-main-java-com-aspose-email-examples-outlook-msg-OutlookTasks-ReadingAMapiTask.java" >}}

#### **Прочитайте задание vTodo**

Задачи Google, экспортированные в формате iCalendar в виде событий vTodo, можно загрузить с помощью [MapiTask](https://reference.aspose.com/email/java/com.aspose.email/mapitask/) класс, как показано в следующем примере кода.

{{< gist "aspose-com-gists" "709d733586ce50505c3bca3f6e8bd18d" "Examples-src-main-java-com-aspose-email-examples-outlook-msg-OutlookTasks-ReadingAVToDoTask.java" >}}

### **Добавить информацию для напоминаний в MapiTask**

Как и Microsoft Outlook, Aspose.Email может добавлять информацию о напоминаниях в [MapiTask](https://reference.aspose.com/email/java/com.aspose.email/mapitask/). В следующем фрагменте кода показано, как добавить в файл напоминания [MapiTask](https://reference.aspose.com/email/java/com.aspose.email/mapitask/).

{{< gist "aspose-com-gists" "709d733586ce50505c3bca3f6e8bd18d" "Examples-src-main-java-com-aspose-email-examples-outlook-msg-OutlookTasks-AddReminderInformationToAMapiTask.java" >}}

### **Добавить вложение в MapiTask**

В следующем фрагменте кода показано, как добавлять вложения в [MapiTask](https://reference.aspose.com/email/java/com.aspose.email/mapitask/).

{{< gist "aspose-com-gists" "709d733586ce50505c3bca3f6e8bd18d" "Examples-src-main-java-com-aspose-email-examples-outlook-msg-OutlookTasks-AddingAttachmentToAMapiTask.java" >}}

### **Преобразование задачи Outlook в MHT**

Aspose.Email может генерировать [MapiMessage](https://reference.aspose.com/email/java/com.aspose.email/mapimessage/) например, вывод во время преобразования [MapiTask](https://reference.aspose.com/email/java/com.aspose.email/mapitask/) в MHT.

{{< gist "aspose-com-gists" "709d733586ce50505c3bca3f6e8bd18d" "Examples-src-main-java-com-aspose-email-examples-outlook-msg-ConvertMapiTaskToMHT-convertMapiTaskToMHT.java" >}}
