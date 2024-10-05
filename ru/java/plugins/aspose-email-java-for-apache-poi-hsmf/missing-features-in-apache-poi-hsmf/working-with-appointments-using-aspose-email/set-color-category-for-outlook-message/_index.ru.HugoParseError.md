---
title: Установить цветовую категорию для сообщения Outlook
type: docs
weight: 30
url: /java/set-color-category-for-outlook-message/
---

## **Aspose.Email - Установить цветовую категорию для сообщения Outlook**

Microsoft Outlook позволяет пользователям назначать цветовые категории, чтобы различать электронные письма. Цветовая категория помечает сообщение как имеющее определенную важность или категорию. Aspose.Email предоставляет ту же функцию через класс [FollowUpManager](https://apireference.aspose.com/email/java/com.aspose.email/class-use/FollowUpManager). Следующий функционал поддерживается через этот класс:

- AddCategory() принимает [MapiMessage](https://apireference.aspose.com/email/java/com.aspose.email/mapimessage) и строку цветовой категории в качестве аргументов.
- removeCategory() принимает MapiMessage и строку цветовой категории, которую нужно удалить из сообщения, в качестве аргументов.
- clearCategories() используется для удаления всех цветовых категорий из сообщения.
- getCategories() используется для получения всех цветовых категорий из конкретного сообщения.

**Java**

```java

 MapiMessage msg = MapiMessage.fromFile(dataDir + "message.msg");

// Добавить категорию

FollowUpManager.addCategory(msg, "Фиолетовая категория");

// Добавить другую категорию

FollowUpManager.addCategory(msg, "Красная категория");

// Получить список доступных категорий

IList categories = FollowUpManager.getCategories(msg);

// Удалить указанную категорию

FollowUpManager.removeCategory(msg, "Красная категория");

// Очистить все категории

//FollowUpManager.clearCategories(msg);

msg.save(dataDir + "AsposeCategories.msg");

```

## **Скачать работающий код**

- [CodePlex](https://asposeemailjavaapachepoi.codeplex.com/releases/view/618811)
- [GitHub](https://github.com/aspose-email/Aspose.Email-for-Java/releases/tag/Aspose.Email_Java_for_Apache_POI-v1.0.0)

## **Скачать пример кода**

- [CodePlex](https://asposeemailjavaapachepoi.codeplex.com/SourceControl/latest#src/main/java/com/aspose/email/examples/asposefeatures/appointments/colorcategory/AsposeCategory.java)
- [GitHub](https://github.com/aspose-email/Aspose.Email-for-Java/tree/master/Plugins/Aspose_Email_for_Apache_POI/src/main/java/com/aspose/email/examples/asposefeatures/appointments/colorcategory/AsposeCategory.java)

{{% alert color="primary" %}}

Для получения дополнительной информации посетите [Установка цветовой категории для файлов сообщений Outlook (MSG)](/email/java/managing-message-files-with-aspose-email-outlook/).

{{% /alert %}}

