---
title: "Удаление сообщений с сервера"
url: /ru/python-net/deleting-messages-from-server/
weight: 20
type: docs
---


## **Удаление сообщений**
Класс IMAPClient может удалять сообщения с сервера IMAP. Функция DeleteMessage () класса IMapClient используется для удаления сообщений. В качестве параметра она принимает порядковый номер сообщения или уникальный идентификатор. IMapClient предоставляет методы DeleteMessage и DeleteMessages для удаления сообщений по одному или по нескольким. В следующем фрагменте кода показано, как удалить сообщение электронной почты с идентификатором сообщения 1 с сервера IMAP.



{{< gist "aspose-email" "356f0e128b9d45a7ee779fc813eb87e5" "Examples-IMAP-DeleteSingleMessage-DeleteSingleMessage.py" >}}
## **Удаление нескольких сообщений**
Несколько писем можно удалить из почтового ящика с помощью IMapClient или Aspose.Email API. Метод DeleteMessages предоставляет ряд вариантов удаления нескольких сообщений с сервера с использованием уникальных идентификаторов, порядковых номеров или элементов IMapMessageInfoCollection. В следующем фрагменте кода показано, как удалить несколько сообщений.



{{< gist "aspose-email" "356f0e128b9d45a7ee779fc813eb87e5" "Examples-IMAP-DeleteMultipleMessages-DeleteMultipleMessages.py" >}}
