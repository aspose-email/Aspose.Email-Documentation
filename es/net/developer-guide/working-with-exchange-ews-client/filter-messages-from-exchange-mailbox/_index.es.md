---
title: "Filtrar mensajes del buzón de Exchange"
url: /es/net/filter-messages-from-exchange-mailbox/
weight: 30
type: docs
---


{{% alert color="primary" %}}

Aspose.Email para.NET ofrece la capacidad de filtrar los mensajes del buzón de Exchange mediante EWSClient y ExchangeQueryBuilder. Los mensajes se pueden filtrar según diferentes criterios, como por fecha, dominio, identificador de mensaje y notificaciones de entrega de correo. En este artículo se muestra cómo filtrar los mensajes de Exchange Server utilizando diferentes criterios.

{{% /alert %}}

## **Filtrado de mensajes mediante EWS**

The [IEWSClient](https://reference.aspose.com/email/net/aspose.email.clients.exchange.webservice/iewsclient/) la interfaz proporciona [ListMessages()](https://reference.aspose.com/email/net/aspose.email.clients.exchange.webservice/iewsclient/listmessages/#listmessages) método que obtiene todos los mensajes de un buzón. Para recibir solo los mensajes que cumplen alguna condición, utilice el método sobrecargado [ListMessages()](https://reference.aspose.com/email/net/aspose.email.clients.exchange.webservice/iewsclient/listmessages/#listmessages) método que toma el [MailQuery](https://reference.aspose.com/email/net/aspose.email.tools.search/mailquery/) clase como argumento. El [MailQuery](https://reference.aspose.com/email/net/aspose.email.tools.search/mailquery/) La clase proporciona varias propiedades para especificar condiciones, por ejemplo, fecha, asunto, remitente y destinatario. Además, la API también permite aplicar filtros que distinguen mayúsculas y minúsculas para recuperar correos electrónicos del buzón.

### **Filtrar mensajes según criterios**

Para obtener los mensajes filtrados de un buzón:

1. Conéctese al servidor Exchange.
1. Crea una instancia de [MailQuery](https://reference.aspose.com/email/net/aspose.email.tools.search/mailquery/) y defina las propiedades deseadas.
1. Llame al [IEWSClient.ListMessages()](https://reference.aspose.com/email/net/aspose.email.clients.exchange.webservice/iewsclient/listmessages/#listmessages) método y pase el [MailQuery](https://reference.aspose.com/email/net/aspose.email.tools.search/mailquery/) en los parámetros para obtener solo los mensajes filtrados.

El siguiente fragmento de código muestra cómo conectarse a un buzón IMAP y recibir los mensajes que tengan la cadena «Boletín» en el asunto y que se hayan enviado hoy.

{{< gist "aspose-com-gists" "6e5185a63aec6fd70d83098e82b06a32" "Examples-CSharp-Exchange_EWS-FilterMessagesUsingEWS-FilterMessagesUsingEWS.cs" >}}

#### **Filtrar mensajes por fecha de hoy**

El siguiente fragmento de código muestra cómo filtrar todos los correos electrónicos en función de la fecha actual.

{{< gist "aspose-com-gists" "6e5185a63aec6fd70d83098e82b06a32" "Examples-CSharp-Exchange_EWS-FilterMessagesOnCriteriaUsingEWS-GetEmailsWithTodayDate.cs" >}}

#### **Filtrar mensajes por rango de fechas**

El siguiente fragmento de código muestra cómo filtrar todos los correos electrónicos en función del intervalo de fechas.

{{< gist "aspose-com-gists" "6e5185a63aec6fd70d83098e82b06a32" "Examples-CSharp-Exchange_EWS-FilterMessagesOnCriteriaUsingEWS-GetEmailsOverDateRange.cs" >}}

#### **Filtrar mensajes por remitente específico**

El siguiente fragmento de código muestra cómo filtrar todos los correos electrónicos en función de un remitente específico.

{{< gist "aspose-com-gists" "6e5185a63aec6fd70d83098e82b06a32" "Examples-CSharp-Exchange_EWS-FilterMessagesOnCriteriaUsingEWS-GetSpecificSenderEmails.cs" >}}

#### **Filtrar mensajes por dominio específico**

El siguiente fragmento de código muestra cómo filtrar todos los correos electrónicos en función de un dominio específico.

{{< gist "aspose-com-gists" "6e5185a63aec6fd70d83098e82b06a32" "Examples-CSharp-Exchange_EWS-FilterMessagesOnCriteriaUsingEWS-GetSpecificDomainEmails.cs" >}}

#### **Filtrar mensajes por destinatario específico**

El siguiente fragmento de código muestra cómo filtrar todos los correos electrónicos en función de un destinatario específico.

{{< gist "aspose-com-gists" "6e5185a63aec6fd70d83098e82b06a32" "Examples-CSharp-Exchange_EWS-FilterMessagesOnCriteriaUsingEWS-GetSpecificRecipientEmails.cs" >}}

#### **Filtrar mensajes por MessageID**

El siguiente fragmento de código muestra cómo filtrar todos los correos electrónicos en función de MessageID.

{{< gist "aspose-com-gists" "6e5185a63aec6fd70d83098e82b06a32" "Examples-CSharp-Exchange_EWS-FilterMessagesOnCriteriaUsingEWS-GetSpecificMessageIdEmail.cs" >}}

#### **Filtrar mensajes por todas las notificaciones de entrega de correo**

El siguiente fragmento de código muestra cómo filtrar todos los correos electrónicos en función de todas las notificaciones de entrega de correo.

{{< gist "aspose-com-gists" "6e5185a63aec6fd70d83098e82b06a32" "Examples-CSharp-Exchange_EWS-FilterMessagesOnCriteriaUsingEWS-GetMailDeliveryNotifications.cs" >}}

#### **Filtrar mensajes por tamaño de mensaje**

{{< gist "aspose-com-gists" "6e5185a63aec6fd70d83098e82b06a32" "Examples-CSharp-Exchange_EWS-FilterMessagesOnCriteriaUsingEWS-FilterMessagesByMessageSize.cs" >}}


### **Creación de consultas complejas**

Si es diferente [MailQueryBuilder](https://reference.aspose.com/email/net/aspose.email.tools.search/mailquerybuilder/) las propiedades se establecen en una declaración separada, se cumplen todas las condiciones. Por ejemplo, para recibir un mensaje en un intervalo de fechas determinado y de un anfitrión específico, escribe tres afirmaciones:

#### **Combinación de consultas con AND**

El siguiente fragmento de código muestra cómo combinar consultas con AND.

{{< gist "aspose-com-gists" "6e5185a63aec6fd70d83098e82b06a32" "Examples-CSharp-Exchange_EWS-FilterWithComplexQueriesUsingEWS-CombineQueriesWithAND.cs" >}}

#### **Combinación de consultas con OR**

[MailQueryBuilder](https://reference.aspose.com/email/net/aspose.email.tools.search/mailquerybuilder/) proporciona la [Or()](https://reference.aspose.com/email/net/aspose.email.tools.search/mailquerybuilder/or/#or) método que requiere dos [MailQuery](https://reference.aspose.com/email/net/aspose.email.tools.search/mailquery/) instancias como parámetros. Recibe mensajes que cumplen cualquiera de las dos condiciones especificadas. El ejemplo siguiente filtra los mensajes que tienen la palabra «test» en el asunto o «noreply@host.com» como remitente. En el siguiente fragmento de código, se muestra cómo combinar consultas con OR.

{{< gist "aspose-com-gists" "6e5185a63aec6fd70d83098e82b06a32" "Examples-CSharp-Exchange_EWS-FilterWithComplexQueriesUsingEWS-CombiningQueriesWithOR.cs" >}}

### **Filtrado de correo electrónico sensible a mayúsculas**

Los correos electrónicos se pueden filtrar en función de la distinción entre mayúsculas y minúsculas especificando el indicador IgnoreCase en los criterios de filtro, como se muestra en el siguiente fragmento de código.

{{< gist "aspose-com-gists" "6e5185a63aec6fd70d83098e82b06a32" "Examples-CSharp-Exchange_EWS-CaseSensitiveEmailsFilteringUsingEWS-CaseSensitiveEmailsFiltering.cs" >}}

## **Filtrado de mensajes con soporte de paginación**

{{< gist "aspose-com-gists" "6e5185a63aec6fd70d83098e82b06a32" "Examples-CSharp-Exchange_EWS-FilterMessagesOnCriteriaUsingEWS-FilterMessagesWithPagingSupport.cs" >}}

## **Clasificación de los mensajes filtrados en orden ascendente/descendente**

El filtrado de correo electrónico puede ser compatible con la clasificación de los mensajes en orden ascendente/descendente. En este caso, [OrderBy](https://reference.aspose.com/email/net/aspose.email.tools.search/comparisonfield/orderby/) El método se usa para especificar el orden en el que se ordenan los resultados de una búsqueda de correo electrónico mediante la clase MailQueryBuilder. Este método permite definir los criterios de clasificación de una consulta de búsqueda, especificando si los resultados se deben ordenar de forma ascendente o descendente en función de una propiedad concreta.

El método acepta el parámetro ascendente, que especifica el orden de clasificación de la propiedad especificada. Si el parámetro ascendente es verdadero, significa que los resultados de la búsqueda deben ordenarse en orden ascendente. Por el contrario, si el parámetro ascendente es falso, significa que los resultados de la búsqueda deben ordenarse en orden descendente.

```cs
MailQueryBuilder builder = new MailQueryBuilder();
builder.Subject.Contains("Report");
builder.InternalDate.Since(new DateTime(2020, 1, 1));
builder.Subject.OrderBy(true); // sort the subject ascending
builder.InternalDate.OrderBy(false); // sort the date descending

MailQuery query = builder.GetQuery();

// Get list of messages
ExchangeMessageInfoCollection messages = client.ListMessages(client.MailboxInfo.InboxUri, query, false);
```

En el fragmento de código anterior, el método orderBy se aplica dos veces, una para el asunto y otra para la fecha de los correos electrónicos. Al ejecutar el método ListMessages con la solicitud aprobada, obtendremos una lista de los mensajes cuyo asunto contiene la palabra «Denunciar» y que se recibieron en la fecha especificada o en una fecha posterior. Al mismo tiempo, los resultados se ordenarán por asunto en orden ascendente. Esto significa que los mensajes se ordenarán alfabéticamente de la A a la Z, según su asunto. Además, los resultados se ordenarán por fecha en orden descendente. Esto significa que las publicaciones se ordenarán de la más reciente a la más antigua.
