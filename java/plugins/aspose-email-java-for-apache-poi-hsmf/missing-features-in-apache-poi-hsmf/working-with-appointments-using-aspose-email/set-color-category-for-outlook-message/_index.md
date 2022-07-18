---
title: Set Color Category for Outlook Message
type: docs
weight: 30
url: /java/set-color-category-for-outlook-message/
---

## **Aspose.Email - Set Color Category for Outlook Message**
Microsoft Outlook lets users assign color categories to differentiate emails. A color category marks an email as being of some kind of importance or category. Aspose.Email provides the same feature through the [FollowUpManager](https://reference.aspose.com/email/java/com.aspose.email/class-use/FollowUpManager) class. The following functionality is supported via this class:

- AddCategory() takes [MapiMessage](https://reference.aspose.com/email/java/com.aspose.email/mapimessage) and the color category string as arguments.
- removeCategory() takes MapiMessage and the color category string to be removed from the message as arguments.
- clearCategories() is used to remove all the color categories from the message.
- getCategories() is used to retrieve all the color categories from a particular message.

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
## **Download Running Code**
- [CodePlex](https://asposeemailjavaapachepoi.codeplex.com/releases/view/618811)
- [GitHub](https://github.com/aspose-email/Aspose.Email-for-Java/releases/tag/Aspose.Email_Java_for_Apache_POI-v1.0.0)
## **Download Sample Code**
- [CodePlex](https://asposeemailjavaapachepoi.codeplex.com/SourceControl/latest#src/main/java/com/aspose/email/examples/asposefeatures/appointments/colorcategory/AsposeCategory.java)
- [GitHub](https://github.com/aspose-email/Aspose.Email-for-Java/tree/master/Plugins/Aspose_Email_for_Apache_POI/src/main/java/com/aspose/email/examples/asposefeatures/appointments/colorcategory/AsposeCategory.java)

{{% alert color="primary" %}} 

For more details, visit [Setting Color Category for Outlook Message (MSG) Files](/email/java/managing-message-files-with-aspose-email-outlook/).

{{% /alert %}}
