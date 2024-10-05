---
title: Загрузка, просмотр и парсинг файла Outlook MSG с использованием библиотеки C++ Email
linktitle: Загрузка, просмотр и парсинг файла MSG
type: docs
weight: 20
url: /cpp/loading-viewing-and-parsing-msg-file/
description: API библиотеки парсинга электронной почты C++ позволяет загружать, просматривать и парсить файлы MSG Outlook из файла или потока.
---

## **Загрузка, просмотр и парсинг файла MSG**
Эта тема объясняет, как загрузить файл сообщения Microsoft Outlook (*.msg) с использованием библиотеки парсинга электронной почты C++. 

Класс MapiMessage используется для загрузки файлов MSG и предоставляет несколько статических функций загрузки для различных сценариев. Следующий фрагмент кода показывает, как загружать файлы MSG из файла или потока.

{{% alert %}}
**Попробуйте сами!**

Парсите email-файлы с помощью бесплатного [**Aspose.Email Parser App**](https://products.aspose.app/email/parser).
{{% /alert %}}

### **Загрузка файлов MSG**
Следующий фрагмент кода показывает, как загружать файлы MSG.

{{< gist "aspose-email" "ef0db907527892c88c557bb418093cee" "Examples-EmailCPP-Outlook-LoadMSGFiles-LoadMSGFiles.cpp" >}}

### **Загрузка из потока**
Следующий фрагмент кода показывает, как загружать файл из потока.

{{< gist "aspose-email" "ef0db907527892c88c557bb418093cee" "Examples-EmailCPP-Outlook-LoadingFromStream-LoadingFromStream.cpp" >}}