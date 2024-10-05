---
title: Работа с задачами Outlook
type: docs
weight: 110
url: /cpp/working-with-outlook-tasks/
---

## **Создание, сохранение и чтение задач**
Aspose.Email для C++ позволяет создавать задачи Outlook и сохранять их в формате MSG. Класс MapiTask предоставляет ряд свойств, таких как Percentcomplete, Estimatedeffort, ActualEffort, History, LastUpdate и другие, для хранения и установки информации, необходимой для задачи Outlook. В этой статье показано, как создать, сохранить и прочитать MapiTask с диска. Для создания и сохранения задачи на диск:

1. Создайте новый объект класса MapiTask.
1. Введите информацию о свойствах задачи.
1. Сохраните задачу на диск в формате MSG.

Следующий фрагмент кода показывает, как создать, сохранить и прочитать задачи.



{{< gist "aspose-email" "ef0db907527892c88c557bb418093cee" "Examples-EmailCPP-Outlook-CreatingAndSavingOutlookTasks-CreatingAndSavingOutlookTasks.cpp" >}}
### **Чтение MapiTask**
Объект класса MapiTask используется для преобразования объекта MapiMessage, который загружает задачу с диска в формате MSG. Следующий фрагмент кода показывает, как читать MapiTask.



{{< gist "aspose-email" "ef0db907527892c88c557bb418093cee" "Examples-EmailCPP-Outlook-LoadingContactFromMSG-LoadingContactFromMSG.cpp" >}}
### **Чтение задачи VToDo**
Задачи Google, экспортированные в формате iCalendar как события VToDo, могут быть загружены с использованием класса MapiTask, как показано в следующем образце кода. Следующий фрагмент кода показывает, как читать задачу VToDo.



{{< gist "aspose-email" "ef0db907527892c88c557bb418093cee" "Examples-EmailCPP-Outlook-ReadingVToDoTask-ReadingVToDoTask.cpp" >}}
### **Добавление информации о напоминании к MapiTask**
Подобно Microsoft Outlook, Aspose.Email может добавлять информацию о напоминании к MapiTask. Следующий фрагмент кода показывает, как добавлять информацию о напоминании к MapiTask.



{{< gist "aspose-email" "ef0db907527892c88c557bb418093cee" "Examples-EmailCPP-Outlook-AddReminderInformationToMapiTask-AddReminderInformationToMapiTask.cpp" >}}
### **Добавление вложений к MapiTask**
Следующий фрагмент кода показывает, как добавлять вложения к MapiTask.



{{< gist "aspose-email" "ef0db907527892c88c557bb418093cee" "Examples-EmailCPP-Outlook-AddAttachmentsToMapiTask-AddAttachmentsToMapiTask.cpp" >}}
### **Добавление повторений к MapiTask**
Aspose.Email позволяет создавать повторяющуюся задачу, где повторение может быть ежедневным, еженедельным, ежемесячным или ежегодным. Следующий фрагмент кода показывает, как создать задачу с различными типами повторений.



{{< gist "aspose-email" "ef0db907527892c88c557bb418093cee" "Examples-EmailCPP-Outlook-AddRecurrenceToMapiTask-AddRecurrenceToMapiTask.cpp" >}}