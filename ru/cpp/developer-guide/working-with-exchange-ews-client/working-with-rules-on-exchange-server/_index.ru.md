---
title: "Работа с правилами на сервере Exchange"
url: /ru/cpp/working-with-rules-on-exchange-server/
weight: 90
type: docs
---

## **Управление правилами**
Aspose.Email можно использовать для управления правилами на сервере Exchange с помощью [EWSClient](https://apireference.aspose.com/cpp/email/class/aspose.email.clients.exchange.web_service.e_w_s_client/) класс. В этом классе используются веб-службы Exchange (EWS), доступные в Exchange Server 2007 и более поздних версиях. Чтобы показать, как управлять правилами, в этой статье объясняется, как:

- Ознакомьтесь с правилами, уже имеющимися на сервере.
- Создайте новое правило.
- Обновите существующее правило.

Для всех функций, описанных в этой статье, требуется пакет обновления 1 для Microsoft Exchange Server 2010.
### **Ознакомьтесь с правилами**
Чтобы получить все правила с сервера Exchange, выполните следующие действия:

1. Подключитесь к серверу Exchange с помощью [IEWSClient](https://apireference.aspose.com/cpp/email/class/aspose.email.clients.exchange.web_service.i_e_w_s_client/) class.
1. Позвоните [IEWSClient->GetInboxRules()](https://apireference.aspose.com/cpp/email/class/aspose.email.clients.exchange.web_service.i_e_w_s_client/#ad8b80596b53806955cdc326b3cd23ebb) метод получения всех правил.
1. По очереди просматривайте все правила и отображайте свойства правила, такие как условия, действия и имена.

В следующем фрагменте кода показано, как читать правила.



{{< gist "aspose-com-gists" "525dd06c8783ebb18fb75cfc4b31d1ef" "Examples-Cpp-source-Exchange_EWS-ExchangeServerReadRules-ExchangeServerReadRules.cpp" >}}
### **Создание нового правила**
Чтобы создать новое правило на сервере Exchange, выполните следующие шаги:

1. Подключитесь к серверу Exchange с помощью [IEWSClient](https://apireference.aspose.com/cpp/email/class/aspose.email.clients.exchange.web_service.i_e_w_s_client/) class.
1. Создайте новый экземпляр *InboxRule* класс и задайте следующие обязательные свойства:
   1. DisplayName
   1. Conditions
   1. Actions
1. Позвоните [IEWSClient->CreateInboxRule()](https://apireference.aspose.com/cpp/email/class/aspose.email.clients.exchange.web_service.i_e_w_s_client/#a7af390adad4a0248d17b11bbebe8e97f) метод создания правила.

В следующем фрагменте кода показано, как создать новое правило.



{{< gist "aspose-com-gists" "525dd06c8783ebb18fb75cfc4b31d1ef" "Examples-Cpp-source-Exchange_EWS-CreateNewRuleOntheExchangeServer-CreateNewRuleOntheExchangeServer.cpp" >}}
### **Обновление правила**
Чтобы обновить правило на сервере Exchange, выполните следующие действия:

1. Подключитесь к серверу Exchange с помощью [IEWSClient](https://apireference.aspose.com/cpp/email/class/aspose.email.clients.exchange.web_service.i_e_w_s_client/) class.
1. Позвоните [IEWSClient->GetInboxRules()](https://apireference.aspose.com/cpp/email/class/aspose.email.clients.exchange.web_service.i_e_w_s_client/#ad8b80596b53806955cdc326b3cd23ebb) метод получения всех правил.
1. По очереди просмотрите все правила и выберите правило, которое хотите изменить, сопоставив *DisplayName* в состоянии.
1. Обновите свойства правила
1. Позвоните [IEWSClient.UpdateInboxRule()](https://apireference.aspose.com/cpp/email/class/aspose.email.clients.exchange.web_service.i_e_w_s_client/#a077ef824948d486b7633ee9f3f61e863) метод обновления правила.

В следующем фрагменте кода показано, как обновить правило.



{{< gist "aspose-com-gists" "525dd06c8783ebb18fb75cfc4b31d1ef" "Examples-Cpp-source-Exchange_EWS-UpdateRuleOntheExchangeServer-UpdateRuleOntheExchangeServer.cpp" >}}
