---
title: Управление элементами беседы
type: docs
weight: 40
url: /net/managing-conversation-items/
---


Aspose.Email для .NET может использоваться для управления элементами беседы на Exchange Server с помощью класса [EWSClient](https://reference.aspose.com/email/net/aspose.email.clients.exchange.webservice/ewsclient/). Этот класс использует веб-службы Exchange, которые доступны только в Exchange Server 2007 и более поздних версиях. Эта статья показывает, как [найти](#finding-conversations), [скопировать](#copying-conversations), [переместить](#moving-conversations) и [удалить](#deleting-conversations) элементы беседы на Exchange Server 2010. Для всех функций, включенных в этот раздел, требуется Microsoft Exchange Server 2010 Service Pack 1.

## **Нахождение бесед**

Чтобы получить информацию о беседе из конкретной папки на Exchange Server:

1. Подключитесь к Exchange Server, используя интерфейс [IEWSClient](https://reference.aspose.com/email/net/aspose.email.clients.exchange.webservice/iewsclient/).
1. Вызовите метод [IEWSClient.FindConversations()](https://reference.aspose.com/email/net/aspose.email.clients.exchange.webservice/iewsclient/findconversations/#findconversations), чтобы найти все элементы беседы из папки.
1. Отобразите свойства элемента беседы, такие как ID, тема беседы и статус флага.

Следующий фрагмент кода показывает, как находить беседы.

{{< gist "aspose-com-gists" "6e5185a63aec6fd70d83098e82b06a32" "Examples-CSharp-Exchange_EWS-FindConversationsOnExchangeServer-FindConversationsOnExchangeServer.cs" >}}

## **Копирование бесед**

Чтобы скопировать беседы из одной папки в другую:

1. Подключитесь к Exchange Server, используя интерфейс [IEWSClient](https://reference.aspose.com/email/net/aspose.email.clients.exchange.webservice/iewsclient/).
1. Вызовите метод [IEWSClient.CopyConversationItems()](https://reference.aspose.com/email/net/aspose.email.clients.exchange.webservice/iewsclient/copyconversationitems/#copyconversationitems), чтобы скопировать элемент беседы из исходной папки в папку назначения.

Следующий фрагмент кода показывает, как копировать беседы.

{{< gist "aspose-com-gists" "6e5185a63aec6fd70d83098e82b06a32" "Examples-CSharp-Exchange_EWS-CopyConversations-CopyConversations.cs" >}}

## **Перемещение бесед**

Чтобы переместить беседы из одной папки в другую:

1. Подключитесь к Exchange Server, используя интерфейс [IEWSClient](https://reference.aspose.com/email/net/aspose.email.clients.exchange.webservice/iewsclient/).
1. Вызовите метод [IEWSClient.MoveConversationItems()](https://reference.aspose.com/email/net/aspose.email.clients.exchange.webservice/iewsclient/moveconversationitems/#moveconversationitems), чтобы переместить беседу из исходной папки в папку назначения.

Следующий фрагмент кода показывает, как перемещать беседы.

{{< gist "aspose-com-gists" "6e5185a63aec6fd70d83098e82b06a32" "Examples-CSharp-Exchange_EWS-MoveConversations-MoveConversations.cs" >}}

## **Удаление бесед**

Чтобы удалить беседы из папки:

1. Подключитесь к Exchange Server, используя интерфейс [IEWSClient](https://reference.aspose.com/email/net/aspose.email.clients.exchange.webservice/iewsclient/).
1. Вызовите метод [IEWSClient.DeleteConversationItems()](https://reference.aspose.com/email/net/aspose.email.clients.exchange.webservice/iewsclient/deleteconversationitems/#deleteconversationitems), чтобы удалить элемент беседы из исходной папки.

Следующий фрагмент кода показывает, как удалять беседы.

{{< gist "aspose-com-gists" "6e5185a63aec6fd70d83098e82b06a32" "Examples-CSharp-Exchange_EWS-DeleteConversations-DeleteConversations.cs" >}}