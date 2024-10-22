---
title: "Trabalhando com Recorrências"
url: /pt/net/trabalhando-com-recorrencias/
weight: 140
type: docs
---

## **Trabalhando com Recorrências Diárias**

Aspose.Email suporta a criação de recorrências diárias usando MapiCalendarDailyRecurrencePattern. Três diferentes tipos de término de recorrência de calendário Mapi podem ser usados, incluindo EndAfterNOccurrences, EndAfterDate e NeverEnd. Esta seção demonstra a criação de diferentes padrões de recorrência diária.

### **Recorrências Diárias: Tipo de Recorrência EndAfterNOccurrence**

Neste tipo de recorrência, o número de recorrências deve ser definido junto com outras informações da seguinte forma:

1. Defina a data de início, fim e vencimento.
1. Crie um MapiTask.
1. Defina o estado da tarefa como NotAssigned.
1. Crie o objeto de recorrência diária definindo propriedades como PatternType, Period, WeekStartDay, EndType e OccurenceCount.
1. Defina a propriedade MapiTask.Recurrence para este objeto de recorrência diária.
1. Salve esta mensagem no disco.

O seguinte trecho de código mostra como criar uma tarefa com o tipo de término de recorrência como EndAfterNOccurrence.

{{< gist "aspose-email" "9e8fbeb51a8cbc4129dc71ca8cd55f0b" "Examples-CSharp-Outlook-EndAfterNoccurrences-EndAfterNoccurrences.cs" >}}

A função a seguir pode ser usada para calcular o número de eventos entre as duas datas:

{{< gist "aspose-email" "9e8fbeb51a8cbc4129dc71ca8cd55f0b" "Examples-CSharp-Outlook-GetOccurrenceCount-GetOccurrenceCount.cs" >}}

#### **Definindo o valor da contagem de Ocorrências**

O seguinte trecho de código mostra como definir o valor da contagem de ocorrências.

{{< gist "aspose-email" "9e8fbeb51a8cbc4129dc71ca8cd55f0b" "Examples-CSharp-Outlook-SetDailyOccurrenceCount-SetDailyOccurrenceCount.cs" >}}

### **Recorrências Diárias: Tipo de Recorrência EndAfterDate**

A opção "End By" na Tarefa Mapi é alcançada definindo a propriedade OccurrenceCount calculada pela função GetOccurrenceCount(). Esta função recebe a data de início, a data de fim e a string RRULE.

#### **Recorrências Diárias: Definindo o valor Every Day**

O seguinte trecho de código mostra como definir o valor do período para 1 e o valor do INTERVAL para 1 na string RRULE também.

{{< gist "aspose-email" "9e8fbeb51a8cbc4129dc71ca8cd55f0b" "Examples-CSharp-Outlook-SetRecurrenceEveryDay-SetRecurrenceEveryDay.cs" >}}

O valor Every Day pode ser definido como qualquer valor apropriado, conforme mostrado no exemplo a seguir:

{{< gist "aspose-email" "9e8fbeb51a8cbc4129dc71ca8cd55f0b" "Examples-CSharp-Outlook-DailyRecurrences-SetEveryDayValueInterval.cs" >}}

### **Recorrências Diárias: Tipo de Recorrência NeverEnd**

O tipo de término pode ser definido usando MapiCalendarRecurrenceEndType.NeverEnd. O período ou INTERVAL pode ser definido para o valor necessário, digamos 1 no exemplo a seguir.

{{< gist "aspose-email" "9e8fbeb51a8cbc4129dc71ca8cd55f0b" "Examples-CSharp-Outlook-SetDailyNeverEndRecurrence-SetDailyNeverEndRecurrence.cs" >}}

## **Trabalhando com Recorrências Semanais**

Aspose.Email fornece recursos ricos para a criação de recorrências semanais usando MapiCalendarWeeklyRecurrencePattern. Três diferentes tipos de término de recorrência de calendário Mapi podem ser usados, incluindo EndAfterNOccurrences, EndAfterDate e NeverEnd. Esta seção demonstra a criação de diferentes padrões de recorrência semanal.

### **Recorrências Semanais: Tipo de Recorrência EndAfterNOccurrences**

Neste tipo de recorrência, o número de recorrências deve ser definido junto com outras informações da seguinte forma:

1. Defina a data de início, fim e vencimento.
1. Crie um MapiTask.
1. Defina o estado da tarefa como NotAssigned.
1. Crie o objeto de recorrência semanal definindo propriedades como PatternType, Period, WeekStartDay, EndType e OccurenceCount.
1. Defina a propriedade MapiTask.Recurrence para este objeto de recorrência semanal.
1. Salve esta mensagem no disco.

O seguinte trecho de código mostra como criar uma tarefa com o tipo de término de recorrência como EndAfterNOccurrence.

