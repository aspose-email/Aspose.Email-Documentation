---
title: "Gestión de Elementos de Conversación"
url: /es/net/gestion-de-elementos-de-conversacion/
weight: 40
type: docs
---

Aspose.Email para .NET se puede utilizar para gestionar los elementos de conversación en Exchange Server con la clase [EWSClient](https://reference.aspose.com/email/net/aspose.email.clients.exchange.webservice/ewsclient/). Esta clase utiliza Exchange Web Services, que solo están disponibles en Exchange Server 2007 y versiones posteriores. Este artículo muestra cómo [encontrar](#finding-conversations), [copiar](#copying-conversations), [mover](#moving-conversations) y [eliminar](#deleting-conversations) elementos de conversación en Exchange Server 2010. Se requiere Microsoft Exchange Server 2010 Service Pack 1 para todas las funcionalidades incluidas en esta sección.

## **Encontrar Conversaciones**

Para obtener la información de la conversación de una carpeta específica en el Exchange Server:

1. Conéctese al Exchange Server utilizando la interfaz [IEWSClient](https://reference.aspose.com/email/net/aspose.email.clients.exchange.webservice/iewsclient/).
1. Llame al método [IEWSClient.FindConversations()](https://reference.aspose.com/email/net/aspose.email.clients.exchange.webservice/iewsclient/findconversations/#findconversations) para encontrar todos los elementos de conversación de una carpeta.
1. Muestre las propiedades del elemento de conversación como ID, tema de conversación y estado de la bandera.

El siguiente fragmento de código le muestra cómo encontrar conversaciones.

{{< gist "aspose-com-gists" "6e5185a63aec6fd70d83098e82b06a32" "Examples-CSharp-Exchange_EWS-FindConversationsOnExchangeServer-FindConversationsOnExchangeServer.cs" >}}

## **Copiar Conversaciones**

Para copiar conversaciones de una carpeta a otra:

1. Conéctese al Exchange Server utilizando la interfaz [IEWSClient](https://reference.aspose.com/email/net/aspose.email.clients.exchange.webservice/iewsclient/).
1. Llame al método [IEWSClient.CopyConversationItems()](https://reference.aspose.com/email/net/aspose.email.clients.exchange.webservice/iewsclient/copyconversationitems/#copyconversationitems) para copiar el elemento de conversación de la carpeta de origen a la carpeta de destino.

El siguiente fragmento de código le muestra cómo copiar conversaciones.

{{< gist "aspose-com-gists" "6e5185a63aec6fd70d83098e82b06a32" "Examples-CSharp-Exchange_EWS-CopyConversations-CopyConversations.cs" >}}

## **Mover Conversaciones**

Para mover conversaciones de una carpeta a otra:

1. Conéctese al Exchange Server utilizando la interfaz [IEWSClient](https://reference.aspose.com/email/net/aspose.email.clients.exchange.webservice/iewsclient/).
1. Llame al método [IEWSClient.MoveConversationItems()](https://reference.aspose.com/email/net/aspose.email.clients.exchange.webservice/iewsclient/moveconversationitems/#moveconversationitems) para mover una conversación de la carpeta de origen a la carpeta de destino.

El siguiente fragmento de código le muestra cómo mover conversaciones.

{{< gist "aspose-com-gists" "6e5185a63aec6fd70d83098e82b06a32" "Examples-CSharp-Exchange_EWS-MoveConversations-MoveConversations.cs" >}}

## **Eliminar Conversaciones**

Para eliminar conversaciones de una carpeta:

1. Conéctese al Exchange Server utilizando la interfaz [IEWSClient](https://reference.aspose.com/email/net/aspose.email.clients.exchange.webservice/iewsclient/).
1. Llame al método [IEWSClient.DeleteConversationItems()](https://reference.aspose.com/email/net/aspose.email.clients.exchange.webservice/iewsclient/deleteconversationitems/#deleteconversationitems) para eliminar el elemento de conversación de la carpeta de origen.

El siguiente fragmento de código le muestra cómo eliminar conversaciones.

{{< gist "aspose-com-gists" "6e5185a63aec6fd70d83098e82b06a32" "Examples-CSharp-Exchange_EWS-DeleteConversations-DeleteConversations.cs" >}}