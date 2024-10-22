---
title: "Generar Ocurrencias a Partir de un Patrón de Recurrencia"
url: /es/java/generate-occurrences-from-a-recurrence-pattern/
weight: 180
type: docs
---


Con Aspose.Email, es posible generar ocurrencias utilizando un patrón de recurrencia. Este artículo explica cómo, cómo [generar la siguiente ocurrencia](#calculate-the-next-occurrence-or-n-next-occurrences) y [obtener descripciones de elementos amigables para el usuario](#get-user-friendly-text-for-a-recurrence). Las ocurrencias de un patrón de recurrencia en un calendario MAPI pueden generarse utilizando Aspose.Email. El siguiente fragmento de código muestra cómo generar ocurrencias a partir de patrones de recurrencia.


## **Calcular la Siguiente Ocurrencia o n Siguientes Ocurrencias**
Para obtener la ocurrencia "siguiente", utiliza el método GenerateOccurrences con el parámetro nNextOccurrences = 1. El siguiente fragmento de código muestra cómo generar 20 ocurrencias utilizando nNextOccurrences = 20. La salida del código a continuación es la siguiente:

![todo:image_alt_text](generate-occurrences-from-a-recurrence-pattern_1.png)


~~~Java
SimpleDateFormat sdf = new SimpleDateFormat("yyyy-MM-dd HH:mm:ss");

CalendarRecurrence recurrencePattern = new CalendarRecurrence();

recurrencePattern.setStartDate(sdf.parse("1997-09-10 09:00:00"));
RecurrenceRule rule = recurrencePattern.getRRules().add();
rule.setFrequency(Frequency.Monthly);
rule.setCount(20);
rule.setInterval(18);
rule.getByMonthDay().add(new int[] { 10, 11, 12, 13, 14, 15 });
DateCollection expectedDates = recurrencePattern.generateOccurrences(20);
System.out.println("expectedDates.Count = " + expectedDates.size());
for (int i = 0; i < expectedDates.size(); i++) {
    System.out.println("DateTime = " + sdf.format(expectedDates.getItem(i)));
}
~~~
## **Obtener Texto Amigable para el Usuario para una Recurrencia**
El texto amigable para una regla se puede obtener utilizando la propiedad FriendlyText como se muestra a continuación. La salida del código será: "Recurre cada mes el día 1 y el 1 desde el final de los días del mes para un máximo de 2 ocurrencias.". El siguiente fragmento de código muestra cómo obtener texto amigable para el usuario para una recurrencia.


~~~Java
RecurrenceRule rule = recurrencePattern.getRRules().add();
rule.setFrequency(Frequency.Monthly);
rule.setCount(2);
rule.getByMonthDay().add(1);
rule.getByMonthDay().add(-1);
System.out.println(rule.getFriendlyText());
~~~