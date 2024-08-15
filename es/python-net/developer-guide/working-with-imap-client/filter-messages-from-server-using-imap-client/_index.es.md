---
title: "Filtrar mensajes del servidor mediante el cliente IMAP"
url: /es/python-net/filter-messages-from-server-using-imap-client/
weight: 30
type: docs
---


La clase ImapClient proporciona el método listMessages () que obtiene todos los mensajes de un buzón. Para obtener solo los mensajes que cumplen alguna condición, usa el método listMessages () sobrecargado, que toma MailQuery como argumento. La clase MailQuery proporciona varias propiedades para especificar las condiciones, por ejemplo, fecha, asunto, remitente, destinatario, etc. El primer ejemplo ilustra cómo filtrar los mensajes en función de la fecha y el asunto. También mostramos cómo filtrar según otros criterios y cómo crear consultas más complejas. La API también ofrece la capacidad de aplicar criterios de búsqueda que distinguen mayúsculas y minúsculas para que coincidan con los criterios de filtrado exactos. La API también permite especificar la codificación de la cadena de búsqueda para filtrar los mensajes del buzón.
## **Filtrar mensajes del buzón**
1. Conectarse e iniciar sesión en un servidor IMAP
1. Crea una instancia de MailQuery y establece las propiedades
1. Llame al `ImapClient.ListMessages(MailQuery query)` y pase el MailQuery con los parámetros para obtener solo los mensajes filtrados.

El siguiente fragmento de código muestra cómo conectarse a un buzón IMAP y recibir los mensajes que han llegado ese día y que tienen la palabra «boletín» en el asunto.



{{< gist "aspose-email" "356f0e128b9d45a7ee779fc813eb87e5" "Examples-IMAP-FilteringMessagesFromIMAPMailbox-FetchEmailMessageFromServer.py" >}}

## **Recibir mensajes que cumplan con criterios específicos**

