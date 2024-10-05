---
title: "Загрузка, сохранение и преобразование различных форматов электронных сообщений в C++"
description: "С библиотекой парсинга электронной почты C++ вы можете загружать, сохранять, экспортировать и конвертировать различные форматы сообщений электронной почты, например EML, MSG, MHTML."
url: /ru/cpp/loading-and-saving-message/
weight: 30
type: docs
linktitle: "Загрузка и сохранение сообщения"
---

## **Загрузка сообщения с параметрами загрузки**
Следующий фрагмент кода показывает, как загрузить сообщение с параметрами загрузки.



{{< gist "aspose-email" "ef0db907527892c88c557bb418093cee" "Examples-EmailCPP-Email-LoadMessageWithLoadOptions-LoadMessageWithLoadOptions.cpp" >}}
## **Сохранение и конвертация сообщений**
Aspose.Email упрощает преобразование любого типа сообщения в другой формат. Чтобы продемонстрировать эту функцию, код в этой статье загружает три типа сообщений с диска и сохраняет их в других форматах. Для сохранения сообщений в другие форматы можно использовать базовый класс SaveOptions и классы EmlSaveOptions, MsgSaveOptions, MhtSaveOptions, HtmlSaveOptions для дополнительных настроек при сохранении MailMessage. Статья показывает, как использовать эти классы для сохранения примера электронной почты в следующем виде:

- Формат EML.
- Outlook MSG.
- Формат MHTML.
- Формат HTML.
### **Загрузка EML и сохранение в формате EML**
Следующий фрагмент кода показывает, как загрузить сообщение EML и сохранить его на диск в том же формате.



{{< gist "aspose-email" "ef0db907527892c88c557bb418093cee" "Examples-EmailCPP-Email-LoadAndSaveFileAsEML-LoadAndSaveFileAsEML.cpp" >}}
### **Загрузка EML и сохранение в формате EML с сохранением оригинальных границ**
Следующий фрагмент кода показывает, как загрузить EML и сохранить в формате EML с сохранением оригинальных границ.



{{< gist "aspose-email" "ef0db907527892c88c557bb418093cee" "Examples-EmailCPP-Email-PreserveOriginalBoundaries-PreservOriginalBoundaries.cpp" >}}
### **Сохранение в формате EML с сохранением вложений TNEF**
Следующий фрагмент кода показывает, как сохранить в формате EML с сохранением вложений TNEF.



{{< gist "aspose-email" "ef0db907527892c88c557bb418093cee" "Examples-EmailCPP-Email-PreserveTNEFAttachment-PreserveTNEFAttachment.cpp" >}}
### **Загрузка EML, сохранение в MSG**
Следующий фрагмент кода показывает, как загрузить сообщение EML и преобразовать его в MSG с использованием соответствующей опции из SaveOptions.



{{< gist "aspose-email" "ef0db907527892c88c557bb418093cee" "Examples-EmailCPP-Email-LoadingEMLAndSavingToMSG-LoadingEMLAndSavingToMSG.cpp" >}}
### **Сохранение MailMessage в формате MHTML**
Можно использовать различные опции MHTML для достижения желаемых результатов. Следующий фрагмент кода показывает, как загрузить сообщение EML в [MailMessage](https://reference.aspose.com/email/net/aspose.email/mailmessage) и преобразовать его в MHTML.



{{< gist "aspose-email" "ef0db907527892c88c557bb418093cee" "Examples-EmailCPP-Email-SaveMailMessageAsMHTML-SaveMailMessageAsMHTML.cpp" >}}
#### **Экспорт электронной почты в MHT с пользовательским смещением времени**
Класс MailMessage предоставляет свойство TimeZoneOffset для установки пользовательского часового пояса при экспорте в MHT. Следующий фрагмент кода показывает, как экспортировать электронную почту в MHT с пользовательским часовым поясом.



{{< gist "aspose-email" "ef0db907527892c88c557bb418093cee" "Examples-EmailCPP-Email-ExportEmailToMHTWithCustomTimezone-ExportEmailToMHTWithCustomTimezone.cpp" >}}
### **Экспорт электронной почты в EML**
Следующий фрагмент кода показывает, как экспортировать электронную почту в EML.

{{< gist "aspose-email" "ef0db907527892c88c557bb418093cee" "Examples-EmailCPP-Email-ExportEmailToEML-ExportEmailToEML.cpp" >}}
