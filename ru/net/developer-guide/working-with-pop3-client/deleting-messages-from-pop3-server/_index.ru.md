---
title: "Удаление сообщений с сервера POP3"
url: /ru/net/deleting-messages-from-pop3-server/
weight: 20
type: docs
---


Aspose.Email — это надежный компонент, который позволяет выполнять настраиваемые операции после определенных действий. Aspose.Email поддерживает множество событий, с которыми пользователи могут выполнять операции. Эта функция предоставляет пользователям больший контроль над своим приложением. Например, пользователи могут выполнять желаемые действия в следующих случаях:

- Все массовые электронные письма отправлены.
- Сообщение скоро будет отправлено.
- Электронное письмо полностью отправлено.
- Когда SMTP-сервер отклоняет получателя.

Почтовые ящики POP3 находятся на сервере POP3. Электронную почту из этих почтовых ящиков можно загрузить на компьютер с помощью [Pop3Client](https://reference.aspose.com/email/net/aspose.email.clients.pop3/pop3client/). [Pop3Client](https://reference.aspose.com/email/net/aspose.email.clients.pop3/pop3client/) класс использует протокол POP3 для копирования почтовых сообщений из почтового ящика POP3 на компьютер. После получения почты вам не нужно подключаться к Интернету во время ее чтения, так как вы можете прочитать полученную почту на своем ПК. Если вам не нужна или вы не хотите хранить копию некоторых почтовых сообщений на сервере POP3, удалите ее. В этом разделе показано, как удалять электронные письма с помощью [Pop3Client](https://reference.aspose.com/email/net/aspose.email.clients.pop3/pop3client/) class.

## **Удалить электронное письмо по индексу**

Следующий фрагмент кода удаляет все почтовые сообщения почтового ящика одно за другим на основе его индекса. Индекс ни в коем случае не должен быть меньше 0 дюймов [Pop3Client.DeleteMessage](https://reference.aspose.com/email/net/aspose.email.clients.pop3/pop3client/deletemessage/#deletemessage/).

{{< gist "aspose-com-gists" "6e5185a63aec6fd70d83098e82b06a32" "Examples-CSharp-POP3-DeleteEmailByIndex-DeleteEmailByIndex.cs" >}}

## **Удалить все электронные письма**

Мы также можем позвонить [Pop3Client.DeleteMessages](https://reference.aspose.com/email/net/aspose.email.clients.pop3/pop3client/deletemessage/#deletemessage/) чтобы удалить все сообщения. В следующем фрагменте кода показано, как удалить все электронные письма.

```cs
// Delete all the messages
client.DeleteMessages();
```

Если соединение с сервером POP3 разорвано сразу после операций удаления, вы больше не сможете вызывать функцию Отменить удаление для выполнения необходимых действий.

## **Отменить удаление**

[Pop3Client.UndeleteMessages](https://reference.aspose.com/email/net/aspose.email.clients.pop3/pop3client/undeletemessages/#undeletemessages/) может использоваться для отмены удаления сообщений электронной почты. В следующем фрагменте кода показано, как отменить удаления.

```cs
// Cancel deletes
client.UndeleteMessages();
```
