---
title: "Работа с вложениями сообщений Outlook с помощью API парсера электронной почты C++"
description: "Вы можете управлять вложениями сообщений Outlook с помощью библиотеки C++ Email Parser, сохранять и удалять их, а также вставлять сообщения в виде вложений."
url: /ru/cpp/working-with-message-attachments/
weight: 70
type: docs
linktitle: "Работа с вложениями сообщений"
---

## **Управление вложениями с помощью Aspose Outlook**
В разделе Создание и сохранение файлов сообщений Outlook (MSG) объясняется, как создавать и сохранять сообщения, а также файлы MSG с вложениями. В этой статье объясняется, как управлять вложениями Microsoft Outlook с помощью Aspose.Email. Доступ к вложениям из файла сообщений и их сохранение на диск осуществляется с помощью свойства «Вложения класса MapiMessage». Свойство «Вложения» представляет собой набор типов класса MapiAttachmentCollection.

### **Сохранить вложения из файла сообщений Outlook (MSG)**
Чтобы сохранить вложения из файла MSG, выполните следующие действия:

1. Просмотрите коллекцию MapiAttachmentCollection и получите отдельные вложения.
1. Чтобы сохранить вложения, вызовите метод Save () класса MapiAttachment.

В следующем фрагменте кода показано, как сохранять вложения на локальный диск.

{{< gist "aspose-email" "ef0db907527892c88c557bb418093cee" "Examples-EmailCPP-Outlook-SaveAttachmentsFromOutlookMSGFile-SaveAttachmentsFromOutlookMSGFile.cpp" >}}

### **Удаление вложений**
Библиотека Aspose Outlook предоставляет возможность удаления вложений из файлов сообщений Microsoft Outlook (.msg):

- Вызовите метод removeAttachments (). В качестве параметра он принимает путь к файлу сообщения. Он реализован как публичный статический метод, поэтому вам не нужно создавать экземпляр объекта.

В следующем фрагменте кода показано, как удалять вложения с помощью библиотеки C++ Email Parser Library.

{{< gist "aspose-email" "ef0db907527892c88c557bb418093cee" "Examples-EmailCPP-Outlook-RemoveAttachmentsFromFile-RemoveAttachmentsFromFile.cpp" >}}

Можно также вызвать статический метод класса MapiMessage DestoryAttachment (). Он работает быстрее, чем removeAttachment (), поскольку метод removeAttachment () анализирует файл сообщения.

{{< gist "aspose-email" "ef0db907527892c88c557bb418093cee" "Examples-EmailCPP-Outlook-DestroyAttachment-DestroyAttachment.cpp" >}}

### **Добавление вложений MSG**
Сообщение Outlook может содержать другие сообщения Microsoft Outlook во вложениях в виде обычных или встроенных сообщений. MapiAttachmentCollection предоставляет перегруженным участникам метода Add возможность создавать сообщения Outlook с обоими типами вложений.

### **Встраивание сообщения в виде вложения**
В следующем фрагменте кода показано, как файлы Outlook MSG, встроенные в файл MSG, содержат метод PR_ATTACH_METHOD, значение которого равно 5.

{{< gist "aspose-email" "ef0db907527892c88c557bb418093cee" "Examples-EmailCPP-Outlook-EmbedMessageAsAttachment-EmbedMessageAsAttachment.cpp" >}}
