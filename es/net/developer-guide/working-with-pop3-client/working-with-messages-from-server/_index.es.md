---
title: "Trabajando con Mensajes del Servidor"
url: /es/net/working-with-messages-from-server/
weight: 50
type: docs
---

## **Obteniendo Información de la Buzón de Correo**

Podemos obtener información sobre la bandeja de entrada, como el número de mensajes y el tamaño de la bandeja, utilizando los métodos [GetMailBoxSize](https://reference.aspose.com/email/net/aspose.email.clients.pop3/pop3client/getmailboxsize/#getmailboxsize/v) y [GetMailBoxInfo](https://reference.aspose.com/email/net/aspose.email.clients.pop3/pop3client/getmailboxinfo/#getmailboxinfo/) de la clase [Pop3Client](https://reference.aspose.com/email/net/aspose.email.clients.pop3/pop3client/).

- El método [GetMailBoxSize](https://reference.aspose.com/email/net/aspose.email.clients.pop3/pop3client/getmailboxsize/#getmailboxsize/) devuelve el tamaño de la bandeja de entrada en bytes.
- El método [GetMailBoxInfo](https://reference.aspose.com/email/net/aspose.email.clients.pop3/pop3client/getmailboxinfo/#getmailboxinfo/) devuelve un objeto de tipo [Pop3MailBoxInfo](https://reference.aspose.com/email/net/aspose.email.clients.pop3/pop3mailboxinfo/).

También es posible obtener el número de mensajes usando la propiedad [MessageCount](https://reference.aspose.com/email/net/aspose.email.clients.pop3/pop3mailboxinfo/messagecount/) y el tamaño usando la propiedad [OccupiedSize](https://reference.aspose.com/email/net/aspose.email.clients.pop3/pop3mailboxinfo/occupiedsize/) de la clase [Pop3MailBoxInfo](https://reference.aspose.com/email/net/aspose.email.clients.pop3/pop3mailboxinfo/). El siguiente código de ejemplo muestra cómo obtener información sobre la bandeja de entrada. Muestra cómo:

1. Crear un [Pop3Client](https://reference.aspose.com/email/net/aspose.email.clients.pop3/pop3client/).
1. Conectarse a un servidor POP3.
1. Obtener el tamaño de la bandeja de entrada.
1. Obtener información de la bandeja de entrada.
1. Obtener el número de mensajes en la bandeja de entrada.
1. Obtener el tamaño ocupado.

{{< gist "aspose-com-gists" "6e5185a63aec6fd70d83098e82b06a32" "Examples-CSharp-POP3-GettingMailboxInfo-GettingMailboxInfo.cs" >}}

## **Obteniendo el conteo de correos en la bandeja de entrada**

El siguiente fragmento de código te muestra cómo contar los mensajes de correo en una bandeja de entrada.

{{< gist "aspose-com-gists" "6e5185a63aec6fd70d83098e82b06a32" "Examples-CSharp-POP3-GetEmailCountIntheMailbox-GetEmailCountIntheMailbox.cs" >}}

Aspose.Email permite a los desarrolladores trabajar con correos electrónicos de muchas maneras diferentes. Por ejemplo, pueden recuperar información del encabezado antes de decidir si descargar un correo electrónico. O pueden recuperar correos electrónicos de un servidor y guardarlos sin analizarlos (más rápido) o después de analizarlos (más lento). Este artículo muestra cómo recuperar y convertir correos electrónicos.

## **Recuperando Información de Encabezados de Correo Electrónico**

Los encabezados de correo electrónico pueden darnos información sobre un mensaje de correo que podemos usar para decidir si recuperar o no el mensaje completo. Típicamente, la información del encabezado contiene el remitente, el asunto, la fecha de recepción, etc. (Los encabezados de correo electrónico se describen en detalle en [Personalizando Encabezados de Correo Electrónico](https://docs.aspose.com/email/es/net/creating-and-setting-contents-of-emails/#set-email-headers). Ese tema es específicamente sobre el envío de un correo electrónico con SMTP, pero la información del contenido del encabezado sigue siendo válida para los correos electrónicos POP3). Los siguientes ejemplos muestran cómo recuperar encabezados de correo de un servidor POP3 por el número de secuencia del mensaje.

{{< gist "aspose-com-gists" "6e5185a63aec6fd70d83098e82b06a32" "Examples-CSharp-POP3-RetrievingEmailHeaders-RetrievingEmailHeaders.cs" >}}

## **Recuperando Mensajes de Correo Electrónico**

La clase [Pop3Client](https://reference.aspose.com/email/net/aspose.email.clients.pop3/pop3client/) proporciona la capacidad de recuperar mensajes de correo electrónico del servidor POP3 y analizarlos en una instancia de [MailMessage](https://reference.aspose.com/email/net/aspose.email/mailmessage/) con la ayuda de los componentes [MailMessage](https://reference.aspose.com/email/net/aspose.email/mailmessage/). La clase [MailMessage](https://reference.aspose.com/email/net/aspose.email/mailmessage/) contiene varias propiedades y métodos para manipular el contenido del correo electrónico. Al usar el método [FetchMessage](https://reference.aspose.com/email/net/aspose.email.clients.pop3/pop3client/fetchmessage/#fetchmessage/) de la clase [Pop3Client](https://reference.aspose.com/email/net/aspose.email.clients.pop3/pop3client/), puedes obtener una instancia de [MailMessage](https://reference.aspose.com/email/net/aspose.email/mailmessage/) directamente desde el servidor POP3. El siguiente fragmento de código te muestra cómo recuperar un mensaje de correo electrónico completo del servidor POP3.

{{< gist "aspose-com-gists" "6e5185a63aec6fd70d83098e82b06a32" "Examples-CSharp-POP3-RetrievingEmailMessages-RetrievingEmailMessages.cs" >}}

## **Recuperando Información de Resumen del Mensaje usando Id Único**

El cliente POP3 de la API puede recuperar información de resumen del mensaje desde el servidor usando el id único del mensaje. Esto proporciona acceso rápido a la información breve del mensaje sin tener que recuperar primero el mensaje completo del servidor. El siguiente fragmento de código te muestra cómo recuperar información de resumen del mensaje.

{{< gist "aspose-com-gists" "6e5185a63aec6fd70d83098e82b06a32" "Examples-CSharp-POP3-RetrieveMessageSummaryInformationUsingUniqueId-RetrieveMessageSummaryInformationUsingUniqueId.cs" >}}

## **Listando Mensajes con MultiConexión**

[Pop3Client](https://reference.aspose.com/email/net/aspose.email.clients.pop3/pop3client/) proporciona una propiedad [UseMultiConnection](https://reference.aspose.com/email/net/aspose.email.clients/emailclient/usemulticonnection/) que puede ser utilizada para crear múltiples conexiones para operaciones pesadas. También puedes establecer el número de conexiones que se utilizarán durante el modo de multi-conexión usando [Pop3Client.ConnectionsQuantity](https://reference.aspose.com/email/net/aspose.email.clients/emailclient/connectionsquantity/). El siguiente fragmento de código demuestra el uso del modo de multi-conexión para listar mensajes y compara su rendimiento con el modo de conexión única.

{{< gist "aspose-com-gists" "522d47278b8ca448dc1d7eb97193322c" "Examples-CSharp-POP3-Pop3ListMessagesWithMultiConnection-1.cs" >}}

{{% alert color="primary" %}} 

Por favor, ten en cuenta que el uso del modo de multi-conexión no garantiza un aumento en el rendimiento.

{{% /alert %}} 

## **Recuperando Mensajes del Servidor y Guardando en Disco**

### **Guardar Mensaje en Disco sin Analizar**

Si deseas descargar mensajes de correo del servidor POP3 sin analizarlos, utiliza la función [SaveMessage](https://reference.aspose.com/email/net/aspose.email.clients.pop3/pop3client/savemessage/#savemessage/) de la clase [Pop3Client](https://reference.aspose.com/email/net/aspose.email.clients.pop3/pop3client/). La función [SaveMessage](https://reference.aspose.com/email/net/aspose.email.clients.pop3/pop3client/savemessage/#savemessage/) no analiza el mensaje de correo, por lo que es más rápido que la función [FetchMessage](https://reference.aspose.com/email/net/aspose.email.clients.pop3/pop3client/fetchmessage/#fetchmessage/). El siguiente fragmento de código muestra cómo guardar un mensaje por su número de secuencia. En este caso, el método [SaveMessage](https://reference.aspose.com/email/net/aspose.email.clients.pop3/pop3client/savemessage/#savemessage/) guarda el mensaje en el formato EML original sin analizarlo.

{{< gist "aspose-com-gists" "6e5185a63aec6fd70d83098e82b06a32" "Examples-CSharp-POP3-SaveToDiskWithoutParsing-SaveToDiskWithoutParsing.cs" >}}

### **Analizar el Mensaje Antes de Guardar**

El siguiente fragmento de código utiliza el método [FetchMessage](https://reference.aspose.com/email/net/aspose.email.clients.pop3/pop3client/fetchmessage/#fetchmessage/) de [Pop3Client](https://reference.aspose.com/email/net/aspose.email.clients.pop3/pop3client/) para recuperar un mensaje de un servidor POP3 por su número de secuencia, y luego guarda el mensaje en disco usando el asunto como nombre de archivo.

{{< gist "aspose-com-gists" "6e5185a63aec6fd70d83098e82b06a32" "Examples-CSharp-POP3-ParseMessageAndSave-ParseMessageAndSave.cs" >}}

## **Recuperación Agrupada de Mensajes**

[Pop3Client](https://reference.aspose.com/email/net/aspose.email.clients.pop3/pop3client/) proporciona un método [FetchMessages](https://docs.aspose.com/email/es/net/working-with-messages-from-server/) que acepta números de secuencia o ID únicos iterables y devuelve una lista de [MailMessage](https://reference.aspose.com/email/net/aspose.email/mailmessage/). El siguiente fragmento de código demuestra el uso del método [FetchMessages](https://docs.aspose.com/email/es/net/working-with-messages-from-server/) para recuperar mensajes por números de secuencia y ID únicos.

{{< gist "aspose-com-gists" "522d47278b8ca448dc1d7eb97193322c" "Examples-CSharp-POP3-Pop3FetchGroupMessages-1.cs" >}}

## **Filtrando Mensajes por Remitente, Destinatario o Fecha**

La clase [Pop3Client](https://reference.aspose.com/email/net/aspose.email.clients.pop3/pop3client/), descrita en [Conectando a un Servidor POP3](https://docs.aspose.com/email/es/net/connect-to-pop3-server/), proporciona el método [ListMessages()](https://reference.aspose.com/email/net/aspose.email.clients.pop3/pop3client/listmessages/#listmessages/) que obtiene todos los mensajes de una bandeja de entrada. Para obtener solo los mensajes que coinciden con alguna condición, utiliza el método sobrecargado [ListMessages()](https://reference.aspose.com/email/net/aspose.email.clients.pop3/pop3client/listmessages/#listmessages/) que toma [MailQuery](https://reference.aspose.com/email/net/aspose.email.tools.search/mailquery/) como argumento. La clase [MailQuery](https://reference.aspose.com/email/net/aspose.email.tools.search/mailquery/) proporciona varias propiedades para especificar las condiciones de consulta, por ejemplo, fecha, asunto, remitente, destinatario, etc. La clase [MailQueryBuilder](https://reference.aspose.com/email/net/aspose.email.tools.search/mailquerybuilder/) se usa para construir la expresión de búsqueda. Primero, se establecen todas las condiciones y restricciones y luego [MailQuery](https://reference.aspose.com/email/net/aspose.email.tools.search/mailquery/) se completa con la consulta desarrollada por [MailQueryBuilder](https://reference.aspose.com/email/net/aspose.email.tools.search/mailquerybuilder/). El objeto de la clase [MailQuery](https://reference.aspose.com/email/net/aspose.email.tools.search/mailquery/) es utilizado por [Pop3Client](https://reference.aspose.com/email/net/aspose.email.clients.pop3/pop3client/) para extraer la información filtrada del servidor. Este artículo muestra cómo filtrar mensajes de correo electrónico de una bandeja de entrada. El primer ejemplo ilustra cómo filtrar mensajes en función de la fecha y el asunto. También mostramos cómo filtrar según otros criterios y cómo construir consultas más complejas. También muestra la aplicación de un filtro de fecha y hora para recuperar correos electrónicos específicos de la bandeja de entrada. Además, también se muestra cómo aplicar filtros que diferencian mayúsculas y minúsculas.

### **Filtrando Mensajes de la Bandeja de Entrada**

Para filtrar mensajes de una bandeja de entrada:

1. [Conéctate e inicia sesión en un servidor POP3](https://docs.aspose.com/email/es/net/connect-to-pop3-server/#connecting-to-pop3-server).
2. Crea una instancia de [MailQuery](https://reference.aspose.com/email/net/aspose.email.tools.search/mailquery/) y establece las propiedades deseadas.
3. Llama al método [`Pop3Client.ListMessages(MailQuery query)`](https://reference.aspose.com/email/net/aspose.email.clients.pop3/pop3client/listmessages/#listmessages_8) y pasa el [MailQuery](https://reference.aspose.com/email/net/aspose.email.tools.search/mailquery/) como parámetro para obtener solo los mensajes filtrados.

El siguiente fragmento de código te muestra cómo conectarte a una bandeja de entrada POP3 y obtener los mensajes que llegaron hoy y tienen la palabra "newsletter" en el asunto.

{{< gist "aspose-com-gists" "6e5185a63aec6fd70d83098e82b06a32" "Examples-CSharp-POP3-FilterMessagesFromPOP3Mailbox-FilterMessagesFromPOP3Mailbox.cs" >}}

### **Obteniendo Mensajes que Cumplen Criterios Específicos**

[Los ejemplos de código anteriores](https://docs.aspose.com/email/es/net/working-with-messages-from-server/#filtering-messages-from-mailbox) muestran cómo puedes filtrar mensajes en función del asunto del correo y la fecha. También podemos usar otras propiedades para establecer otras condiciones admitidas. A continuación se presentan algunos ejemplos de establecer condiciones usando [MailQuery](https://reference.aspose.com/email/net/aspose.email.tools.search/mailquery/).

Los fragmentos de código que siguen muestran cómo filtrar correos electrónicos según otros criterios:

- Encontrar correos electrónicos entregados hoy.
- Encontrar correos electrónicos recibidos dentro de un rango.
- Encontrar correos electrónicos de un remitente específico.
- Encontrar correos electrónicos enviados desde un dominio específico.
- Encontrar correos electrónicos enviados a un destinatario específico.

#### **Fecha de Hoy**

El siguiente fragmento de código te muestra cómo encontrar correos electrónicos entregados hoy.

{{< gist "aspose-com-gists" "6e5185a63aec6fd70d83098e82b06a32" "Examples-CSharp-POP3-GetMessagesUsingSpecificCriteria-GetEmailsWithTodayDate.cs" >}}

#### **Rango de Fechas**

El siguiente fragmento de código te muestra cómo encontrar correos electrónicos recibidos dentro de un rango.

{{< gist "aspose-com-gists" "6e5185a63aec6fd70d83098e82b06a32" "Examples-CSharp-POP3-GetMessagesUsingSpecificCriteria-GetEmailsOverDateRange.cs" >}}

#### **Remitente Específico**

El siguiente fragmento de código te muestra cómo encontrar correos electrónicos de un remitente específico.

{{< gist "aspose-com-gists" "6e5185a63aec6fd70d83098e82b06a32" "Examples-CSharp-POP3-GetMessagesUsingSpecificCriteria-GetSpecificSenderEmails.cs" >}}

#### **Dominio Específico**

El siguiente fragmento de código te muestra cómo encontrar correos electrónicos enviados desde un dominio específico.

{{< gist "aspose-com-gists" "6e5185a63aec6fd70d83098e82b06a32" "Examples-CSharp-POP3-GetMessagesUsingSpecificCriteria-GetSpecificDomainEmails.cs" >}}

#### **Destinatario Específico**

El siguiente fragmento de código te muestra cómo encontrar correos electrónicos enviados a un destinatario específico.

{{< gist "aspose-com-gists" "6e5185a63aec6fd70d83098e82b06a32" "Examples-CSharp-POP3-GetMessagesUsingSpecificCriteria-GetSpecificRecipientEmails.cs" >}}

### **Construyendo Consultas Complejas**

Si se establecen diferentes propiedades de [MailQueryBuilder](https://reference.aspose.com/email/net/aspose.email.tools.search/mailquerybuilder/) en declaraciones separadas, se cumplirán todas las condiciones. Por ejemplo, si queremos obtener mensajes entre un rango de fechas y de un host específico, necesitamos escribir tres declaraciones.

#### **Combinando Consultas con AND**

El siguiente fragmento de código te muestra cómo combinar consultas usando AND.

{{< gist "aspose-com-gists" "6e5185a63aec6fd70d83098e82b06a32" "Examples-CSharp-POP3-BuildComplexQueries-CombineQueriesWithAND.cs" >}}

#### **Combinando Consultas con OR**

[MailQueryBuilder](https://reference.aspose.com/email/net/aspose.email.tools.search/mailquerybuilder/) proporciona el método [Or()](https://reference.aspose.com/email/net/aspose.email.tools.search/mailquerybuilder/or/#or) que toma dos instancias de [MailQuery](https://reference.aspose.com/email/net/aspose.email.tools.search/mailquery/) como parámetros. Obtiene los mensajes que coinciden con cualquiera de las dos condiciones especificadas. El siguiente fragmento de código muestra cómo filtrar mensajes que tengan "test" en el asunto o "noreply@host.com" como remitente. El siguiente fragmento de código te muestra cómo combinar consultas usando OR.

{{< gist "aspose-com-gists" "6e5185a63aec6fd70d83098e82b06a32" "Examples-CSharp-POP3-BuildComplexQueries-CombiningQueriesWithOR.cs" >}}

#### **Aplicando Filtros Sensibles a Mayúsculas y Minúsculas**

La API también proporciona la capacidad de filtrar correos electrónicos de la bandeja de entrada basándose en un criterio sensible a mayúsculas y minúsculas. Los siguientes métodos ofrecen la capacidad de buscar correos electrónicos especificando una bandera sensible a mayúsculas y minúsculas.

- Método `Aspose.Email.StringComparisonField.Contains(string value, bool ignoreCase)`
- Método `Aspose.Email.StringComparisonField.Equals(string value, bool ignoreCase)`
- Método `Aspose.Email.StringComparisonField.NotContains(string value, bool ignoreCase)`
- Método `Aspose.Email.StringComparisonField.NotEquals(string value, bool ignoreCase)`

{{< gist "aspose-com-gists" "6e5185a63aec6fd70d83098e82b06a32" "Examples-CSharp-POP3-ApplyCaseSensitiveFilters-ApplyCaseSensitiveFilters.cs" >}}