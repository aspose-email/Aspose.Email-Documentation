---
title: "Introducción a los patrones de recurrencia"
url: /es/net/introducing-recurrence-patterns/
weight: 60
type: docs
---


Puedes pensar en un *patrón de recurrencia* como una forma de describir un horario en particular. Contiene la información suficiente para crear una lista de ocurrencias (fechas y horas) de acuerdo con un cronograma determinado. Un patrón de recurrencia puede contener reglas de recurrencia que describen los ciclos que se combinan para formar el patrón general. En general, cuanto más complejo sea un patrón de recurrencia, más reglas de recurrencia contendrá. Los patrones de recurrencia pueden incluir *exceptions* (no debe confundirse con las excepciones que representan errores que se producen durante la ejecución de la aplicación). Las excepciones añaden o eliminan las fechas de aparición del patrón original. Las excepciones se pueden especificar como ocurrencias explícitas o como un patrón en sí mismas. Ejemplos de patrones de recurrencia con excepciones:

- Cada segundo viernes, excepto de junio a agosto.
- El día 1 de cada mes, excepto enero, que debería ser el día 2.

Los patrones de recurrencia suelen ser periódicos, pero no tienen por qué serlo. Un patrón de recurrencia se puede describir completamente simplemente como un conjunto de fechas y horas de aparición predefinidas. El RFC de iCalendar define *components*, como VEVENT o VTODO que representan eventos o tareas. Los componentes pueden tener propiedades como la fecha y hora de inicio, la descripción, la ubicación, los asistentes y la periodicidad. Por lo tanto, un patrón de recurrencia normalmente existe como una propiedad de una tarea o un evento que se repite. Las propiedades del patrón de recurrencia definidas por iCalendar son:

- DTSTART: la fecha y hora de inicio del patrón (también representa la primera aparición si no se excluye explícitamente).
- RRULE: especifica una regla de repetición para un conjunto de periodicidad.
- RDATE: define una lista de fechas y horas para incluir en un conjunto de periodicidad.
- EXRULE: especifica una regla de repetición para las excepciones de un conjunto de periodicidad.
- EXDATE: define una lista de excepciones de fecha y hora de un conjunto de recurrencias.

Solo se requiere DTSTART y solo debe haber un DTSTART. Todas las demás propiedades son opcionales y se pueden especificar más de una vez. iCalendar toma una cadena en formato iCalendar y lee el patrón de recurrencia en un [RecurrencePattern](https://apireference.aspose.com/email/net/aspose.email.calendar.recurrences/recurrencepattern) objeto. La cadena puede ser una descripción completa de un componente de iCalendar (por ejemplo, un VEVENT completo) o puede ser solo un fragmento que contenga solo el patrón de recurrencia. Una vez cargado el patrón de recurrencia en un objeto RecurrencePattern, puedes:

- Examine y modifique el patrón mediante programación a través de los métodos y propiedades proporcionados por Aspose.iCalendar
- Genere fechas y horas de aparición en un rango de fechas específico.
- Guarda el patrón en formato iCalendar.

El siguiente fragmento de código muestra que la parte RRULE contiene la regla de recurrencia.



{{< gist "aspose-email" "9e8fbeb51a8cbc4129dc71ca8cd55f0b" "Examples-CSharp-RecurrencePattern-RecurrencePattern.cs" >}}



Mira el [patrones de recurrencia muestrales](#sample-patterns) para ver ilustraciones sobre cómo crear patrones de recurrencia.
## **Acerca del modelo de objetos Aspose.iCalendar**
El espacio de nombres Aspose.iCalendar contiene todas las clases proporcionadas por el componente Aspose.iCalendar. RecurrencePattern y RecurrenceRule son las clases centrales de Aspose.iCalendar y proporcionan implementaciones concretas de los elementos RFC 2445 correspondientes.

La clase RecurrencePattern representa todo el patrón de recurrencia. Puedes crear un nuevo patrón de recurrencia desde cero con el constructor predeterminado o cargar un patrón existente en formato iCalendar con el método estático fromCalendar. La clase RecurrenceRule representa la parte RRULE o EXRULE de un patrón de recurrencia. RecurrenceRule expone una serie de propiedades que se asignan directamente a sus homólogas en el estándar iCalendar. Por ejemplo, byMonth se asigna a BYMONTH en iCalendar, etc. Al examinar o establecer los valores de las propiedades de RecurrenceRule, puede analizar o modificar una regla de periodicidad. Para obtener más información y ejemplos de código, consulta RecurrencePattern y RecurrenceRule en la referencia de la API.
## **Patrones de muestra**
En esta sección se incluyen los siguientes temas:

- El último día del mes.
- El último día hábil de cada mes.
- El último lunes del año.
- Viernes de la primera semana del año según la norma ISO 8601.
- Primer viernes del año.
### **El último día del mes**
Estas muestras [patrón de recurrencia](/email/net/introducing-recurrence-patterns/) especifica el último día del mes, todos los meses.

RRULE:FREQ=MONTHLY;BYMONTHDAY=-1

Del mismo modo, si quieres que ocurra un día antes del último día del mes, usa BYMONTHDAY=-2. Si especificas BYMONTHDAY=31, de acuerdo con el estándar de iCalendar, no se generará ninguna incidencia en los meses que tengan menos de 31 días.
### **El último día laboral de cada mes**
Estas muestras [patrón de recurrencia](/email/net/introducing-recurrence-patterns/) especifica el último día laborable del mes, todos los meses. Los días laborables se definen como los días en los que se trabaja. En Europa, por ejemplo, los días laborables son normalmente de lunes a viernes.

RRULE:FREQ=MONTHLY;BYDAY=MO,TU,WE,TH,FR;BYSETPOS=-1

La regla anterior especifica todos los días laborables de un mes y selecciona el último de ellos. El resultado neto es el último día laborable del mes.
### **El último lunes del año**
Esta muestra [patrón de recurrencia](/email/net/introducing-recurrence-patterns/) especifica un evento que ocurre el último lunes del año.

RRULE:FREQ=YEARLY;BYDAY=-1MO
### **Viernes de la primera semana del año según la norma ISO 8601**
Esta muestra [patrón de recurrencia](/email/net/introducing-recurrence-patterns/) especifica el viernes de la primera semana del año. En la especificación ISO 8601, la primera semana del año es la primera semana del año si tiene al menos cuatro días. Cuando un año comienza un sábado, por ejemplo, la semana 1 es la semana inmediatamente siguiente, a partir del lunes 3 de enero.

FREQ=YEARLY;BYWEEKNO=1;BYDAY=FR
### **Primer viernes del año**
Esta muestra [patrón de recurrencia](/email/net/introducing-recurrence-patterns/) especifica un evento que ocurre el primer viernes del año.

FREQ=YEARLY;BYDAY=1FR

En 1999, por ejemplo, el primer viernes del año es el 01/01 de 1999, mientras que el viernes de la primera semana de la ISO 8601 es el 01/08 de 1999.
