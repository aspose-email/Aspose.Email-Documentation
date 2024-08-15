---
title: "Работа с правилами на сервере Exchange"
url: /ru/net/working-with-rules-on-exchange-server/
weight: 90
type: docs
---


## **Управление правилами**

Aspose.Email for .NET можно использовать для управления правилами на сервере Exchange с помощью [EWSClient](https://reference.aspose.com/email/net/aspose.email.clients.exchange.webservice/ewsclient/) класс. В этом классе используются веб-службы Exchange (EWS), доступные в Exchange Server 2007 и более поздних версиях. В этой статье описывается, как управлять правилами:

- Ознакомьтесь с правилами, уже имеющимися на сервере.
- Создайте новое правило.
- Обновите существующее правило.

Для всех функций, описанных в этой статье, требуется пакет обновления 1 для Microsoft Exchange Server 2010.

### **Ознакомьтесь с правилами**

Чтобы получить все правила с сервера Exchange, выполните следующие действия:

1. Подключитесь к серверу Exchange с помощью [IEWSClient](https://reference.aspose.com/email/net/aspose.email.clients.exchange.webservice/iewsclient/) class.
1. Позвоните [IEWSClient.GetInboxRules()](https://reference.aspose.com/email/net/aspose.email.clients.exchange.webservice/iewsclient/getinboxrules/#getinboxrules) метод получения всех правил.
1. В цикле foreach просмотрите все правила и отобразите свойства правила, такие как условия, действия и имя.

В следующем фрагменте кода показано, как читать правила.

{{< gist "aspose-com-gists" "6e5185a63aec6fd70d83098e82b06a32" "Examples-CSharp-Exchange_EWS-ExchangeServerReadRules-ExchangeServerReadRules.cs" >}}

### **Создание нового правила**

Чтобы создать новое правило на сервере Exchange, выполните следующие шаги:

1. Подключитесь к серверу Exchange с помощью [IEWSClient](https://reference.aspose.com/email/net/aspose.email.clients.exchange.webservice/iewsclient/) interface.
1. Создайте новый экземпляр [InboxRule](https://reference.aspose.com/email/net/aspose.email.clients.exchange/inboxrule/) класс и задайте следующие обязательные свойства:
   1. DisplayName
   1. Conditions
   1. Actions
1. Позвоните [IEWSClient.CreateInboxRule()](https://reference.aspose.com/email/net/aspose.email.clients.exchange.webservice/iewsclient/createinboxrule/#createinboxrule) метод создания правила.

В следующем фрагменте кода показано, как создать новое правило.

{{< gist "aspose-com-gists" "6e5185a63aec6fd70d83098e82b06a32" "Examples-CSharp-Exchange_EWS-CreateNewRuleOntheExchangeServer-CreateNewRuleOntheExchangeServer.cs" >}}

### **Обновление правила**

Чтобы обновить правило на сервере Exchange, выполните следующие действия:

1. Подключитесь к серверу Exchange с помощью [IEWSClient](https://reference.aspose.com/email/net/aspose.email.clients.exchange.webservice/iewsclient/) class.
1. Позвоните [IEWSClient.GetInboxRules()](https://reference.aspose.com/email/net/aspose.email.clients.exchange.webservice/iewsclient/getinboxrules/#getinboxrules) метод получения всех правил.
1. В цикле foreach просмотрите все правила и выберите правило, которое вы хотите изменить, сопоставив DisplayName в условии.
1. Обновите свойства правила.
1. Позвоните [IEWSClient.UpdateInboxRule()](https://reference.aspose.com/email/net/aspose.email.clients.exchange.webservice/iewsclient/updateinboxrule/#updateinboxrule/) метод обновления правила.

В следующем фрагменте кода показано, как обновить правило.

{{< gist "aspose-com-gists" "6e5185a63aec6fd70d83098e82b06a32" "Examples-CSharp-Exchange_EWS-UpdateRuleOntheExchangeServer-UpdateRuleOntheExchangeServer.cs" >}}
