---
title: Проверка защиты паролем PST
type: docs
weight: 10
url: /java/check-pst-password-protection/
---

## **Aspose.Email - Проверка защиты паролем PST**
Microsoft Outlook позволяет пользователям защищать файлы PST паролем для ограничения доступа к ним. Aspose.Email может обнаружить защиту паролем на файле PST. Эта страница показывает, как проверить файл PST на наличие пароля, а также как определить, правильный ли применённый пароль.

**Java**

``` java

 if (pst.getMessageStoreProperties().contains(MapiPropertyTag.PR_PST_PASSWORD))

{

    long passwordHash = pst.getMessageStoreProperties().get_Item(MapiPropertyTag.PR_PST_PASSWORD).getLong();

    return passwordHash != 0;

}

```
## **Скачать работающий код**
- [CodePlex](https://archive.codeplex.com/?p=asposeemailjavaapachepoi)
- [GitHub](https://github.com/aspose-email/Aspose.Email-for-Java/releases/tag/Aspose.Email_Java_for_Apache_POI-v1.0.0)
## **Скачать пример кода**
- [CodePlex](https://archive.codeplex.com/?p=asposeemailjavaapachepoi#src/main/java/com/aspose/email/examples/asposefeatures/outlookstorage/checkprotection/AsposeCheckProtection.java)
- [GitHub](https://github.com/aspose-email/Aspose.Email-for-Java/blob/master/Plugins/Aspose_Email_for_Apache_POI/src/main/java/com/aspose/email/examples/asposefeatures/outlookstorage/checkprotection/AsposeCheckProtection.java)

{{% alert color="primary" %}} 

Для получения дополнительной информации посетите страницу [Работа с свойствами защиты паролем PST](/email/java/working-with-calendar-items-in-pst-file/).

{{% /alert %}}