{{< gist "aspose-email" "9e8fbeb51a8cbc4129dc71ca8cd55f0b" "Examples-CSharp-Outlook-WeeklyEndAfterNoccurrences-WeeklyEndAfterNoccurrences.cs" >}}

A função a seguir pode ser usada para calcular o número de eventos entre as duas datas:

{{< gist "aspose-email" "9e8fbeb51a8cbc4129dc71ca8cd55f0b" "Examples-CSharp-Outlook-WeeklyEndAfterNoccurrences-EventsBetweenTheTwoDates.cs" >}}

#### **Selecionando múltiplos dias na semana**

O seguinte trecho de código mostra como selecionar múltiplos dias na semana.

{{< gist "aspose-email" "9e8fbeb51a8cbc4129dc71ca8cd55f0b" "Examples-CSharp-Outlook-EndAfterNoccurrenceSelectMultipleDaysInweek-EndAfterNoccurrenceSelectMultipleDaysInweek.cs" >}}

#### **Selecionando múltiplos dias na semana e definindo intervalos**

O seguinte trecho de código mostra como selecionar múltiplos dias na semana e definir intervalos.

{{< gist "aspose-email" "9e8fbeb51a8cbc4129dc71ca8cd55f0b" "Examples-CSharp-Outlook-SetWeeklyRecurrenceMultipleDaysInWeekWithInterval-SetWeeklyRecurrenceMultipleDaysInWeekWithInterval.cs" >}}

### **Recorrências Semanais: Tipo de Recorrência EndAfterDate**

A opção "End By" na Tarefa Mapi é alcançada definindo a propriedade OccurrenceCount calculada pela função GetOccurrenceCount(). Esta função recebe a data de início, a data de fim e a string RRULE.

#### **Recorrências Semanais: Definindo o valor Every Day**

O seguinte trecho de código mostra como definir o valor do período para 1 e o valor do INTERVAL para 1 na string RRULE também.

{{< gist "aspose-email" "9e8fbeb51a8cbc4129dc71ca8cd55f0b" "Examples-CSharp-Outlook-SetWeeklyEndAfterDateRecurrence-SetWeeklyEndAfterDateEveryDayRecurrence.cs" >}}

O valor Every Day pode ser definido como qualquer valor apropriado e múltiplos dias podem ser selecionados, conforme mostrado no exemplo a seguir:

{{< gist "aspose-email" "9e8fbeb51a8cbc4129dc71ca8cd55f0b" "Examples-CSharp-Outlook-SetWeeklyEndAfterDateRecurrence-SetWeeklyEndAfterDateMultipleDaysRecurrence.cs" >}}

### **Recorrências Semanais: Tipo de Recorrência NeverEnd**

O tipo de término pode ser definido usando MapiCalendarRecurrenceEndType.NeverEnd. O período ou INTERVAL pode ser definido para o valor necessário, digamos 1 no exemplo a seguir.

{{< gist "aspose-email" "9e8fbeb51a8cbc4129dc71ca8cd55f0b" "Examples-CSharp-Outlook-SetWeeklyNeverEndRecurrence-SetWeeklyNeverEndRecurrence.cs" >}}

## **Trabalhando com Recorrências Mensais**

Aspose.Email suporta a criação de recorrências mensais usando MapiCalendarMonthlyRecurrencePattern. Três diferentes tipos de término de recorrência de calendário Mapi podem ser usados, incluindo EndAfterNOccurrences, EndAfterDate e NeverEnd. Esta seção demonstra a criação de diferentes padrões de recorrência mensal.

### **Recorrências Mensais: Tipo de Recorrência EndAfterNOccurrences**

Neste tipo de recorrência, o número de recorrências deve ser definido junto com outras informações da seguinte forma:

1. Defina a data de início, fim e vencimento.
1. Crie um MapiTask.
1. Defina o estado da tarefa como NotAssigned.
1. Crie o objeto de recorrência mensal definindo propriedades como PatternType, Period, WeekStartDay, EndType e OccurenceCount.
1. Defina a propriedade MapiTask.Recurrence para este objeto de recorrência mensal.
1. Salve esta mensagem no disco.

O seguinte trecho de código mostra como criar uma tarefa com o tipo de término de recorrência como EndAfterNOccurrence.

{{< gist "aspose-email" "9e8fbeb51a8cbc4129dc71ca8cd55f0b" "Examples-CSharp-Outlook-MonthlyEndAfterNoccurrences-MonthlyEndAfterNoccurrences.cs" >}}

A função a seguir pode ser usada para calcular o número de eventos entre as duas datas:

{{< gist "aspose-email" "9e8fbeb51a8cbc4129dc71ca8cd55f0b" "Examples-CSharp-Outlook-MonthlyEndAfterNoccurrences-EventsBetweenTheTwoDates.cs" >}}

#### **Definindo um número fixo de ocorrências**

O seguinte trecho de código mostra como definir um número fixo de ocorrências.

