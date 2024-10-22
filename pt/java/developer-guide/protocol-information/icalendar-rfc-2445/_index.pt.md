---
title: "iCalendar RFC 2445"
url: /pt/java/icalendar-rfc-2445/
weight: 30
type: docs
---


{{% alert color="primary" %}} 

O iCalendar RFC 2445 descreve um conjunto de elementos de agendamento e calendário interoperáveis que permitem que aplicativos de agendamento em grupo, gerenciamento de informações pessoais e calendários troquem informações em um formato comum.

Aspose.Email implementa os elementos relacionados ao agendamento do RFC, uma vez que estes têm ampla aplicação. Versões futuras podem implementar outros elementos do RFC 2445, dependendo da demanda.

Este artigo descreve os elementos do RFC que se relacionam com Aspose.Email. Recomendamos que você consulte o padrão iCalendar <http://www.faqs.org/rfcs/rfc2445.html> para uma visão completa. 

{{% /alert %}} 
## **Padrões de Recorrência no Mundo Real**
Um padrão de recorrência descreve as regras de quando o evento ocorre. Um mecanismo de padrão de recorrência, como o Aspose iCalendar, é necessário para calcular as datas e horários das ocorrências para um dado padrão de recorrência.
Encontramos horários ou padrões de recorrência em muitas situações, por exemplo:

- Dez reuniões de equipe, toda segunda-feira às 10h.
- Processar pagamento de salário no último dia útil de cada mês.
- Verificar a temperatura do paciente todos os dias durante duas semanas.
- Ir à academia na segunda, quarta e sexta-feira.
- Executar backup a cada 4 horas em dias úteis.
- Gerar relatório de vendas em …
- Atualizar estatísticas do site a cada …

Quase qualquer evento que ocorra periodicamente pode ser representado como um padrão de recorrência. Por exemplo, o seguinte código retornará um array contendo dez ocorrências do exemplo anterior da reunião de equipe:

~~~java
CalendarRecurrence recurrencePattern = new CalendarRecurrence("DTSTART:20040301T100000\nRRULE:FREQ=WEEKLY;COUNT=10;BYDAY=MO");
DateCollection expectedDates = recurrencePattern.generateOccurrences();
System.out.println("expectedDates.Count = " + expectedDates.size());
for (int i = 0; i < expectedDates.size(); i++) {
    System.out.println("DateTime = " + sdf.format(expectedDates.getItem(i)));
}
~~~

{{% alert color="primary" %}} 

Os padrões de recorrência podem se tornar bastante complexos e requerem um mecanismo de padrão de recorrência confiável para analisar e validar a entrada e gerar ocorrências corretamente. 

{{% /alert %}}