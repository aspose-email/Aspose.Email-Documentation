---
title: "Administración de los elementos de conversación"
url: /es/net/managing-conversation-items/
weight: 40
type: docs
---


Aspose.Email para.NET se puede usar para administrar los elementos de conversación en Exchange Server con [EWSClient](https://reference.aspose.com/email/net/aspose.email.clients.exchange.webservice/ewsclient/) clase. Esta clase usa los servicios web de Exchange, que solo están disponibles en Exchange Server 2007 y versiones posteriores. En este artículo se muestra cómo [find](#finding-conversations), [copy](#copying-conversations), [move](#moving-conversations) and [delete](#deleting-conversations) elementos de conversación en Exchange Server 2010. Todas las funciones incluidas en esta sección requieren el Service Pack 1 de Microsoft Exchange Server 2010.

## **Búsqueda de conversaciones**

Para obtener la información de la conversación de una carpeta específica del servidor Exchange:

1. Conéctese al servidor Exchange mediante [IEWSClient](https://reference.aspose.com/email/net/aspose.email.clients.exchange.webservice/iewsclient/) interface.
1. Llame al [IEWSClient.FindConversations()](https://reference.aspose.com/email/net/aspose.email.clients.exchange.webservice/iewsclient/findconversations/#findconversations) método para encontrar todos los elementos de conversación de una carpeta.
1. Muestra las propiedades del elemento de conversación, como el identificador, el tema de la conversación y el estado de la marca.

El siguiente fragmento de código muestra cómo buscar conversaciones.

{{< gist "aspose-com-gists" "6e5185a63aec6fd70d83098e82b06a32" "Examples-CSharp-Exchange_EWS-FindConversationsOnExchangeServer-FindConversationsOnExchangeServer.cs" >}}

## **Copiar conversaciones**

Para copiar conversaciones de una carpeta a otra:

1. Conéctese al servidor Exchange mediante [IEWSClient](https://reference.aspose.com/email/net/aspose.email.clients.exchange.webservice/iewsclient/) interface.
1. Llame al [IEWSClient.CopyConversationItems()](https://reference.aspose.com/email/net/aspose.email.clients.exchange.webservice/iewsclient/copyconversationitems/#copyconversationitems) método para copiar el elemento de conversación de la carpeta de origen a la carpeta de destino.

El siguiente fragmento de código muestra cómo copiar conversaciones.

{{< gist "aspose-com-gists" "6e5185a63aec6fd70d83098e82b06a32" "Examples-CSharp-Exchange_EWS-CopyConversations-CopyConversations.cs" >}}

## **Conversaciones conmovedoras**

Para mover conversaciones de una carpeta a otra:

1. Conéctese al servidor Exchange mediante [IEWSClient](https://reference.aspose.com/email/net/aspose.email.clients.exchange.webservice/iewsclient/) interface.
1. Llame al [IEWSClient.MoveConversationItems()](https://reference.aspose.com/email/net/aspose.email.clients.exchange.webservice/iewsclient/moveconversationitems/#moveconversationitems) método para mover una conversación de la carpeta de origen a la carpeta de destino.

En el siguiente fragmento de código, se muestra cómo mover las conversaciones.

{{< gist "aspose-com-gists" "6e5185a63aec6fd70d83098e82b06a32" "Examples-CSharp-Exchange_EWS-MoveConversations-MoveConversations.cs" >}}

## **Eliminar conversaciones**

Para eliminar conversaciones de una carpeta:

1. Conéctese al servidor Exchange mediante [IEWSClient](https://reference.aspose.com/email/net/aspose.email.clients.exchange.webservice/iewsclient/) interface.
1. Llame al [IEWSClient.DeleteConversationItems()](https://reference.aspose.com/email/net/aspose.email.clients.exchange.webservice/iewsclient/deleteconversationitems/#deleteconversationitems) método para eliminar el elemento de conversación de la carpeta de origen.

En el siguiente fragmento de código, se muestra cómo eliminar conversaciones.

{{< gist "aspose-com-gists" "6e5185a63aec6fd70d83098e82b06a32" "Examples-CSharp-Exchange_EWS-DeleteConversations-DeleteConversations.cs" >}}
