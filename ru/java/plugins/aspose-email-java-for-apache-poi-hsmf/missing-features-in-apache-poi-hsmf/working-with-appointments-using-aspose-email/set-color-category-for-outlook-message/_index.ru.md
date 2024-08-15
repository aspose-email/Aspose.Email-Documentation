---
title: "Задать цветовую категорию для сообщения Outlook"
url: /ru/java/set-color-category-for-outlook-message/
weight: 30
type: docs
---

## **Aspose.Email - установите цветовую категорию для сообщения Outlook**
Microsoft Outlook позволяет пользователям назначать цветовые категории для различения писем. Цветовая категория обозначает электронное письмо как относящееся к какой-то важности или категории. Aspose.Email предоставляет ту же функцию через [FollowUpManager](https://apireference.aspose.com/email/java/com.aspose.email/class-use/FollowUpManager) класс. Этот класс поддерживает следующие функции:

- AddCategory() takes [MapiMessage](https://apireference.aspose.com/email/java/com.aspose.email/mapimessage) и строку цветовой категории в качестве аргументов.
- removeCategory () принимает mapiMessage и строку цветовой категории, которую нужно удалить из сообщения, в качестве аргументов.
- clearCategories () используется для удаления всех цветовых категорий из сообщения.
- getCategories () используется для извлечения всех цветовых категорий из определенного сообщения.

**Java**

``` java

 MapiMessage msg = MapiMessage.fromFile(dataDir + "message.msg");

// Add category

FollowUpManager.addCategory(msg, "Purple Category");

// Add another category

FollowUpManager.addCategory(msg, "Red Category");

// Retrieve the list of available categories

IList categories = FollowUpManager.getCategories(msg);

// Remove the specified category

FollowUpManager.removeCategory(msg, "Red Category");

// Clear all categories

//FollowUpManager.clearCategories(msg);

msg.save(dataDir + "AsposeCategories.msg");

```
## **Загрузить рабочий код**
- [CodePlex](https://asposeemailjavaapachepoi.codeplex.com/releases/view/618811)
- [GitHub](https://github.com/aspose-email/Aspose.Email-for-Java/releases/tag/Aspose.Email_Java_for_Apache_POI-v1.0.0)
## **Загрузить образец кода**
- [CodePlex](https://asposeemailjavaapachepoi.codeplex.com/SourceControl/latest#src/main/java/com/aspose/email/examples/asposefeatures/appointments/colorcategory/AsposeCategory.java)
- [GitHub](https://github.com/aspose-email/Aspose.Email-for-Java/tree/master/Plugins/Aspose_Email_for_Apache_POI/src/main/java/com/aspose/email/examples/asposefeatures/appointments/colorcategory/AsposeCategory.java)

{{% alert color="primary" %}}

Для получения дополнительной информации посетите [Настройка цветовой категории для файлов сообщений Outlook (MSG)](/email/java/managing-message-files-with-aspose-email-outlook/).

{{% /alert %}}
