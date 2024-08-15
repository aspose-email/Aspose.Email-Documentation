---
title: "Trabajar con reglas en Exchange Server"
url: /es/net/working-with-rules-on-exchange-server/
weight: 90
type: docs
---


## **Gestión de reglas**

Aspose.Email para.NET se puede usar para administrar las reglas de Exchange Server mediante [EWSClient](https://reference.aspose.com/email/net/aspose.email.clients.exchange.webservice/ewsclient/) clase. Esta clase usa los servicios web de Exchange (EWS), que están disponibles en Exchange Server 2007 y versiones posteriores. En este artículo se explica cómo administrar las reglas:

- Lea las reglas que ya están en el servidor.
- Crea una regla nueva.
- Actualiza una regla existente.

Se requiere el Service Pack 1 de Microsoft Exchange Server 2010 para todas las funciones descritas en este artículo.

### **Lea las reglas**

Para obtener todas las reglas del servidor Exchange:

1. Conéctese a un servidor Exchange mediante el [IEWSClient](https://reference.aspose.com/email/net/aspose.email.clients.exchange.webservice/iewsclient/) class.
1. Llame al [IEWSClient.GetInboxRules()](https://reference.aspose.com/email/net/aspose.email.clients.exchange.webservice/iewsclient/getinboxrules/#getinboxrules) método para obtener todas las reglas.
1. En un bucle para cada uno, examine todas las reglas y muestre sus propiedades, como las condiciones, las acciones y el nombre.

El siguiente fragmento de código muestra cómo leer las reglas.

{{< gist "aspose-com-gists" "6e5185a63aec6fd70d83098e82b06a32" "Examples-CSharp-Exchange_EWS-ExchangeServerReadRules-ExchangeServerReadRules.cs" >}}

### **Creación de una nueva regla**

Para crear una nueva regla en el servidor Exchange, lleve a cabo los siguientes pasos:

1. Conéctese a un servidor Exchange mediante el [IEWSClient](https://reference.aspose.com/email/net/aspose.email.clients.exchange.webservice/iewsclient/) interface.
1. Cree una nueva instancia del [InboxRule](https://reference.aspose.com/email/net/aspose.email.clients.exchange/inboxrule/) clase y establezca las siguientes propiedades obligatorias:
   1. DisplayName
   1. Conditions
   1. Actions
1. Llame al [IEWSClient.CreateInboxRule()](https://reference.aspose.com/email/net/aspose.email.clients.exchange.webservice/iewsclient/createinboxrule/#createinboxrule) método para crear la regla.

El siguiente fragmento de código muestra cómo crear una regla nueva.

{{< gist "aspose-com-gists" "6e5185a63aec6fd70d83098e82b06a32" "Examples-CSharp-Exchange_EWS-CreateNewRuleOntheExchangeServer-CreateNewRuleOntheExchangeServer.cs" >}}

### **Actualización de una regla**

Para actualizar una regla en Exchange Server:

1. Conéctese a un servidor Exchange mediante el [IEWSClient](https://reference.aspose.com/email/net/aspose.email.clients.exchange.webservice/iewsclient/) class.
1. Llame al [IEWSClient.GetInboxRules()](https://reference.aspose.com/email/net/aspose.email.clients.exchange.webservice/iewsclient/getinboxrules/#getinboxrules) método para obtener todas las reglas.
1. En un bucle de foreach, examine todas las reglas y obtenga la regla que desea cambiar haciendo coincidir el nombre de visualización de una condición.
1. Actualice las propiedades de la regla.
1. Llame al [IEWSClient.UpdateInboxRule()](https://reference.aspose.com/email/net/aspose.email.clients.exchange.webservice/iewsclient/updateinboxrule/#updateinboxrule/) método para actualizar la regla.

El siguiente fragmento de código muestra cómo actualizar una regla.

{{< gist "aspose-com-gists" "6e5185a63aec6fd70d83098e82b06a32" "Examples-CSharp-Exchange_EWS-UpdateRuleOntheExchangeServer-UpdateRuleOntheExchangeServer.cs" >}}