{{< gist "aspose-email" "9e8fbeb51a8cbc4129dc71ca8cd55f0b" "Examples-CSharp-Outlook-MonthlyEndAfterNoccurrences-SetFixNumberOfOccurrences.cs" >}}

### **Recorrências Mensais: Tipo de Recorrência EndAfterDate**

A opção "End By" na Tarefa Mapi é alcançada definindo a propriedade OccurrenceCount calculada pela função GetOccurrenceCount(). Esta função recebe a data de início, a data de fim e a string RRULE. O seguinte trecho de código mostra como criar uma recorrência no dia 15 de cada mês entre a data de início e a data de fim.

{{< gist "aspose-email" "9e8fbeb51a8cbc4129dc71ca8cd55f0b" "Examples-CSharp-Outlook-SetMonthlyEndAfterDateRecurrence-SetMonthlyEndAfterDateRecurrence.cs" >}}

### **Recorrências Mensais: Tipo de Recorrência NeverEnd**

O seguinte trecho de código mostra como definir o tipo de término usando MapiCalendarRecurrenceEndType.NeverEnd.

{{< gist "aspose-email" "9e8fbeb51a8cbc4129dc71ca8cd55f0b" "Examples-CSharp-Outlook-SetMonthlyNeverEndRecurrence-SetMonthlyNeverEndRecurrence.cs" >}}

## **Trabalhando com Recorrências Anuais**

Aspose.Email suporta a criação de recorrências anuais usando MapiCalendarMonthlyRecurrencePattern. Definindo a propriedade do período para 12, podemos alcançar o padrão de recorrência anual. Três diferentes tipos de término de recorrência de calendário Mapi podem ser usados, incluindo EndAfterNOccurrences, EndAfterDate e NeverEnd. Esta seção demonstra a criação de diferentes padrões de recorrência anual.

### **Recorrências Anuais: Tipo de Recorrência EndAfterNOccurrences**

Neste tipo de recorrência, o número de recorrências deve ser definido junto com outras informações da seguinte forma:

1. Defina a data de início, fim e vencimento.
1. Crie um MapiTask.
1. Defina o estado da tarefa como NotAssigned.
1. Crie o objeto de recorrência mensal definindo propriedades como PatternType, Period, WeekStartDay, EndType e OccurenceCount.
1. Defina a propriedade MapiTask.Recurrence para este objeto de recorrência mensal para alcançar a recorrência anual.
1. Salve esta mensagem no disco.

O seguinte trecho de código mostra como criar uma tarefa com o tipo de término de recorrência como EndAfterNOccurrence.

{{< gist "aspose-email" "9e8fbeb51a8cbc4129dc71ca8cd55f0b" "Examples-CSharp-Outlook-YearlyRecurrences-EndAfterNOccurrences.cs" >}}

### **Recorrências Anuais: Tipo de Recorrência EndAfterDate**

A opção "End By" na Tarefa Mapi é alcançada definindo a propriedade OccurrenceCount calculada pela função GetOccurrenceCount(). Esta função recebe a data de início, a data de fim e a string RRULE. O seguinte trecho de código mostra como criar uma recorrência no dia 15 de cada 7º mês entre a data de início e a data de fim.

{{< gist "aspose-email" "9e8fbeb51a8cbc4129dc71ca8cd55f0b" "Examples-CSharp-Outlook-YearlyEndAfterDate-YearlyEndAfterDate.cs" >}}

### **Recorrências Anuais: Tipo de Recorrência NeverEnd**

O seguinte trecho de código mostra como definir o tipo de término usando MapiCalendarRecurrenceEndType.NeverEnd.

{{< gist "aspose-email" "9e8fbeb51a8cbc4129dc71ca8cd55f0b" "Examples-CSharp-Outlook-SetYearlyNeverEndRecurrence-SetYearlyNeverEndRecurrence.cs" >}}

## **Gerar Recorrência a partir da Regra de Recorrência**

A API Aspose.Email fornece a capacidade de gerar um Padrão de Recorrência a partir da Regra de Recorrência (RRULE). Ela analisa as informações da RRULE de acordo com as especificações iCal RFC 5545 e gera o padrão de recorrência usando o método MapiCalendarRecurrencePatternFactory.FromString. O seguinte trecho de código mostra como gerar um padrão de recorrência a partir da regra de recorrência.

{{< gist "aspose-email" "9e8fbeb51a8cbc4129dc71ca8cd55f0b" "Examples-CSharp-Outlook-GenerateRecurrenceFromRecurrenceRule-GenerateRecurrenceFromRecurrenceRule.cs" >}}

## **Adicionar um Anexo a Eventos de Calendário Recorrentes**

A API Aspose.Email fornece a capacidade de adicionar anexos a eventos de calendário recorrentes.

{{< gist "aspose-email" "9e8fbeb51a8cbc4129dc71ca8cd55f0b" "Examples-CSharp-Outlook-AddAttachmentToMapiExceptionInfo-AddAttachmentToMapiExceptionInfo.cs" >}}