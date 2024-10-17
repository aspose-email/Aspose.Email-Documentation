---
title: "Filtrar Mensajes del Servidor usando Cliente IMAP"
url: /es/python-net/filter-messages-from-server-using-imap-client/
weight: 30
type: docs
---

La clase ImapClient proporciona el método ListMessages() que obtiene todos los mensajes de un buzón. Para obtener solo los mensajes que coinciden con alguna condición, utiliza el método ListMessages() sobrecargado que toma MailQuery como argumento. La clase MailQuery ofrece varias propiedades para especificar las condiciones, por ejemplo, fecha, asunto, remitente, destinatario, etc. El primer ejemplo ilustra cómo filtrar mensajes en función de la fecha y el asunto. También mostramos cómo filtrar por otros criterios y cómo construir consultas más complejas. La API también proporciona la capacidad de aplicar criterios de búsqueda sensibles a minúsculas y mayúsculas para coincidir con criterios de filtrado exactos. La API también permite especificar la codificación de la cadena de búsqueda para filtrar mensajes del buzón.
## **Filtrando Mensajes del Buzón**
1. Conectar e iniciar sesión en un servidor IMAP
1. Crear una instancia de MailQuery y establecer las propiedades
1. Llamar al `ImapClient.ListMessages(MailQuery query)` método y pasar el MailQuery con los parámetros para obtener solo los mensajes filtrados.

El siguiente fragmento de código muestra cómo conectarse a un buzón IMAP y obtener los mensajes que llegaron hoy y tienen la palabra "newsletter" en el asunto.

{{< gist "aspose-email" "356f0e128b9d45a7ee779fc813eb87e5" "Examples-IMAP-FilteringMessagesFromIMAPMailbox-FetchEmailMessageFromServer.py" >}}

## **Obteniendo Mensajes que Cumplen Criterios Específicos**

