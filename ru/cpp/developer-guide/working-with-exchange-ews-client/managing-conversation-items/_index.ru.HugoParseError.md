---
title: Управление элементами беседы
type: docs
weight: 40
url: /cpp/managing-conversation-items/
---

Aspose.Email можно использовать для управления элементами беседы на Exchange Server с помощью класса [EWSClient](https://apireference.aspose.com/email/cpp/class/aspose.email.clients.exchange.web_service.e_w_s_client). Этот класс использует Exchange Web Services, которые доступны только в Exchange Server 2007 и более поздних версиях. В этой статье показано, как найти, скопировать, переместить и удалить элементы беседы на Exchange Server 2010. Для всех функций, включенных в этот раздел, требуется Microsoft Exchange Server 2010 Service Pack 1.
##  **Поиск бесед**
Чтобы получить информацию о беседе из определенной папки на Exchange Server:

1. Подключитесь к Exchange Server с помощью класса [IEWSClient](https://apireference.aspose.com/email/cpp/class/aspose.email.clients.exchange.web_service.i_e_w_s_client).
1. Вызовите метод [FindConversations()](https://apireference.aspose.com/email/cpp/class/aspose.email.clients.exchange.web_service.i_e_w_s_client), чтобы найти все элементы беседы в папке.
1. Отобразите свойства элемента беседы, такие как ID, тема беседы и статус флага.

Следующий фрагмент кода показывает, как найти беседы.

{{< gist "aspose-com-gists" "525dd06c8783ebb18fb75cfc4b31d1ef" "Examples-Cpp-source-Exchange_EWS-FindConversationsOnExchangeServer-FindConversationsOnExchangeServer.cpp" >}}
##  **Копирование бесед**
Чтобы скопировать беседы из одной папки в другую:

1. Подключитесь к Exchange Server с помощью класса [IEWSClient](https://apireference.aspose.com/email/cpp/class/aspose.email.clients.exchange.web_service.i_e_w_s_client).
1. Вызовите метод [CopyConversationItems()](https://apireference.aspose.com/email/cpp/class/aspose.email.clients.exchange.web_service.i_e_w_s_client), чтобы скопировать элемент беседы из исходной папки в папку назначения.

Следующий фрагмент кода показывает, как копировать беседы.

{{< gist "aspose-com-gists" "525dd06c8783ebb18fb75cfc4b31d1ef" "Examples-Cpp-source-Exchange_EWS-CopyConversations-CopyConversations.cpp" >}}
##  **Перемещение бесед**
Чтобы переместить беседы из одной папки в другую:

1. Подключитесь к Exchange Server с помощью класса [IEWSClient](https://apireference.aspose.com/email/cpp/class/aspose.email.clients.exchange.web_service.i_e_w_s_client).
1. Вызовите метод [MoveConversationItems()](https://apireference.aspose.com/email/cpp/class/aspose.email.clients.exchange.web_service.i_e_w_s_client), чтобы переместить беседу из исходной папки в папку назначения.

Следующий фрагмент кода показывает, как перемещать беседы.

{{< gist "aspose-com-gists" "525dd06c8783ebb18fb75cfc4b31d1ef" "Examples-Cpp-source-Exchange_EWS-MoveConversations-MoveConversations.cpp" >}}
##  **Удаление бесед**
Чтобы удалить беседы из папки:

1. Подключитесь к Exchange Server с помощью класса [IEWSClient](https://apireference.aspose.com/email/cpp/class/aspose.email.clients.exchange.web_service.i_e_w_s_client).
1. Вызовите метод [DeleteConversationItems()](https://apireference.aspose.com/email/cpp/class/aspose.email.clients.exchange.web_service.i_e_w_s_client), чтобы удалить элемент беседы из исходной папки.

Следующий фрагмент кода показывает, как удалять беседы.

{{< gist "aspose-com-gists" "525dd06c8783ebb18fb75cfc4b31d1ef" "Examples-Cpp-source-Exchange_EWS-DeleteConversations-DeleteConversations.cpp" >}}