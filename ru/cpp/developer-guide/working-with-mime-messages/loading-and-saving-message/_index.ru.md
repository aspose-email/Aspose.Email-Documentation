---
title: "Загрузка, сохранение и преобразование различных форматов сообщений электронной почты в C++"
description: "С помощью библиотеки C++ Email Parser Library вы можете загружать, сохранять, экспортировать и конвертировать различные форматы сообщений электронной почты, например EML, MSG, MHTML."
url: /ru/cpp/loading-and-saving-message/
weight: 30
type: docs
linktitle: "Загрузка и сохранение сообщения"
---

## **Загрузка сообщения с опциями загрузки**
В следующем фрагменте кода показано, как загрузить сообщение с опциями загрузки.



{{< gist "aspose-email" "ef0db907527892c88c557bb418093cee" "Examples-EmailCPP-Email-LoadMessageWithLoadOptions-LoadMessageWithLoadOptions.cpp" >}}
## **Сохранение и преобразование сообщений**
Aspose.Email позволяет легко конвертировать сообщения любого типа в другой формат. Чтобы продемонстрировать эту функцию, приведенный в этой статье код загружает три типа сообщений с диска и сохраняет их в других форматах. Базовый класс SaveOptions и классы EMLSaveOptions, MsgSaveOptions, MhtSaveOptions, HTMLSaveOptions для дополнительных настроек при сохранении MailMessage можно использовать для сохранения сообщений в других форматах. В статье показано, как использовать эти классы для сохранения образца электронного письма в виде:

- Формат EML.
- MSG для Outlook.
- Формат MHTML.
- Формат HTML.
### **Загрузка EML и сохранение как EML**
В следующем фрагменте кода показано, как загрузить сообщение EML и сохранить его на диск в том же формате.



{{< gist "aspose-email" "ef0db907527892c88c557bb418093cee" "Examples-EmailCPP-Email-LoadAndSaveFileAsEML-LoadAndSaveFileAsEML.cpp" >}}
### **Загрузка EML и сохранение как EML с сохранением исходных границ**
В следующем фрагменте кода показано, как загрузить EML и сохранить его как EML с сохранением исходных границ.



{{< gist "aspose-email" "ef0db907527892c88c557bb418093cee" "Examples-EmailCPP-Email-PreserveOriginalBoundaries-PreservOriginalBoundaries.cpp" >}}
### **Сохранение в формате EML Сохранение вложений TNEF**
В следующем фрагменте кода показано, как сохранить вложения TNEF в формате EML.



{{< gist "aspose-email" "ef0db907527892c88c557bb418093cee" "Examples-EmailCPP-Email-PreserveTNEFAttachment-PreserveTNEFAttachment.cpp" >}}
### **Загрузка EML, сохранение в MSG**
В следующем фрагменте кода показано, как загрузить сообщение EML и преобразовать его в MSG с помощью соответствующей опции из SaveOptions.



{{< gist "aspose-email" "ef0db907527892c88c557bb418093cee" "Examples-EmailCPP-Email-LoadingEMLAndSavingToMSG-LoadingEMLAndSavingToMSG.cpp" >}}
### **Сохранение почтового сообщения в формате MHTML**
Для получения желаемых результатов можно использовать различные варианты MHTML. В следующем фрагменте кода показано, как загрузить сообщение EML в [MailMessage](https://reference.aspose.com/email/net/aspose.email/mailmessage) и преобразует его в MHTML.



{{< gist "aspose-email" "ef0db907527892c88c557bb418093cee" "Examples-EmailCPP-Email-SaveMailMessageAsMHTML-SaveMailMessageAsMHTML.cpp" >}}
#### **Экспорт электронной почты в MHT с настраиваемым часовым поясом**
Класс MailMessage предоставляет свойство TimeZoneOffset для установки настраиваемого часового пояса при экспорте в MHT. В следующем фрагменте кода показано, как экспортировать электронное письмо в MHT с помощью настраиваемого TimeZone.



{{< gist "aspose-email" "ef0db907527892c88c557bb418093cee" "Examples-EmailCPP-Email-ExportEmailToMHTWithCustomTimezone-ExportEmailToMHTWithCustomTimezone.cpp" >}}
### **Экспорт электронной почты в EML**
В следующем фрагменте кода показано, как экспортировать электронную почту в eml.

{{< gist "aspose-email" "ef0db907527892c88c557bb418093cee" "Examples-EmailCPP-Email-ExportEmailToEML-ExportEmailToEML.cpp" >}}




