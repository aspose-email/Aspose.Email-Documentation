---
title: "Detalles importantes de iCalendar RFC 2445"
url: /es/net/important-icalendar-rfc-2445-details/
weight: 70
type: docs
---


## **Acerca del modelo de objetos Aspose.iCalendar**
The [Aspose.iCalendar](https://apireference.aspose.com/email/net/aspose.email.calendar) El espacio de nombres contiene todas las clases proporcionadas por el componente Aspose.iCalendar RecurrencePattern y RecurrenceRule son las clases centrales de Aspose.iCalendar y proporcionan implementaciones concretas de los elementos RFC 2445 correspondientes.

La clase RecurrencePattern representa todo el patrón de recurrencia. Puedes crear un nuevo patrón de recurrencia desde cero con el constructor predeterminado o cargar un patrón existente en formato iCalendar con el método estático fromCalendar. La clase RecurrenceRule representa la parte RRULE o EXRULE de un patrón de recurrencia. RecurrenceRule expone una serie de propiedades que se asignan directamente a sus homólogas en el estándar iCalendar. Por ejemplo, byMonth se asigna a BYMONTH en iCalendar, etc. Al examinar o establecer los valores de las propiedades de RecurrenceRule, puede analizar o modificar una regla de periodicidad. Para obtener más información y ejemplos de código, consulta RecurrencePattern y RecurrenceRule en la referencia de la API.
## **Detalles importantes de iCalendar RFC 2445**
En esta sección se incluyen los siguientes temas:

- Formatos de fecha y hora.
- DATE.
- FECHA-HORA con hora local.
- FECHA-HORA con hora UTC.
- FECHA-HORA con hora local y zona horaria.
- BYWEEKNO cumple con la norma ISO 8601
### **Formatos de fecha y hora**
Las fechas, o fechas con horas asociadas, se pueden usar en los elementos DTSTART, UNTIL, EXDATE y RDATE al especificar un patrón de periodicidad. iCalendar define el tipo de valor DATE para identificar los valores que contienen una fecha del calendario y también define el tipo DATE-TIME para identificar los valores que especifican una fecha y hora precisas del calendario. Los valores de fecha y hora se pueden especificar de tres formas, con:

- Hora local.
- Hora UTC.
- Hora local y zona horaria.
### **DATE**
Según el estándar iCalendar, los valores de FECHA deben seguir el formato aaaaMmdd. El siguiente ejemplo representa el 14 de julio de 1997:19970714
### **FECHA-HORA con hora local**
El formulario de fecha con hora local es simplemente un valor de fecha y hora que no contiene el designador UTC y no hace referencia a una zona horaria. Por ejemplo, lo siguiente representa el 18 de enero de 1998 a las 11 p. m.: DTSTART:19980118T230000. Se dice que los valores de fecha y hora de este tipo son «flotantes» y no están vinculados a ninguna zona horaria en particular. Se utilizan para representar el mismo valor de hora, minuto y segundo independientemente de la zona horaria que se esté observando actualmente.
### **FECHA-HORA con hora UTC**
La fecha con hora UTC, o hora absoluta, se identifica con un sufijo Z en mayúscula latina, el designador UTC, adjunto al valor de hora. Por ejemplo, lo siguiente representa el 19 de enero de 1998 a las 07:00 UTC: DTSTART:19980119T070000Z Tenga en cuenta que Aspose.iCalendar ignora el sufijo Z del formato UTC y trata la hora como hora local. El estándar RFC2445 establece que la porción de tiempo especificada en la regla HASTA de un patrón de periodicidad debe estar en formato UTC. Esta afirmación es muy extraña y, de hecho, hay ejemplos en el estándar que se calculan incorrectamente. Aspose.iCalendar acepta la hora en cualquier formato de la regla UNTIL.
### **FECHA-HORA con hora local y zona horaria**
Para hacer referencia a la zona horaria, DATE-TIME se modifica con la propiedad TZID. Por ejemplo, lo siguiente representa a las 2 de la mañana en Nueva York el 19 de enero de 1998: DTSTART; TZID=US-eastern:19980119T020000. Tenga en cuenta que, por el momento, aspose.iCalendar ignora el parámetro TZID y trata la hora como una hora local.
### **BYWEEKNO cumple con la norma ISO 8601**
Utilice BYWEEKNO solo cuando cumpla con [ISO 8601](https://en.wikipedia.org/wiki/ISO_8601) es obligatorio. Los números de semana, tal como los define la norma ISO 8601, son muy diferentes de los números de semana en el sentido normal. Según la norma ISO 8601, la semana número uno del año natural es la primera semana de un año calendario que contiene al menos cuatro días. Esta regla hace que el algoritmo sea específico para las aplicaciones que requieren la conformidad con la norma ISO 8601 y lo hace casi inaplicable a otros usos. La ISO 8601 es compatible con algunas aplicaciones bancarias y financieras europeas. También se usa en televisión para reservar anuncios. La regla BYWEEKNO especifica una lista de números delimitados por comas que identifican las semanas del año. Los valores válidos van del 1 al 53 y del 1 al 53. Esto corresponde a las semanas según la numeración de semanas definida en la norma ISO 8601. BYWEEKNO solo es válido para las reglas ANUALES.
