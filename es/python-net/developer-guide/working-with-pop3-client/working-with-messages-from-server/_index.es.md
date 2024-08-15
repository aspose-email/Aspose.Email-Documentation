---
title: "Trabajando con mensajes del servidor"
url: /es/python-net/working-with-messages-from-server/
weight: 40
type: docs
---

## **Obtener información sobre el buzón**
Podemos obtener información sobre el buzón, como el número de mensajes y el tamaño del buzón, mediante los métodos getMailboxSize () y getMailboxInfo ().

- The `GetMailBoxSize()` el método devuelve el tamaño del buzón en bytes.
- The `GetMailBoxInfo()` el método devuelve un objeto de tipo POP3MailboxInfo.

También es posible obtener el número de mensajes mediante la propiedad MessageCount y el tamaño mediante la propiedad OccupiedSize. El siguiente código de ejemplo muestra cómo obtener información sobre el buzón. Muestra cómo:

1. Crea un [Pop3Client](https://apireference.aspose.com/email/net/aspose.email.clients.pop3/pop3client).
1. Conéctese a un servidor POP3.
1. Obtenga el tamaño del buzón.
1. Obtenga información sobre el buzón.
1. Obtenga el número de mensajes del buzón.
1. Consigue el tamaño ocupado.



{{< gist "aspose-email" "356f0e128b9d45a7ee779fc813eb87e5" "Examples-POP3-GettingMailboxInfo-GettingMailboxInfo.py" >}}
## **Obteniendo el recuento de correos electrónicos en el buzón**
El siguiente fragmento de código muestra cómo contar los mensajes de correo electrónico de un buzón.



{{< gist "aspose-email" "356f0e128b9d45a7ee779fc813eb87e5" "Examples-POP3-GetEmailCountInMailbox-GetEmailCountInMailbox.py" >}}



Aspose.Email permite a los desarrolladores trabajar con los correos electrónicos de muchas maneras diferentes. Por ejemplo, pueden recuperar la información del encabezado antes de decidir si descargan un correo electrónico. O pueden recuperar los correos electrónicos de un servidor y guardarlos sin analizarlos (más rápido) o después de analizarlos (más lento). En este artículo se muestra cómo recuperar y convertir correos electrónicos.
## **Recuperación de información de encabezados de correo electrónico**
Los encabezados de correo electrónico pueden proporcionarnos información sobre un mensaje de correo electrónico que podemos usar para decidir si queremos recuperar o no el mensaje de correo electrónico completo. Por lo general, la información del encabezado contiene el remitente, el asunto, la fecha de recepción, etc. (Los encabezados de los correos electrónicos se describen en detalle en Personalización de los encabezados de los correos electrónicos). Este tema trata específicamente sobre el envío de correos electrónicos con SMTP, pero la información sobre el contenido del encabezado del correo electrónico sigue siendo válida para los correos electrónicos POP3). Los siguientes ejemplos muestran cómo recuperar los encabezados de correo electrónico de un servidor POP3 por el número de secuencia del mensaje.



{{< gist "aspose-email" "356f0e128b9d45a7ee779fc813eb87e5" "Examples-POP3-RetrievingEmailHeaders-RetrievingEmailHeaders.py" >}}
## **Recuperación de mensajes de correo electrónico**
El componente de clase Aspose.Email.Pop3 ofrece la capacidad de recuperar mensajes de correo electrónico del servidor POP3 y analizarlos en una instancia de MailMessage con la ayuda de los componentes MailMessage. La clase MailMessage contiene varias propiedades y métodos para manipular el contenido del correo electrónico. Mediante la función FetchMessage de la clase Pop3Client, puede obtener una instancia de MailMessage directamente desde el servidor POP3. El siguiente fragmento de código muestra cómo recuperar un mensaje de correo electrónico completo del servidor POP3.



{{< gist "aspose-email" "356f0e128b9d45a7ee779fc813eb87e5" "Examples-POP3-RetrievingEmailMessages-RetrievingEmailMessages.py" >}}
## **Recuperación de la información resumida del mensaje mediante un identificador único**
El cliente POP3 de la API puede recuperar la información resumida del mensaje del servidor mediante el identificador único del mensaje. Esto proporciona un acceso rápido a la información breve del mensaje sin tener que recuperar primero el mensaje completo del servidor. El siguiente fragmento de código muestra cómo recuperar la información resumida del mensaje.



{{< gist "aspose-email" "356f0e128b9d45a7ee779fc813eb87e5" "Examples-POP3-RetrieveMessageSummaryInformationUsingUniqueId-RetrieveMessageSummaryInformationUsingUniqueId.py" >}}
## **Listar mensajes con MultiConnection**

