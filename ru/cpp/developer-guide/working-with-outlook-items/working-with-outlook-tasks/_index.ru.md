---
title: "Работа с задачами Outlook"
url: /ru/cpp/working-with-outlook-tasks/
weight: 110
type: docs
---

## **Создание, сохранение и чтение заданий**
Aspose.Email для C++ позволяет создавать задачи Outlook и сохранять их в формате MSG. Класс MapiTask предоставляет ряд свойств, таких как Percentcomplete, Estimatedefort, ActualEffort, History, LastUpdate и другие, позволяющие разместить и настроить информацию, необходимую для выполнения задачи Outlook. В этой статье показано, как создать, сохранить и прочитать MapiTask с диска. Чтобы создать и сохранить задачу на диске, выполните следующие действия:

1. Создайте новый объект класса MapiTask.
1. Введите информацию о свойствах задачи.
1. Сохраните задачу на диске в формате MSG.

В следующем фрагменте кода показано, как создавать, сохранять и читать задачи.



{{< gist "aspose-email" "ef0db907527892c88c557bb418093cee" "Examples-EmailCPP-Outlook-CreatingAndSavingOutlookTasks-CreatingAndSavingOutlookTasks.cpp" >}}
### **Чтение задачи MapiTask**
Объект класса MapiTask используется для преобразования объекта MapiMessage, который загружает задачу с диска в формате MSG. В следующем фрагменте кода показано, как читать файл MapiTask.



{{< gist "aspose-email" "ef0db907527892c88c557bb418093cee" "Examples-EmailCPP-Outlook-LoadingContactFromMSG-LoadingContactFromMSG.cpp" >}}
### **Чтение задачи vTodo**
Задачи Google, экспортированные в формате iCalendar в виде событий vTodo, можно загрузить с помощью класса MapiTask, как показано в следующем примере кода. В следующем фрагменте кода показано, как читать задачу vTodo.



{{< gist "aspose-email" "ef0db907527892c88c557bb418093cee" "Examples-EmailCPP-Outlook-ReadingVToDoTask-ReadingVToDoTask.cpp" >}}
### **Добавление информации о напоминаниях в MapiTask**
Как и Microsoft Outlook, Aspose.Email может добавлять напоминания в MapiTask. В следующем фрагменте кода показано, как добавить напоминание в MapiTask.



{{< gist "aspose-email" "ef0db907527892c88c557bb418093cee" "Examples-EmailCPP-Outlook-AddReminderInformationToMapiTask-AddReminderInformationToMapiTask.cpp" >}}
### **Добавление вложений в MapiTask**
В следующем фрагменте кода показано, как добавлять вложения в MapiTask.



{{< gist "aspose-email" "ef0db907527892c88c557bb418093cee" "Examples-EmailCPP-Outlook-AddAttachmentsToMapiTask-AddAttachmentsToMapiTask.cpp" >}}
### **Добавление повторения в MapiTask**
Aspose.Email позволяет создавать повторяющиеся задачи, повторяющиеся ежедневно, еженедельно, ежемесячно или ежегодно. В следующем фрагменте кода показано, как создать задачу с различными типами повторения.



{{< gist "aspose-email" "ef0db907527892c88c557bb418093cee" "Examples-EmailCPP-Outlook-AddRecurrenceToMapiTask-AddRecurrenceToMapiTask.cpp" >}}
