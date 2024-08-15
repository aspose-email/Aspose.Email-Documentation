---
title: "Generar ocurrencias a partir de un patrón de recurrencia"
url: /es/java/generate-occurrences-from-a-recurrence-pattern/
weight: 180
type: docs
---


Con Aspose.Email, es posible generar ocurrencias utilizando un patrón de recurrencia. Este artículo explica cómo, cómo [generar la próxima aparición](#calculate-the-next-occurrence-or-n-next-occurrences) and [obtener descripciones de artículos fáciles de usar](#get-user-friendly-text-for-a-recurrence). Las ocurrencias a partir de un patrón de periodicidad del calendario MAPI se pueden generar mediante Aspose.Email. El siguiente fragmento de código muestra cómo generar ocurrencias a partir de patrones de periodicidad.


## **Calcular la siguiente aparición o n siguientes apariciones**
Para obtener la «siguiente» aparición, utilice el método GenerateOccurrences con el parámetro nNextOccurrences = 1. En el siguiente fragmento de código, se muestra cómo generar 20 ocurrencias mediante nNextOccurrences = 20. El resultado del código siguiente es el siguiente:

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
## **Obtenga texto fácil de usar para una recurrencia**
El texto fácil de usar para una regla se puede obtener mediante la propiedad FriendlyText, como se muestra a continuación. El resultado del código será: «Se repite cada mes los días 1 y 1 a partir de los días finales del mes, hasta un máximo de 2 veces». En el siguiente fragmento de código, se muestra cómo obtener texto fácil de usar para una repetición.


~~~Java
RecurrenceRule rule = recurrencePattern.getRRules().add();
rule.setFrequency(Frequency.Monthly);
rule.setCount(2);
rule.getByMonthDay().add(1);
rule.getByMonthDay().add(-1);
System.out.println(rule.getFriendlyText());
~~~