---
title: "Trabajando con Mensajes del Servidor"
url: /es/python-net/working-with-messages-from-server/
weight: 40
type: docs
---

## **Obtener Información del Buzón de Correo**
Podemos obtener información sobre el buzón de correo, como el número de mensajes y el tamaño del buzón, utilizando los métodos GetMailBoxSize() y GetMailBoxInfo().

- El método `GetMailBoxSize()` devuelve el tamaño del buzón en bytes.
- El método `GetMailBoxInfo()` devuelve un objeto de tipo Pop3MailBoxInfo.

También es posible obtener el número de mensajes utilizando la propiedad MessageCount y el tamaño utilizando la propiedad OccupiedSize. El siguiente código de muestra muestra cómo obtener información sobre el buzón de correo. Muestra cómo:

1. Crear un [Pop3Client](https://apireference.aspose.com/email/net/aspose.email.clients.pop3/pop3client).
1. Conectar a un servidor POP3.
1. Obtener el tamaño del buzón.
1. Obtener información del buzón.
1. Obtener el número de mensajes en el buzón.
1. Obtener el tamaño ocupado.



{{< gist "aspose-email" "356f0e128b9d45a7ee779fc813eb87e5" "Examples-POP3-GettingMailboxInfo-GettingMailboxInfo.py" >}}
## **Obtener conteo de correos en el buzón**
El siguiente código de muestra muestra cómo contar los mensajes de correo en un buzón.



{{< gist "aspose-email" "356f0e128b9d45a7ee779fc813eb87e5" "Examples-POP3-GetEmailCountInMailbox-GetEmailCountInMailbox.py" >}}



Aspose.Email permite a los desarrolladores trabajar con correos electrónicos de muchas maneras diferentes. Por ejemplo, pueden recuperar información del encabezado antes de decidir si descargar o no un correo electrónico. O pueden recuperar correos electrónicos de un servidor y guardarlos sin analizarlos (más rápido) o después de analizarlos (más lento). Este artículo muestra cómo recuperar y convertir correos electrónicos.
## **Recuperar Información de Encabezados de Correo Electrónico**
Los encabezados de correo electrónico pueden darnos información sobre un mensaje de correo electrónico que podemos utilizar para decidir si recuperar o no el mensaje completo. Típicamente, la información del encabezado contiene el remitente, el asunto, la fecha de recepción, etc. (Los encabezados de correo electrónico se describen en detalle en la personalización de encabezados de correo electrónico. Ese tema es específicamente sobre el envío de correo electrónico con SMTP, pero la información del contenido del encabezado de correo sigue siendo válida para los correos electrónicos POP3). Los siguientes ejemplos muestran cómo recuperar encabezados de correo electrónico de un servidor POP3 por el número de secuencia del mensaje.



{{< gist "aspose-email" "356f0e128b9d45a7ee779fc813eb87e5" "Examples-POP3-RetrievingEmailHeaders-RetrievingEmailHeaders.py" >}}
## **Recuperar Mensajes de Correo Electrónico**
El componente Aspose.Email.Pop3 proporciona la capacidad de recuperar mensajes de correo electrónico del servidor POP3 y analizarlos en una instancia de MailMessage con la ayuda de los componentes MailMessage. La clase MailMessage contiene varias propiedades y métodos para manipular el contenido del correo electrónico. Al utilizar la función FetchMessage de la clase Pop3Client, puedes obtener una instancia de MailMessage directamente del servidor POP3. El siguiente código de muestra muestra cómo recuperar un mensaje de correo electrónico completo del servidor POP3.



{{< gist "aspose-email" "356f0e128b9d45a7ee779fc813eb87e5" "Examples-POP3-RetrievingEmailMessages-RetrievingEmailMessages.py" >}}
## **Recuperar Información de Resumen de Mensajes utilizando Id Único**
El cliente POP3 de la API puede recuperar información resumen de los mensajes desde el servidor utilizando el id único del mensaje. Esto proporciona acceso rápido a la información corta del mensaje sin tener que recuperar primero el mensaje completo del servidor. El siguiente código de muestra muestra cómo recuperar información resumen de mensajes.



{{< gist "aspose-email" "356f0e128b9d45a7ee779fc813eb87e5" "Examples-POP3-RetrieveMessageSummaryInformationUsingUniqueId-RetrieveMessageSummaryInformationUsingUniqueId.py" >}}
## **Listar Mensajes con MultiConexión**

Para operaciones de alta carga, Aspose.Email ofrece la propiedad 'use_multi_connection' de la clase [Pop3Client](https://reference.aspose.com/email/python-net/aspose.email.clients.pop3/pop3client/#pop3client-class) para utilizar múltiples conexiones mientras se recuperan correos electrónicos. Sin embargo, utilizar este modo no necesariamente tiene que llevar a un aumento en el rendimiento. El siguiente código de muestra muestra cómo establecer una conexión a un servidor POP3, configurar el cliente para permitir hasta 5 conexiones concurrentes y habilitar el modo de multi-conexión para recuperar información sobre los mensajes presentes en el servidor:

```py
import aspose.email as ae

client = ae.clients.pop3.Pop3Client("host", 995, "username", "password", ae.clients.SecurityOptions.AUTO)

client.connections_quantity = 5
client.use_multi_connection = ae.clients.MultiConnectionMode.ENABLE
message_info_coll = client.list_messages()
```

## **Recuperar Mensajes del Servidor y Guardar en Disco**
### **Guardar Mensaje en Disco sin Analizar**
Si deseas descargar mensajes de correo electrónico del servidor POP3 sin analizarlos, utiliza la función SaveMessage de la clase Pop3Client. La función SaveMessage no analiza el mensaje de correo electrónico, por lo que es más rápida que la función FetchMessage. El siguiente código de muestra muestra cómo guardar un mensaje por su número de secuencia, en este caso el número 1. El método SaveMessage guarda el mensaje en el formato original EML sin analizarlo.



{{< gist "aspose-email" "356f0e128b9d45a7ee779fc813eb87e5" "Examples-POP3-SaveToDiscWithoutParsing-SaveToDiscWithoutParsing.py" >}}

### **Analizar Mensaje Antes de Guardar**

Utiliza el método 'fetch_message' del objeto cliente creado utilizando la clase [Pop3Client](https://reference.aspose.com/email/python-net/aspose.email.clients.pop3/pop3client/#pop3client-class) para recuperar el mensaje con un número de secuencia específico. El siguiente código de muestra demuestra cómo recuperar un mensaje específico y guardarlo utilizando su asunto como nombre de archivo al llamar al método 'save' en el objeto msg:

```py
import aspose.email as ae

client = ae.clients.pop3.Pop3Client("host", 995, "username", "password", ae.clients.SecurityOptions.AUTO)

# Recuperar el mensaje por su número de secuencia y guardar el mensaje utilizando su asunto como nombre de archivo
msg = client.fetch_message(1)
msg.save("first-message_out.eml", ae.SaveOptions.default_eml)
```
### **Filtrar Mensajes por Remitente, Destinatario o Fecha**
La clase Pop3Client, descrita en la conexión a un servidor POP3, proporciona el método list_messages() que obtiene todos los mensajes de un buzón. Para obtener solo los mensajes que coinciden con alguna condición, utiliza el método sobrecargado ListMessages() que toma MailQuery como argumento. La clase MailQuery proporciona varias propiedades para especificar las condiciones de la consulta, por ejemplo, fecha, asunto, remitente, destinatario, etc. La clase MailQueryBuilder se utiliza para construir la expresión de búsqueda. Primero, se establecen todas las condiciones y restricciones y luego se llena MailQuery con la consulta desarrollada por MailQueryBuilder. El objeto de la clase MailQuery es utilizado por Pop3Client para extraer la información filtrada del servidor. Este artículo muestra cómo filtrar mensajes de correo electrónico de un buzón. El primer ejemplo ilustra cómo filtrar mensajes según la fecha y el asunto. También mostramos cómo filtrar por otros criterios y cómo construir consultas más complejas. También se muestra la aplicación del filtro de Fecha y Hora para recuperar correos electrónicos específicos del buzón. Además, también se muestra cómo aplicar filtros que distinguen entre mayúsculas y minúsculas.
### **Filtrar Mensajes del Buzón**
Para filtrar mensajes de un buzón:

1. Conéctate e inicia sesión en un servidor POP3.
1. Crea una instancia de MailQuery y establece las propiedades deseadas.
1. Llama al método `Pop3Client.list_messages(MailQuery query)` y pasa el MailQuery como parámetro para obtener solo los mensajes filtrados.

El siguiente código de muestra muestra cómo conectarse a un buzón POP3 y obtener mensajes que llegaron hoy y tienen la palabra "boletín" en el asunto.



{{< gist "aspose-email" "356f0e128b9d45a7ee779fc813eb87e5" "Examples-POP3-FilterMessagesFromMailbox-FilterMessagesFromMailbox.py" >}}

### **Obtener Mensajes que Cumplen Criterios Específicos**

Aspose.Email también hace posible construir criterios de búsqueda complejos para consultar y filtrar mensajes de correo electrónico. Para este propósito, utiliza la clase [MailQueryBuilder](https://reference.aspose.com/email/python-net/aspose.email.tools.search/mailquerybuilder/#mailquerybuilder-class) y sus propiedades. Los criterios para la obtención son los siguientes:

- Obtener mensajes por fecha de entrega.
- Obtener mensajes dentro de un rango.
- Obtener mensajes de un remitente específico.
- Obtener mensajes de un dominio específico.
- Obtener mensajes a un destinatario específico.

#### **Fecha de hoy**

Para obtener mensajes por fecha de entrega, utiliza la propiedad 'internal_date' como se muestra en el código de muestra a continuación:

```py
import aspose.email as ae
from datetime import datetime

builder = ae.tools.search.MailQueryBuilder()
builder.internal_date.on(datetime.now())
```
#### **Rango de fechas**

Para obtener mensajes dentro de un rango de fechas, utiliza la misma propiedad 'internal_date' especificando el rango de fechas como se muestra en el código de muestra a continuación:

```py
import aspose.email as ae
from datetime import datetime, timedelta

builder = ae.tools.search.MailQueryBuilder()
# Correos que llegaron en los últimos 7 días
builder.internal_date.before(datetime.now())
builder.internal_date.since(datetime.today() - timedelta(days=7))
```
#### **Remitente Específico**

Para obtener mensajes de un remitente específico, utiliza la propiedad 'from_address' como se muestra en el código de muestra a continuación:

```py
import aspose.email as ae

builder = ae.tools.search.MailQueryBuilder()
builder.from_address.contains("saqib.razzaq@127.0.0.1")
```
#### **Dominio Específico**

Para obtener mensajes de un dominio específico, utiliza la propiedad 'from_address' como se muestra en el código de muestra a continuación:

```py
import aspose.email as ae

builder = ae.tools.search.MailQueryBuilder()
builder.from_address.contains("SpecificHost.com")
```
#### **Destinatario Específico**

Para obtener mensajes a un destinatario específico, utiliza la propiedad 'to' como se muestra en el código de muestra a continuación:

```py
import aspose.email as ae

builder = ae.tools.search.MailQueryBuilder()
builder.to.contains("recipient")
```
### **Construir Consultas Complejas**

A veces es necesario satisfacer más de una consulta. Aspose.Email hace posible combinar consultas en varias declaraciones. Crea un objeto [MailQueryBuilder](https://reference.aspose.com/email/python-net/aspose.email.tools.search/mailquerybuilder/#mailquerybuilder-class) y utiliza sus propiedades para construir consultas específicas.

#### **Combinar Consultas con AND**

El siguiente código de muestra muestra cómo combinar consultas con AND.

```py
import aspose.email as ae
from datetime import datetime, timedelta

builder = ae.tools.search.MailQueryBuilder()
builder.internal_date.before(datetime.now())
builder.internal_date.since(datetime.today() - timedelta(days=7))
builder.from_address.contains("SpecificHost.com")
```
#### **Combinar Consultas con OR**

El siguiente código de muestra muestra cómo combinar consultas con OR.

```py
import aspose.email as ae

builder = ae.tools.search.MailQueryBuilder()
builder.either(builder.subject.contains("test"), builder.from_address.contains("noreply@host.com"))
```

#### **Aplicar Filtros que Distinguen Mayúsculas**

La API también proporciona la capacidad de filtrar correos electrónicos del buzón según criterios que distinguen entre mayúsculas y minúsculas. Los siguientes métodos de la clase [StringComparisonField](https://reference.aspose.com/email/python-net/aspose.email.tools.search/stringcomparisonfield/#stringcomparisonfield-class) proporcionan la capacidad de buscar correos electrónicos especificando flags que distinguen mayúsculas y minúsculas.  

- Método `Aspose.Email.StringComparisonField.contains(value, ignore_case)`
- Método `Aspose.Email.StringComparisonField.equals(value, ignore_case)`
- Método `Aspose.Email.StringComparisonField.not_contains(value, ignore_case)`
- Método `Aspose.Email.StringComparisonField.not_equals(value, ignore_case)`

El siguiente código de muestra muestra cómo implementar esta capacidad en tu proyecto:

```py
import aspose.email as ae

builder = ae.tools.search.MailQueryBuilder()
builder.from_address.contains("noreply@host.com", True)
```