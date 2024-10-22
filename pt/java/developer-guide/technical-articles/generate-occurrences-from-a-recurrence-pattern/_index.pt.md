---
title: "Gerar Ocorrências a partir de um Padrão de Recorrência"
url: /pt/java/generate-occurrences-from-a-recurrence-pattern/
weight: 180
type: docs
---


Com Aspose.Email, é possível gerar ocorrências usando um padrão de recorrência. Este artigo explica como, como [gerar a próxima ocorrência](#calculate-the-next-occurrence-or-n-next-occurrences) e [obter descrições de itens amigáveis ao usuário](#get-user-friendly-text-for-a-recurrence). Ocorrências de um padrão de recorrência de calendário MAPI podem ser geradas usando Aspose.Email. O seguinte trecho de código mostra como gerar ocorrências a partir de padrões de recorrência.


## **Calcular a Próxima Ocorrência ou n Próximas Ocorrências**
Para obter a "próxima" ocorrência, use o método GenerateOccurrences com o parâmetro nNextOccurrences = 1. O seguinte trecho de código mostra como gerar 20 ocorrências usando nNextOccurrences = 20. A saída do código abaixo é a seguinte:

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
## **Obter Texto Amigável ao Usuário para uma Recorrência**
O texto amigável ao usuário para uma regra pode ser obtido usando a propriedade FriendlyText, como mostrado abaixo. A saída do código será: "Recorrer todo mês no 1º e 1º do(s) último(s) dia(s) do mês para um máximo de 2 ocorrências.". O seguinte trecho de código mostra como obter texto amigável ao usuário para uma recorrência.


~~~Java
RecurrenceRule rule = recurrencePattern.getRRules().add();
rule.setFrequency(Frequency.Monthly);
rule.setCount(2);
rule.getByMonthDay().add(1);
rule.getByMonthDay().add(-1);
System.out.println(rule.getFriendlyText());
~~~