Aspose.Email también permite construir criterios de búsqueda complejos para consultar y filtrar mensajes de correo electrónico. Para este propósito, utiliza la clase [MailQueryBuilder](https://reference.aspose.com/email/python-net/aspose.email.tools.search/mailquerybuilder/#mailquerybuilder-class) y sus propiedades. Los criterios para la obtención son los siguientes:

- Obtener mensajes por fecha de entrega.
- Obtener mensajes dentro de un rango.
- Obtener mensajes de un remitente específico.
- Obtener mensajes de un dominio específico.
- Obtener mensajes a un destinatario específico.

### **Fecha de hoy**

Para obtener mensajes por una fecha de entrega, utiliza la propiedad 'internal_date' como se muestra en el siguiente ejemplo de código:

```py
import aspose.email as ae
from datetime import datetime

builder = ae.tools.search.MailQueryBuilder()
builder.internal_date.on(datetime.now())
```
### **Rango de fechas**

Para obtener mensajes dentro de un rango de fechas, utiliza la misma propiedad 'internal_date' especificando el rango de fechas como se muestra en el siguiente ejemplo de código:

```py
import aspose.email as ae
from datetime import datetime, timedelta

builder = ae.tools.search.MailQueryBuilder()
# Correos que llegaron en los últimos 7 días
builder.internal_date.before(datetime.now())
builder.internal_date.since(datetime.today() - timedelta(days=7))
```
### **Remitente específico**

Para obtener mensajes de un remitente específico, utiliza la propiedad 'from_address' como se muestra en el siguiente ejemplo de código:

```py
import aspose.email as ae

builder = ae.tools.search.MailQueryBuilder()
builder.from_address.contains("saqib.razzaq@127.0.0.1")
```
### **Dominio específico**

Para obtener mensajes de un dominio específico, utiliza la propiedad 'from_address' como se muestra en el siguiente ejemplo de código:

```py
import aspose.email as ae

builder = ae.tools.search.MailQueryBuilder()
builder.from_address.contains("SpecificHost.com")
```
### **Destinatario específico**

Para obtener mensajes a un destinatario específico, utiliza la propiedad 'to' como se muestra en el siguiente ejemplo de código:

```py
import aspose.email as ae

builder = ae.tools.search.MailQueryBuilder()
builder.to.contains("recipient")
```

## **Construyendo Consultas Complejas**

A veces es necesario satisfacer más de una consulta. Aspose.Email permite esto combinando consultas en varias declaraciones. Crea un objeto [MailQueryBuilder](https://reference.aspose.com/email/python-net/aspose.email.tools.search/mailquerybuilder/#mailquerybuilder-class) y utiliza sus propiedades para construir consultas específicas.

### **Combinando Consultas con AND**

El siguiente fragmento de código muestra cómo combinar consultas con AND.

```py
import aspose.email as ae
from datetime import datetime, timedelta

builder = ae.tools.search.MailQueryBuilder()
builder.internal_date.before(datetime.now())
builder.internal_date.since(datetime.today() - timedelta(days=7))
builder.from_address.contains("SpecificHost.com")
```
### **Combinando Consultas con OR**

El siguiente fragmento de código muestra cómo combinar consultas con OR.

```py
import aspose.email as ae

builder = ae.tools.search.MailQueryBuilder()
builder.either(builder.subject.contains("test"), builder.from_address.contains("noreply@host.com"))
```
## **Filtración en InternalDate**

La API proporciona la capacidad de recuperar una lista de mensajes del servidor que cumplen con las condiciones especificadas. El siguiente ejemplo de código muestra cómo construir una consulta sobre las condiciones "fecha interna" y "el asunto contiene". La "fecha interna" se refiere a la fecha y hora en que se recibió un mensaje de correo electrónico o se agregó al servidor de correo y se puede establecer utilizando la propiedad 'internal_date' de la clase [ImapQueryBuilder](https://reference.aspose.com/email/python-net/aspose.email.clients.imap/imapquerybuilder/#imapquerybuilder-class).

```py
import aspose.email as ae
from datetime import datetime

client = ae.clients.imap.ImapClient("imap.domain.com", 993, "user@domain.com", "pwd")
client.select_folder("Inbox")

# Establecer condiciones, El asunto contiene "Newsletter", Correos que llegaron hoy
builder = ae.clients.imap.ImapQueryBuilder()
builder.subject.contains("Newsletter")
builder.internal_date.on(datetime.now())

# Construir la consulta y obtener la lista de mensajes
query = builder.get_query()
messages = client.list_messages(query)
for info in messages:
    print(f"Internal Date: {info.internal_date}")
```
El código imprime la fecha interna de cada mensaje que cumple con las condiciones especificadas.

## **Filtrar Mensajes por Banderas de Palabras Clave Personalizadas**

La biblioteca Aspose.Email permite crear una consulta para buscar en un buzón IMAP correos electrónicos que contengan banderas de palabras clave personalizadas. En el ejemplo a continuación, las palabras clave personalizadas utilizadas son "custom1" y "custom2". Utiliza la clase [ImapQueryBuilder](https://reference.aspose.com/email/python-net/aspose.email.clients.imap/imapquerybuilder/#imapquerybuilder-class) que es una herramienta que permite construir consultas de búsqueda que pueden ser utilizadas para filtrar correos electrónicos al recuperarlos de un servidor IMAP. Crea un generador de consultas. Utilizando el método 'has_flags' del generador, agrega condiciones a la consulta para incluir solo correos electrónicos que tengan las palabras clave de las banderas IMAP. Las palabras clave personalizadas en IMAP también se conocen como banderas definidas por el usuario que se pueden utilizar para etiquetar o marcar correos electrónicos en el buzón para varios propósitos, incluyendo categorización, estado, y más. El siguiente fragmento de código demuestra cómo crear una consulta para recuperar correos electrónicos específicos por banderas de palabras clave personalizadas:

```py
import aspose.email as ae

builder = ae.clients.imap.ImapQueryBuilder()
builder.has_flags(ae.clients.imap.ImapMessageFlags.keyword("custom1"))
builder.has_flags(ae.clients.imap.ImapMessageFlags.keyword("custom2"))
```
## **Filtrar Mensajes usando Búsqueda Personalizada**

La biblioteca de Python se puede utilizar para crear una consulta de búsqueda para un buzón IMAP que filtre correos electrónicos basados en un criterio de búsqueda personalizado de Gmail, específicamente correos electrónicos que tienen archivos adjuntos. Crea una instancia de [ImapQueryBuilder](https://reference.aspose.com/email/python-net/aspose.email.clients.imap/imapquerybuilder/#imapquerybuilder-class), que te permite construir consultas de búsqueda IMAP complejas que pueden ser utilizadas para filtrar correos electrónicos de un servidor IMAP. Llamando al método 'custom_search', agrega una cadena de búsqueda personalizada al generador de consultas. La cadena X-GM-RAW "has:attachment" es un término de búsqueda específico de Gmail que utiliza el atributo X-GM-RAW. Gmail permite el uso de su sintaxis de búsqueda web en búsquedas IMAP a través de este atributo. El término "has:attachment" es un operador de búsqueda de Gmail que encuentra todos los correos electrónicos que contienen un archivo adjunto. El siguiente fragmento de código demuestra cómo filtrar correos electrónicos de acuerdo con los criterios definidos (en este caso, todos los correos electrónicos con un archivo adjunto):

```py
import aspose.email as ae

builder = ae.clients.imap.ImapQueryBuilder()
builder.custom_search("X-GM-RAW \"has:attachment\"")

mailQuery = builder.get_query()
```

### **Aplicando Filtros Sensibles a Mayúsculas y Minúsculas**

La API también proporciona la capacidad de filtrar correos electrónicos del buzón basándose en un criterio sensible a mayúsculas y minúsculas. Los siguientes métodos de la clase [StringComparisonField](https://reference.aspose.com/email/python-net/aspose.email.tools.search/stringcomparisonfield/#stringcomparisonfield-class) proporcionan la capacidad de buscar correos electrónicos especificando banderas sensibles a mayúsculas y minúsculas.  

- Método `Aspose.Email.StringComparisonField.contains(value, ignore_case)`
- Método `Aspose.Email.StringComparisonField.equals(value, ignore_case)`
- Método `Aspose.Email.StringComparisonField.not_contains(value, ignore_case)`
- Método `Aspose.Email.StringComparisonField.not_equals(value, ignore_case)`

El siguiente fragmento de código muestra cómo implementar esta capacidad en tu proyecto:

```py
import aspose.email as ae

builder = ae.tools.search.MailQueryBuilder()
builder.from_address.contains("noreply@host.com", True)
```