---
title: "Работа с напоминанием и сроком выполнения для файлов Outlook MSG"
url: /ru/java/working-with-follow-up-and-due-date-for-outlook-msg-files/
weight: 50
type: docs
---


## **Установка напоминания и срока выполнения для файлов Outlook MSG**

Флаг напоминания помечает электронное письмо для выполнения какого-либо действия. Microsoft Outlook позволяет пользователям устанавливать флажки для сообщений и в настройках флага назначать срок выполнения для напоминания. Microsoft Outlook отправляет напоминание получателю, чтобы побудить его ответить на письмо. Установка флажков для электронных писем и назначение сроков выполнения программно позволяет разработчикам автоматизировать определенные типы сообщений и помогает получателям помнить о необходимости совершения действий. Например, это может использоваться для отправки ежемесячных сообщений команде продаж с целью напомнить им о необходимости завершить свои отчеты; или для отправки сообщения всем сотрудникам с напоминанием о собрании компании. Aspose.Email для Java поддерживает установку флага напоминания и срока выполнения для объектов [MapiMessage](https://reference.aspose.com/email/java/com.aspose.email/mapimessage/) с использованием [FollowUpManager](https://reference.aspose.com/email/java/com.aspose.email/followupmanager/) и [FollowUpOptions](https://reference.aspose.com/email/java/com.aspose.email/followupoptions/). Существует несколько вариантов того, как флаг напоминания может быть установлен на сообщение. Все они используются в приведенном ниже примере кода:

1. Установить флаг напоминания для сообщения
1. Добавить срок выполнения и дату напоминания к сообщению
1. Добавить флажок к сообщению получателя.
1. Пометить как завершенное.
1. Удалить флажок.
1. Прочитать параметры напоминания.
   
### **Установка флага напоминания**

Следующий фрагмент кода показывает, как установить флаг напоминания.

~~~Java
// Для полного примера и файлов данных, пожалуйста, перейдите по адресу https://github.com/aspose-email/Aspose.Email-for-Java
// Путь к директории файлов.
String dataDir = "outlook/";

MailMessage mailMsg = new MailMessage();
mailMsg.setSender(new MailAddress("AETest12@gmail.com"));
mailMsg.getTo().addMailAddress(new MailAddress("receiver@gmail.com"));
mailMsg.setBody("Это сообщение протестирует, могут ли параметры напоминания быть добавлены к новому mapi сообщению.");
MapiMessage mapi = MapiMessage.fromMailMessage(mailMsg);

Calendar calendar = Calendar.getInstance();
calendar.set(2013, Calendar.MAY, 23, 14, 40, 0);
Date dtStartDate = calendar.getTime();

calendar.set(2013, Calendar.MAY, 23, 16, 40, 0);
Date dtReminderDate = calendar.getTime();

calendar.add(Calendar.DATE, 1);
Date dtDueDate = calendar.getTime();

FollowUpOptions options = new FollowUpOptions("Напоминание", dtStartDate, dtDueDate, dtReminderDate);
FollowUpManager.setOptions(mapi, options);
mapi.save(dataDir + "SetFollowUpflag_out.msg");
~~~ 

### **Установка напоминания для получателей**

Следующий фрагмент кода показывает, как установить напоминание для получателей.

~~~Java
// Для полного примера и файлов данных, пожалуйста, перейдите по адресу https://github.com/aspose-email/Aspose.Email-for-Java
// Путь к директории файлов.
String dataDir = "outlook/";

MailMessage mailMsg = new MailMessage();
mailMsg.setSender(new MailAddress("AETest12@gmail.com"));
mailMsg.getTo().addMailAddress(new MailAddress("receiver@gmail.com"));
mailMsg.setBody("Это сообщение протестирует, могут ли параметры напоминания быть добавлены к новому mapi сообщению.");

MapiMessage mapi = MapiMessage.fromMailMessage(mailMsg);
mapi.setMessageFlags(MapiMessageFlags.MSGFLAG_UNSENT); // пометить это сообщение как черновик

Calendar calendar = Calendar.getInstance();
calendar.set(2013, Calendar.MAY, 23, 16, 40, 0);
Date dtReminderDate = calendar.getTime();

// Добавить флаг напоминания для получателя теперь
FollowUpManager.setFlagForRecipients(mapi, "Напоминание", dtReminderDate);
mapi.save(dataDir + "SetFollowUpForRecipients_out.msg");
~~~ 

### **Пометка флага напоминания как завершенного**

Следующий фрагмент кода показывает, как пометить флаг напоминания как завершенный.

~~~Java
// Для полного примера и файлов данных, пожалуйста, перейдите по адресу https://github.com/aspose-email/Aspose.Email-for-Java
// Путь к директории файлов.
String dataDir = "outlook/";

MapiMessage mapi = MapiMessage.fromFile(dataDir + "message.msg");
FollowUpManager.markAsCompleted(mapi);
mapi.save(dataDir + "MarkedCompleted_out.msg");
~~~ 

### **Удаление флага напоминания**

Следующий фрагмент кода показывает, как удалить флаг напоминания.

~~~Java
// Для полного примера и файлов данных, пожалуйста, перейдите по адресу https://github.com/aspose-email/Aspose.Email-for-Java
// Путь к директории файлов.
String dataDir = "outlook/";

MapiMessage mapi = MapiMessage.fromFile(dataDir + "message.msg");
FollowUpManager.clearFlag(mapi);
mapi.save(dataDir + "FollowUpFlagRemoved_out.msg");
~~~ 

### **Чтение параметров флага напоминания для сообщения**

Следующий фрагмент кода показывает, как прочитать параметры флага напоминания для сообщения.

~~~Java
// Для полного примера и файлов данных, пожалуйста, перейдите по адресу https://github.com/aspose-email/Aspose.Email-for-Java
// Путь к директории файлов.
String dataDir = "outlook/";

MapiMessage mapi = MapiMessage.fromFile(dataDir + "message.msg");
FollowUpOptions options = FollowUpManager.getOptions(mapi);
~~~