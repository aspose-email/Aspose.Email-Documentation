---
title: Работа с вложениями сообщений Outlook с использованием C++ Email Parser API
linktitle: Работа с вложениями сообщений
type: docs
weight: 70
url: /cpp/working-with-message-attachments/
description: Вы можете управлять вложениями сообщений Outlook с помощью библиотеки C++ Email Parser, сохранять и удалять их, а также встраивать сообщения в качестве вложений.
---

## **Управление вложениями с Aspose Outlook**
Создание и сохранение файлов сообщений Outlook (MSG) объясняет, как создавать и сохранять сообщения, а также как создавать файлы MSG с вложениями. Эта статья объясняет, как управлять вложениями Microsoft Outlook с помощью Aspose.Email. Вложения из файла сообщения доступны и сохраняются на диск с использованием свойства Attachments класса MapiMessage. Свойство Attachments является коллекцией типа MapiAttachmentCollection.

### **Сохранение вложений из файла сообщения Outlook (MSG)**
Чтобы сохранить вложения из файла MSG:

1. Переберите коллекцию MapiAttachmentCollection и получите отдельные вложения.
1. Для сохранения вложений вызовите метод Save() класса MapiAttachment.

Следующий фрагмент кода показывает, как сохранить вложения на локальном диске.

{{< gist "aspose-email" "ef0db907527892c88c557bb418093cee" "Examples-EmailCPP-Outlook-SaveAttachmentsFromOutlookMSGFile-SaveAttachmentsFromOutlookMSGFile.cpp" >}}

### **Удаление вложений**
Библиотека Aspose Outlook предоставляет функциональность для удаления вложений из файлов сообщений Microsoft Outlook (.msg):

- Вызовите метод RemoveAttachments(). Он принимает путь к файлу сообщения в качестве параметра. Он реализован как публичный статический метод, поэтому вам не нужно создавать объект.

Следующий фрагмент кода показывает, как удалить вложения с использованием библиотеки C++ Email Parser.

{{< gist "aspose-email" "ef0db907527892c88c557bb418093cee" "Examples-EmailCPP-Outlook-RemoveAttachmentsFromFile-RemoveAttachmentsFromFile.cpp" >}}

Вы также можете вызвать статический метод класса MapiMessage DestoryAttachment(). Он работает быстрее, чем RemoveAttachment(), потому что метод RemoveAttachment() разбирает файл сообщения.

{{< gist "aspose-email" "ef0db907527892c88c557bb418093cee" "Examples-EmailCPP-Outlook-DestroyAttachment-DestroyAttachment.cpp" >}}

### **Добавление вложений MSG**
Сообщение Outlook может содержать другие сообщения Microsoft Outlook во вложениях как обычные или встроенные сообщения. MapiAttachmentCollection предоставляет перегруженные члены метода Add для создания сообщений Outlook с обоими типами вложений.

### **Встраивание сообщения в качестве вложения**
Следующий фрагмент кода показывает, как сообщение MSG встроенное в файл MSG содержит PR_ATTACH_METHOD, значение которого равно 5.

{{< gist "aspose-email" "ef0db907527892c88c557bb418093cee" "Examples-EmailCPP-Outlook-EmbedMessageAsAttachment-EmbedMessageAsAttachment.cpp" >}}