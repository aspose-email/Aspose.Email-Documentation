---
title: "Introducción a los Patrones de Recurrencia"
url: /es/net/introducing-recurrence-patterns/
weight: 60
type: docs
---

Puedes pensar en un *patrón de recurrencia* como una forma de describir un programa particular. Contiene solo la información suficiente para construir una lista de ocurrencias (fechas y horas) de acuerdo con un programa dado. Un patrón de recurrencia puede contener reglas de recurrencia que describen ciclos que se combinan para formar el patrón general. En general, cuanto más complejo sea un patrón de recurrencia, más reglas de recurrencia contendrá. Los patrones de recurrencia pueden incluir *excepciones* (no confundir con excepciones que representan errores que ocurren durante la ejecución de la aplicación). Las excepciones añaden o eliminan fechas de ocurrencia al patrón original. Las excepciones pueden especificarse como ocurrencias explícitas o como un patrón en sí. Ejemplos de patrones de recurrencia con excepciones:

- Todos los segundos viernes, excepto de junio a agosto.
- El 1 de cada mes, excepto en enero, cuando debe ser el 2.

Los patrones de recurrencia son frecuentemente periódicos, pero no tienen que serlo. Un patrón de recurrencia puede describirse completamente solo como un conjunto de fechas y horas de ocurrencia predefinidas. El RFC de iCalendar define *componentes*, como VEVENT o VTODO que representan eventos o tareas. Los componentes pueden tener propiedades como fecha y hora de inicio, descripción, ubicación, asistentes y recurrencia. Un patrón de recurrencia, por lo tanto, normalmente existe como una propiedad de una tarea o un evento recurrente. Las propiedades del patrón de recurrencia definidas por iCalendar son:

- DTSTART - la fecha y hora de inicio del patrón (también representa la primera ocurrencia si no se excluye explícitamente).
- RRULE - especifica una regla de repetición para un conjunto de recurrencia.
- RDATE - define una lista de fechas y horas para incluir en un conjunto de recurrencia.
- EXRULE - especifica una regla de repetición para excepciones de un conjunto de recurrencia.
- EXDATE - define una lista de fechas y horas de excepciones de un conjunto de recurrencia.

Solo se requiere DTSTART y debe haber solo un DTSTART. Todas las demás propiedades son opcionales y pueden especificarse más de una vez. Aspose.iCalendar toma una cadena en formato iCalendar y lee el patrón de recurrencia en un objeto [RecurrencePattern](https://apireference.aspose.com/email/net/aspose.email.calendar.recurrences/recurrencepattern). La cadena puede ser una descripción completa de un componente iCalendar (por ejemplo, un VEVENT completo) o puede ser solo un fragmento que contiene solo el patrón de recurrencia. Una vez que el patrón de recurrencia se carga en un objeto RecurrencePattern, puedes:

- Examinar y modificar el patrón programáticamente a través de métodos y propiedades provistas por Aspose.iCalendar.
- Generar fechas/hora de ocurrencia en un rango de fechas especificado.
- Guardar el patrón en formato iCalendar.

El siguiente fragmento de código muestra que la parte RRULE contiene la regla de recurrencia.

{{< gist "aspose-email" "9e8fbeb51a8cbc4129dc71ca8cd55f0b" "Examples-CSharp-RecurrencePattern-RecurrencePattern.cs" >}}

Consulta los [patrones de recurrencia de muestra](#sample-patterns) para ilustraciones sobre cómo crear patrones de recurrencia.
## **Acerca del Modelo de Objetos de Aspose.iCalendar**
El espacio de nombres Aspose.iCalendar contiene todas las clases proporcionadas por el componente Aspose.iCalendar. RecurrencePattern y RecurrenceRule son las clases centrales de Aspose.iCalendar y proporcionan implementaciones concretas de los elementos correspondientes del RFC 2445.

La clase RecurrencePattern representa todo el patrón de recurrencia. Puedes crear un nuevo patrón de recurrencia desde cero usando el constructor predeterminado o cargar un patrón existente en formato iCalendar usando el método estático FromiCalendar. La clase RecurrenceRule representa la parte RRULE o EXRULE de un patrón de recurrencia. RecurrenceRule expone una serie de propiedades que se mapean directamente a sus equivalentes en el estándar de iCalendar. Por ejemplo, ByMonth se mapea a BYMONTH en iCalendar y así sucesivamente. Al examinar o establecer valores de las propiedades de RecurrenceRule, puedes analizar o modificar una regla de recurrencia. Para obtener más información y ejemplos de código, consulta RecurrencePattern y RecurrenceRule en la Referencia de API.
## **Patrones de Muestra**
Esta sección incluye los siguientes temas:

- El Último Día del Mes.
- El Último Día Laboral de Cada Mes.
- El Último Lunes del Año.
- El Viernes de la Primera Semana ISO 8601 del Año.
- El Primer Viernes del Año.
### **El Último Día del Mes**
Este [patrón de recurrencia](/email/net/introducing-recurrence-patterns/) especifica el último día del mes, cada mes.

RRULE:FREQ=MONTHLY;BYMONTHDAY=-1

De manera similar, si deseas una ocurrencia un día antes del último día del mes, usa BYMONTHDAY=-2. Si especificas BYMONTHDAY=31, entonces de acuerdo con el estándar de iCalendar, no habrá ninguna ocurrencia generada en los meses que tienen menos de 31 días.
### **El Último Día Laboral de Cada Mes**
Este [patrón de recurrencia](/email/net/introducing-recurrence-patterns/) especifica el último día laboral del mes, cada mes. Los días laborales se definen como los días en los que trabajas. En Europa, por ejemplo, los días laborales son normalmente de lunes a viernes.

RRULE:FREQ=MONTHLY;BYDAY=MO,TU,WE,TH,FR;BYSETPOS=-1

La regla anterior especifica todos los días laborales de un mes y selecciona el último de ellos. El resultado neto es un último día laboral en un mes.
### **El Último Lunes del Año**
Este [patrón de recurrencia](/email/net/introducing-recurrence-patterns/) especifica un evento que ocurre el último lunes del año.

RRULE:FREQ=YEARLY;BYDAY=-1MO
### **El Viernes de la Primera Semana ISO 8601 del Año**
Este [patrón de recurrencia](/email/net/introducing-recurrence-patterns/) especifica el viernes de la primera semana del año. En la especificación ISO 8601, la primera semana del año es la primera semana del año que tiene al menos cuatro días. Cuando un año comienza un sábado, por ejemplo, la semana 1 es la semana inmediatamente siguiente, comenzando el lunes 3 de enero.

FREQ=YEARLY;BYWEEKNO=1;BYDAY=FR
### **El Primer Viernes del Año**
Este [patrón de recurrencia](/email/net/introducing-recurrence-patterns/) especifica un evento que ocurre el primer viernes del año.

FREQ=YEARLY;BYDAY=1FR

En 1999, por ejemplo, el primer viernes del año es 1999/01/01, mientras que el viernes de la primera semana ISO 8601 es 1999/01/08.