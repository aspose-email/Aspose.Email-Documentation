---
title: "Работа с флагами сообщений на сервере"
url: /ru/java/working-with-message-flags-on-server/
weight: 30
type: docs
---


## **Изменение флагов сообщений**

Вы можете изменить флаги сообщений, используя [changeMessageFlags()](https://reference.aspose.com/email/java/com.aspose.email/imapclient/#changeMessageFlags-com.aspose.email.IConnection-int-com.aspose.email.ImapMessageFlags-) метод. Этот метод принимает два параметра.

1. Порядковый номер сообщения или уникальный идентификатор.
1. [MessageFlag](https://reference.aspose.com/email/java/com.aspose.email/imapmessageflags/).

Можно установить следующие флаги:

- [Answered](https://reference.aspose.com/email/java/com.aspose.email/imapmessageflags/#getAnswered--)
- [Deleted](https://reference.aspose.com/email/java/com.aspose.email/imapmessageflags/#getDeleted--)
- [Draft](https://reference.aspose.com/email/java/com.aspose.email/imapmessageflags/#getDraft--)
- [Empty](https://reference.aspose.com/email/java/com.aspose.email/imapmessageflags/#getEmpty--)
- [Flagged](https://reference.aspose.com/email/java/com.aspose.email/imapmessageflags/#getFlagged--)
- [isRead](https://reference.aspose.com/email/java/com.aspose.email/imapmessageflags/#isRead--)
- [Recent](https://reference.aspose.com/email/java/com.aspose.email/imapmessageflags/#getRecent--)
 
### **Настройка флагов сообщений**

В следующем фрагменте кода показано, как изменить флаги сообщений на сервере IMAP с помощью Aspose.Email.

~~~Java
// For complete examples and data files, please go to https://github.com/aspose-email/Aspose.Email-for-Java
// Mark the message as read
client.changeMessageFlags(1, ImapMessageFlags.isRead());
~~~

### **Удаление флагов сообщений**

Флаги сообщений также можно удалить с помощью [removeMessageFlags()](https://reference.aspose.com/email/java/com.aspose.email/imapclient/#removeMessageFlags-com.aspose.email.IConnection-int-com.aspose.email.ImapMessageFlags-) метод. Использование аналогично использованию [changeMessageFlags()](https://reference.aspose.com/email/java/com.aspose.email/imapclient/#changeMessageFlags-com.aspose.email.IConnection-int-com.aspose.email.ImapMessageFlags-) метод. Он принимает порядковый номер или уникальный идентификатор сообщения и [MessageFlag](https://reference.aspose.com/email/java/com.aspose.email/imapmessageflags/). В следующем фрагменте кода показано, как удалить флаги сообщений.

~~~Java
// For complete examples and data files, please go to https://github.com/aspose-email/Aspose.Email-for-Java
// Remove the message flag
client.removeMessageFlags(1, ImapMessageFlags.isRead());
~~~

## **Настройка собственных флагов**

Вы также можете установить собственные флаги для сообщения, используя [ImapClient](https://reference.aspose.com/email/java/com.aspose.email/imapclient/) API. Клиент IMAP [AddMessageFlags](https://reference.aspose.com/email/java/com.aspose.email/imapclient/#addMessageFlags-com.aspose.email.IConnection-int-com.aspose.email.ImapMessageFlags-) предоставляет возможность устанавливать собственные флаги в сообщениях.

~~~Java
// For complete examples and data files, please go to https://github.com/aspose-email/Aspose.Email-for-Java
// Create a message
MailMessage message = new MailMessage("user@domain1.com", "user@domain2.com", "subject", "message");

// Append the message to mailbox
String uid = client.appendMessage(ImapFolderInfo.IN_BOX, message);

// Add custom flags to the added messge
client.addMessageFlags(uid, com.aspose.email.ImapMessageFlags.op_BitwiseOr(ImapMessageFlags.keyword("custom1"), ImapMessageFlags.keyword("custom1_0")));

// Retreive the messages for checking the presence of custom flag
client.selectFolder(ImapFolderInfo.IN_BOX);

ImapMessageInfoCollection messageInfos = client.listMessages();
for (ImapMessageInfo inf : messageInfos) {
    ImapMessageFlags[] flags = inf.getFlags().split();

    if (inf.containsKeyword("custom1"))
        System.out.println("Keyword found");
}
~~~
