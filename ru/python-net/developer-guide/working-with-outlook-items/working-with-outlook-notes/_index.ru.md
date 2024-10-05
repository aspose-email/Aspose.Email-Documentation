---
title: "Работа с заметками Outlook"
url: /ru/python-net/working-with-outlook-notes/
weight: 100
type: docs
---


## **Создание, сохранение и чтение заметок**
Aspose.Email предоставляет возможность создавать заметки Outlook и сохранять их на диск в формате MSG. Класс MapiNote предоставляет свойства и методы для установки информации о задаче. В этой статье показано, как создать, сохранить и прочитать MapiNote с диска.
### **Создание и сохранение заметки Outlook**
Для создания и сохранения заметки на диск можно использовать следующие шаги:

1. Создайте объект класса MapiNote.
1. Установите различные свойства.
1. Сохраните заметку на диск как файл MSG.

Следующий фрагмент кода показывает, как создать и сохранить заметку Outlook.



{{< gist "aspose-email" "356f0e128b9d45a7ee779fc813eb87e5" "Examples-WorkingWithOutlookMSGs-CreateAndSaveOutlookNote-CreateAndSaveOutlookNote.py" >}}
### **Чтение MapiNote**
Объект класса MapiNote используется для приведения объекта MapiMessage, который загружает заметку с диска в формате MSG. Следующий фрагмент кода показывает, как прочитать MapiNote.



{{< gist "aspose-email" "356f0e128b9d45a7ee779fc813eb87e5" "Examples-WorkingWithOutlookMSGs-ReadingMapiNote-ReadingMapiNote.py" >}}