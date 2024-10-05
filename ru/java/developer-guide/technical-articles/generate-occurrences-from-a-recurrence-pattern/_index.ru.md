---
title: "Генерация событий на основе шаблона повторения"
url: /ru/java/generate-occurrences-from-a-recurrence-pattern/
weight: 180
type: docs
---


С помощью Aspose.Email можно генерировать события, используя шаблон повторения. Эта статья объясняет, как это сделать, как [сгенерировать следующее событие](#calculate-the-next-occurrence-or-n-next-occurrences) и [получить удобоваримые описания элементов](#get-user-friendly-text-for-a-recurrence). События на основе шаблона повторения календаря MAPI могут быть сгенерированы с использованием Aspose.Email. Следующий фрагмент кода показывает, как генерировать события на основе шаблонов повторения.


## **Расчет следующего события или n следующих событий**
Чтобы получить "следующее" событие, используйте метод GenerateOccurrences с параметром nNextOccurrences = 1. Следующий фрагмент кода показывает, как сгенерировать 20 событий, используя nNextOccurrences = 20. Вывод кода ниже будет следующим:

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
## **Получение удобного текста для повторения**
Удобный текст для правила можно получить с помощью свойства FriendlyText, как показано ниже. Вывод кода будет: "Повторять каждый месяц 1-го и 1-го по последним дням месяца с максимальным количеством 2 событий.". Следующий фрагмент кода показывает, как получить удобный текст для повторения.


~~~Java
RecurrenceRule rule = recurrencePattern.getRRules().add();
rule.setFrequency(Frequency.Monthly);
rule.setCount(2);
rule.getByMonthDay().add(1);
rule.getByMonthDay().add(-1);
System.out.println(rule.getFriendlyText());
~~~