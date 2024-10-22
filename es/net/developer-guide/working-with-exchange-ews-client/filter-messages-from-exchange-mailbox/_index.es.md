---
title: "Filtrar Mensajes Desde el Buzón de Exchange"
url: /es/net/filter-messages-from-exchange-mailbox/
weight: 30
type: docs
---

{{% alert color="primary" %}}

Aspose.Email para .NET proporciona la capacidad de filtrar mensajes desde el Buzón de Exchange utilizando EWSClient y ExchangeQueryBuilder. Los mensajes se pueden filtrar a través de diferentes criterios como por fecha, dominio, mensaje-id, y por Notificaciones de Entrega de Correo. Este artículo muestra cómo filtrar mensajes desde Exchange Server utilizando diferentes Criterios.

{{% /alert %}} 

## **Filtrando Mensajes utilizando EWS**

La [IEWSClient](https://reference.aspose.com/email/net/aspose.email.clients.exchange.webservice/iewsclient/) interface proporciona el [ListMessages()](https://reference.aspose.com/email/net/aspose.email.clients.exchange.webservice/iewsclient/listmessages/#listmessages) método que obtiene todos los mensajes de un buzón. Para obtener solo los mensajes que coinciden con alguna condición, utiliza el método sobrecargado [ListMessages()](https://reference.aspose.com/email/net/aspose.email.clients.exchange.webservice/iewsclient/listmessages/#listmessages) que toma la clase [MailQuery](https://reference.aspose.com/email/net/aspose.email.tools.search/mailquery/) como argumento. La clase [MailQuery](https://reference.aspose.com/email/net/aspose.email.tools.search/mailquery/) proporciona varias propiedades para especificar condiciones, por ejemplo, fecha, asunto, remitente y destinatario. Además, la API también permite aplicar filtros de case-sensitivity para recuperar correos electrónicos del buzón.

### **Filtrar Mensajes por Criterio**

Para obtener mensajes filtrados de un buzón:

1. Conéctate al servidor de Exchange.
2. Crea una instancia de [MailQuery](https://reference.aspose.com/email/net/aspose.email.tools.search/mailquery/) y establece las propiedades deseadas.
3. Llama al método [IEWSClient.ListMessages()](https://reference.aspose.com/email/net/aspose.email.clients.exchange.webservice/iewsclient/listmessages/#listmessages) y pasa el [MailQuery](https://reference.aspose.com/email/net/aspose.email.tools.search/mailquery/) en los parámetros para obtener solo los mensajes filtrados.

El siguiente fragmento de código muestra cómo conectarse a un buzón IMAP y obtener los mensajes que contienen la cadena "Newsletter" en el asunto y fueron enviados hoy.

{{< gist "aspose-com-gists" "6e5185a63aec6fd70d83098e82b06a32" "Examples-CSharp-Exchange_EWS-FilterMessagesUsingEWS-FilterMessagesUsingEWS.cs" >}}

#### **Filtrar Mensajes por la Fecha de Hoy**

El siguiente fragmento de código muestra cómo filtrar todos los correos electrónicos en función de la fecha de hoy.

{{< gist "aspose-com-gists" "6e5185a63aec6fd70d83098e82b06a32" "Examples-CSharp-Exchange_EWS-FilterMessagesOnCriteriaUsingEWS-GetEmailsWithTodayDate.cs" >}}

#### **Filtrar Mensajes por Rango de Fechas**

El siguiente fragmento de código muestra cómo filtrar todos los correos electrónicos en función del rango de fechas.

{{< gist "aspose-com-gists" "6e5185a63aec6fd70d83098e82b06a32" "Examples-CSharp-Exchange_EWS-FilterMessagesOnCriteriaUsingEWS-GetEmailsOverDateRange.cs" >}}

#### **Filtrar Mensajes por Remitente Específico**

El siguiente fragmento de código muestra cómo filtrar todos los correos electrónicos en función de un remitente específico.

{{< gist "aspose-com-gists" "6e5185a63aec6fd70d83098e82b06a32" "Examples-CSharp-Exchange_EWS-FilterMessagesOnCriteriaUsingEWS-GetSpecificSenderEmails.cs" >}}

#### **Filtrar Mensajes por Dominio Específico**

El siguiente fragmento de código muestra cómo filtrar todos los correos electrónicos en función de un dominio específico.

{{< gist "aspose-com-gists" "6e5185a63aec6fd70d83098e82b06a32" "Examples-CSharp-Exchange_EWS-FilterMessagesOnCriteriaUsingEWS-GetSpecificDomainEmails.cs" >}}

#### **Filtrar Mensajes por Destinatario Específico**

El siguiente fragmento de código muestra cómo filtrar todos los correos electrónicos en función de un destinatario específico.

{{< gist "aspose-com-gists" "6e5185a63aec6fd70d83098e82b06a32" "Examples-CSharp-Exchange_EWS-FilterMessagesOnCriteriaUsingEWS-GetSpecificRecipientEmails.cs" >}}

#### **Filtrar Mensajes por MessageID**

El siguiente fragmento de código muestra cómo filtrar todos los correos electrónicos en función del MessageID.

{{< gist "aspose-com-gists" "6e5185a63aec6fd70d83098e82b06a32" "Examples-CSharp-Exchange_EWS-FilterMessagesOnCriteriaUsingEWS-GetSpecificMessageIdEmail.cs" >}}

#### **Filtrar Mensajes por Todas las Notificaciones de Entrega de Correo**

El siguiente fragmento de código muestra cómo filtrar todos los correos electrónicos en función de todas las notificaciones de entrega de correo.

{{< gist "aspose-com-gists" "6e5185a63aec6fd70d83098e82b06a32" "Examples-CSharp-Exchange_EWS-FilterMessagesOnCriteriaUsingEWS-GetMailDeliveryNotifications.cs" >}}

#### **Filtrar Mensajes por Tamaño de Mensaje**

{{< gist "aspose-com-gists" "6e5185a63aec6fd70d83098e82b06a32" "Examples-CSharp-Exchange_EWS-FilterMessagesOnCriteriaUsingEWS-FilterMessagesByMessageSize.cs" >}}

### **Construyendo Consultas Complejas**

Si diferentes [MailQueryBuilder](https://reference.aspose.com/email/net/aspose.email.tools.search/mailquerybuilder/) propiedades se establecen en una declaración separada, se cumplen todas las condiciones. Por ejemplo, para obtener un mensaje en un rango de fechas particular y de un host específico, escribe tres declaraciones:

#### **Combinando Consultas con AND**

El siguiente fragmento de código muestra cómo combinar consultas con AND.

{{< gist "aspose-com-gists" "6e5185a63aec6fd70d83098e82b06a32" "Examples-CSharp-Exchange_EWS-FilterWithComplexQueriesUsingEWS-CombineQueriesWithAND.cs" >}}

#### **Combinando Consultas con OR**

[MailQueryBuilder](https://reference.aspose.com/email/net/aspose.email.tools.search/mailquerybuilder/) proporciona el método [Or()](https://reference.aspose.com/email/net/aspose.email.tools.search/mailquerybuilder/or/#or) que toma dos instancias de [MailQuery](https://reference.aspose.com/email/net/aspose.email.tools.search/mailquery/) como parámetros. Obtiene mensajes que coinciden con alguna de las dos condiciones especificadas. El ejemplo a continuación filtra mensajes que tienen la palabra “test” en el asunto o “noreply@host.com” como remitente. El siguiente fragmento de código muestra cómo combinar consultas con OR.

{{< gist "aspose-com-gists" "6e5185a63aec6fd70d83098e82b06a32" "Examples-CSharp-Exchange_EWS-FilterWithComplexQueriesUsingEWS-CombiningQueriesWithOR.cs" >}}

### **Filtrado de Correos Electrónicos Sensible a Mayúsculas y Minúsculas**

Los correos electrónicos se pueden filtrar en función de la sensibilidad a mayúsculas y minúsculas especificando la bandera IgnoreCase en los criterios de filtro como se muestra en el siguiente fragmento de código.

{{< gist "aspose-com-gists" "6e5185a63aec6fd70d83098e82b06a32" "Examples-CSharp-Exchange_EWS-CaseSensitiveEmailsFilteringUsingEWS-CaseSensitiveEmailsFiltering.cs" >}}

## **Filtrando Mensajes con Soporte de Paginación**

{{< gist "aspose-com-gists" "6e5185a63aec6fd70d83098e82b06a32" "Examples-CSharp-Exchange_EWS-FilterMessagesOnCriteriaUsingEWS-FilterMessagesWithPagingSupport.cs" >}}

## **Ordenando mensajes filtrados en orden ascendente/descendente**

El filtrado de correos electrónicos puede estar soportado con la clasificación de mensajes en orden ascendente/descendente. En este caso, el método [OrderBy](https://reference.aspose.com/email/net/aspose.email.tools.search/comparisonfield/orderby/) se utiliza para especificar el orden en que se ordenan los resultados de una búsqueda de correos electrónicos utilizando la clase MailQueryBuilder. Este método te permite definir criterios de ordenación para una consulta de búsqueda, especificando si los resultados deben clasificarse en orden ascendente o descendente según una propiedad particular.

El método acepta el parámetro ascendente, que especifica el orden de clasificación para la propiedad especificada. Si el parámetro ascendente es verdadero, significa que los resultados de la búsqueda deben ordenarse en orden ascendente. Por el contrario, si el parámetro ascendente es falso, significa que los resultados de la búsqueda deben ordenarse en orden descendente.

```cs
MailQueryBuilder builder = new MailQueryBuilder();
builder.Subject.Contains("Report");
builder.InternalDate.Since(new DateTime(2020, 1, 1));
builder.Subject.OrderBy(true); // ordenar el asunto de manera ascendente
builder.InternalDate.OrderBy(false); // ordenar la fecha de manera descendente

MailQuery query = builder.GetQuery();

// Obtener lista de mensajes
ExchangeMessageInfoCollection messages = client.ListMessages(client.MailboxInfo.InboxUri, query, false);
```

En el fragmento de código anterior, el método OrderBy se aplica dos veces, una para el asunto y otra para la fecha de los correos electrónicos. Como resultado de ejecutar el método ListMessages con la solicitud pasada, obtendremos una lista de mensajes con el asunto que contiene la palabra "Report" que fueron recibidos en la fecha especificada o después. Al mismo tiempo, los resultados estarán ordenados por asunto en orden ascendente. Esto significa que los mensajes se ordenarán alfabéticamente de A a Z, dependiendo de su asunto. Además, los resultados se ordenarán por fecha en orden descendente. Esto significa que las publicaciones se ordenarán de las más recientes a las más antiguas.