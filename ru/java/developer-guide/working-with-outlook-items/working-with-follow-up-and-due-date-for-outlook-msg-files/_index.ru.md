---
title: "Работа с отслеживанием и сроками выполнения файлов Outlook MSG"
url: /ru/java/working-with-follow-up-and-due-date-for-outlook-msg-files/
weight: 50
type: docs
---


## **Настройка сроков и сроков выполнения файлов Outlook MSG**

Флаг «Повторное действие» отмечает сообщение электронной почты, требующее какого-либо действия. Microsoft Outlook позволяет пользователям отмечать сообщения и при настройке флага назначать срок выполнения последующих действий. Microsoft Outlook отправляет получателю напоминание с просьбой ответить на сообщение электронной почты. Пометка писем и программная настройка сроков выполнения позволяют разработчикам программного обеспечения автоматизировать определенные типы электронных писем и помогать получателям не забывать принимать меры. Например, его можно использовать для отправки ежемесячных сообщений отделу продаж с напоминанием о необходимости заполнения отчетов или для отправки всем сотрудникам сообщений с напоминанием о собрании компании. Aspose.Email для Java поддерживает настройку флажка и срока выполнения [MapiMessage](https://reference.aspose.com/email/java/com.aspose.email/mapimessage/) объекты, использующие [FollowUpManager](https://reference.aspose.com/email/java/com.aspose.email/followupmanager/) and [FollowUpOptions](https://reference.aspose.com/email/java/com.aspose.email/followupoptions/). Существует несколько вариантов, в которых на сообщении можно установить следующий флаг. Все они используются в приведенном ниже примере кода:

1. Установите флажок отслеживания для сообщения
1. Добавьте к сообщению срок и дату напоминания
1. Добавьте флаг к сообщению получателя.
1. Отметить как завершенное.
1. Удалить флаг.
1. Ознакомьтесь с вариантами последующих действий.
  
### **Настройка флага FollowUp**

В следующем фрагменте кода показано, как установить дополнительный флаг.

~~~Java
// For complete examples and data files, please go to https://github.com/aspose-email/Aspose.Email-for-Java
// The path to the File directory.
String dataDir = "outlook/";

MailMessage mailMsg = new MailMessage();
mailMsg.setSender(new MailAddress("AETest12@gmail.com"));
mailMsg.getTo().addMailAddress(new MailAddress("receiver@gmail.com"));
mailMsg.setBody("This message will test if follow up options can be added to a new mapi message.");
MapiMessage mapi = MapiMessage.fromMailMessage(mailMsg);

Calendar calendar = Calendar.getInstance();
calendar.set(2013, Calendar.MAY, 23, 14, 40, 0);
Date dtStartDate = calendar.getTime();

calendar.set(2013, Calendar.MAY, 23, 16, 40, 0);
Date dtReminderDate = calendar.getTime();

calendar.add(Calendar.DATE, 1);
Date dtDueDate = calendar.getTime();

FollowUpOptions options = new FollowUpOptions("Follow Up", dtStartDate, dtDueDate, dtReminderDate);
FollowUpManager.setOptions(mapi, options);
mapi.save(dataDir + "SetFollowUpflag_out.msg");
~~~

### **Настройка отслеживания получателей**

В следующем фрагменте кода показано, как настроить отслеживание для получателей.

~~~Java
// For complete examples and data files, please go to https://github.com/aspose-email/Aspose.Email-for-Java
// The path to the File directory.
String dataDir = "outlook/";

MailMessage mailMsg = new MailMessage();
mailMsg.setSender(new MailAddress("AETest12@gmail.com"));
mailMsg.getTo().addMailAddress(new MailAddress("receiver@gmail.com"));
mailMsg.setBody("This message will test if follow up options can be added to a new mapi message.");

MapiMessage mapi = MapiMessage.fromMailMessage(mailMsg);
mapi.setMessageFlags(MapiMessageFlags.MSGFLAG_UNSENT); // mark this message as draft

Calendar calendar = Calendar.getInstance();
calendar.set(2013, Calendar.MAY, 23, 16, 40, 0);
Date dtReminderDate = calendar.getTime();

// Add the follow up flag for recipient now
FollowUpManager.setFlagForRecipients(mapi, "Follow up", dtReminderDate);
mapi.save(dataDir + "SetFollowUpForRecipients_out.msg");
~~~

### **Пометка флага FollowUp как завершенного**

В следующем фрагменте кода показано, как пометить следующий флаг как завершенный.

~~~Java
// For complete examples and data files, please go to https://github.com/aspose-email/Aspose.Email-for-Java
// The path to the File directory.
String dataDir = "outlook/";

MapiMessage mapi = MapiMessage.fromFile(dataDir + "message.msg");
FollowUpManager.markAsCompleted(mapi);
mapi.save(dataDir + "MarkedCompleted_out.msg");
~~~

### **Удаление флага FollowUp**

В следующем фрагменте кода показано, как удалить последующий флаг.

~~~Java
// For complete examples and data files, please go to https://github.com/aspose-email/Aspose.Email-for-Java
// The path to the File directory.
String dataDir = "outlook/";

MapiMessage mapi = MapiMessage.fromFile(dataDir + "message.msg");
FollowUpManager.clearFlag(mapi);
mapi.save(dataDir + "FollowUpFlagRemoved_out.msg");
~~~

### **Прочитайте варианты флагов отслеживания сообщения**

В следующем фрагменте кода показано, как прочитать варианты последующих флагов для сообщения.

~~~Java
// For complete examples and data files, please go to https://github.com/aspose-email/Aspose.Email-for-Java
// The path to the File directory.
String dataDir = "outlook/";

MapiMessage mapi = MapiMessage.fromFile(dataDir + "message.msg");
FollowUpOptions options = FollowUpManager.getOptions(mapi);
~~~
