---
title: "Работа с правилами на Exchange Server"
url: /ru/net/working-with-rules-on-exchange-server/
weight: 90
type: docs
---


## **Управление правилами**

Aspose.Email для .NET может быть использован для управления правилами на Exchange Server с использованием класса [EWSClient](https://reference.aspose.com/email/net/aspose.email.clients.exchange.webservice/ewsclient/). Этот класс использует Exchange Web Services (EWS), которые доступны в Exchange Server 2007 и более поздних версиях. В этой статье объясняется, как управлять правилами:

- Чтение правил, уже находящихся на сервере.
- Создание нового правила.
- Обновление существующего правила.

Для всех функций, описанных в этой статье, требуется Microsoft Exchange Server 2010 Service Pack 1.

### **Чтение правил**

Чтобы получить все правила с Exchange Server:

1. Подключитесь к Exchange Server с использованием класса [IEWSClient](https://reference.aspose.com/email/net/aspose.email.clients.exchange.webservice/iewsclient/).
2. Вызовите метод [IEWSClient.GetInboxRules()](https://reference.aspose.com/email/net/aspose.email.clients.exchange.webservice/iewsclient/getinboxrules/#getinboxrules), чтобы получить все правила.
3. В цикле foreach просмотрите все правила и отобразите свойства правила, такие как условия, действия и имя.

Следующий фрагмент кода показывает, как читать правила.

{{< gist "aspose-com-gists" "6e5185a63aec6fd70d83098e82b06a32" "Examples-CSharp-Exchange_EWS-ExchangeServerReadRules-ExchangeServerReadRules.cs" >}}

### **Создание нового правила**

Чтобы создать новое правило на Exchange Server, выполните следующие шаги:

1. Подключитесь к Exchange Server с использованием интерфейса [IEWSClient](https://reference.aspose.com/email/net/aspose.email.clients.exchange.webservice/iewsclient/).
2. Создайте новый экземпляр класса [InboxRule](https://reference.aspose.com/email/net/aspose.email.clients.exchange/inboxrule/) и установите следующие обязательные свойства:
   1. DisplayName
   2. Conditions
   3. Actions
3. Вызовите метод [IEWSClient.CreateInboxRule()](https://reference.aspose.com/email/net/aspose.email.clients.exchange.webservice/iewsclient/createinboxrule/#createinboxrule), чтобы создать правило.

Следующий фрагмент кода показывает, как создать новое правило.

{{< gist "aspose-com-gists" "6e5185a63aec6fd70d83098e82b06a32" "Examples-CSharp-Exchange_EWS-CreateNewRuleOntheExchangeServer-CreateNewRuleOntheExchangeServer.cs" >}}

### **Обновление правила**

Чтобы обновить правило на Exchange Server:

1. Подключитесь к Exchange Server с использованием класса [IEWSClient](https://reference.aspose.com/email/net/aspose.email.clients.exchange.webservice/iewsclient/).
2. Вызовите метод [IEWSClient.GetInboxRules()](https://reference.aspose.com/email/net/aspose.email.clients.exchange.webservice/iewsclient/getinboxrules/#getinboxrules), чтобы получить все правила.
3. В цикле foreach просмотрите все правила и получите правило, которое вы хотите изменить, сопоставив DisplayName в условии.
4. Обновите свойства правила.
5. Вызовите метод [IEWSClient.UpdateInboxRule()](https://reference.aspose.com/email/net/aspose.email.clients.exchange.webservice/iewsclient/updateinboxrule/#updateinboxrule/) для обновления правила.

Следующий фрагмент кода показывает, как обновить правило.

{{< gist "aspose-com-gists" "6e5185a63aec6fd70d83098e82b06a32" "Examples-CSharp-Exchange_EWS-UpdateRuleOntheExchangeServer-UpdateRuleOntheExchangeServer.cs" >}}