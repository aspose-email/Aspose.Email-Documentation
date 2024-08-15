---
title: "Filtrar mensajes del buzón de Exchange"
url: /es/cpp/filter-messages-from-exchange-mailbox/
weight: 30
type: docs
---

{{% alert color="primary" %}}

Aspose.Email ofrece la capacidad de filtrar los mensajes del buzón de Exchange mediante el [EWSClient](https://apireference.aspose.com/cpp/email/class/aspose.email.clients.exchange.web_service.e_w_s_client/) y ExchangeQueryBuilder. Los mensajes se pueden filtrar según diferentes criterios, como por fecha, dominio, ID de mensaje y notificaciones de entrega de correo. En este artículo se muestra cómo filtrar los mensajes de Exchange Server utilizando distintos criterios.

{{% /alert %}}
The [IEWSClient](https://apireference.aspose.com/cpp/email/class/aspose.email.clients.exchange.web_service.i_e_w_s_client/) la clase proporciona la [ListMessages()](https://apireference.aspose.com/cpp/email/class/aspose.email.clients.exchange.web_service.i_e_w_s_client/#aad8420247acd17cb1d73303ed1982d1e) método que obtiene todos los mensajes de un buzón. Para recibir solo los mensajes que cumplen alguna condición, utilice el método sobrecargado [ListMessages()](https://apireference.aspose.com/cpp/email/class/aspose.email.clients.exchange.web_service.i_e_w_s_client/#ac7bbdcc7ccacd4e8288ae6c7d929ea52) método que toma el *MailQuery* clase como argumento. El *MailQuery* La clase proporciona varias propiedades para especificar condiciones, por ejemplo, fecha, asunto, remitente y destinatario.
##  **Filtrado de mensajes**
Para obtener los mensajes filtrados de un buzón:

1. Conéctese al servidor Exchange.
1. Crea una instancia de *MailQuery* y defina las propiedades deseadas.
1. Llame al [IEWSClient->ListMessages](https://apireference.aspose.com/cpp/email/class/aspose.email.clients.exchange.web_service.i_e_w_s_client/#ac7bbdcc7ccacd4e8288ae6c7d929ea52) método y pase el *MailQuery* en los parámetros para obtener solo los mensajes filtrados.

El siguiente fragmento de código muestra cómo recibir los mensajes que tienen la cadena «Boletín» en el asunto y que se enviaron hoy.

{{< gist "aspose-com-gists" "525dd06c8783ebb18fb75cfc4b31d1ef" "Examples-Cpp-source-Exchange_EWS-FilterMessagesUsingEWS-FilterMessagesUsingEWS.cpp" >}}
##  **Filtrar mensajes según criterios**
Los ejemplos de código anteriores filtran los mensajes según el asunto y la fecha del correo electrónico. También podemos filtrar por otras propiedades. A continuación se muestran algunos ejemplos de cómo configurar las condiciones utilizando *MailQuery*.
###  **Filtrar criterios Fecha de hoy**
El siguiente fragmento de código muestra cómo filtrar los correos electrónicos en función de la fecha actual.



{{< gist "aspose-com-gists" "525dd06c8783ebb18fb75cfc4b31d1ef" "Examples-Cpp-source-Exchange_EWS-FilterMessagesOnCriteriaUsingEWS-GetEmailsWithTodayDate.cpp" >}}
###  **Rango de fechas de criterios de filtro**
El siguiente fragmento de código muestra cómo filtrar los correos electrónicos en función de un intervalo de fechas.



{{< gist "aspose-com-gists" "525dd06c8783ebb18fb75cfc4b31d1ef" "Examples-Cpp-source-Exchange_EWS-FilterMessagesOnCriteriaUsingEWS-GetEmailsOverDateRange.cpp" >}}
###  **Remitente específico de criterios de filtro**
El siguiente fragmento de código muestra cómo filtrar los correos electrónicos en función de un remitente específico.



{{< gist "aspose-com-gists" "525dd06c8783ebb18fb75cfc4b31d1ef" "Examples-Cpp-source-Exchange_EWS-FilterMessagesOnCriteriaUsingEWS-GetSpecificSenderEmails.cpp" >}}
###  **Dominio específico de criterios de filtrado**
El siguiente fragmento de código muestra cómo filtrar los correos electrónicos en función de un dominio específico.



{{< gist "aspose-com-gists" "525dd06c8783ebb18fb75cfc4b31d1ef" "Examples-Cpp-source-Exchange_EWS-FilterMessagesOnCriteriaUsingEWS-GetSpecificDomainEmails.cpp" >}}
###  **Destinatario específico de criterios de filtrado**
El siguiente fragmento de código muestra cómo filtrar los correos electrónicos en función de un destinatario específico.



{{< gist "aspose-com-gists" "525dd06c8783ebb18fb75cfc4b31d1ef" "Examples-Cpp-source-Exchange_EWS-FilterMessagesOnCriteriaUsingEWS-GetSpecificRecipientEmails.cpp" >}}
###  **Filtrar criterios por MessageID**
El siguiente fragmento de código muestra cómo filtrar los correos electrónicos en función de MessageID.



{{< gist "aspose-com-gists" "525dd06c8783ebb18fb75cfc4b31d1ef" "Examples-Cpp-source-Exchange_EWS-FilterMessagesOnCriteriaUsingEWS-GetSpecificMessageIdEmail.cpp" >}}
###  **Criterios de filtrado Todas las notificaciones de entrega de correo**
El siguiente fragmento de código muestra cómo filtrar los correos electrónicos en función de todas las notificaciones de entrega de correo.



{{< gist "aspose-com-gists" "525dd06c8783ebb18fb75cfc4b31d1ef" "Examples-Cpp-source-Exchange_EWS-FilterMessagesOnCriteriaUsingEWS-GetMailDeliveryNotifications.cpp" >}}
###  **Filtrar por tamaño de mensaje**
{{< gist "aspose-com-gists" "525dd06c8783ebb18fb75cfc4b31d1ef" "Examples-Cpp-source-Exchange_EWS-FilterMessagesOnCriteriaUsingEWS-FilterMessagesByMessageSize.cpp" >}}
##  **Creación de consultas complejas**
Si es diferente [MailQueryBuilder](https://apireference.aspose.com/cpp/email/class/aspose.email.tools.search.mail_query_builder/) las propiedades se establecen en una declaración separada, se cumplen todas las condiciones. Por ejemplo, para recibir un mensaje en un intervalo de fechas determinado y de un anfitrión específico, escribe tres afirmaciones:
###  **Combinación de consultas con AND**
El siguiente fragmento de código muestra cómo combinar consultas con AND.



{{< gist "aspose-com-gists" "525dd06c8783ebb18fb75cfc4b31d1ef" "Examples-Cpp-source-Exchange_EWS-FilterWithComplexQueriesUsingEWS-CombineQueriesWithAND.cpp" >}}
###  **Combinación de consultas con OR**

[MailQueryBuilder](https://apireference.aspose.com/cpp/email/class/aspose.email.tools.search.mail_query_builder/) proporciona la [Or()](https://apireference.aspose.com/cpp/email/class/aspose.email.tools.search.mail_query_builder/#afc735b8cd80758418502678ac69eecd4) método que requiere dos *MailQuery* instancias como parámetros. Recibe mensajes que cumplen cualquiera de las dos condiciones especificadas. El ejemplo siguiente filtra los mensajes que tienen la palabra «test» en el asunto o «noreply@host.com» como remitente. En el siguiente fragmento de código, se muestra cómo combinar consultas con OR.



{{< gist "aspose-com-gists" "525dd06c8783ebb18fb75cfc4b31d1ef" "Examples-Cpp-source-Exchange_EWS-FilterWithComplexQueriesUsingEWS-CombiningQueriesWithOR.cpp" >}}
##  **Filtrado de correo electrónico sensible a mayúsculas**
Los correos electrónicos se pueden filtrar en función de la distinción entre mayúsculas y minúsculas especificando el indicador IgnoreCase en los criterios de filtro, como se muestra en el siguiente fragmento de código.



{{< gist "aspose-com-gists" "525dd06c8783ebb18fb75cfc4b31d1ef" "Examples-Cpp-source-Exchange_EWS-CaseSensitiveEmailsFilteringUsingEWS-CaseSensitiveEmailsFiltering.cpp" >}}
#  **Filtrado de mensajes con soporte de paginación**
{{< gist "aspose-com-gists" "525dd06c8783ebb18fb75cfc4b31d1ef" "Examples-Cpp-source-Exchange_EWS-FilterMessagesOnCriteriaUsingEWS-FilterMessagesWithPagingSupport.cpp" >}}
