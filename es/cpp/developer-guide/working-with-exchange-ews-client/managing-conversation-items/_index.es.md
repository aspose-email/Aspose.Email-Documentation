---
title: "Administración de los elementos de conversación"
url: /es/cpp/managing-conversation-items/
weight: 40
type: docs
---

Aspose.Email se puede usar para administrar los elementos de conversación en Exchange Server con el [EWSClient](https://apireference.aspose.com/email/cpp/class/aspose.email.clients.exchange.web_service.e_w_s_client) clase. Esta clase usa los servicios web de Exchange, que solo están disponibles en Exchange Server 2007 y versiones posteriores. En este artículo se muestra cómo buscar, copiar, mover y eliminar elementos de conversación en Exchange Server 2010. Todas las funciones incluidas en esta sección requieren el Service Pack 1 de Microsoft Exchange Server 2010.
##  **Búsqueda de conversaciones**
Para obtener la información de la conversación de una carpeta específica del servidor Exchange:

1. Conéctese al servidor Exchange mediante [IEWSClient](https://apireference.aspose.com/email/cpp/class/aspose.email.clients.exchange.web_service.i_e_w_s_client) class.
1. Llame al [FindConversations()](https://apireference.aspose.com/email/cpp/class/aspose.email.clients.exchange.web_service.i_e_w_s_client) método para encontrar todos los elementos de conversación en una carpeta.
1. Muestra las propiedades del elemento de conversación, como el identificador, el tema de la conversación y el estado de la marca.

El siguiente fragmento de código muestra cómo buscar conversaciones.



{{< gist "aspose-com-gists" "525dd06c8783ebb18fb75cfc4b31d1ef" "Examples-Cpp-source-Exchange_EWS-FindConversationsOnExchangeServer-FindConversationsOnExchangeServer.cpp" >}}
##  **Copiar conversaciones**
Para copiar conversaciones de una carpeta a otra:

1. Conéctese al servidor Exchange mediante [IEWSClient](https://apireference.aspose.com/email/cpp/class/aspose.email.clients.exchange.web_service.i_e_w_s_client) class.
1. Llame al [CopyConversationItems()](https://apireference.aspose.com/email/cpp/class/aspose.email.clients.exchange.web_service.i_e_w_s_client) método para copiar el elemento de conversación de la carpeta de origen a la carpeta de destino.

El siguiente fragmento de código muestra cómo copiar conversaciones.



{{< gist "aspose-com-gists" "525dd06c8783ebb18fb75cfc4b31d1ef" "Examples-Cpp-source-Exchange_EWS-CopyConversations-CopyConversations.cpp" >}}
##  **Conversaciones conmovedoras**
Para mover conversaciones de una carpeta a otra:

1. Conéctese al servidor Exchange mediante [IEWSClient](https://apireference.aspose.com/email/cpp/class/aspose.email.clients.exchange.web_service.i_e_w_s_client) class.
1. Llame al [MoveConversationItems()](https://apireference.aspose.com/email/cpp/class/aspose.email.clients.exchange.web_service.i_e_w_s_client) método para mover una conversación de la carpeta de origen a la carpeta de destino.

En el siguiente fragmento de código, se muestra cómo mover las conversaciones.



{{< gist "aspose-com-gists" "525dd06c8783ebb18fb75cfc4b31d1ef" "Examples-Cpp-source-Exchange_EWS-MoveConversations-MoveConversations.cpp" >}}
##  **Eliminar conversaciones**
Para eliminar conversaciones de una carpeta:

1. Conéctese al servidor Exchange mediante [IEWSClient](https://apireference.aspose.com/email/cpp/class/aspose.email.clients.exchange.web_service.i_e_w_s_client) class.
1. Llame al [DeleteConversationItems()](https://apireference.aspose.com/email/cpp/class/aspose.email.clients.exchange.web_service.i_e_w_s_client) método para eliminar el elemento de conversación de la carpeta de origen.

En el siguiente fragmento de código, se muestra cómo eliminar conversaciones.



{{< gist "aspose-com-gists" "525dd06c8783ebb18fb75cfc4b31d1ef" "Examples-Cpp-source-Exchange_EWS-DeleteConversations-DeleteConversations.cpp" >}}
