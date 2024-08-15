---
title: "Trabajar con reglas en Exchange Server"
url: /es/cpp/working-with-rules-on-exchange-server/
weight: 90
type: docs
---

## **Gestión de reglas**
Aspose.Email se puede usar para administrar las reglas en Exchange Server mediante el [EWSClient](https://apireference.aspose.com/cpp/email/class/aspose.email.clients.exchange.web_service.e_w_s_client/) clase. Esta clase usa los servicios web de Exchange (EWS), que están disponibles en Exchange Server 2007 y versiones posteriores. Para mostrar cómo administrar las reglas, en este artículo se explica cómo:

- Lea las reglas que ya están en el servidor.
- Crea una regla nueva.
- Actualiza una regla existente.

Se requiere el Service Pack 1 de Microsoft Exchange Server 2010 para todas las funciones descritas en este artículo.
### **Lea las reglas**
Para obtener todas las reglas del servidor Exchange:

1. Conéctese a un servidor Exchange mediante el [IEWSClient](https://apireference.aspose.com/cpp/email/class/aspose.email.clients.exchange.web_service.i_e_w_s_client/) class.
1. Llame al [IEWSClient->GetInboxRules()](https://apireference.aspose.com/cpp/email/class/aspose.email.clients.exchange.web_service.i_e_w_s_client/#ad8b80596b53806955cdc326b3cd23ebb) método para obtener todas las reglas.
1. En un bucle, explore todas las reglas y muestre sus propiedades, como condiciones, acciones y nombres.

El siguiente fragmento de código muestra cómo leer las reglas.



{{< gist "aspose-com-gists" "525dd06c8783ebb18fb75cfc4b31d1ef" "Examples-Cpp-source-Exchange_EWS-ExchangeServerReadRules-ExchangeServerReadRules.cpp" >}}
### **Creación de una nueva regla**
Para crear una nueva regla en el servidor Exchange, lleve a cabo los siguientes pasos:

1. Conéctese a un servidor Exchange mediante el [IEWSClient](https://apireference.aspose.com/cpp/email/class/aspose.email.clients.exchange.web_service.i_e_w_s_client/) class.
1. Cree una nueva instancia del *InboxRule* clase y establezca las siguientes propiedades obligatorias:
   1. DisplayName
   1. Conditions
   1. Actions
1. Llame al [IEWSClient->CreateInboxRule()](https://apireference.aspose.com/cpp/email/class/aspose.email.clients.exchange.web_service.i_e_w_s_client/#a7af390adad4a0248d17b11bbebe8e97f) método para crear la regla.

El siguiente fragmento de código muestra cómo crear una regla nueva.



{{< gist "aspose-com-gists" "525dd06c8783ebb18fb75cfc4b31d1ef" "Examples-Cpp-source-Exchange_EWS-CreateNewRuleOntheExchangeServer-CreateNewRuleOntheExchangeServer.cpp" >}}
### **Actualización de una regla**
Para actualizar una regla en Exchange Server:

1. Conéctese a un servidor Exchange mediante el [IEWSClient](https://apireference.aspose.com/cpp/email/class/aspose.email.clients.exchange.web_service.i_e_w_s_client/) class.
1. Llame al [IEWSClient->GetInboxRules()](https://apireference.aspose.com/cpp/email/class/aspose.email.clients.exchange.web_service.i_e_w_s_client/#ad8b80596b53806955cdc326b3cd23ebb) método para obtener todas las reglas.
1. En un bucle, navegue por todas las reglas y obtenga la regla que desea cambiar haciendo coincidir el *DisplayName* en una condición.
1. Actualizar las propiedades de la regla
1. Llame al [IEWSClient.UpdateInboxRule()](https://apireference.aspose.com/cpp/email/class/aspose.email.clients.exchange.web_service.i_e_w_s_client/#a077ef824948d486b7633ee9f3f61e863) método para actualizar la regla.

El siguiente fragmento de código muestra cómo actualizar una regla.



{{< gist "aspose-com-gists" "525dd06c8783ebb18fb75cfc4b31d1ef" "Examples-Cpp-source-Exchange_EWS-UpdateRuleOntheExchangeServer-UpdateRuleOntheExchangeServer.cpp" >}}
