---
title: "Управление элементами беседы"
url: /ru/net/managing-conversation-items/
weight: 40
type: docs
---


Aspose.Email for .NET можно использовать для управления элементами беседы на сервере Exchange с помощью [EWSClient](https://reference.aspose.com/email/net/aspose.email.clients.exchange.webservice/ewsclient/) класс. В этом классе используются веб-службы Exchange, доступные только в Exchange Server 2007 и более поздних версиях. В этой статье показано, как [find](#finding-conversations), [copy](#copying-conversations), [move](#moving-conversations) and [delete](#deleting-conversations) элементы беседы на сервере Exchange 2010. Для всех функций, описанных в этом разделе, требуется пакет обновления 1 для Microsoft Exchange Server 2010.

## **Поиск разговоров**

Чтобы получить информацию о разговоре из определенной папки на сервере Exchange, выполните следующие действия:

1. Подключитесь к серверу Exchange с помощью [IEWSClient](https://reference.aspose.com/email/net/aspose.email.clients.exchange.webservice/iewsclient/) interface.
1. Позвоните [IEWSClient.FindConversations()](https://reference.aspose.com/email/net/aspose.email.clients.exchange.webservice/iewsclient/findconversations/#findconversations) метод поиска всех элементов беседы в папке.
1. Отобразите свойства элемента беседы, такие как идентификатор, тема разговора и статус флага.

В следующем фрагменте кода показано, как найти разговоры.

{{< gist "aspose-com-gists" "6e5185a63aec6fd70d83098e82b06a32" "Examples-CSharp-Exchange_EWS-FindConversationsOnExchangeServer-FindConversationsOnExchangeServer.cs" >}}

## **Копирование разговоров**

Чтобы скопировать разговоры из одной папки в другую, выполните следующие действия:

1. Подключитесь к серверу Exchange с помощью [IEWSClient](https://reference.aspose.com/email/net/aspose.email.clients.exchange.webservice/iewsclient/) interface.
1. Позвоните [IEWSClient.CopyConversationItems()](https://reference.aspose.com/email/net/aspose.email.clients.exchange.webservice/iewsclient/copyconversationitems/#copyconversationitems) метод копирования элемента беседы из исходной папки в папку назначения.

В следующем фрагменте кода показано, как копировать разговоры.

{{< gist "aspose-com-gists" "6e5185a63aec6fd70d83098e82b06a32" "Examples-CSharp-Exchange_EWS-CopyConversations-CopyConversations.cs" >}}

## **Трогательные разговоры**

Чтобы перенести беседы из одной папки в другую, выполните следующие действия:

1. Подключитесь к серверу Exchange с помощью [IEWSClient](https://reference.aspose.com/email/net/aspose.email.clients.exchange.webservice/iewsclient/) interface.
1. Позвоните [IEWSClient.MoveConversationItems()](https://reference.aspose.com/email/net/aspose.email.clients.exchange.webservice/iewsclient/moveconversationitems/#moveconversationitems) метод перемещения беседы из исходной папки в папку назначения.

В следующем фрагменте кода показано, как перемещать разговоры.

{{< gist "aspose-com-gists" "6e5185a63aec6fd70d83098e82b06a32" "Examples-CSharp-Exchange_EWS-MoveConversations-MoveConversations.cs" >}}

## **Удаление разговоров**

Чтобы удалить разговоры из папки, выполните следующие действия:

1. Подключитесь к серверу Exchange с помощью [IEWSClient](https://reference.aspose.com/email/net/aspose.email.clients.exchange.webservice/iewsclient/) interface.
1. Позвоните [IEWSClient.DeleteConversationItems()](https://reference.aspose.com/email/net/aspose.email.clients.exchange.webservice/iewsclient/deleteconversationitems/#deleteconversationitems) метод удаления элемента беседы из исходной папки.

В следующем фрагменте кода показано, как удалять разговоры.

{{< gist "aspose-com-gists" "6e5185a63aec6fd70d83098e82b06a32" "Examples-CSharp-Exchange_EWS-DeleteConversations-DeleteConversations.cs" >}}
