---
title: "Управление элементами беседы"
url: /ru/cpp/managing-conversation-items/
weight: 40
type: docs
---

Aspose.Email можно использовать для управления элементами беседы на сервере Exchange с помощью [EWSClient](https://apireference.aspose.com/email/cpp/class/aspose.email.clients.exchange.web_service.e_w_s_client) класс. В этом классе используются веб-службы Exchange, доступные только в Exchange Server 2007 и более поздних версиях. В этой статье показано, как находить, копировать, перемещать и удалять элементы беседы в Exchange Server 2010. Для всех функций, описанных в этом разделе, требуется пакет обновления 1 для Microsoft Exchange Server 2010.
##  **Поиск разговоров**
Чтобы получить информацию о разговоре из определенной папки на сервере Exchange, выполните следующие действия:

1. Подключитесь к серверу Exchange с помощью [IEWSClient](https://apireference.aspose.com/email/cpp/class/aspose.email.clients.exchange.web_service.i_e_w_s_client) class.
1. Позвоните [FindConversations()](https://apireference.aspose.com/email/cpp/class/aspose.email.clients.exchange.web_service.i_e_w_s_client) метод поиска всех элементов беседы в папке.
1. Отобразите свойства элемента беседы, такие как идентификатор, тема разговора и статус флага.

В следующем фрагменте кода показано, как найти разговоры.



{{< gist "aspose-com-gists" "525dd06c8783ebb18fb75cfc4b31d1ef" "Examples-Cpp-source-Exchange_EWS-FindConversationsOnExchangeServer-FindConversationsOnExchangeServer.cpp" >}}
##  **Копирование разговоров**
Чтобы скопировать разговоры из одной папки в другую, выполните следующие действия:

1. Подключитесь к серверу Exchange с помощью [IEWSClient](https://apireference.aspose.com/email/cpp/class/aspose.email.clients.exchange.web_service.i_e_w_s_client) class.
1. Позвоните [CopyConversationItems()](https://apireference.aspose.com/email/cpp/class/aspose.email.clients.exchange.web_service.i_e_w_s_client) метод копирования элемента беседы из исходной папки в папку назначения.

В следующем фрагменте кода показано, как копировать разговоры.



{{< gist "aspose-com-gists" "525dd06c8783ebb18fb75cfc4b31d1ef" "Examples-Cpp-source-Exchange_EWS-CopyConversations-CopyConversations.cpp" >}}
##  **Трогательные разговоры**
Чтобы перенести беседы из одной папки в другую, выполните следующие действия:

1. Подключитесь к серверу Exchange с помощью [IEWSClient](https://apireference.aspose.com/email/cpp/class/aspose.email.clients.exchange.web_service.i_e_w_s_client) class.
1. Позвоните [MoveConversationItems()](https://apireference.aspose.com/email/cpp/class/aspose.email.clients.exchange.web_service.i_e_w_s_client) метод перемещения беседы из исходной папки в папку назначения.

В следующем фрагменте кода показано, как перемещать разговоры.



{{< gist "aspose-com-gists" "525dd06c8783ebb18fb75cfc4b31d1ef" "Examples-Cpp-source-Exchange_EWS-MoveConversations-MoveConversations.cpp" >}}
##  **Удаление разговоров**
Чтобы удалить разговоры из папки, выполните следующие действия:

1. Подключитесь к серверу Exchange с помощью [IEWSClient](https://apireference.aspose.com/email/cpp/class/aspose.email.clients.exchange.web_service.i_e_w_s_client) class.
1. Позвоните [DeleteConversationItems()](https://apireference.aspose.com/email/cpp/class/aspose.email.clients.exchange.web_service.i_e_w_s_client) метод удаления элемента беседы из исходной папки.

В следующем фрагменте кода показано, как удалять разговоры.



{{< gist "aspose-com-gists" "525dd06c8783ebb18fb75cfc4b31d1ef" "Examples-Cpp-source-Exchange_EWS-DeleteConversations-DeleteConversations.cpp" >}}
