---
title: "Работа с задачами Outlook"
url: /ru/java/working-with-outlook-tasks/
weight: 90
type: docs
---

## **Создание, сохранение и чтение задач Outlook**

Aspose.Email для Java позволяет разработчикам создавать задачи Outlook и сохранять их в формате MSG. Класс [MapiTask](https://reference.aspose.com/email/java/com.aspose.email/mapitask/) предоставляет ряд свойств, таких как [PercentComplete](https://reference.aspose.com/email/java/com.aspose.email/mapitask/#getPercentComplete--), [EstimatedEffort](https://reference.aspose.com/email/java/com.aspose.email/mapitask/#getEstimatedEffort--), [ActualEffort](https://reference.aspose.com/email/java/com.aspose.email/mapitask/#getActualEffort--), [History](https://reference.aspose.com/email/java/com.aspose.email/mapitask/#getHistory--), [LastUpdate](https://reference.aspose.com/email/java/com.aspose.email/mapitask/#getLastUpdate--) и др., для управления и установки информации, необходимой для задачи Outlook. В этой статье показано, как создать, сохранить и прочитать [MapiTask](https://reference.aspose.com/email/java/com.aspose.email/mapitask/) с диска.

### **Создание и сохранение MapiTask**

Следующие шаги можно использовать для создания и сохранения задачи на диск.

1. Создайте новый объект класса [MapiTask](https://reference.aspose.com/email/java/com.aspose.email/mapitask/).
1. Введите информацию для различных свойств задачи.
1. Сохраните задачу на диск в формате MSG.

{{< gist "aspose-com-gists" "709d733586ce50505c3bca3f6e8bd18d" "Examples-src-main-java-com-aspose-email-examples-outlook-msg-OutlookTasks-CreateAndSaveMapiTask.java" >}}

#### **Чтение MapiTask**

Объект класса [MapiTask](https://reference.aspose.com/email/java/com.aspose.email/mapitask/) используется для преобразования объекта [MapiMessage](https://reference.aspose.com/email/java/com.aspose.email/mapimessage/), который загружает задачу с диска в формате MSG.

{{< gist "aspose-com-gists" "709d733586ce50505c3bca3f6e8bd18d" "Examples-src-main-java-com-aspose-email-examples-outlook-msg-OutlookTasks-ReadingAMapiTask.java" >}}

#### **Чтение задачи VToDo**

Задачи Google, экспортированные в формате iCalendar в виде событий VToDo, могут быть загружены с использованием класса [MapiTask](https://reference.aspose.com/email/java/com.aspose.email/mapitask/), как показано в следующем примере кода.

{{< gist "aspose-com-gists" "709d733586ce50505c3bca3f6e8bd18d" "Examples-src-main-java-com-aspose-email-examples-outlook-msg-OutlookTasks-ReadingAVToDoTask.java" >}}

### **Добавление информации о напоминании к MapiTask**

Аналогично Microsoft Outlook, Aspose.Email может добавлять информацию о напоминании к [MapiTask](https://reference.aspose.com/email/java/com.aspose.email/mapitask/). Следующий пример кода показывает, как добавлять информацию о напоминании к [MapiTask](https://reference.aspose.com/email/java/com.aspose.email/mapitask/).

{{< gist "aspose-com-gists" "709d733586ce50505c3bca3f6e8bd18d" "Examples-src-main-java-com-aspose-email-examples-outlook-msg-OutlookTasks-AddReminderInformationToAMapiTask.java" >}}

### **Добавление вложения к MapiTask**

Следующий пример кода показывает, как добавлять вложения к [MapiTask](https://reference.aspose.com/email/java/com.aspose.email/mapitask/).

{{< gist "aspose-com-gists" "709d733586ce50505c3bca3f6e8bd18d" "Examples-src-main-java-com-aspose-email-examples-outlook-msg-OutlookTasks-AddingAttachmentToAMapiTask.java" >}}

### **Конвертация задачи Outlook в MHT**

Aspose.Email может генерировать выходные данные, похожие на [MapiMessage](https://reference.aspose.com/email/java/com.aspose.email/mapimessage/), во время конвертации [MapiTask](https://reference.aspose.com/email/java/com.aspose.email/mapitask/) в MHT.

{{< gist "aspose-com-gists" "709d733586ce50505c3bca3f6e8bd18d" "Examples-src-main-java-com-aspose-email-examples-outlook-msg-ConvertMapiTaskToMHT-convertMapiTaskToMHT.java" >}}