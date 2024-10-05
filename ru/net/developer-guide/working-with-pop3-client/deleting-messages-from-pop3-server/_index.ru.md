---
title: "Удаление сообщений с сервера POP3"
url: /ru/net/deleting-messages-from-pop3-server/
weight: 20
type: docs
---


Aspose.Email является мощным компонентом, который позволяет выполнять пользовательские операции после определенных действий. Aspose.Email поддерживает множество событий, при которых пользователи могут выполнять операции. Эта функция предоставляет пользователям больший контроль над их приложением. Например, пользователи могут выполнять желаемые действия, когда:

- Все массовые письма отправлены.
- Сообщение собирается отправить.
- Электронное письмо полностью отправлено.
- Когда получатель был отклонен SMTP сервером.

POP3 почтовые ящики находятся на POP3 сервере. Письма в этих ящиках можно получить на ваш ПК с помощью [Pop3Client](https://reference.aspose.com/email/net/aspose.email.clients.pop3/pop3client/). Класс [Pop3Client](https://reference.aspose.com/email/net/aspose.email.clients.pop3/pop3client/) использует протокол POP3 для копирования почтовых сообщений из вашего POP3 почтового ящика на ваш ПК. Как только почта была получена, вам не нужно быть подключенным к интернету во время ее чтения, так как вы можете читать полученные письма на вашем ПК. Если вам не нужна или не хотите копию некоторых почтовых сообщений, остающихся на POP3 сервере, вы можете их удалить. Этот раздел показывает, как удалить электронные письма, используя класс [Pop3Client](https://reference.aspose.com/email/net/aspose.email.clients.pop3/pop3client/).

## **Удалить электронное письмо по индексу**

Следующий код удаляет все почтовые сообщения почтового ящика по одному, основываясь на его индексе. Индекс никогда не должен быть <=0 в [Pop3Client.DeleteMessage](https://reference.aspose.com/email/net/aspose.email.clients.pop3/pop3client/deletemessage/#deletemessage/).

{{< gist "aspose-com-gists" "6e5185a63aec6fd70d83098e82b06a32" "Examples-CSharp-POP3-DeleteEmailByIndex-DeleteEmailByIndex.cs" >}}

## **Удалить все электронные письма**

Мы также можем вызвать [Pop3Client.DeleteMessages](https://reference.aspose.com/email/net/aspose.email.clients.pop3/pop3client/deletemessage/#deletemessage/), чтобы удалить все сообщения. Следующий код показывает, как удалить все электронные письма.

```cs
// Удалить все сообщения
client.DeleteMessages();
```

Если связь с сервером POP3 прервалась сразу после удаления, вы больше не сможете вызвать Cancel Deletes для выполнения желаемых действий.

## **Отменить удаления**

[Pop3Client.UndeleteMessages](https://reference.aspose.com/email/net/aspose.email.clients.pop3/pop3client/undeletemessages/#undeletemessages/) может быть использован для отмены удаления электронных сообщений. Следующий код показывает, как отменить удаления.

```cs
// Отменить удаления
client.UndeleteMessages();
```