Para operaciones con mucha carga, Aspose.Email ofrece la propiedad 'use_multi_connection' del [Pop3Client](https://reference.aspose.com/email/python-net/aspose.email.clients.pop3/pop3client/#pop3client-class) clase para usar múltiples conexiones al recuperar correos electrónicos. Sin embargo, el uso de este modo no tiene por qué conducir necesariamente a un aumento del rendimiento. El siguiente fragmento de código muestra cómo establecer una conexión con un servidor POP3, configurar el cliente para permitir hasta 5 conexiones simultáneas y habilitar el modo de conexión múltiple para recuperar información sobre los mensajes presentes en el servidor:

```py
import aspose.email as ae

client = ae.clients.pop3.Pop3Client("host", 995, "username", "password", ae.clients.SecurityOptions.AUTO)

client.connections_quantity = 5
client.use_multi_connection = ae.clients.MultiConnectionMode.ENABLE
message_info_coll = client.list_messages()
```

## **Obtener mensajes del servidor y guardarlos en el disco**
### **Guardar el mensaje en el disco sin analizarlo**
Si desea descargar mensajes de correo electrónico del servidor POP3 sin analizarlos, utilice la función SaveMessage de la clase Pop3Client. La función SaveMessage no analiza el mensaje de correo electrónico, por lo que es más rápida que la función FetchMessage. El siguiente fragmento de código muestra cómo guardar un mensaje por su número de secuencia, en este caso el número 1. El método SaveMessageMethod guarda el mensaje en el formato EML original sin analizarlo.



{{< gist "aspose-email" "356f0e128b9d45a7ee779fc813eb87e5" "Examples-POP3-SaveToDiscWithoutParsing-SaveToDiscWithoutParsing.py" >}}

### **Analiza el mensaje antes de guardarlo**

Utilice el método 'fetch_message' del objeto de cliente creado con [Pop3Client](https://reference.aspose.com/email/python-net/aspose.email.clients.pop3/pop3client/#pop3client-class) clase para recuperar el mensaje con un número de secuencia específico. El ejemplo de código que aparece a continuación muestra cómo recuperar un mensaje específico y guardarlo con el asunto como nombre de archivo mediante una llamada al método «guardar» en el objeto msg:

```py
import aspose.email as ae

client = ae.clients.pop3.Pop3Client("host", 995, "username", "password", ae.clients.SecurityOptions.AUTO)

# Fetch the message by its sequence number and Save the message using its subject as the file name
msg = client.fetch_message(1)
msg.save("first-message_out.eml", ae.SaveOptions.default_eml)
```
### **Filtrar mensajes por remitente, destinatario o fecha**
La clase Pop3Client, descrita en Conectarse a un servidor POP3, proporciona el método list_messages () que obtiene todos los mensajes de un buzón. Para obtener solo los mensajes que cumplan alguna condición, utilice el método listMessages () sobrecargado, que toma MailQuery como argumento. La clase MailQuery proporciona varias propiedades para especificar las condiciones de la consulta, por ejemplo, la fecha, el asunto, el remitente, el destinatario, etc. La clase MailQueryBuilder se usa para crear la expresión de búsqueda. En primer lugar, se establecen todas las condiciones y restricciones y, a continuación, MailQuery se rellena con la consulta desarrollada por MailQueryBuilder. Pop3Client utiliza el objeto de clase MailQuery para extraer la información filtrada del servidor. En este artículo se muestra cómo filtrar los mensajes de correo electrónico de un buzón. El primer ejemplo ilustra cómo filtrar los mensajes según la fecha y el asunto. También mostramos cómo filtrar según otros criterios y cómo crear consultas más complejas. También muestra la aplicación del filtro de fecha y hora para recuperar los correos electrónicos específicos del buzón. Además, también muestra cómo aplicar el filtrado que distingue entre mayúsculas y minúsculas.
### **Filtrar mensajes del buzón**
Para filtrar los mensajes de un buzón:

1. Conéctese a un servidor POP3 e inicie sesión en él.
1. Crea una instancia de MailQuery y establece las propiedades deseadas.
1. Llame al `Pop3Client.list_messages(MailQuery query)` y pase el MailQuery en los parámetros para obtener solo los mensajes filtrados.

El siguiente fragmento de código muestra cómo conectarse a un buzón POP3 y recibir los mensajes que han llegado ese día y que tienen la palabra «boletín» en el asunto.



{{< gist "aspose-email" "356f0e128b9d45a7ee779fc813eb87e5" "Examples-POP3-FilterMessagesFromMailbox-FilterMessagesFromMailbox.py" >}}

### **Recibir mensajes que cumplan con criterios específicos**

Aspose.Email también permite crear criterios de búsqueda complejos para consultar y filtrar los mensajes de correo electrónico. Para ello, utilice el [MailQueryBuilder](https://reference.aspose.com/email/python-net/aspose.email.tools.search/mailquerybuilder/#mailquerybuilder-class) clase y sus propiedades. Los criterios de búsqueda son los siguientes:

- Busca mensajes por fecha de entrega.
- Busca mensajes dentro de un rango.
- Obtiene los mensajes de un remitente específico.
- Obtiene mensajes de un dominio específico.
- Extrae los mensajes a un destinatario específico.

#### **La fecha de hoy**

Para recuperar los mensajes antes de una fecha de entrega, usa la propiedad 'internal_date' como se muestra en el ejemplo de código siguiente:

```py
import aspose.email as ae
from datetime import datetime

builder = ae.tools.search.MailQueryBuilder()
builder.internal_date.on(datetime.now())
```
#### **Intervalo de fechas**

Para buscar mensajes dentro de un intervalo de fechas, utiliza la misma propiedad 'internal_date' para especificar el intervalo de fechas, tal y como se muestra en el ejemplo de código siguiente:

```py
import aspose.email as ae
from datetime import datetime, timedelta

builder = ae.tools.search.MailQueryBuilder()
# Emails that arrived in last 7 days
builder.internal_date.before(datetime.now())
builder.internal_date.since(datetime.today() - timedelta(days=7))
```
#### **Remitente específico**

Para obtener mensajes de un remitente específico, usa la propiedad 'from_address' como se muestra en el ejemplo de código siguiente:

```py
import aspose.email as ae

builder = ae.tools.search.MailQueryBuilder()
builder.from_address.contains("saqib.razzaq@127.0.0.1")
```
#### **Dominio específico**

Para obtener mensajes de un dominio específico, usa la propiedad 'from_address' como se muestra en el ejemplo de código siguiente:

```py
import aspose.email as ae

builder = ae.tools.search.MailQueryBuilder()
builder.from_address.contains("SpecificHost.com")
```
#### **Destinatario específico**

Para enviar mensajes a un destinatario específico, utilice la propiedad 'to', tal y como se muestra en el ejemplo de código siguiente:

```py
import aspose.email as ae

builder = ae.tools.search.MailQueryBuilder()
builder.to.contains("recipient")
```
### **Creación de consultas complejas**

En ocasiones es necesario satisfacer más de una consulta. Aspose.Email lo hace posible mediante la combinación de consultas en varias sentencias. Crea un [MailQueryBuilder](https://reference.aspose.com/email/python-net/aspose.email.tools.search/mailquerybuilder/#mailquerybuilder-class) objeto y usa sus propiedades para crear consultas específicas.

#### **Combinación de consultas con AND**

El siguiente fragmento de código muestra cómo combinar consultas con AND.

```py
import aspose.email as ae
from datetime import datetime, timedelta

builder = ae.tools.search.MailQueryBuilder()
builder.internal_date.before(datetime.now())
builder.internal_date.since(datetime.today() - timedelta(days=7))
builder.from_address.contains("SpecificHost.com")
```
#### **Combinación de consultas con OR**

El siguiente fragmento de código muestra cómo combinar consultas con OR.

```py
import aspose.email as ae

builder = ae.tools.search.MailQueryBuilder()
builder.either(builder.subject.contains("test"), builder.from_address.contains("noreply@host.com"))
```

#### **Aplicar filtros que distinguen mayúsculas y minúsculas**

La API también ofrece la capacidad de filtrar los correos electrónicos del buzón según un criterio que distingue mayúsculas y minúsculas. Los siguientes métodos del [StringComparisonField](https://reference.aspose.com/email/python-net/aspose.email.tools.search/stringcomparisonfield/#stringcomparisonfield-class) La clase brinda la capacidad de buscar correos electrónicos especificando marcas que distingan entre mayúsculas y minúsculas. 

- Method `Aspose.Email.StringComparisonField.contains(value, ignore_case)`
- Method `Aspose.Email.StringComparisonField.equals(value, ignore_case)`
- Method `Aspose.Email.StringComparisonField.not_contains(value, ignore_case)`
- Method `Aspose.Email.StringComparisonField.not_equals(value, ignore_case)`

En el siguiente fragmento de código, se muestra cómo implementar esta capacidad en el proyecto:

```py
import aspose.email as ae

builder = ae.tools.search.MailQueryBuilder()
builder.from_address.contains("noreply@host.com", True)
```

