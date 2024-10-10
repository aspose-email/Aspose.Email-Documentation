---
title: "Конвертирование файла папки Outlook в Offline (OST) в другие форматы"
url: /ru/java/convert-outlook-offline-folder-file-ost-to-other-formats/
weight: 20
type: docs
---

## **Aspose.Email - Конвертирование OST в другие форматы**
{{% alert color="primary" %}} 

Microsoft Outlook создает файл PST для хранения электронной почты, когда вы используете почтовые серверы POP3 или IMAP для загрузки сообщений. Он создает файл OST, когда вы используете Microsoft Exchange в качестве почтового сервера. OST поддерживает большие размеры файлов по сравнению с PST.

{{% /alert %}} 

Aspose.Email позволяет конвертировать файл OST в PST всего одной строкой кода. Аналогично, файл OST может быть создан из файла PST с использованием той же строки кода с перечислением FileFormat.

**Java**

```java

 PersonalStorage ost = PersonalStorage.fromFile(dataDir + "outlook.ost");

ost.saveAs(dataDir + "AsposeOST-PST.pst", FileFormat.Pst);

```
## **Скачать исполняемый код**
- [CodePlex](https://archive.codeplex.com/?p=asposeemailjavaapachepoi)
- [GitHub](https://github.com/aspose-email/Aspose.Email-for-Java/releases/tag/Aspose.Email_Java_for_Apache_POI-v1.0.0)
## **Скачать пример кода**
- [CodePlex](https://archive.codeplex.com/?p=asposeemailjavaapachepoi#src/main/java/com/aspose/email/examples/asposefeatures/conversion/osttopst/AsposeOSTtoPST.java)
- [GitHub](https://github.com/aspose-email/Aspose.Email-for-Java/blob/master/Plugins/Aspose_Email_for_Apache_POI/src/main/java/com/aspose/email/examples/asposefeatures/conversion/osttopst/AsposeOSTtoPST.java)