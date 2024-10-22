---
title: "Filtrar Mensajes Desde el Buzón de Exchange"
url: /es/cpp/filter-messages-from-exchange-mailbox/
weight: 30
type: docs
---

{{% alert color="primary" %}} 

Aspose.Email proporciona la capacidad de filtrar mensajes desde el buzón de Exchange utilizando el [EWSClient](https://apireference.aspose.com/cpp/email/class/aspose.email.clients.exchange.web_service.e_w_s_client/) y ExchangeQueryBuilder. Los mensajes se pueden filtrar a través de diferentes criterios, como por fecha, dominio, messageId y por notificaciones de entrega de correo. Este artículo muestra cómo filtrar mensajes desde el servidor de Exchange utilizando diferentes criterios.

{{% /alert %}} 
La clase [IEWSClient](https://apireference.aspose.com/cpp/email/class/aspose.email.clients.exchange.web_service.i_e_w_s_client/) proporciona el método [ListMessages()](https://apireference.aspose.com/cpp/email/class/aspose.email.clients.exchange.web_service.i_e_w_s_client/#aad8420247acd17cb1d73303ed1982d1e) que obtiene todos los mensajes de un buzón. Para obtener solo los mensajes que coinciden con alguna condición, utiliza el método sobrecargado [ListMessages()](https://apireference.aspose.com/cpp/email/class/aspose.email.clients.exchange.web_service.i_e_w_s_client/#ac7bbdcc7ccacd4e8288ae6c7d929ea52) que toma la clase *MailQuery* como argumento. La clase *MailQuery* proporciona varias propiedades para especificar condiciones, por ejemplo, fecha, asunto, remitente y destinatario.
##  **Filtrando Mensajes**
Para obtener mensajes filtrados de un buzón:

1. Conéctate al servidor de Exchange.
1. Crea una instancia de *MailQuery* y establece las propiedades deseadas.
1. Llama al método [IEWSClient->ListMessages](https://apireference.aspose.com/cpp/email/class/aspose.email.clients.exchange.web_service.i_e_w_s_client/#ac7bbdcc7ccacd4e8288ae6c7d929ea52) y pasa el *MailQuery* en los parámetros para obtener solo los mensajes filtrados.

El siguiente fragmento de código te muestra cómo obtener mensajes que contienen la cadena "Newsletter" en el asunto y que fueron enviados hoy.

{{< gist "aspose-com-gists" "525dd06c8783ebb18fb75cfc4b31d1ef" "Examples-Cpp-source-Exchange_EWS-FilterMessagesUsingEWS-FilterMessagesUsingEWS.cpp" >}}
##  **Filtrar Mensajes Basado en Criterios**
Los ejemplos de código anteriores filtran mensajes basados en el asunto de correo y la fecha. También podemos filtrar en otras propiedades. A continuación se presentan algunos ejemplos de cómo establecer las condiciones utilizando *MailQuery*.
###  **Criterios de Filtrado Fecha de Hoy**
El siguiente fragmento de código te muestra cómo filtrar correos en base a la fecha de hoy.

{{< gist "aspose-com-gists" "525dd06c8783ebb18fb75cfc4b31d1ef" "Examples-Cpp-source-Exchange_EWS-FilterMessagesOnCriteriaUsingEWS-GetEmailsWithTodayDate.cpp" >}}
###  **Criterios de Filtrado Rango de Fechas**
El siguiente fragmento de código te muestra cómo filtrar correos en base a un rango de fechas.

{{< gist "aspose-com-gists" "525dd06c8783ebb18fb75cfc4b31d1ef" "Examples-Cpp-source-Exchange_EWS-FilterMessagesOnCriteriaUsingEWS-GetEmailsOverDateRange.cpp" >}}
###  **Criterios de Filtrado Remitente Específico**
El siguiente fragmento de código te muestra cómo filtrar correos en base a un remitente específico.

{{< gist "aspose-com-gists" "525dd06c8783ebb18fb75cfc4b31d1ef" "Examples-Cpp-source-Exchange_EWS-FilterMessagesOnCriteriaUsingEWS-GetSpecificSenderEmails.cpp" >}}
###  **Criterios de Filtrado Dominio Específico**
El siguiente fragmento de código te muestra cómo filtrar correos en base a un dominio específico.

{{< gist "aspose-com-gists" "525dd06c8783ebb18fb75cfc4b31d1ef" "Examples-Cpp-source-Exchange_EWS-FilterMessagesOnCriteriaUsingEWS-GetSpecificDomainEmails.cpp" >}}
###  **Criterios de Filtrado Destinatario Específico**
El siguiente fragmento de código te muestra cómo filtrar correos en base a un destinatario específico.

{{< gist "aspose-com-gists" "525dd06c8783ebb18fb75cfc4b31d1ef" "Examples-Cpp-source-Exchange_EWS-FilterMessagesOnCriteriaUsingEWS-GetSpecificRecipientEmails.cpp" >}}
###  **Criterios de Filtrado Por MessageID**
El siguiente fragmento de código te muestra cómo filtrar correos en base a MessageID.

{{< gist "aspose-com-gists" "525dd06c8783ebb18fb75cfc4b31d1ef" "Examples-Cpp-source-Exchange_EWS-FilterMessagesOnCriteriaUsingEWS-GetSpecificMessageIdEmail.cpp" >}}
###  **Criterios de Filtrado Todas las Notificaciones de Entrega de Correo**
El siguiente fragmento de código te muestra cómo filtrar correos en base a todas las notificaciones de entrega de correo.

{{< gist "aspose-com-gists" "525dd06c8783ebb18fb75cfc4b31d1ef" "Examples-Cpp-source-Exchange_EWS-FilterMessagesOnCriteriaUsingEWS-GetMailDeliveryNotifications.cpp" >}}
###  **Filtrar por Tamaño de Mensaje**
{{< gist "aspose-com-gists" "525dd06c8783ebb18fb75cfc4b31d1ef" "Examples-Cpp-source-Exchange_EWS-FilterMessagesOnCriteriaUsingEWS-FilterMessagesByMessageSize.cpp" >}}
##  **Construyendo Consultas Complejas**
Si se establecen diferentes propiedades de [MailQueryBuilder](https://apireference.aspose.com/cpp/email/class/aspose.email.tools.search.mail_query_builder/) en una declaración separada, se cumplen todas las condiciones. Por ejemplo, para obtener un mensaje en un rango de fechas particular y de un host específico, escribe tres declaraciones:
###  **Combinando Consultas con AND**
El siguiente fragmento de código te muestra cómo combinar consultas con AND.

{{< gist "aspose-com-gists" "525dd06c8783ebb18fb75cfc4b31d1ef" "Examples-Cpp-source-Exchange_EWS-FilterWithComplexQueriesUsingEWS-CombineQueriesWithAND.cpp" >}}
###  **Combinando Consultas con OR**
[MailQueryBuilder](https://apireference.aspose.com/cpp/email/class/aspose.email.tools.search.mail_query_builder/) proporciona el método [Or()](https://apireference.aspose.com/cpp/email/class/aspose.email.tools.search.mail_query_builder/#afc735b8cd80758418502678ac69eecd4) que toma dos instancias de *MailQuery* como parámetros. Obtiene mensajes que coinciden con cualquiera de las dos condiciones especificadas. El siguiente ejemplo filtra mensajes que tienen la palabra “test” en el asunto o “noreply@host.com” como remitente. El siguiente fragmento de código te muestra cómo combinar consultas con OR.

{{< gist "aspose-com-gists" "525dd06c8783ebb18fb75cfc4b31d1ef" "Examples-Cpp-source-Exchange_EWS-FilterWithComplexQueriesUsingEWS-CombiningQueriesWithOR.cpp" >}}
##  **Filtrado de Correos Sensible a Mayúsculas y Minúsculas**
Los correos se pueden filtrar en función de la sensibilidad a mayúsculas y minúsculas al especificar la bandera IgnoreCase en los criterios de filtrado, como se muestra en el siguiente fragmento de código.

{{< gist "aspose-com-gists" "525dd06c8783ebb18fb75cfc4b31d1ef" "Examples-Cpp-source-Exchange_EWS-CaseSensitiveEmailsFilteringUsingEWS-CaseSensitiveEmailsFiltering.cpp" >}}
#  **Filtrando Mensajes con Soporte de Paginación**
{{< gist "aspose-com-gists" "525dd06c8783ebb18fb75cfc4b31d1ef" "Examples-Cpp-source-Exchange_EWS-FilterMessagesOnCriteriaUsingEWS-FilterMessagesWithPagingSupport.cpp" >}}