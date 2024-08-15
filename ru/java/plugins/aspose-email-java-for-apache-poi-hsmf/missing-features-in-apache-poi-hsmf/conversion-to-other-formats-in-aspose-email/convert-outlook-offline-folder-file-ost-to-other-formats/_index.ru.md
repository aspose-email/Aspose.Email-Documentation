---
title: "Преобразование файла автономной папки Outlook (OST) в другие форматы"
url: /ru/java/convert-outlook-offline-folder-file-ost-to-other-formats/
weight: 20
type: docs
---

## **Aspose.Email - конвертируйте OST в другие форматы**
{{% alert color="primary" %}}

Microsoft Outlook создает файл PST для хранения электронной почты при использовании почтовых серверов POP3 или IMAP для загрузки сообщений. Он создает OST-файл, когда вы используете Microsoft Exchange в качестве почтового сервера. OST поддерживает большие размеры файлов по сравнению с PST.

{{% /alert %}}

Aspose.Email позволяет конвертировать OST-файл в PST с помощью одной строки кода. Точно так же файл OST можно создать из файла PST, используя ту же строку кода, что и перечислитель FileFormat.

**Java**

```java

 PersonalStorage ost = PersonalStorage.fromFile(dataDir + "outlook.ost");

ost.saveAs(dataDir + "AsposeOST-PST.pst", FileFormat.Pst);

```
## **Загрузить рабочий код**
- [CodePlex](https://archive.codeplex.com/?p=asposeemailjavaapachepoi)
- [GitHub](https://github.com/aspose-email/Aspose.Email-for-Java/releases/tag/Aspose.Email_Java_for_Apache_POI-v1.0.0)
## **Загрузить образец кода**
- [CodePlex](https://archive.codeplex.com/?p=asposeemailjavaapachepoi#src/main/java/com/aspose/email/examples/asposefeatures/conversion/osttopst/AsposeOSTtoPST.java)
- [GitHub](https://github.com/aspose-email/Aspose.Email-for-Java/blob/master/Plugins/Aspose_Email_for_Apache_POI/src/main/java/com/aspose/email/examples/asposefeatures/conversion/osttopst/AsposeOSTtoPST.java)
