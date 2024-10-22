---
title: "Trabajando con Reglas en Exchange Server"
url: /es/cpp/working-with-rules-on-exchange-server/
weight: 90
type: docs
---

## **Gestionando Reglas**
Aspose.Email se puede utilizar para gestionar las reglas en Exchange Server utilizando la clase [EWSClient](https://apireference.aspose.com/cpp/email/class/aspose.email.clients.exchange.web_service.e_w_s_client/). Esta clase utiliza Exchange Web Services (EWS), que están disponibles en Exchange Server 2007 y versiones posteriores. Para mostrar cómo gestionar reglas, este artículo explica cómo:

- Leer las reglas ya existentes en el servidor.
- Crear una nueva regla.
- Actualizar una regla existente.

Se requiere Microsoft Exchange Server 2010 Service Pack 1 para todas las funciones descritas en este artículo.
### **Leer Reglas**
Para obtener todas las reglas del Exchange Server:

1. Conectarse a un Exchange Server utilizando la clase [IEWSClient](https://apireference.aspose.com/cpp/email/class/aspose.email.clients.exchange.web_service.i_e_w_s_client/).
1. Llamar al método [IEWSClient->GetInboxRules()](https://apireference.aspose.com/cpp/email/class/aspose.email.clients.exchange.web_service.i_e_w_s_client/#ad8b80596b53806955cdc326b3cd23ebb) para obtener todas las reglas.
1. En un bucle, recorrer todas las reglas y mostrar las propiedades de la regla como condiciones, acciones y nombres.

El siguiente fragmento de código muestra cómo leer reglas.



{{< gist "aspose-com-gists" "525dd06c8783ebb18fb75cfc4b31d1ef" "Examples-Cpp-source-Exchange_EWS-ExchangeServerReadRules-ExchangeServerReadRules.cpp" >}}
### **Crear una Nueva Regla**
Para crear una nueva regla en el Exchange Server, realiza los siguientes pasos:

1. Conectarse a un Exchange Server utilizando la clase [IEWSClient](https://apireference.aspose.com/cpp/email/class/aspose.email.clients.exchange.web_service.i_e_w_s_client/).
1. Crear una nueva instancia de la clase *InboxRule* y establecer las siguientes propiedades obligatorias:
   1. DisplayName
   1. Conditions
   1. Actions
1. Llamar al método [IEWSClient->CreateInboxRule()](https://apireference.aspose.com/cpp/email/class/aspose.email.clients.exchange.web_service.i_e_w_s_client/#a7af390adad4a0248d17b11bbebe8e97f) para crear la regla.

El siguiente fragmento de código muestra cómo crear una nueva regla.



{{< gist "aspose-com-gists" "525dd06c8783ebb18fb75cfc4b31d1ef" "Examples-Cpp-source-Exchange_EWS-CreateNewRuleOntheExchangeServer-CreateNewRuleOntheExchangeServer.cpp" >}}
### **Actualizar una Regla**
Para actualizar una regla en el Exchange Server:

1. Conectarse a un Exchange Server utilizando la clase [IEWSClient](https://apireference.aspose.com/cpp/email/class/aspose.email.clients.exchange.web_service.i_e_w_s_client/).
1. Llamar al método [IEWSClient->GetInboxRules()](https://apireference.aspose.com/cpp/email/class/aspose.email.clients.exchange.web_service.i_e_w_s_client/#ad8b80596b53806955cdc326b3cd23ebb) para obtener todas las reglas.
1. En un bucle, recorrer todas las reglas y obtener la regla que quieres cambiar emparejando el *DisplayName* en una condición.
1. Actualizar las propiedades de la regla.
1. Llamar al método [IEWSClient.UpdateInboxRule()](https://apireference.aspose.com/cpp/email/class/aspose.email.clients.exchange.web_service.i_e_w_s_client/#a077ef824948d486b7633ee9f3f61e863) para actualizar la regla.

El siguiente fragmento de código muestra cómo actualizar una regla.



{{< gist "aspose-com-gists" "525dd06c8783ebb18fb75cfc4b31d1ef" "Examples-Cpp-source-Exchange_EWS-UpdateRuleOntheExchangeServer-UpdateRuleOntheExchangeServer.cpp" >}}