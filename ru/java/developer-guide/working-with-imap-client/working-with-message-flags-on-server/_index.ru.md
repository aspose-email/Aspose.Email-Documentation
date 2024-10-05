---
title: "Работа с флагами сообщений на сервере"
url: /ru/java/работа-с-флагами-сообщений-на-сервере/
weight: 30
type: docs
---


## **Изменение флагов сообщений**

Вы можете изменить флаги сообщений, используя метод [changeMessageFlags()](https://reference.aspose.com/email/java/com.aspose.email/imapclient/#changeMessageFlags-com.aspose.email.IConnection-int-com.aspose.email.ImapMessageFlags-). Этот метод принимает два параметра.

1. Номер последовательности сообщения или уникальный идентификатор.
1. [MessageFlag](https://reference.aspose.com/email/java/com.aspose.email/imapmessageflags/).

Следующие флаги могут быть установлены:

- [Answered](https://reference.aspose.com/email/java/com.aspose.email/imapmessageflags/#getAnswered--)
- [Deleted](https://reference.aspose.com/email/java/com.aspose.email/imapmessageflags/#getDeleted--)
- [Draft](https://reference.aspose.com/email/java/com.aspose.email/imapmessageflags/#getDraft--)
- [Empty](https://reference.aspose.com/email/java/com.aspose.email/imapmessageflags/#getEmpty--)
- [Flagged](https://reference.aspose.com/email/java/com.aspose.email/imapmessageflags/#getFlagged--)
- [isRead](https://reference.aspose.com/email/java/com.aspose.email/imapmessageflags/#isRead--)
- [Recent](https://reference.aspose.com/email/java/com.aspose.email/imapmessageflags/#getRecent--)
  
### **Установка флагов сообщений**

Следующий фрагмент кода показывает, как изменить флаги сообщений на IMAP-сервере с помощью Aspose.Email.

~~~Java
// For complete examples and data files, please go to https://github.com/aspose-email/Aspose.Email-for-Java
// Пометить сообщение как прочитанное
client.changeMessageFlags(1, ImapMessageFlags.isRead());
~~~

### **Удаление флагов сообщений**

Флаги сообщений также можно удалить с помощью метода [removeMessageFlags()](https://reference.aspose.com/email/java/com.aspose.email/imapclient/#removeMessageFlags-com.aspose.email.IConnection-int-com.aspose.email.ImapMessageFlags-). Использование аналогично методу [changeMessageFlags()](https://reference.aspose.com/email/java/com.aspose.email/imapclient/#changeMessageFlags-com.aspose.email.IConnection-int-com.aspose.email.ImapMessageFlags-). Он принимает номер последовательности или уникальный идентификатор сообщения и [MessageFlag](https://reference.aspose.com/email/java/com.aspose.email/imapmessageflags/). Следующий фрагмент кода показывает, как удалить флаги сообщений.

~~~Java
// For complete examples and data files, please go to https://github.com/aspose-email/Aspose.Email-for-Java
// Удалить флаг сообщения
client.removeMessageFlags(1, ImapMessageFlags.isRead());
~~~

## **Установка пользовательских флагов**

Вы также можете установить пользовательские флаги для сообщения с использованием [ImapClient](https://reference.aspose.com/email/java/com.aspose.email/imapclient/) API. Метод ImapClient [AddMessageFlags](https://reference.aspose.com/email/java/com.aspose.email/imapclient/#addMessageFlags-com.aspose.email.IConnection-int-com.aspose.email.ImapMessageFlags-) предоставляет возможность устанавливать пользовательские флаги для сообщений.

~~~Java
// For complete examples and data files, please go to https://github.com/aspose-email/Aspose.Email-for-Java
// Создать сообщение
MailMessage message = new MailMessage("user@domain1.com", "user@domain2.com", "subject", "message");

// Добавить сообщение в почтовый ящик
String uid = client.appendMessage(ImapFolderInfo.IN_BOX, message);

// Добавить пользовательские флаги к добавленному сообщению
client.addMessageFlags(uid, com.aspose.email.ImapMessageFlags.op_BitwiseOr(ImapMessageFlags.keyword("custom1"), ImapMessageFlags.keyword("custom1_0")));

// Извлечь сообщения для проверки наличия пользовательского флага
client.selectFolder(ImapFolderInfo.IN_BOX);

ImapMessageInfoCollection messageInfos = client.listMessages();
for (ImapMessageInfo inf : messageInfos) {
    ImapMessageFlags[] flags = inf.getFlags().split();

    if (inf.containsKeyword("custom1"))
        System.out.println("Ключевое слово найдено");
}
~~~