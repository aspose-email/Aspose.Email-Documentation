---
title: "Trabajando con Reglas en Exchange Server"
url: /es/net/working-with-rules-on-exchange-server/
weight: 90
type: docs
---


## **Gestionando Reglas**

Aspose.Email para .NET se puede utilizar para gestionar las reglas en Exchange Server utilizando la clase [EWSClient](https://reference.aspose.com/email/net/aspose.email.clients.exchange.webservice/ewsclient/). Esta clase utiliza los Servicios Web de Exchange (EWS), que están disponibles en Exchange Server 2007 y versiones posteriores. Este artículo explica cómo gestionar las reglas:

- Leer las reglas ya existentes en el servidor.
- Crear una nueva regla.
- Actualizar una regla existente.

Se requiere Microsoft Exchange Server 2010 Service Pack 1 para todas las funciones descritas en este artículo.

### **Leer Reglas**

Para obtener todas las reglas del Exchange Server:

1. Conéctese a un Exchange Server utilizando la clase [IEWSClient](https://reference.aspose.com/email/net/aspose.email.clients.exchange.webservice/iewsclient/).
1. Llame al método [IEWSClient.GetInboxRules()](https://reference.aspose.com/email/net/aspose.email.clients.exchange.webservice/iewsclient/getinboxrules/#getinboxrules) para obtener todas las reglas.
1. En un bucle foreach, recorra todas las reglas y muestre las propiedades de la regla, como condiciones, acciones y nombre.

El siguiente fragmento de código le muestra cómo leer reglas.

{{< gist "aspose-com-gists" "6e5185a63aec6fd70d83098e82b06a32" "Examples-CSharp-Exchange_EWS-ExchangeServerReadRules-ExchangeServerReadRules.cs" >}}

### **Creando una Nueva Regla**

Para crear una nueva regla en el Exchange Server, realice los siguientes pasos:

1. Conéctese a un Exchange Server utilizando la interfaz [IEWSClient](https://reference.aspose.com/email/net/aspose.email.clients.exchange.webservice/iewsclient/).
1. Cree una nueva instancia de la clase [InboxRule](https://reference.aspose.com/email/net/aspose.email.clients.exchange/inboxrule/) y establezca las siguientes propiedades obligatorias:
   1. DisplayName
   1. Conditions
   1. Actions
1. Llame al método [IEWSClient.CreateInboxRule()](https://reference.aspose.com/email/net/aspose.email.clients.exchange.webservice/iewsclient/createinboxrule/#createinboxrule) para crear la regla.

El siguiente fragmento de código le muestra cómo crear una nueva regla.

{{< gist "aspose-com-gists" "6e5185a63aec6fd70d83098e82b06a32" "Examples-CSharp-Exchange_EWS-CreateNewRuleOntheExchangeServer-CreateNewRuleOntheExchangeServer.cs" >}}

### **Actualizando una Regla**

Para actualizar una regla en el Exchange Server:

1. Conéctese a un Exchange Server utilizando la clase [IEWSClient](https://reference.aspose.com/email/net/aspose.email.clients.exchange.webservice/iewsclient/).
1. Llame al método [IEWSClient.GetInboxRules()](https://reference.aspose.com/email/net/aspose.email.clients.exchange.webservice/iewsclient/getinboxrules/#getinboxrules) para obtener todas las reglas.
1. En un bucle foreach, recorra todas las reglas y obtenga la regla que desea cambiar, coincidiendo con el DisplayName en una condición.
1. Actualice las propiedades de la regla.
1. Llame al método [IEWSClient.UpdateInboxRule()](https://reference.aspose.com/email/net/aspose.email.clients.exchange.webservice/iewsclient/updateinboxrule/#updateinboxrule/) para actualizar la regla.

El siguiente fragmento de código le muestra cómo actualizar una regla.

{{< gist "aspose-com-gists" "6e5185a63aec6fd70d83098e82b06a32" "Examples-CSharp-Exchange_EWS-UpdateRuleOntheExchangeServer-UpdateRuleOntheExchangeServer.cs" >}}