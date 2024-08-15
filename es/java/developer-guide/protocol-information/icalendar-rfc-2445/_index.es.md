---
title: "iCalendar RFC 2445"
url: /es/java/icalendar-rfc-2445/
weight: 30
type: docs
---


{{% alert color="primary" %}}

El iCalendar RFC 2445 describe un conjunto de elementos de calendario y programación interoperables que permiten que las aplicaciones de programación grupal, administración de información personal y calendario intercambien información en un formato común.

Aspose.Email implementa los elementos del RFC relacionados con la programación, ya que tienen una aplicación muy amplia. Las versiones futuras pueden implementar otros elementos del RFC 2445, según la demanda.

En este artículo se describen los elementos del RFC relacionados con Aspose.Email. Le recomendamos que consulte con el estándar iCalendar <http://www.faqs.org/rfcs/rfc2445.html> para ver la imagen completa.

{{% /alert %}}
## **Patrones de recurrencia en el mundo real**
Un patrón de recurrencia describe las reglas cuando se produce el evento. Se necesita un motor de patrones de recurrencia como Aspose iCalendar para calcular las fechas y horas de las ocurrencias de un patrón de recurrencia determinado.
Encontramos cronogramas o patrones de recurrencia en muchas situaciones, por ejemplo:

- Diez reuniones de equipo, todos los lunes a las 10 de la mañana.
- Procese el pago del salario el último día hábil de cada mes.
- Controle la temperatura del paciente todos los días durante dos semanas.
- Ve al gimnasio los lunes, miércoles y viernes.
- Realice copias de seguridad cada 4 horas los días laborables.
- Generar informe de ventas sobre…
- Actualice las estadísticas del sitio web cada…

Casi cualquier evento que ocurre periódicamente se puede representar como un patrón de recurrencia. Por ejemplo, el código siguiente devolverá una matriz que contiene diez ocurrencias del ejemplo de la reunión de equipo anterior:

~~~java
CalendarRecurrence recurrencePattern = new CalendarRecurrence("DTSTART:20040301T100000\nRRULE:FREQ=WEEKLY;COUNT=10;BYDAY=MO");
DateCollection expectedDates = recurrencePattern.generateOccurrences();
System.out.println("expectedDates.Count = " + expectedDates.size());
for (int i = 0; i < expectedDates.size(); i++) {
    System.out.println("DateTime = " + sdf.format(expectedDates.getItem(i)));
}
~~~

{{% alert color="primary" %}}

Los patrones de recurrencia pueden volverse bastante complejos y requieren un motor de patrones de recurrencia confiable para analizar y validar la entrada y generar ocurrencias correctamente.

{{% /alert %}}