Aspose.Email también permite crear criterios de búsqueda complejos para consultar y filtrar los mensajes de correo electrónico. Para ello, utilice el [MailQueryBuilder](https://reference.aspose.com/email/python-net/aspose.email.tools.search/mailquerybuilder/#mailquerybuilder-class) clase y sus propiedades. Los criterios de búsqueda son los siguientes:

- Busca mensajes por fecha de entrega.
- Busca mensajes dentro de un rango.
- Obtiene los mensajes de un remitente específico.
- Obtiene mensajes de un dominio específico.
- Extrae los mensajes a un destinatario específico.

### **La fecha de hoy**

Para recuperar los mensajes antes de una fecha de entrega, usa la propiedad 'internal_date' como se muestra en el ejemplo de código siguiente:

```py
import aspose.email as ae
from datetime import datetime

builder = ae.tools.search.MailQueryBuilder()
builder.internal_date.on(datetime.now())
```
### **Intervalo de fechas**

Para buscar mensajes dentro de un intervalo de fechas, utiliza la misma propiedad 'internal_date' para especificar el intervalo de fechas, tal y como se muestra en el ejemplo de código siguiente:

```py
import aspose.email as ae
from datetime import datetime, timedelta

builder = ae.tools.search.MailQueryBuilder()
# Emails that arrived in last 7 days
builder.internal_date.before(datetime.now())
builder.internal_date.since(datetime.today() - timedelta(days=7))
```
### **Remitente específico**

Para obtener mensajes de un remitente específico, usa la propiedad 'from_address' como se muestra en el ejemplo de código siguiente:

```py
import aspose.email as ae

builder = ae.tools.search.MailQueryBuilder()
builder.from_address.contains("saqib.razzaq@127.0.0.1")
```
### **Dominio específico**

Para obtener mensajes de un dominio específico, usa la propiedad 'from_address' como se muestra en el ejemplo de código siguiente:

```py
import aspose.email as ae

builder = ae.tools.search.MailQueryBuilder()
builder.from_address.contains("SpecificHost.com")
```
### **Destinatario específico**

Para enviar mensajes a un destinatario específico, utilice la propiedad 'to', tal y como se muestra en el ejemplo de código siguiente:

```py
import aspose.email as ae

builder = ae.tools.search.MailQueryBuilder()
builder.to.contains("recipient")
```

## **Creación de consultas complejas**

En ocasiones es necesario satisfacer más de una consulta. Aspose.Email lo hace posible mediante la combinación de consultas en varias sentencias. Crea un [MailQueryBuilder](https://reference.aspose.com/email/python-net/aspose.email.tools.search/mailquerybuilder/#mailquerybuilder-class) objeto y usa sus propiedades para crear consultas específicas.

### **Combinación de consultas con AND**

El siguiente fragmento de código muestra cómo combinar consultas con AND.

```py
import aspose.email as ae
from datetime import datetime, timedelta

builder = ae.tools.search.MailQueryBuilder()
builder.internal_date.before(datetime.now())
builder.internal_date.since(datetime.today() - timedelta(days=7))
builder.from_address.contains("SpecificHost.com")
```
### **Combinación de consultas con OR**

El siguiente fragmento de código muestra cómo combinar consultas con OR.

```py
import aspose.email as ae

builder = ae.tools.search.MailQueryBuilder()
builder.either(builder.subject.contains("test"), builder.from_address.contains("noreply@host.com"))
```
## **Filtración en InternalDate**

La API ofrece la capacidad de recuperar una lista de mensajes del servidor que cumplen las condiciones especificadas. El ejemplo de código que aparece a continuación muestra cómo crear una consulta con las condiciones de «fecha interna» y «el asunto contiene». La «fecha interna» hace referencia a la fecha y la hora en que se recibió o se añadió un mensaje de correo electrónico al servidor de correo electrónico y se puede configurar mediante la propiedad 'internal_date' del [ImapQueryBuilder](https://reference.aspose.com/email/python-net/aspose.email.clients.imap/imapquerybuilder/#imapquerybuilder-class) class.


```py
import aspose.email as ae
from datetime import datetime

client = ae.clients.imap.ImapClient("imap.domain.com", 993, "user@domain.com", "pwd")
client.select_folder("Inbox")

# Set conditions, Subject contains "Newsletter", Emails that arrived today
builder = ae.clients.imap.ImapQueryBuilder()
builder.subject.contains("Newsletter")
builder.internal_date.on(datetime.now())

# Build the query and Get list of messages
query = builder.get_query()
messages = client.list_messages(query)
for info in messages:
    print(f"Internal Date: {info.internal_date}")
```
El código imprime la fecha interna de cada mensaje que cumple las condiciones especificadas.

## **Filtrar mensajes por marcas de palabras clave personalizadas**

La biblioteca Aspose.Email permite crear una consulta para buscar correos electrónicos que contengan marcas de palabras clave personalizadas en un buzón IMAP. En el ejemplo siguiente, las palabras clave personalizadas utilizadas son «custom1\" y «custom2\". Usa el [ImapQueryBuilder](https://reference.aspose.com/email/python-net/aspose.email.clients.imap/imapquerybuilder/#imapquerybuilder-class) clase que es una herramienta que le permite crear consultas de búsqueda que se pueden usar para filtrar correos electrónicos al recuperarlos de un servidor IMAP. Crea un generador de consultas. Con el método «has_flags» del generador, agrega condiciones a la consulta para incluir solo los correos electrónicos que tengan las palabras clave de los indicadores IMAP. Las palabras clave personalizadas en IMAP también se conocen como marcas definidas por el usuario y se pueden usar para etiquetar o marcar correos electrónicos en el buzón con diversos fines, como la categorización, el estado, etc. En el siguiente fragmento de código, se muestra cómo crear una consulta para recuperar correos electrónicos específicos mediante marcas de palabras clave personalizadas: 

```py
import aspose.email as ae

builder = ae.clients.imap.ImapQueryBuilder()
builder.has_flags(ae.clients.imap.ImapMessageFlags.keyword("custom1"))
builder.has_flags(ae.clients.imap.ImapMessageFlags.keyword("custom2"))
```
## **Filtrar mensajes mediante la búsqueda personalizada**

La biblioteca de Python se puede usar para crear una consulta de búsqueda para un buzón IMAP que filtre los correos electrónicos según un criterio de búsqueda personalizado de Gmail, específicamente los correos electrónicos que tienen archivos adjuntos. Crea una instancia de [ImapQueryBuilder](https://reference.aspose.com/email/python-net/aspose.email.clients.imap/imapquerybuilder/#imapquerybuilder-class), que permite crear consultas de búsqueda IMAP complejas que se pueden utilizar para filtrar los correos electrónicos de un servidor IMAP. Al llamar al método «custom_search», agrega una cadena de búsqueda personalizada al generador de consultas. La cadena X-GM-RAW «has:attachment» es un término de búsqueda específico de Gmail que usa el atributo X-GM-RAW. Gmail permite el uso de su sintaxis de búsqueda de correo web en las búsquedas IMAP mediante este atributo. El término «has:attachment» es un operador de búsqueda de Gmail que busca todos los correos electrónicos que contienen un archivo adjunto. El siguiente fragmento de código muestra cómo filtrar los correos electrónicos según los criterios definidos (en este caso, todos los correos electrónicos con un archivo adjunto):

```py
import aspose.email as ae

builder = ae.clients.imap.ImapQueryBuilder()
builder.custom_search("X-GM-RAW \"has:attachment\"")

mailQuery = builder.get_query()
```

### **Aplicar filtros que distinguen mayúsculas y minúsculas**

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
