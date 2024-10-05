---
title: "Работа с Правилами на Exchange Server"
url: /ru/cpp/working-with-rules-on-exchange-server/
weight: 90
type: docs
---

## **Управление Правилами**
Aspose.Email можно использовать для управления правилами на Exchange Server с помощью класса [EWSClient](https://apireference.aspose.com/cpp/email/class/aspose.email.clients.exchange.web_service.e_w_s_client/). Этот класс использует Exchange Web Services (EWS), которые доступны в Exchange Server 2007 и более поздних версиях. Чтобы показать, как управлять правилами, в этой статье объясняется, как:

- Прочитать правила, уже находящиеся на сервере.
- Создать новое правило.
- Обновить существующее правило.

Для всех функций, описанных в этой статье, требуется Microsoft Exchange Server 2010 Service Pack 1.
### **Чтение Правил**
Чтобы получить все правила из Exchange Server:

1. Подключитесь к Exchange Server, используя класс [IEWSClient](https://apireference.aspose.com/cpp/email/class/aspose.email.clients.exchange.web_service.i_e_w_s_client/).
1. Вызовите метод [IEWSClient->GetInboxRules()](https://apireference.aspose.com/cpp/email/class/aspose.email.clients.exchange.web_service.i_e_w_s_client/#ad8b80596b53806955cdc326b3cd23ebb) для получения всех правил.
1. В цикле просмотрите все правила и отобразите свойства правила, такие как условия, действия и имена.

Следующий фрагмент кода показывает, как читать правила.



{{< gist "aspose-com-gists" "525dd06c8783ebb18fb75cfc4b31d1ef" "Examples-Cpp-source-Exchange_EWS-ExchangeServerReadRules-ExchangeServerReadRules.cpp" >}}
### **Создание Нового Правила**
Чтобы создать новое правило на Exchange Server, выполните следующие шаги:

1. Подключитесь к Exchange Server, используя класс [IEWSClient](https://apireference.aspose.com/cpp/email/class/aspose.email.clients.exchange.web_service.i_e_w_s_client/).
1. Создайте новый экземпляр класса *InboxRule* и задайте следующие обязательные свойства:
   1. DisplayName
   1. Условия
   1. Действия
1. Вызовите метод [IEWSClient->CreateInboxRule()](https://apireference.aspose.com/cpp/email/class/aspose.email.clients.exchange.web_service.i_e_w_s_client/#a7af390adad4a0248d17b11bbebe8e97f) для создания правила.

Следующий фрагмент кода показывает, как создать новое правило.



{{< gist "aspose-com-gists" "525dd06c8783ebb18fb75cfc4b31d1ef" "Examples-Cpp-source-Exchange_EWS-CreateNewRuleOntheExchangeServer-CreateNewRuleOntheExchangeServer.cpp" >}}
### **Обновление Правила**
Чтобы обновить правило на Exchange Server:

1. Подключитесь к Exchange Server, используя класс [IEWSClient](https://apireference.aspose.com/cpp/email/class/aspose.email.clients.exchange.web_service.i_e_w_s_client/).
1. Вызовите метод [IEWSClient->GetInboxRules()](https://apireference.aspose.com/cpp/email/class/aspose.email.clients.exchange.web_service.i_e_w_s_client/#ad8b80596b53806955cdc326b3cd23ebb) для получения всех правил.
1. В цикле просмотрите все правила и получите правило, которое вы хотите изменить, сопоставив *DisplayName* в условии.
1. Обновите свойства правила
1. Вызовите метод [IEWSClient.UpdateInboxRule()](https://apireference.aspose.com/cpp/email/class/aspose.email.clients.exchange.web_service.i_e_w_s_client/#a077ef824948d486b7633ee9f3f61e863) для обновления правила.

Следующий фрагмент кода показывает, как обновить правило.



{{< gist "aspose-com-gists" "525dd06c8783ebb18fb75cfc4b31d1ef" "Examples-Cpp-source-Exchange_EWS-UpdateRuleOntheExchangeServer-UpdateRuleOntheExchangeServer.cpp" >}}