---
title: Working with Rules On Exchange Server
type: docs
weight: 90
url: /cpp/working-with-rules-on-exchange-server/
---

## **Managing Rules**
Aspose.Email can be used to manage the rules on Exchange Server using the [EWSClient](https://reference.aspose.com/cpp/email/class/aspose.email.clients.exchange.web_service.e_w_s_client/) class. This class uses Exchange Web Services (EWS), which are available in Exchange Server 2007 and later releases. To show how to manage rules, this article explains how to:

- Read the rules already on the server.
- Create a new rule.
- Update an existing rule.

Microsoft Exchange Server 2010 Service Pack 1 is required for all features described in this article.
### **Read Rules**
To get all the rules from the Exchange Server:

1. Connect to an Exchange Server using the [IEWSClient](https://reference.aspose.com/cpp/email/class/aspose.email.clients.exchange.web_service.i_e_w_s_client/) class.
1. Call the [IEWSClient->GetInboxRules()](https://reference.aspose.com/cpp/email/class/aspose.email.clients.exchange.web_service.i_e_w_s_client/#ad8b80596b53806955cdc326b3cd23ebb) method to get all the rules.
1. In a loop, browse through all the rules and display the rule properties like conditions, actions, and names.

The following code snippet shows you how to read rules.



{{< gist "aspose-com-gists" "525dd06c8783ebb18fb75cfc4b31d1ef" "Examples-Cpp-source-Exchange_EWS-ExchangeServerReadRules-ExchangeServerReadRules.cpp" >}}
### **Creating a New Rule**
To create a new rule on the Exchange Server, perform the following steps:

1. Connect to an Exchange Server using the [IEWSClient](https://reference.aspose.com/cpp/email/class/aspose.email.clients.exchange.web_service.i_e_w_s_client/) class.
1. Create a new instance of the *InboxRule* class and set the following mandatory properties:
   1. DisplayName
   1. Conditions
   1. Actions
1. Call the [IEWSClient->CreateInboxRule()](https://reference.aspose.com/cpp/email/class/aspose.email.clients.exchange.web_service.i_e_w_s_client/#a7af390adad4a0248d17b11bbebe8e97f) method to create the rule.

The following code snippet shows you how to create a new rule.



{{< gist "aspose-com-gists" "525dd06c8783ebb18fb75cfc4b31d1ef" "Examples-Cpp-source-Exchange_EWS-CreateNewRuleOntheExchangeServer-CreateNewRuleOntheExchangeServer.cpp" >}}
### **Updating a Rule**
To update a rule on the Exchange Server:

1. Connect to an Exchange Server using the [IEWSClient](https://reference.aspose.com/cpp/email/class/aspose.email.clients.exchange.web_service.i_e_w_s_client/) class.
1. Call the [IEWSClient->GetInboxRules()](https://reference.aspose.com/cpp/email/class/aspose.email.clients.exchange.web_service.i_e_w_s_client/#ad8b80596b53806955cdc326b3cd23ebb) method to get all the rules.
1. In a loop, browse through all the rules and get the rule you want to change by matching the *DisplayName* in a condition.
1. Update the rule properties
1. Call the [IEWSClient.UpdateInboxRule()](https://reference.aspose.com/cpp/email/class/aspose.email.clients.exchange.web_service.i_e_w_s_client/#a077ef824948d486b7633ee9f3f61e863) method to update the rule.

The following code snippet shows you how to update a rule.



{{< gist "aspose-com-gists" "525dd06c8783ebb18fb75cfc4b31d1ef" "Examples-Cpp-source-Exchange_EWS-UpdateRuleOntheExchangeServer-UpdateRuleOntheExchangeServer.cpp" >}}
