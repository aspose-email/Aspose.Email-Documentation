---
title: "Проверьте защиту паролем PST"
url: /ru/java/check-pst-password-protection/
weight: 10
type: docs
---

## **Aspose.Email - Проверьте защиту паролем PST**
Microsoft Outlook позволяет пользователям защищать файлы PST паролем для ограничения доступа к ним. Aspose.Email может обнаруживать защиту паролем в PST-файле. На этой странице показано, как проверить пароль в PST, а также как проверить правильность примененного к нему пароля.

**Java**

``` java

 if (pst.getMessageStoreProperties().contains(MapiPropertyTag.PR_PST_PASSWORD))

{

    long passwordHash = pst.getMessageStoreProperties().get_Item(MapiPropertyTag.PR_PST_PASSWORD).getLong();

    return passwordHash != 0;

}

```
## **Загрузить рабочий код**
- [CodePlex](https://archive.codeplex.com/?p=asposeemailjavaapachepoi)
- [GitHub](https://github.com/aspose-email/Aspose.Email-for-Java/releases/tag/Aspose.Email_Java_for_Apache_POI-v1.0.0)
## **Загрузить образец кода**
- [CodePlex](https://archive.codeplex.com/?p=asposeemailjavaapachepoi#src/main/java/com/aspose/email/examples/asposefeatures/outlookstorage/checkprotection/AsposeCheckProtection.java)
- [GitHub](https://github.com/aspose-email/Aspose.Email-for-Java/blob/master/Plugins/Aspose_Email_for_Apache_POI/src/main/java/com/aspose/email/examples/asposefeatures/outlookstorage/checkprotection/AsposeCheckProtection.java)

{{% alert color="primary" %}}

Для получения дополнительной информации посетите [Работа со свойствами защиты паролем PST](/email/java/working-with-calendar-items-in-pst-file/).

{{% /alert %}}
