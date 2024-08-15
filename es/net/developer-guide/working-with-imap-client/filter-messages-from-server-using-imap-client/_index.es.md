---
title: "Filtrar mensajes del servidor mediante el cliente IMAP"
url: /es/net/filter-messages-from-server-using-imap-client/
weight: 40
type: docs
---


The [ImapClient](https://reference.aspose.com/email/net/aspose.email.clients.imap/imapclient/) la clase proporciona la [ListMessages()](https://reference.aspose.com/email/net/aspose.email.clients.imap/imapclient/listmessages/#listmessages) método que obtiene todos los mensajes de un buzón. Para recibir solo los mensajes que cumplen alguna condición, utilice el método sobrecargado [ListMessages()](https://reference.aspose.com/email/net/aspose.email.clients.imap/imapclient/listmessages/#listmessages) método que toma [MailQuery](https://reference.aspose.com/email/net/aspose.email.tools.search/mailquery/) como argumento. El [MailQuery](https://reference.aspose.com/email/net/aspose.email.tools.search/mailquery/) La clase proporciona varias propiedades para especificar las condiciones, por ejemplo, fecha, asunto, remitente, destinatario, etc. El primer ejemplo ilustra cómo filtrar los mensajes en función de la fecha y el asunto. También mostramos cómo filtrar según otros criterios y cómo crear consultas más complejas. La API también ofrece la capacidad de aplicar criterios de búsqueda que distinguen mayúsculas y minúsculas para que coincidan con los criterios de filtrado exactos. La API también permite especificar la codificación de la cadena de búsqueda para filtrar los mensajes del buzón.

## **Filtrar mensajes del buzón**

1. [Conectarse e iniciar sesión en un servidor IMAP](https://docs.aspose.com/email/es/net/connecting-to-imap-server/#connecting-with-imap-server)
2. Crea una instancia del [MailQuery](https://reference.aspose.com/email/net/aspose.email.tools.search/mailquery/) y establecer las propiedades
3. Llame al [`ImapClient.ListMessages(MailQuery query)`](https://reference.aspose.com/email/net/aspose.email.clients.imap/imapclient/listmessages/#listmessages_14) método y pase el [`MailQuery`](https://reference.aspose.com/email/net/aspose.email.tools.search/mailquery/) con los parámetros para obtener solo los mensajes filtrados.

El siguiente fragmento de código muestra cómo conectarse a un buzón IMAP y recibir los mensajes que llegaron hoy y que tienen la palabra «boletín» en el asunto.

{{< gist "aspose-com-gists" "6e5185a63aec6fd70d83098e82b06a32" "Examples-CSharp-IMAP-FilteringMessagesFromIMAPMailbox-FilteringMessagesFromIMAPMailbox.cs" >}}

## **Reciba mensajes que cumplan con criterios específicos**

[Los ejemplos de código anteriores](#filtering-messages-from-mailbox) filtra los mensajes según el asunto y la fecha del correo electrónico. También podemos usar otras propiedades para establecer otras condiciones compatibles. A continuación se muestran algunos ejemplos de cómo configurar las condiciones mediante [MailQuery](https://reference.aspose.com/email/net/aspose.email.tools.search/mailquery/). Los siguientes fragmentos de código muestran cómo filtrar los correos electrónicos según:

1. La fecha de hoy.
1. Un intervalo de fechas.
1. De un remitente específico.
1. De un dominio específico.
1. De un destinatario específico.

### **Fecha de hoy**

El siguiente fragmento de código muestra cómo filtrar los correos electrónicos en Fecha de hoy.

{{< gist "aspose-com-gists" "6e5185a63aec6fd70d83098e82b06a32" "Examples-CSharp-IMAP-GetMessagesWithSpecificCriteria-GetEmailsWithTodayDate.cs" >}}

### **Intervalo de fechas**

En el siguiente fragmento de código, se muestra cómo filtrar los correos electrónicos por intervalo de fechas.

{{< gist "aspose-com-gists" "6e5185a63aec6fd70d83098e82b06a32" "Examples-CSharp-IMAP-GetMessagesWithSpecificCriteria-GetEmailsOverDateRange.cs" >}}

### **Remitente específico**

El siguiente fragmento de código muestra cómo filtrar los correos electrónicos de un remitente específico.

{{< gist "aspose-com-gists" "6e5185a63aec6fd70d83098e82b06a32" "Examples-CSharp-IMAP-GetMessagesWithSpecificCriteria-GetSpecificSenderEmails.cs" >}}

### **Dominio específico**

El siguiente fragmento de código muestra cómo filtrar los correos electrónicos en un dominio específico.

{{< gist "aspose-com-gists" "6e5185a63aec6fd70d83098e82b06a32" "Examples-CSharp-IMAP-GetMessagesWithSpecificCriteria-GetSpecificDomainEmails.cs" >}}

### **Destinatario específico**

El siguiente fragmento de código muestra cómo filtrar los correos electrónicos de un destinatario específico.

{{< gist "aspose-com-gists" "6e5185a63aec6fd70d83098e82b06a32" "Examples-CSharp-IMAP-GetMessagesWithSpecificCriteria-GetSpecificRecipientEmails.cs" >}}

## **Creación de consultas complejas**

Si es diferente [MailQueryBuilder](https://reference.aspose.com/email/net/aspose.email.tools.search/mailquerybuilder/) las propiedades se establecen en declaraciones separadas, entonces todas las condiciones coincidirían. Por ejemplo, si queremos recibir mensajes entre un intervalo de fechas y los de un anfitrión específico, necesitamos escribir tres declaraciones.

### **Combinación de consultas con AND**

El siguiente fragmento de código muestra cómo combinar consultas con AND.

{{< gist "aspose-com-gists" "6e5185a63aec6fd70d83098e82b06a32" "Examples-CSharp-IMAP-BuildingComplexQueries-CombineQueriesWithAND.cs" >}}

### **Combinación de consultas con OR**

[MailQueryBuilder](https://reference.aspose.com/email/net/aspose.email.tools.search/mailquerybuilder/) proporciona la [Or()](https://reference.aspose.com/email/net/aspose.email.tools.search/mailquerybuilder/or/#or) método que requiere dos [MailQuery](https://reference.aspose.com/email/net/aspose.email.tools.search/mailquery/) instancias como parámetros. Obtiene los mensajes que cumplen cualquiera de las dos condiciones especificadas. El siguiente fragmento de código muestra cómo filtrar los mensajes que tienen la palabra «test» en el asunto o «noreply@host.com» como remitente. En el siguiente fragmento de código, se muestra cómo combinar consultas con OR.

{{< gist "aspose-com-gists" "6e5185a63aec6fd70d83098e82b06a32" "Examples-CSharp-IMAP-BuildingComplexQueries-CombiningQueriesWithOR.cs" >}}

## **Filtración en InternalDate**

Los mensajes se pueden extraer del servidor en función de InternalDate; sin embargo, a veces el servidor no devuelve todos los mensajes tal como aparecen en la bandeja de entrada. Su motivo puede ser la zona horaria del servidor, ya que es posible que no sea UTC para todos los servidores, como [Gmail](https://www.google.com.ua/search?client=opera&q=timezone+gmail&sourceid=opera&ie=utf-8&oe=utf-8&channel=suggest#channel=suggest&q=gmail+server+timezone++). Aspose envía comandos como 008 SEARCH EL 4 de mayo de 2014 según el [Protocolo IMAP](https://www.rfc-editor.org/rfc/rfc1730) sin embargo, el resultado puede variar debido a la configuración de la zona horaria del servidor. Se agrega un nuevo miembro en [ImapMessageInfo](https://reference.aspose.com/email/net/aspose.email.clients.imap/imapmessageinfo/) as [InternalDate](https://reference.aspose.com/email/net/aspose.email.clients.imap/imapmessageinfo/internaldate/) lo que ayuda aún más a filtrar los mensajes. El siguiente fragmento de código muestra el uso de [InternalDate](https://reference.aspose.com/email/net/aspose.email.clients.imap/imapmessageinfo/internaldate/) para filtrar los mensajes.

{{< gist "aspose-com-gists" "6e5185a63aec6fd70d83098e82b06a32" "Examples-CSharp-IMAP-InternalDateFilter-InternalDateFilter.cs" >}}

### **Filtrado de correos electrónicos sensibles a mayúsculas**

El siguiente fragmento de código muestra cómo usar el filtrado de correos electrónicos que distingue mayúsculas y minúsculas.

{{< gist "aspose-com-gists" "6e5185a63aec6fd70d83098e82b06a32" "Examples-CSharp-IMAP-CaseSensitiveEmailsFiltering-CaseSensitiveEmailsFiltering.cs" >}}

### **Especificar la codificación para Query Builder**

Las API [ImapQueryBuilder](https://reference.aspose.com/email/net/aspose.email.clients.imap/imapquerybuilder/) el constructor se puede usar para especificar la codificación de la cadena de búsqueda. Esto también se puede configurar usando el [DefaultEncoding](https://reference.aspose.com/email/net/aspose.email.tools.search/mailquerybuilder/defaultencoding/) propiedad de MailQueryBuilder. El siguiente fragmento de código muestra cómo especificar la codificación del generador de consultas.

{{< gist "aspose-com-gists" "6e5185a63aec6fd70d83098e82b06a32" "Examples-CSharp-IMAP-SpecifyEncodingForQueryBuilder-SpecifyEncodingForQueryBuilder.cs" >}}

### **Filtrar mensajes con soporte de paginación**

The [ImapClient](https://reference.aspose.com/email/net/aspose.email.clients.imap/imapclient/) brinda la capacidad de buscar mensajes en el buzón y enumerarlos con soporte de paginación. El siguiente fragmento de código muestra cómo filtrar los mensajes que admiten la paginación.

{{< gist "aspose-com-gists" "6e5185a63aec6fd70d83098e82b06a32" "Examples-CSharp-IMAP-SearchWithPagingSupport-SearchWithPagingSupport.cs" >}}

## **Filtrar mensajes con bandera personalizada**

{{< gist "aspose-com-gists" "6e5185a63aec6fd70d83098e82b06a32" "Examples-CSharp-IMAP-GetMessagesWithSpecificCriteria-GetMessagesWithCustomFlags.cs" >}}

## **Filtrar mensajes mediante la búsqueda personalizada**

Por ejemplo, el estándar RFC 3501 no permite una búsqueda de mensajes basada en la existencia de archivos adjuntos en los mensajes. Pero **Gmail** provides [Extensiones IMAP](https://developers.google.com/gmail/imap/imap-extensions?hl=ru) que permiten realizar dicha búsqueda. El siguiente fragmento de código muestra cómo realizar la consulta correspondiente.

```csharp
ImapQueryBuilder queryBuilder = new ImapQueryBuilder();
queryBuilder.CustomSearch("X-GM-RAW \"has:attachment\"");

MailQuery mailQuery = queryBuilder.GetQuery();
ImapMessageInfoCollection messageInfoCollection = imapClient.ListMessages(mailQuery);
```
