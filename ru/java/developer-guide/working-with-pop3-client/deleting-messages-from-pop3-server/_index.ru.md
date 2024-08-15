---
title: "Удаление сообщений с сервера POP3"
url: /ru/java/deleting-messages-from-pop3-server/
weight: 20
type: docs
---


Aspose.Email — это надежный компонент, который позволяет выполнять настраиваемые операции после определенных действий. Aspose.Email запускает множество событий, с которыми пользователи могут выполнять операции. Эта функция предоставляет пользователям больший контроль над своим приложением. Например, пользователи могут выполнять желаемые действия в следующих случаях:

- Все массовые электронные письма отправлены.
- Сообщение скоро будет отправлено.
- Электронное письмо полностью отправлено.
- Когда SMTP-сервер отклоняет получателя.

Почтовые ящики POP3 находятся на сервере POP3. Электронную почту из этих почтовых ящиков можно загрузить на компьютер с помощью [Pop3Client](https://reference.aspose.com/email/java/com.aspose.email/pop3client/). [Pop3Client](https://reference.aspose.com/email/java/com.aspose.email/pop3client/) класс использует протокол POP3 для копирования почтовых сообщений из почтового ящика POP3 на компьютер. После получения почты вам не нужно подключаться к Интернету во время ее чтения, так как вы можете прочитать полученную почту на своем ПК. Если вам не нужна или вы не хотите хранить копию некоторых почтовых сообщений на сервере POP3, удалите ее. В этом разделе показано, как удалять электронные письма с помощью [Pop3Client](https://reference.aspose.com/email/java/com.aspose.email/pop3client/) class.

## **Удалить электронное письмо по индексу**

Следующий фрагмент кода удаляет все почтовые сообщения почтового ящика одно за другим на основе его индекса. Индекс ни в коем случае не должен быть меньше 0 дюймов [Pop3Client.deleteMessage](https://reference.aspose.com/email/java/com.aspose.email/pop3client/#deleteMessage-int-).

~~~Java
// For complete examples and data files, please go to https://github.com/aspose-email/Aspose.Email-for-Java

// Create a POP3 client
Pop3Client client = new Pop3Client("mail.aspose.com", 110, "username", "psw");
try {
    // Delete all the message one by one
    int messageCount = client.getMessageCount();
    for (int i = 1; i <= messageCount; i++) {
        client.deleteMessage(i);
    }
} catch (Exception ex) {
    System.out.println(ex.getMessage());
}
~~~

## **Удалить все электронные письма**

Мы также можем позвонить [Pop3Client.deleteMessages](https://reference.aspose.com/email/java/com.aspose.email/pop3client/#undeleteMessages--) чтобы удалить все сообщения. В следующем фрагменте кода показано, как удалить все электронные письма.

~~~Java
// For complete examples and data files, please go to https://github.com/aspose-email/Aspose.Email-for-Java

// Delete all the messages
client.deleteMessages();
~~~

Если соединение с сервером POP3 разорвано сразу после операций удаления, вы больше не сможете звонить [Pop3Client](https://reference.aspose.com/email/java/com.aspose.email/pop3client/).cancelDeletes (), чтобы делать то, что вы хотите.

## **Отменить удаление**

[Pop3Client.undeleteMessages](https://reference.aspose.com/email/java/com.aspose.email/pop3client/#undeleteMessages--) может использоваться для отмены удаления сообщений электронной почты. В следующем фрагменте кода показано, как отменить удаления.

~~~Java
// For complete examples and data files, please go to https://github.com/aspose-email/Aspose.Email-for-Java

// Cancel deletes
client.undeleteMessages();
~~~
