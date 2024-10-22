---
title: "iCalendar RFC 2445"
url: /es/java/icalendar-rfc-2445/
weight: 30
type: docs
---


{{% alert color="primary" %}} 

El iCalendar RFC 2445 describe un conjunto de elementos de calendarios y programación interoperables que permiten a las aplicaciones de programación grupal, gestión de información personal y calendarios intercambiar información en un formato común.

Aspose.Email implementa los elementos relacionados con la programación del RFC, ya que estos tienen una aplicación muy amplia. Las versiones futuras pueden implementar otros elementos del RFC 2445, dependiendo de la demanda.

Este artículo describe los elementos del RFC que se relacionan con Aspose.Email. Recomendamos que consulte el estándar iCalendar <http://www.faqs.org/rfcs/rfc2445.html> para una visión completa. 

{{% /alert %}} 
## **Patrones de Recurrencia en el Mundo Real**
Un patrón de recurrencia describe las reglas sobre cuándo ocurre el evento. Se necesita un motor de patrones de recurrencia como Aspose iCalendar para calcular las fechas y horas de las ocurrencias para un patrón de recurrencia dado.
Encontramos horarios o patrones de recurrencia en muchas situaciones, por ejemplo:

- Diez reuniones de equipo, cada lunes a las 10am.
- Procesar el pago de salario el último día laborable de cada mes.
- Revisar la temperatura del paciente todos los días durante dos semanas.
- Ir al gimnasio los lunes, miércoles y viernes.
- Ejecutar una copia de seguridad cada 4 horas en días laborables.
- Generar informe de ventas el …
- Actualizar estadísticas del sitio web cada …

Casi cualquier evento que ocurra periódicamente puede ser representado como un patrón de recurrencia. Por ejemplo, el siguiente código devolverá un array que contiene diez ocurrencias del ejemplo anterior de la reunión de equipo: 

~~~java
CalendarRecurrence recurrencePattern = new CalendarRecurrence("DTSTART:20040301T100000\nRRULE:FREQ=WEEKLY;COUNT=10;BYDAY=MO");
DateCollection expectedDates = recurrencePattern.generateOccurrences();
System.out.println("expectedDates.Count = " + expectedDates.size());
for (int i = 0; i < expectedDates.size(); i++) {
    System.out.println("DateTime = " + sdf.format(expectedDates.getItem(i)));
}
~~~

{{% alert color="primary" %}} 

Los patrones de recurrencia pueden volverse bastante complejos y requieren un motor de patrones de recurrencia confiable para analizar y validar la entrada y generar las ocurrencias correctamente. 

{{% /alert %}}