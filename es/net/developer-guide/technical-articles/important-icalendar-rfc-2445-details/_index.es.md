---
title: "Detalles Importantes de iCalendar RFC 2445"
url: /es/net/detalles-importantes-de-icalendar-rfc-2445/
weight: 70
type: docs
---


## **Acerca del Modelo de Objetos de Aspose.iCalendar**
El espacio de nombres [Aspose.iCalendar](https://apireference.aspose.com/email/net/aspose.email.calendar) contiene todas las clases proporcionadas por el componente Aspose.iCalendar. RecurrencePattern y RecurrenceRule son las clases centrales de Aspose.iCalendar y proporcionan implementaciones concretas de los elementos correspondientes de RFC 2445.

La clase RecurrencePattern representa todo el patrón de recurrencia. Puedes crear un nuevo patrón de recurrencia desde cero utilizando el constructor predeterminado o cargar un patrón existente en formato iCalendar utilizando el método estático FromiCalendar. La clase RecurrenceRule representa la parte RRULE o EXRULE de un patrón de recurrencia. RecurrenceRule expone una serie de propiedades que se corresponden directamente con sus contrapartes en el estándar iCalendar. Por ejemplo, ByMonth se corresponde con BYMONTH en iCalendar, y así sucesivamente. Al examinar o establecer valores de las propiedades de RecurrenceRule, puedes analizar o modificar una regla de recurrencia. Para obtener más información y ejemplos de código, consulta RecurrencePattern y RecurrenceRule en la Referencia de la API.
## **Detalles Importantes de iCalendar RFC 2445**
Esta sección incluye los siguientes temas:

- Formatos de Fecha y Hora.
- DATE.
- DATE-TIME con Hora Local.
- DATE-TIME con Hora UTC.
- DATE-TIME con Hora Local y Zona Horaria.
- BYWEEKNO Proporciona Cumplimiento con ISO 8601
### **Formatos de Fecha y Hora**
Las fechas, o fechas con horas asociadas, pueden ser utilizadas en los elementos DTSTART, UNTIL, EXDATE y RDATE al especificar un patrón de recurrencia. iCalendar define el tipo de valor DATE para identificar valores que contienen una fecha del calendario y también define el tipo de DATE-TIME para identificar valores que especifican una fecha del calendario precisa y la hora del día. Los valores DATE-TIME pueden especificarse en tres formas, con:

- Hora local.
- Hora UTC.
- Hora local y zona horaria.
### **DATE**
Según el estándar iCalendar, los valores DATE deben seguir el formato yyyyMMdd. El siguiente ejemplo representa el 14 de julio de 1997: 19970714 
### **DATE-TIME con Hora Local**
La forma de fecha con hora local es simplemente un valor de fecha-hora que no contiene el designador UTC y no hace referencia a una zona horaria. Por ejemplo, lo siguiente representa el 18 de enero de 1998 a las 11 PM: DTSTART:19980118T230000. Los valores de fecha-hora de este tipo se consideran "flotantes" y no están vinculados a ninguna zona horaria en particular. Se utilizan para representar el mismo valor de hora, minuto y segundo independientemente de la zona horaria que se esté observando actualmente. 
### **DATE-TIME con Hora UTC**
La fecha con hora UTC, o tiempo absoluto, se identifica mediante un carácter sufijo de letra mayúscula latina Z, el designador UTC, añadido al valor de tiempo. Por ejemplo, lo siguiente representa el 19 de enero de 1998 a las 0700 UTC: DTSTART:19980119T070000Z Ten en cuenta que Aspose.iCalendar ignora el sufijo Z del formato UTC y trata el tiempo como hora local. El estándar RFC2445 establece que una parte de tiempo especificada en la regla UNTIL de un patrón de recurrencia debe estar en formato UTC. Esta es una afirmación muy extraña, y de hecho, hay ejemplos en el estándar que están calculados incorrectamente. Aspose.iCalendar acepta tiempo en cualquier formato en la regla UNTIL. 
### **DATE-TIME con Hora Local y Zona Horaria**
Para hacer referencia a la zona horaria, DATE-TIME se modifica con la propiedad TZID. Por ejemplo, lo siguiente representa las 2 AM en Nueva York el 19 de enero de 1998: DTSTART;TZID=US-Eastern:19980119T020000. Ten en cuenta que Aspose.iCalendar en este momento ignora el parámetro TZID y trata el tiempo como hora local. 
### **BYWEEKNO Proporciona Cumplimiento con ISO 8601**
Utiliza BYWEEKNO solo cuando se requiera conformidad con [ISO 8601](https://en.wikipedia.org/wiki/ISO_8601). Los números de semana definidos por ISO 8601 son muy diferentes de los números de semana en el sentido normal. Según ISO 8601, el número de semana uno del año calendario es la primera semana de un año calendario que contiene al menos cuatro días. Esta regla hace que el algoritmo sea específico para aplicaciones que requieren conformidad con ISO 8601 y lo hace casi inaplicable a otros usos. ISO 8601 es compatible con algunas aplicaciones bancarias y financieras europeas. También se utiliza en televisión para la contratación de comerciales. La regla BYWEEKNO especifica una lista delimitada por comas de números que identifican las semanas del año. Los valores válidos son del 1 al 53. Esto se corresponde con las semanas según la numeración de semanas definida en ISO 8601. BYWEEKNO solo es válido para reglas ANUALES.