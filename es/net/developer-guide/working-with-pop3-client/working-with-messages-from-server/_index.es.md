---
title: "Trabajando con mensajes del servidor"
url: /es/net/working-with-messages-from-server/
weight: 50
type: docs
---


## **Obtener información sobre el buzón**

Podemos obtener información sobre el buzón, como el número de mensajes y el tamaño del buzón, mediante el [GetMailBoxSize](https://reference.aspose.com/email/net/aspose.email.clients.pop3/pop3client/getmailboxsize/#getmailboxsize/v) and [GetMailBoxInfo](https://reference.aspose.com/email/net/aspose.email.clients.pop3/pop3client/getmailboxinfo/#getmailboxinfo/) métodos del [Pop3Client](https://reference.aspose.com/email/net/aspose.email.clients.pop3/pop3client/) class.

- The [GetMailBoxSize](https://reference.aspose.com/email/net/aspose.email.clients.pop3/pop3client/getmailboxsize/#getmailboxsize/) el método devuelve el tamaño del buzón en bytes.
- The [GetMailBoxInfo](https://reference.aspose.com/email/net/aspose.email.clients.pop3/pop3client/getmailboxinfo/#getmailboxinfo/) método devuelve un objeto de tipo [Pop3MailBoxInfo](https://reference.aspose.com/email/net/aspose.email.clients.pop3/pop3mailboxinfo/).

También es posible obtener el número de mensajes mediante el [MessageCount](https://reference.aspose.com/email/net/aspose.email.clients.pop3/pop3mailboxinfo/messagecount/) propiedad y el tamaño utilizando el [OccupiedSize](https://reference.aspose.com/email/net/aspose.email.clients.pop3/pop3mailboxinfo/occupiedsize/) propiedad del [Pop3MailBoxInfo](https://reference.aspose.com/email/net/aspose.email.clients.pop3/pop3mailboxinfo/) clase. El siguiente código de ejemplo muestra cómo obtener información sobre el buzón. Muestra cómo:

1. Crea un [Pop3Client](https://reference.aspose.com/email/net/aspose.email.clients.pop3/pop3client/).
1. Conéctese a un servidor POP3.
1. Obtenga el tamaño del buzón.
1. Obtenga información sobre el buzón.
1. Obtenga el número de mensajes del buzón.
1. Consigue el tamaño ocupado.

{{< gist "aspose-com-gists" "6e5185a63aec6fd70d83098e82b06a32" "Examples-CSharp-POP3-GettingMailboxInfo-GettingMailboxInfo.cs" >}}

## **Obteniendo el recuento de correos electrónicos en el buzón**

El siguiente fragmento de código muestra cómo contar los mensajes de correo electrónico de un buzón.

{{< gist "aspose-com-gists" "6e5185a63aec6fd70d83098e82b06a32" "Examples-CSharp-POP3-GetEmailCountIntheMailbox-GetEmailCountIntheMailbox.cs" >}}

Aspose.Email permite a los desarrolladores trabajar con los correos electrónicos de muchas maneras diferentes. Por ejemplo, pueden recuperar la información del encabezado antes de decidir si descargan un correo electrónico. O pueden recuperar los correos electrónicos de un servidor y guardarlos sin analizarlos (más rápido) o después de analizarlos (más lento). En este artículo se muestra cómo recuperar y convertir correos electrónicos.

## **Recuperación de información de encabezados de correo electrónico**

Los encabezados de correo electrónico pueden proporcionarnos información sobre un mensaje de correo electrónico que podemos usar para decidir si queremos recuperar o no el mensaje de correo electrónico completo. Por lo general, la información del encabezado contiene el remitente, el asunto, la fecha de recepción, etc. (los encabezados de los correos electrónicos se describen en detalle en [Personalización de encabezados de correo electrónico](https://docs.aspose.com/email/es/net/creating-and-setting-contents-of-emails/#set-email-headers). Ese tema trata específicamente sobre el envío de un correo electrónico con SMTP, pero la información sobre el contenido del encabezado del correo electrónico sigue siendo válida (para los correos electrónicos POP3). En los siguientes ejemplos se muestra cómo recuperar los encabezados de correo electrónico de un servidor POP3 por el número de secuencia del mensaje.

{{< gist "aspose-com-gists" "6e5185a63aec6fd70d83098e82b06a32" "Examples-CSharp-POP3-RetrievingEmailHeaders-RetrievingEmailHeaders.cs" >}}

## **Recuperación de mensajes de correo electrónico**

The [Pop3Client](https://reference.aspose.com/email/net/aspose.email.clients.pop3/pop3client/) el componente de clase proporciona la capacidad de recuperar mensajes de correo electrónico del servidor POP3 y analizarlos en un [MailMessage](https://reference.aspose.com/email/net/aspose.email/mailmessage/) instancia con la ayuda de [MailMessage](https://reference.aspose.com/email/net/aspose.email/mailmessage/) componentes. El [MailMessage](https://reference.aspose.com/email/net/aspose.email/mailmessage/) La clase contiene varias propiedades y métodos para manipular el contenido del correo electrónico. Mediante el uso [FetchMessage](https://reference.aspose.com/email/net/aspose.email.clients.pop3/pop3client/fetchmessage/#fetchmessage/) método del [Pop3Client](https://reference.aspose.com/email/net/aspose.email.clients.pop3/pop3client/) clase, puedes obtener un [MailMessage](https://reference.aspose.com/email/net/aspose.email/mailmessage/) instancia directamente desde el servidor POP3. El siguiente fragmento de código muestra cómo recuperar un mensaje de correo electrónico completo del servidor POP3.

{{< gist "aspose-com-gists" "6e5185a63aec6fd70d83098e82b06a32" "Examples-CSharp-POP3-RetrievingEmailMessages-RetrievingEmailMessages.cs" >}}

## **Recuperación de la información resumida del mensaje mediante un identificador único**

El cliente POP3 de la API puede recuperar la información resumida del mensaje del servidor mediante el identificador único del mensaje. Esto proporciona un acceso rápido a la información breve del mensaje sin tener que recuperar primero el mensaje completo del servidor. El siguiente fragmento de código muestra cómo recuperar la información resumida del mensaje.

{{< gist "aspose-com-gists" "6e5185a63aec6fd70d83098e82b06a32" "Examples-CSharp-POP3-RetrieveMessageSummaryInformationUsingUniqueId-RetrieveMessageSummaryInformationUsingUniqueId.cs" >}}

## **Listar mensajes con MultiConnection**

[Pop3Client](https://reference.aspose.com/email/net/aspose.email.clients.pop3/pop3client/) proporciona un [UseMultiConnection](https://reference.aspose.com/email/net/aspose.email.clients/emailclient/usemulticonnection/) propiedad que se puede usar para crear múltiples conexiones para operaciones pesadas. También puede establecer el número de conexiones que se usarán durante el modo multiconexión utilizando [Pop3Client.ConnectionsQuantity](https://reference.aspose.com/email/net/aspose.email.clients/emailclient/connectionsquantity/). El siguiente fragmento de código muestra el uso del modo multiconexión para enumerar los mensajes y compara su rendimiento con el modo de conexión única.

{{< gist "aspose-com-gists" "522d47278b8ca448dc1d7eb97193322c" "Examples-CSharp-POP3-Pop3ListMessagesWithMultiConnection-1.cs" >}}

{{% alert color="primary" %}}

Tenga en cuenta que el uso del modo multiconexión no garantiza un aumento del rendimiento.

{{% /alert %}}

## **Obtener mensajes del servidor y guardarlos en el disco**

### **Guardar el mensaje en el disco sin analizarlo**

Si desea descargar mensajes de correo electrónico del servidor POP3 sin analizarlos, utilice el [Pop3Client](https://reference.aspose.com/email/net/aspose.email.clients.pop3/pop3client/) class [SaveMessage](https://reference.aspose.com/email/net/aspose.email.clients.pop3/pop3client/savemessage/#savemessage/) función. El [SaveMessage](https://reference.aspose.com/email/net/aspose.email.clients.pop3/pop3client/savemessage/#savemessage/) la función no analiza el mensaje de correo electrónico, por lo que es más rápida que [FetchMessage](https://reference.aspose.com/email/net/aspose.email.clients.pop3/pop3client/fetchmessage/#fetchmessage/) función. El siguiente fragmento de código muestra cómo guardar un mensaje por su número de secuencia. En este caso, el [SaveMessage](https://reference.aspose.com/email/net/aspose.email.clients.pop3/pop3client/savemessage/#savemessage/) El método guarda el mensaje en el formato EML original sin analizarlo.

{{< gist "aspose-com-gists" "6e5185a63aec6fd70d83098e82b06a32" "Examples-CSharp-POP3-SaveToDiskWithoutParsing-SaveToDiskWithoutParsing.cs" >}}

### **Analiza el mensaje antes de guardarlo**

El siguiente fragmento de código usa el [Pop3Client](https://reference.aspose.com/email/net/aspose.email.clients.pop3/pop3client/) [FetchMessage](https://reference.aspose.com/email/net/aspose.email.clients.pop3/pop3client/fetchmessage/#fetchmessage/) método para recuperar un mensaje de un servidor POP3 por su número de secuencia y, a continuación, guardar el mensaje en el disco con el asunto como nombre de archivo.

{{< gist "aspose-com-gists" "6e5185a63aec6fd70d83098e82b06a32" "Examples-CSharp-POP3-ParseMessageAndSave-ParseMessageAndSave.cs" >}}

## **Mensajes de búsqueda grupales**

[Pop3Client](https://reference.aspose.com/email/net/aspose.email.clients.pop3/pop3client/) proporciona un [FetchMessages](https://docs.aspose.com/email/es/net/working-with-messages-from-server/) método que acepta números de secuencia iterables o ID únicos y devuelve una lista de [MailMessage](https://reference.aspose.com/email/net/aspose.email/mailmessage/). El siguiente fragmento de código demuestra el uso del [FetchMessages](https://docs.aspose.com/email/es/net/working-with-messages-from-server/) método para buscar mensajes por números de secuencia e ID único.

{{< gist "aspose-com-gists" "522d47278b8ca448dc1d7eb97193322c" "Examples-CSharp-POP3-Pop3FetchGroupMessages-1.cs" >}}

## **Filtrar mensajes por remitente, destinatario o fecha**

The [Pop3Client](https://reference.aspose.com/email/net/aspose.email.clients.pop3/pop3client/) clase, descrita en [Conexión a un servidor POP3](https://docs.aspose.com/email/es/net/connect-to-pop3-server/), proporciona la [ListMessages()](https://reference.aspose.com/email/net/aspose.email.clients.pop3/pop3client/listmessages/#listmessages/) método que obtiene todos los mensajes de un buzón. Para recibir solo los mensajes que cumplen alguna condición, utilice el método sobrecargado [ListMessages()](https://reference.aspose.com/email/net/aspose.email.clients.pop3/pop3client/listmessages/#listmessages/) método que toma [MailQuery](https://reference.aspose.com/email/net/aspose.email.tools.search/mailquery/) como argumento. El [MailQuery](https://reference.aspose.com/email/net/aspose.email.tools.search/mailquery/) La clase proporciona varias propiedades para especificar las condiciones de la consulta, por ejemplo, fecha, asunto, remitente, destinatario, etc. El [MailQueryBuilder](https://reference.aspose.com/email/net/aspose.email.tools.search/mailquerybuilder/) la clase se usa para construir la expresión de búsqueda. En primer lugar, se establecen todas las condiciones y restricciones y, a continuación [MailQuery](https://reference.aspose.com/email/net/aspose.email.tools.search/mailquery/) se rellena con la consulta desarrollada por [MailQueryBuilder](https://reference.aspose.com/email/net/aspose.email.tools.search/mailquerybuilder/). El [MailQuery](https://reference.aspose.com/email/net/aspose.email.tools.search/mailquery/) el objeto de clase es utilizado por [Pop3Client](https://reference.aspose.com/email/net/aspose.email.clients.pop3/pop3client/) para extraer la información filtrada del servidor. En este artículo se muestra cómo filtrar los mensajes de correo electrónico de un buzón. El primer ejemplo ilustra cómo filtrar los mensajes según la fecha y el asunto. También mostramos cómo filtrar según otros criterios y cómo crear consultas más complejas. También muestra la aplicación del filtro de fecha y hora para recuperar los correos electrónicos específicos del buzón. Además, también muestra cómo aplicar el filtrado que distingue entre mayúsculas y minúsculas.

### **Filtrar mensajes del buzón**

Para filtrar los mensajes de un buzón:

1. [Conectarse e iniciar sesión en un servidor POP3](https://docs.aspose.com/email/es/net/connect-to-pop3-server/#connecting-to-pop3-server).
2. Crea una instancia de [MailQuery](https://reference.aspose.com/email/net/aspose.email.tools.search/mailquery/) y defina las propiedades deseadas.
3. Llame al [`Pop3Client.ListMessages(MailQuery query)`](https://reference.aspose.com/email/net/aspose.email.clients.pop3/pop3client/listmessages/#listmessages_8) método y pase el [MailQuery](https://reference.aspose.com/email/net/aspose.email.tools.search/mailquery/) en los parámetros para obtener solo los mensajes filtrados.

El siguiente fragmento de código muestra cómo conectarse a un buzón POP3 y recibir los mensajes que llegaron hoy y que tienen la palabra «boletín» en el asunto.

{{< gist "aspose-com-gists" "6e5185a63aec6fd70d83098e82b06a32" "Examples-CSharp-POP3-FilterMessagesFromPOP3Mailbox-FilterMessagesFromPOP3Mailbox.cs" >}}

### **Recibir mensajes que cumplan con criterios específicos**

[Los ejemplos de código anteriores](https://docs.aspose.com/email/es/net/working-with-messages-from-server/#filtering-messages-from-mailbox) muestra cómo puede filtrar los mensajes según el asunto y la fecha del correo electrónico. También podemos usar otras propiedades para establecer otras condiciones admitidas. A continuación se muestran algunos ejemplos de cómo configurar las condiciones mediante [MailQuery](https://reference.aspose.com/email/net/aspose.email.tools.search/mailquery/).

Los siguientes fragmentos de código muestran cómo filtrar los correos electrónicos según otros criterios:

- Encuentra los correos electrónicos enviados hoy.
- Busca los correos electrónicos recibidos dentro de un rango.
- Busca correos electrónicos de un remitente específico.
- Busca correos electrónicos enviados desde un dominio específico.
- Busca los correos electrónicos enviados a un destinatario específico.
 
#### **Fecha de hoy**

En el siguiente fragmento de código, se muestra cómo encontrar los correos electrónicos que se han entregado hoy.

{{< gist "aspose-com-gists" "6e5185a63aec6fd70d83098e82b06a32" "Examples-CSharp-POP3-GetMessagesUsingSpecificCriteria-GetEmailsWithTodayDate.cs" >}}

#### **Intervalo de fechas**

El siguiente fragmento de código muestra cómo buscar los correos electrónicos recibidos dentro de un rango.

{{< gist "aspose-com-gists" "6e5185a63aec6fd70d83098e82b06a32" "Examples-CSharp-POP3-GetMessagesUsingSpecificCriteria-GetEmailsOverDateRange.cs" >}}

#### **Remitente específico**

El siguiente fragmento de código muestra cómo buscar correos electrónicos de un remitente específico.

{{< gist "aspose-com-gists" "6e5185a63aec6fd70d83098e82b06a32" "Examples-CSharp-POP3-GetMessagesUsingSpecificCriteria-GetSpecificSenderEmails.cs" >}}

#### **Dominio específico**

El siguiente fragmento de código muestra cómo encontrar los correos electrónicos enviados desde un dominio específico.

{{< gist "aspose-com-gists" "6e5185a63aec6fd70d83098e82b06a32" "Examples-CSharp-POP3-GetMessagesUsingSpecificCriteria-GetSpecificDomainEmails.cs" >}}

#### **Destinatario específico**

El siguiente fragmento de código muestra cómo encontrar los correos electrónicos enviados a un destinatario específico.

{{< gist "aspose-com-gists" "6e5185a63aec6fd70d83098e82b06a32" "Examples-CSharp-POP3-GetMessagesUsingSpecificCriteria-GetSpecificRecipientEmails.cs" >}}

### **Creación de consultas complejas**

Si es diferente [MailQueryBuilder](https://reference.aspose.com/email/net/aspose.email.tools.search/mailquerybuilder/) las propiedades se establecen en declaraciones separadas, entonces todas las condiciones coincidirían. Por ejemplo, si queremos recibir mensajes entre un intervalo de fechas y los de un anfitrión específico, necesitamos escribir tres declaraciones.

#### **Combinación de consultas con AND**

El siguiente fragmento de código muestra cómo combinar consultas con AND.

{{< gist "aspose-com-gists" "6e5185a63aec6fd70d83098e82b06a32" "Examples-CSharp-POP3-BuildComplexQueries-CombineQueriesWithAND.cs" >}}

#### **Combinación de consultas con OR**

[MailQueryBuilder](https://reference.aspose.com/email/net/aspose.email.tools.search/mailquerybuilder/) proporciona la [Or()](https://reference.aspose.com/email/net/aspose.email.tools.search/mailquerybuilder/or/#or) método que requiere dos [MailQuery](https://reference.aspose.com/email/net/aspose.email.tools.search/mailquery/) instancias como parámetros. Obtiene los mensajes que cumplen cualquiera de las dos condiciones especificadas. El siguiente fragmento de código muestra cómo filtrar los mensajes que tienen la palabra «test» en el asunto o «noreply@host.com» como remitente. En el siguiente fragmento de código, se muestra cómo combinar consultas con OR.

{{< gist "aspose-com-gists" "6e5185a63aec6fd70d83098e82b06a32" "Examples-CSharp-POP3-BuildComplexQueries-CombiningQueriesWithOR.cs" >}}

#### **Aplicar filtros que distinguen mayúsculas y minúsculas**

La API también ofrece la capacidad de filtrar los correos electrónicos del buzón según un criterio que distingue mayúsculas y minúsculas. Los siguientes métodos permiten buscar correos electrónicos especificando la distinción entre mayúsculas y minúsculas.

- Method `Aspose.Email.StringComparisonField.Contains(string value, bool ignoreCase)`
- Method `Aspose.Email.StringComparisonField.Equals(string value, bool ignoreCase)`
- Method `Aspose.Email.StringComparisonField.NotContains(string value, bool ignoreCase)`
- Method `Aspose.Email.StringComparisonField.NotEquals(string value, bool ignoreCase)`

{{< gist "aspose-com-gists" "6e5185a63aec6fd70d83098e82b06a32" "Examples-CSharp-POP3-ApplyCaseSensitiveFilters-ApplyCaseSensitiveFilters.cs" >}}
