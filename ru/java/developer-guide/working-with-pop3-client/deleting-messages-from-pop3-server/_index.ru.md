---
title: "Удаление сообщений с POP3 сервера"
url: /ru/java/deleting-messages-from-pop3-server/
weight: 20
type: docs
---

Aspose.Email — это мощный компонент, который позволяет выполнять настраиваемые операции после определенных действий. Aspose.Email генерирует множество событий, по которым пользователи могут выполнять операции. Эта функция дает пользователям больший контроль над своим приложением. Например, пользователи могут выполнять желаемые действия, когда:

- Все массовые электронные письма были отправлены.
- Сообщение готовится к отправке.
- Электронное письмо полностью отправлено.
- Когда получатель был отклонен SMTP сервером.

POP3 почтовые ящики находятся на POP3 сервере. Электронные письма в этих почтовых ящиках могут быть извлечены на ваш ПК с помощью [Pop3Client](https://reference.aspose.com/email/java/com.aspose.email/pop3client/). Класс [Pop3Client](https://reference.aspose.com/email/java/com.aspose.email/pop3client/) использует протокол POP3 для копирования почтовых сообщений из вашего POP3 почтового ящика на ваш ПК. После того, как почта была извлечена, вам не нужно быть подключенным к интернету, пока вы её читаете, так как вы можете читать извлечённые письма на своем ПК. Если вам не нужна или не хотите, чтобы некоторые почтовые сообщения хранились на POP3 сервере, вы можете их удалить. В этом разделе показано, как удалить электронные письма с помощью класса [Pop3Client](https://reference.aspose.com/email/java/com.aspose.email/pop3client/).

## **Удаление электронного письма по индексу**

Следующий код удаляет все почтовые сообщения почтового ящика одно за другим, основываясь на их индексе. Индекс никогда не должен быть <=0 в [Pop3Client.deleteMessage](https://reference.aspose.com/email/java/com.aspose.email/pop3client/#deleteMessage-int-).

~~~Java
// For complete examples and data files, please go to https://github.com/aspose-email/Aspose.Email-for-Java

// Создание POP3 клиента
Pop3Client client = new Pop3Client("mail.aspose.com", 110, "username", "psw");
try {
    // Удаление всех сообщений одно за другим
    int messageCount = client.getMessageCount();
    for (int i = 1; i <= messageCount; i++) {
        client.deleteMessage(i);
    }
} catch (Exception ex) {
    System.out.println(ex.getMessage());
}
~~~

## **Удаление всех электронных писем**

Мы также можем вызвать [Pop3Client.deleteMessages](https://reference.aspose.com/email/java/com.aspose.email/pop3client/#undeleteMessages--) для удаления всех сообщений. Следующий код показывает, как удалить все электронные письма.

~~~Java
// For complete examples and data files, please go to https://github.com/aspose-email/Aspose.Email-for-Java

// Удаление всех сообщений
client.deleteMessages();
~~~

Если соединение с POP3 сервером разорвано сразу после операций удаления, вы больше не сможете вызывать [Pop3Client](https://reference.aspose.com/email/java/com.aspose.email/pop3client/).cancelDeletes(), чтобы выполнить желаемые действия.

## **Отмена удаления**

[Pop3Client.undeleteMessages](https://reference.aspose.com/email/java/com.aspose.email/pop3client/#undeleteMessages--) может быть использован для отмены удаления электронных сообщений. Следующий код показывает, как отменить удаления.

~~~Java
// For complete examples and data files, please go to https://github.com/aspose-email/Aspose.Email-for-Java

// Отмена удаления
client.undeleteMessages();
~~~