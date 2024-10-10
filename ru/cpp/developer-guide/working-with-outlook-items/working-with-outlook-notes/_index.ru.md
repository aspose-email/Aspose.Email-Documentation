---
title: "Работа с заметками Outlook"
url: /ru/cpp/working-with-outlook-notes/
weight: 100
type: docs
---

## **Создание, сохранение и чтение заметок**
Aspose.Email предоставляет возможность создавать заметки Outlook и сохранять их на диск в формате MSG. Класс MapiNote предоставляет свойства и методы для установки информации о задаче. В этой статье показано, как создать, сохранить и прочитать MapiNote с диска.
### **Создание и сохранение заметки Outlook**
Следующие шаги можно использовать для создания и сохранения заметки на диск:

1. Создайте объект класса MapiNote.
1. Установите различные свойства.
1. Сохраните заметку на диск в виде файла MSG.

Следующий фрагмент кода показывает, как создать и сохранить заметку Outlook.



{{< gist "aspose-email" "ef0db907527892c88c557bb418093cee" "Examples-EmailCPP-Outlook-CreatAndSaveAnOutlookNote-CreatAndSaveAnOutlookNote.cpp" >}}
### **Чтение MapiNote**
Объект класса MapiNote используется для приведения объекта MapiMessage, который загружает заметку с диска в формате MSG. Следующий фрагмент кода показывает, как прочитать MapiNote.



{{< gist "aspose-email" "ef0db907527892c88c557bb418093cee" "Examples-EmailCPP-Outlook-ReadMapiNote-ReadMapiNote.cpp" >}}