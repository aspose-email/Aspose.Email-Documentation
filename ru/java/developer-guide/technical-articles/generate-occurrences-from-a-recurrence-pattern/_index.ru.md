---
title: "Генерация повторов на основе шаблона повторения"
url: /ru/java/generate-occurrences-from-a-recurrence-pattern/
weight: 180
type: docs
---


С помощью Aspose.Email можно создавать повторения, используя шаблон повторения. В этой статье объясняется, как и как [сгенерировать следующее событие](#calculate-the-next-occurrence-or-n-next-occurrences) and [получите удобные описания товаров](#get-user-friendly-text-for-a-recurrence). Случаи из шаблона повторения календаря MAPI можно генерировать с помощью Aspose.Email. В следующем фрагменте кода показано, как генерировать повторения на основе шаблонов повторения.


## **Вычислите следующее или n следующих вхождений**
Чтобы получить «следующее» вхождение, используйте метод generateOccurrences с параметром nNextOccurrences = 1. В следующем фрагменте кода показано, как создать 20 повторов, используя nNextOccurrences = 20. Вывод приведенного ниже кода выглядит следующим образом:

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
## **Получите удобный текст для повторения**
Удобный для пользователя текст правила можно получить с помощью свойства friendlyText, как показано ниже. Вывод кода будет выглядеть следующим образом: «Повторяйте каждый месяц 1-го и 1-го числа конца месяца, максимум 2 раза». В следующем фрагменте кода показано, как создать удобный для пользователя текст для повторения.


~~~Java
RecurrenceRule rule = recurrencePattern.getRRules().add();
rule.setFrequency(Frequency.Monthly);
rule.setCount(2);
rule.getByMonthDay().add(1);
rule.getByMonthDay().add(-1);
System.out.println(rule.getFriendlyText());
~~~