---
title: "Introduzindo Padrões de Recorrência"
url: /pt/net/introducing-recurrence-patterns/
weight: 60
type: docs
---


Você pode pensar em um *padrão de recorrência* como uma forma de descrever um cronograma particular. Ele contém informações suficientes para construir uma lista de ocorrências (datas e horários) de acordo com um cronograma dado. Um padrão de recorrência pode conter regras de recorrência que descrevem ciclos que se combinam para formar o padrão geral. Em geral, quanto mais complexo for um padrão de recorrência, mais regras de recorrência ele conterá. Padrões de recorrência podem incluir *exceções* (não devem ser confundidas com exceções que representam erros que ocorrem durante a execução do aplicativo). As exceções adicionam ou removem datas de ocorrência do padrão original. As exceções podem ser especificadas como ocorrências explícitas ou como um padrão em si. Exemplos de padrões de recorrência com exceções:

- Toda 2ª sexta-feira, exceto de junho a agosto.
- O 1º de cada mês, exceto em janeiro, quando deve ser no 2º.

Padrões de recorrência são geralmente periódicos, mas não precisam ser. Um padrão de recorrência pode ser descrito completamente apenas como um conjunto de datas e horários de ocorrência predefinidos. A RFC do iCalendar define *componentes*, como VEVENT ou VTODO que representam eventos ou tarefas. Os componentes podem ter propriedades como data/hora de início, descrição, localização, participantes e recorrência. Um padrão de recorrência, portanto, normalmente existe como uma propriedade de uma tarefa ou evento recorrente. As propriedades do padrão de recorrência definidas pelo iCalendar são:

- DTSTART - a data e hora de início do padrão (também representa a primeira ocorrência se não excluída explicitamente).
- RRULE - especifica uma regra de repetição para um conjunto de recorrência.
- RDATE - define uma lista de datas e horários a serem incluídos em um conjunto de recorrência.
- EXRULE - especifica uma regra de repetição para exceções de um conjunto de recorrência.
- EXDATE - define uma lista de datas e horários de exceções de um conjunto de recorrência.

Apenas o DTSTART é obrigatório e deve haver apenas um DTSTART. Todas as outras propriedades são opcionais e podem ser especificadas mais de uma vez. Aspose.iCalendar aceita uma string no formato iCalendar e lê o padrão de recorrência em um [RecurrencePattern](https://apireference.aspose.com/email/net/aspose.email.calendar.recurrences/recurrencepattern) objeto. A string pode ser uma descrição completa de um componente iCalendar (por exemplo, um VEVENT completo) ou pode ser apenas um fragmento que contém apenas o padrão de recorrência. Uma vez que o padrão de recorrência é carregado em um objeto RecurrencePattern, você pode:

- Examinar e modificar o padrão programaticamente por meio de métodos e propriedades fornecidos pela Aspose.iCalendar
- Gerar datas/horários de ocorrência em um intervalo de datas especificado.
- Salvar o padrão no formato iCalendar.

O seguinte trecho de código mostra que a parte RRULE contém a regra de recorrência.

{{< gist "aspose-email" "9e8fbeb51a8cbc4129dc71ca8cd55f0b" "Examples-CSharp-RecurrencePattern-RecurrencePattern.cs" >}}

Veja os [padrões de recorrência de amostra](#sample-patterns) para ilustrações sobre como criar padrões de recorrência.
## **Sobre o Modelo de Objeto Aspose.iCalendar**
O namespace Aspose.iCalendar contém todas as classes fornecidas pelo componente Aspose.iCalendar. RecurrencePattern e RecurrenceRule são as classes centrais do Aspose.iCalendar e fornecem implementações concretas dos elementos correspondentes da RFC 2445.

A classe RecurrencePattern representa todo o padrão de recorrência. Você pode criar um novo padrão de recorrência do zero usando o construtor padrão ou carregar um padrão existente no formato iCalendar usando o método estático FromiCalendar. A classe RecurrenceRule representa a parte RRULE ou EXRULE de um padrão de recorrência. RecurrenceRule expõe uma série de propriedades que se mapeiam diretamente para seus correspondentes no padrão iCalendar. Por exemplo, ByMonth se mapeia para BYMONTH no iCalendar e assim por diante. Ao examinar ou definir valores das propriedades da RecurrenceRule, você pode analisar ou modificar uma regra de recorrência. Para mais informações e exemplos de código, consulte RecurrencePattern e RecurrenceRule na Referência da API.
## **Padrões de Amostra**
Esta seção inclui os seguintes tópicos:

- O Último Dia do Mês.
- O Último Dia Útil de Cada Mês.
- A Última Segunda-feira do Ano.
- A Sexta-feira da Primeira Semana ISO 8601 do Ano.
- A Primeira Sexta-feira do Ano.
### **O Último Dia do Mês**
Este [padrão de recorrência](/email/net/introducing-recurrence-patterns/) especifica o último dia do mês, todo mês.

RRULE:FREQ=MONTHLY;BYMONTHDAY=-1

Da mesma forma, se você quiser uma ocorrência em um dia antes do último dia do mês, use BYMONTHDAY=-2. Se você especificar BYMONTHDAY=31 então, de acordo com o padrão iCalendar, não haverá ocorrência gerada nos meses que tiverem menos de 31 dias.
### **O Último Dia Útil de Cada Mês**
Este [padrão de recorrência](/email/net/introducing-recurrence-patterns/) especifica o último dia útil do mês, todo mês. Os dias úteis são definidos como os dias em que você trabalha. Na Europa, por exemplo, os dias úteis normalmente vão de segunda a sexta.

RRULE:FREQ=MONTHLY;BYDAY=MO,TU,WE,TH,FR;BYSETPOS=-1

A regra acima especifica todos os dias úteis de um mês e seleciona o último deles. O resultado líquido é um último dia útil em um mês.
### **A Última Segunda-feira do Ano**
Este [padrão de recorrência](/email/net/introducing-recurrence-patterns/) especifica um evento que ocorre na última segunda-feira do ano.

RRULE:FREQ=YEARLY;BYDAY=-1MO
### **Sexta-feira da Primeira Semana ISO 8601 do Ano**
Este [padrão de recorrência](/email/net/introducing-recurrence-patterns/) especifica a sexta-feira da primeira semana do ano. Na especificação ISO 8601, a primeira semana do ano é a primeira semana do ano que tem pelo menos quatro dias. Quando um ano começa em um sábado, por exemplo, a semana 1 é a semana imediatamente seguinte, começando na segunda-feira, 3 de janeiro.

FREQ=YEARLY;BYWEEKNO=1;BYDAY=FR
### **Primeira Sexta-feira do Ano**
Este [padrão de recorrência](/email/net/introducing-recurrence-patterns/) especifica um evento que ocorre na 1ª sexta-feira do ano.

FREQ=YEARLY;BYDAY=1FR

Em 1999, por exemplo, a 1ª sexta-feira do ano é 1999/01/01, enquanto a sexta-feira da 1ª semana ISO 8601 é 1999/01/08.