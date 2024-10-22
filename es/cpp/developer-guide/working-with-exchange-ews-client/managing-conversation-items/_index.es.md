---
title: "Gestión de Elementos de Conversación"
url: /es/cpp/gestion-de-elementos-de-conversacion/
weight: 40
type: docs
---

Aspose.Email se puede utilizar para gestionar los elementos de conversación en Exchange Server con la clase [EWSClient](https://apireference.aspose.com/email/cpp/class/aspose.email.clients.exchange.web_service.e_w_s_client). Esta clase utiliza los Servicios Web de Exchange, que solo están disponibles en Exchange Server 2007 y versiones posteriores. Este artículo muestra cómo encontrar, copiar, mover y eliminar elementos de conversación en Exchange Server 2010. Se requiere Microsoft Exchange Server 2010 Service Pack 1 para todas las características incluidas en esta sección.
##  **Encontrando Conversaciones**
Para obtener la información de conversación de una carpeta específica en el Exchange Server:

1. Conéctese al Exchange Server usando la clase [IEWSClient](https://apireference.aspose.com/email/cpp/class/aspose.email.clients.exchange.web_service.i_e_w_s_client).
1. Llame al método [FindConversations()](https://apireference.aspose.com/email/cpp/class/aspose.email.clients.exchange.web_service.i_e_w_s_client) para encontrar todos los elementos de conversación en una carpeta.
1. Muestra las propiedades del elemento de conversación como ID, tema de conversación y estado de la bandera.

El siguiente fragmento de código te muestra cómo encontrar conversaciones.



{{< gist "aspose-com-gists" "525dd06c8783ebb18fb75cfc4b31d1ef" "Examples-Cpp-source-Exchange_EWS-FindConversationsOnExchangeServer-FindConversationsOnExchangeServer.cpp" >}}
##  **Copiando Conversaciones**
Para copiar conversaciones de una carpeta a otra:

1. Conéctese al Exchange Server usando la clase [IEWSClient](https://apireference.aspose.com/email/cpp/class/aspose.email.clients.exchange.web_service.i_e_w_s_client).
1. Llame al método [CopyConversationItems()](https://apireference.aspose.com/email/cpp/class/aspose.email.clients.exchange.web_service.i_e_w_s_client) para copiar el elemento de conversación de la carpeta de origen a la carpeta de destino.

El siguiente fragmento de código te muestra cómo copiar conversaciones.



{{< gist "aspose-com-gists" "525dd06c8783ebb18fb75cfc4b31d1ef" "Examples-Cpp-source-Exchange_EWS-CopyConversations-CopyConversations.cpp" >}}
##  **Moviendo Conversaciones**
Para mover conversaciones de una carpeta a otra:

1. Conéctese al Exchange Server usando la clase [IEWSClient](https://apireference.aspose.com/email/cpp/class/aspose.email.clients.exchange.web_service.i_e_w_s_client).
1. Llame al método [MoveConversationItems()](https://apireference.aspose.com/email/cpp/class/aspose.email.clients.exchange.web_service.i_e_w_s_client) para mover una conversación de la carpeta de origen a la carpeta de destino.

El siguiente fragmento de código te muestra cómo mover conversaciones.



{{< gist "aspose-com-gists" "525dd06c8783ebb18fb75cfc4b31d1ef" "Examples-Cpp-source-Exchange_EWS-MoveConversations-MoveConversations.cpp" >}}
##  **Eliminando Conversaciones**
Para eliminar conversaciones de una carpeta:

1. Conéctese al Exchange Server usando la clase [IEWSClient](https://apireference.aspose.com/email/cpp/class/aspose.email.clients.exchange.web_service.i_e_w_s_client).
1. Llame al método [DeleteConversationItems()](https://apireference.aspose.com/email/cpp/class/aspose.email.clients.exchange.web_service.i_e_w_s_client) para eliminar el elemento de conversación de la carpeta de origen.

El siguiente fragmento de código te muestra cómo eliminar conversaciones.



{{< gist "aspose-com-gists" "525dd06c8783ebb18fb75cfc4b31d1ef" "Examples-Cpp-source-Exchange_EWS-DeleteConversations-DeleteConversations.cpp" >}}