---
title: "Filtrar Mensajes del Servidor usando Cliente IMAP"
url: /es/net/filter-messages-from-server-using-imap-client/
weight: 40
type: docs
---

La clase [ImapClient](https://reference.aspose.com/email/net/aspose.email.clients.imap/imapclient/) ofrece el método [ListMessages()](https://reference.aspose.com/email/net/aspose.email.clients.imap/imapclient/listmessages/#listmessages) que obtiene todos los mensajes de un buzón. Para obtener solo los mensajes que coinciden con alguna condición, utiliza el método sobrecargado [ListMessages()](https://reference.aspose.com/email/net/aspose.email.clients.imap/imapclient/listmessages/#listmessages) que toma [MailQuery](https://reference.aspose.com/email/net/aspose.email.tools.search/mailquery/) como argumento. La clase [MailQuery](https://reference.aspose.com/email/net/aspose.email.tools.search/mailquery/) proporciona varias propiedades para especificar las condiciones, por ejemplo, fecha, asunto, remitente, destinatario, etc. El primer ejemplo ilustra cómo filtrar mensajes según la fecha y el asunto. También mostramos cómo filtrar por otros criterios y cómo construir consultas más complejas. La API también proporciona la capacidad de aplicar criterios de búsqueda que son sensibles a mayúsculas y minúsculas para hacer coincidir criterios de filtrado exactos. La API también permite especificar la codificación de la cadena de búsqueda para filtrar mensajes del buzón.

## **Filtrar Mensajes del Buzón**

1. [Conectar e iniciar sesión en un servidor IMAP](https://docs.aspose.com/email/es/net/connecting-to-imap-server/#connecting-with-imap-server)
2. Crear una instancia de [MailQuery](https://reference.aspose.com/email/net/aspose.email.tools.search/mailquery/) y establecer las propiedades
3. Llamar al método [`ImapClient.ListMessages(MailQuery query)`](https://reference.aspose.com/email/net/aspose.email.clients.imap/imapclient/listmessages/#listmessages_14) y pasar el [`MailQuery`](https://reference.aspose.com/email/net/aspose.email.tools.search/mailquery/) con los parámetros para obtener solo los mensajes filtrados.

El siguiente fragmento de código muestra cómo conectarse a un buzón IMAP y obtener mensajes que llegaron hoy y tienen la palabra "newsletter" en el asunto.

{{< gist "aspose-com-gists" "6e5185a63aec6fd70d83098e82b06a32" "Examples-CSharp-IMAP-FilteringMessagesFromIMAPMailbox-FilteringMessagesFromIMAPMailbox.cs" >}}

## **Obtener Mensajes que Cumplen Criterios Específicos**

[Los ejemplos de código anteriores](#filtering-messages-from-mailbox) filtran mensajes en función del asunto y la fecha del correo electrónico. También podemos usar otras propiedades para establecer otras condiciones soportadas. A continuación se presentan algunos ejemplos de cómo establecer las condiciones utilizando [MailQuery](https://reference.aspose.com/email/net/aspose.email.tools.search/mailquery/). Los siguientes fragmentos de código muestran cómo filtrar correos electrónicos en:

1. La fecha de hoy.
1. Un rango de fechas.
1. De un remitente específico.
1. De un dominio específico.
1. De un destinatario específico.

### **Fecha de Hoy**

El siguiente fragmento de código muestra cómo filtrar correos electrónicos en la Fecha de Hoy.

{{< gist "aspose-com-gists" "6e5185a63aec6fd70d83098e82b06a32" "Examples-CSharp-IMAP-GetMessagesWithSpecificCriteria-GetEmailsWithTodayDate.cs" >}}

### **Rango de Fechas**

El siguiente fragmento de código muestra cómo filtrar correos electrónicos en el rango de fechas.

{{< gist "aspose-com-gists" "6e5185a63aec6fd70d83098e82b06a32" "Examples-CSharp-IMAP-GetMessagesWithSpecificCriteria-GetEmailsOverDateRange.cs" >}}

### **Remitente Específico**

El siguiente fragmento de código muestra cómo filtrar correos electrónicos de un remitente específico.

{{< gist "aspose-com-gists" "6e5185a63aec6fd70d83098e82b06a32" "Examples-CSharp-IMAP-GetMessagesWithSpecificCriteria-GetSpecificSenderEmails.cs" >}}

### **Dominio Específico**

El siguiente fragmento de código muestra cómo filtrar correos electrónicos de un dominio específico.

{{< gist "aspose-com-gists" "6e5185a63aec6fd70d83098e82b06a32" "Examples-CSharp-IMAP-GetMessagesWithSpecificCriteria-GetSpecificDomainEmails.cs" >}}

### **Destinatario Específico**

El siguiente fragmento de código muestra cómo filtrar correos electrónicos de un destinatario específico.

{{< gist "aspose-com-gists" "6e5185a63aec6fd70d83098e82b06a32" "Examples-CSharp-IMAP-GetMessagesWithSpecificCriteria-GetSpecificRecipientEmails.cs" >}}

## **Construir Consultas Complejas**

Si diferentes propiedades de [MailQueryBuilder](https://reference.aspose.com/email/net/aspose.email.tools.search/mailquerybuilder/) se establecen en declaraciones separadas, entonces todas las condiciones se igualarán. Por ejemplo, si queremos obtener mensajes entre un rango de fechas y de un host específico, necesitamos escribir tres declaraciones.

### **Combinando Consultas con AND**

El siguiente fragmento de código muestra cómo combinar consultas con AND.

{{< gist "aspose-com-gists" "6e5185a63aec6fd70d83098e82b06a32" "Examples-CSharp-IMAP-BuildingComplexQueries-CombineQueriesWithAND.cs" >}}

### **Combinando Consultas con OR**

[MailQueryBuilder](https://reference.aspose.com/email/net/aspose.email.tools.search/mailquerybuilder/) proporciona el método [Or()](https://reference.aspose.com/email/net/aspose.email.tools.search/mailquerybuilder/or/#or) que toma dos instancias de [MailQuery](https://reference.aspose.com/email/net/aspose.email.tools.search/mailquery/) como parámetros. Obtiene los mensajes que coinciden con cualquiera de las dos condiciones especificadas. El siguiente fragmento de código muestra cómo filtrar mensajes que tienen “test” en el asunto o “noreply@host.com” como remitente. El siguiente fragmento de código muestra cómo combinar consultas con OR.

{{< gist "aspose-com-gists" "6e5185a63aec6fd70d83098e82b06a32" "Examples-CSharp-IMAP-BuildingComplexQueries-CombiningQueriesWithOR.cs" >}}

## **Filtración en InternalDate**

Los mensajes se pueden extraer del servidor en función de la InternalDate, sin embargo, a veces el servidor no devuelve todos los mensajes como se ve en la bandeja de entrada. Su razón puede ser la zona horaria del servidor, ya que puede no ser UTC para todos los servidores como [Gmail](https://www.google.com.ua/search?client=opera&q=timezone+gmail&sourceid=opera&ie=utf-8&oe=utf-8&channel=suggest#channel=suggest&q=gmail+server+timezone++). Aspose envía comandos como 008 SEARCH ON 4-May-2014 de acuerdo con el [protocolo IMAP](https://www.rfc-editor.org/rfc/rfc1730), sin embargo, el resultado puede diferir debido a la configuración de la zona horaria del servidor. Se añade un nuevo miembro en [ImapMessageInfo](https://reference.aspose.com/email/net/aspose.email.clients.imap/imapmessageinfo/) como [InternalDate](https://reference.aspose.com/email/net/aspose.email.clients.imap/imapmessageinfo/internaldate/) que ayuda además en la filtración de mensajes. El siguiente fragmento de código muestra el uso de [InternalDate](https://reference.aspose.com/email/net/aspose.email.clients.imap/imapmessageinfo/internaldate/) para filtrar mensajes.

{{< gist "aspose-com-gists" "6e5185a63aec6fd70d83098e82b06a32" "Examples-CSharp-IMAP-InternalDateFilter-InternalDateFilter.cs" >}}

### **Filtrado de Correos Electrónicos Sensible a Mayúsculas y Minúsculas**

El siguiente fragmento de código muestra cómo utilizar el filtrado de correos electrónicos sensible a mayúsculas y minúsculas.

{{< gist "aspose-com-gists" "6e5185a63aec6fd70d83098e82b06a32" "Examples-CSharp-IMAP-CaseSensitiveEmailsFiltering-CaseSensitiveEmailsFiltering.cs" >}}

### **Especificar Codificación para el Constructor de Consultas**

El constructor [ImapQueryBuilder](https://reference.aspose.com/email/net/aspose.email.clients.imap/imapquerybuilder/) de la API se puede utilizar para especificar la codificación para la cadena de búsqueda. Esto también se puede establecer utilizando la propiedad [DefaultEncoding](https://reference.aspose.com/email/net/aspose.email.tools.search/mailquerybuilder/defaultencoding/) del MailQueryBuilder. El siguiente fragmento de código muestra cómo especificar la codificación para el constructor de consultas.

{{< gist "aspose-com-gists" "6e5185a63aec6fd70d83098e82b06a32" "Examples-CSharp-IMAP-SpecifyEncodingForQueryBuilder-SpecifyEncodingForQueryBuilder.cs" >}}

### **Filtrar Mensajes con Soporte de Paginación**

El [ImapClient](https://reference.aspose.com/email/net/aspose.email.clients.imap/imapclient/) proporciona la capacidad de buscar mensajes del buzón y listarlos con soporte de paginación. El siguiente fragmento de código muestra cómo filtrar mensajes con soporte de paginación.

{{< gist "aspose-com-gists" "6e5185a63aec6fd70d83098e82b06a32" "Examples-CSharp-IMAP-SearchWithPagingSupport-SearchWithPagingSupport.cs" >}}

## **Filtrar Mensajes con Bandera Personalizada**

{{< gist "aspose-com-gists" "6e5185a63aec6fd70d83098e82b06a32" "Examples-CSharp-IMAP-GetMessagesWithSpecificCriteria-GetMessagesWithCustomFlags.cs" >}}

## **Filtrar Mensajes usando Búsquedas Personalizadas**

Por ejemplo, el estándar RFC 3501 no permite buscar mensajes en función de la existencia de archivos adjuntos en los mensajes. Pero **Gmail** proporciona [Extensiones IMAP](https://developers.google.com/gmail/imap/imap-extensions?hl=ru) que permiten realizar tal búsqueda. El siguiente fragmento de código muestra cómo hacer una consulta correspondiente.

```csharp
ImapQueryBuilder queryBuilder = new ImapQueryBuilder();
queryBuilder.CustomSearch("X-GM-RAW \"has:attachment\"");

MailQuery mailQuery = queryBuilder.GetQuery();
ImapMessageInfoCollection messageInfoCollection = imapClient.ListMessages(mailQuery);
```