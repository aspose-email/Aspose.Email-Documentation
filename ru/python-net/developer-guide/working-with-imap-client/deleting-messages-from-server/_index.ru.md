---
title: "Удаление сообщений с сервера"
url: /ru/python-net/deleting-messages-from-server/
weight: 20
type: docs
---


## **Удаление сообщений**
Класс ImapClient может удалять сообщения с IMAP-сервера. Функция DeleteMessage() класса ImapClient используется для удаления сообщений. Она принимает номер последовательности сообщения или уникальный идентификатор в качестве параметра. ImapClient предоставляет методы DeleteMessage и DeleteMessages для удаления сообщений по одному или несколькими. Следующий фрагмент кода показывает, как удалить сообщение электронной почты с идентификатором сообщения 1 с IMAP-сервера.



{{< gist "aspose-email" "356f0e128b9d45a7ee779fc813eb87e5" "Examples-IMAP-DeleteSingleMessage-DeleteSingleMessage.py" >}}
## **Удаление нескольких сообщений**
Несколько электронных писем можно удалить из почтового ящика с помощью ImapClient API Aspose.Email. Метод DeleteMessages предоставляет несколько вариантов для удаления нескольких сообщений с сервера, используя уникальные идентификаторы, номера последовательности или элементы ImapMessageInfoCollection. Следующий фрагмент кода показывает, как удалить несколько сообщений.



{{< gist "aspose-email" "356f0e128b9d45a7ee779fc813eb87e5" "Examples-IMAP-DeleteMultipleMessages-DeleteMultipleMessages.py" >}}