---
title: "Работа с рецидивами"
url: /ru/net/working-with-recurrences/
weight: 140
type: docs
---


## **Работа с ежедневными рецидивами**

Aspose.Email поддерживает создание ежедневных повторов с использованием MapicaLendarDailyRecurrencePattern. Можно использовать три разных типа окончания повторения в календаре Mapi, включая EndAfterNoCcurences, EndAfterDate и NeverEnd. В этом разделе показано создание различных моделей ежедневных повторов.

### **Ежедневные рецидивы: тип рецидива в конце дня**

В этом типе повторения количество рецидивов должно быть установлено вместе с другой информацией следующим образом:

1. Установите дату начала, окончания и срока.
1. Создайте задачу MapiTask.
1. Задайте для состояния задачи значение NotAssigned.
1. Создайте объект ежедневного повторения, задав такие свойства, как PatternType, Period, WeekStartDay, endType и OccucenceCount.
1. Присвойте этому объекту ежедневного повторения свойство MapitAsk.Recrecircent.
1. Сохраните это сообщение на диске.

В следующем фрагменте кода показано, как создать задачу с типом окончания повторения EndAfterNoccurrence.

{{< gist "aspose-email" "9e8fbeb51a8cbc4129dc71ca8cd55f0b" "Examples-CSharp-Outlook-EndAfterNoccurrences-EndAfterNoccurrences.cs" >}}

Для вычисления количества событий между двумя датами можно использовать следующую функцию:

{{< gist "aspose-email" "9e8fbeb51a8cbc4129dc71ca8cd55f0b" "Examples-CSharp-Outlook-GetOccurrenceCount-GetOccurrenceCount.cs" >}}

#### **Настройка значения количества появлений**

В следующем фрагменте кода показано, как установить значение количества вхождений.

{{< gist "aspose-email" "9e8fbeb51a8cbc4129dc71ca8cd55f0b" "Examples-CSharp-Outlook-SetDailyOccurrenceCount-SetDailyOccurrenceCount.cs" >}}

### **Ежедневные повторения: тип рецидива EndAfterDate**

Опция «End By» в задании Mapi достигается путем установки свойства OccurrenceCount, вычисляемого функцией getOccurrenceCount (). Эта функция принимает дату начала, дату окончания и строку RRULE.

#### **Ежедневные повторения: настройка значения «Каждый день»**

В следующем фрагменте кода также показано, как установить значение периода на 1 и значение INTERVAL на 1 в строке RRULE.

{{< gist "aspose-email" "9e8fbeb51a8cbc4129dc71ca8cd55f0b" "Examples-CSharp-Outlook-SetRecurrenceEveryDay-SetRecurrenceEveryDay.cs" >}}

Для значения «Каждый день» можно задать любое подходящее значение, как показано в следующем примере:

{{< gist "aspose-email" "9e8fbeb51a8cbc4129dc71ca8cd55f0b" "Examples-CSharp-Outlook-DailyRecurrences-SetEveryDayValueInterval.cs" >}}

### **Ежедневные рецидивы: тип повторения NeverEnd**

Тип конца можно задать с помощью команды MapicaLendarRecurrenceEndType.NeverEnd. В следующем примере для периода или ИНТЕРВАЛА можно задать требуемое значение, например, 1.

{{< gist "aspose-email" "9e8fbeb51a8cbc4129dc71ca8cd55f0b" "Examples-CSharp-Outlook-SetDailyNeverEndRecurrence-SetDailyNeverEndRecurrence.cs" >}}

## **Работа с еженедельными рецидивами**

Aspose.Email предоставляет широкие возможности для создания еженедельных повторов с использованием MapicaLendarWeeklyRecurrencePattern. Можно использовать три разных типа окончания повторов в календаре Mapi, включая EndAfterNoCcurrences, EndAfterDate и NeverEnd. В этом разделе показано создание различных моделей еженедельных повторов.

### **Еженедельные рецидивы: тип повторения событий в конце дня**

В этом типе повторения количество рецидивов должно быть установлено вместе с другой информацией следующим образом:

1. Установите дату начала, окончания и срока.
1. Создайте задачу MapiTask.
1. Задайте для состояния задачи значение NotAssigned.
1. Создайте объект еженедельного повторения, задав такие свойства, как PatternType, Period, WeekStartDay, endType и OccucenceCount.
1. Присвойте этому объекту еженедельного повторения свойство MapitAsk.Recrecircent.
1. Сохраните это сообщение на диске.

В следующем фрагменте кода показано, как создать задачу с повторяющимся типом окончания EndAfterNOccurrence.

{{< gist "aspose-email" "9e8fbeb51a8cbc4129dc71ca8cd55f0b" "Examples-CSharp-Outlook-WeeklyEndAfterNoccurrences-WeeklyEndAfterNoccurrences.cs" >}}

Для вычисления количества событий между двумя датами можно использовать следующую функцию:

{{< gist "aspose-email" "9e8fbeb51a8cbc4129dc71ca8cd55f0b" "Examples-CSharp-Outlook-WeeklyEndAfterNoccurrences-EventsBetweenTheTwoDates.cs" >}}

#### **Выбор нескольких дней в неделю**

В следующем фрагменте кода показано, как выбрать несколько дней в неделю.

{{< gist "aspose-email" "9e8fbeb51a8cbc4129dc71ca8cd55f0b" "Examples-CSharp-Outlook-EndAfterNoccurrenceSelectMultipleDaysInweek-EndAfterNoccurrenceSelectMultipleDaysInweek.cs" >}}

#### **Выбор нескольких дней в неделю и настройка интервалов**

В следующем фрагменте кода показано, как выбрать несколько дней в неделю и установить интервалы.

{{< gist "aspose-email" "9e8fbeb51a8cbc4129dc71ca8cd55f0b" "Examples-CSharp-Outlook-SetWeeklyRecurrenceMultipleDaysInWeekWithInterval-SetWeeklyRecurrenceMultipleDaysInWeekWithInterval.cs" >}}

### **Еженедельные повторения: тип повторения EndAfterDate**

Опция «End By» в задании Mapi достигается путем установки свойства OccurrenceCount, вычисляемого функцией getOccurrenceCount (). Эта функция принимает дату начала, дату окончания и строку RRULE.

#### **Еженедельные повторения: установка значения «Каждый день»**

В следующем фрагменте кода также показано, как установить значение периода на 1 и значение INTERVAL на 1 в строке RRULE.

{{< gist "aspose-email" "9e8fbeb51a8cbc4129dc71ca8cd55f0b" "Examples-CSharp-Outlook-SetWeeklyEndAfterDateRecurrence-SetWeeklyEndAfterDateEveryDayRecurrence.cs" >}}

Для значения «Каждый день» можно задать любое подходящее значение и выбрать несколько дней, как показано в следующем примере:

{{< gist "aspose-email" "9e8fbeb51a8cbc4129dc71ca8cd55f0b" "Examples-CSharp-Outlook-SetWeeklyEndAfterDateRecurrence-SetWeeklyEndAfterDateMultipleDaysRecurrence.cs" >}}

### **Еженедельные рецидивы: тип повторения NeverEnd**

Тип конца можно задать с помощью команды MapicaLendarRecurrenceEndType.NeverEnd. В следующем примере для периода или ИНТЕРВАЛА можно задать требуемое значение, например, 1.

{{< gist "aspose-email" "9e8fbeb51a8cbc4129dc71ca8cd55f0b" "Examples-CSharp-Outlook-SetWeeklyNeverEndRecurrence-SetWeeklyNeverEndRecurrence.cs" >}}

## **Работа с ежемесячными рецидивами**

Aspose.Email поддерживает создание ежемесячных рецидивов с использованием шаблона MapicaLendarMonthlyRecurrencePattern. Можно использовать три разных типа окончания повторения в календаре Mapi, включая EndAfterNoCcurences, EndAfterDate и NeverEnd. В этом разделе показано создание различных моделей ежемесячных повторов.

### **Ежемесячные рецидивы: тип повторения событий в конце дня**

В этом типе повторения количество рецидивов должно быть установлено вместе с другой информацией следующим образом:

1. Установите дату начала, окончания и срока.
1. Создайте задачу MapiTask.
1. Задайте для состояния задачи значение NotAssigned.
1. Создайте объект ежемесячного повторения, задав такие свойства, как PatternType, Period, WeekStartDay, endType и OccucenceCount.
1. Присвойте этому объекту ежемесячного повторения свойство MapitAsk.Recrecircent.
1. Сохраните это сообщение на диске.

В следующем фрагменте кода показано, как создать задачу с повторяющимся типом окончания EndAfterNOccurrence.

{{< gist "aspose-email" "9e8fbeb51a8cbc4129dc71ca8cd55f0b" "Examples-CSharp-Outlook-MonthlyEndAfterNoccurrences-MonthlyEndAfterNoccurrences.cs" >}}

Для вычисления количества событий между двумя датами можно использовать следующую функцию:

{{< gist "aspose-email" "9e8fbeb51a8cbc4129dc71ca8cd55f0b" "Examples-CSharp-Outlook-MonthlyEndAfterNoccurrences-EventsBetweenTheTwoDates.cs" >}}

#### **Задайте количество исправлений**

В следующем фрагменте кода показано, как установить исправление количества вхождений.

{{< gist "aspose-email" "9e8fbeb51a8cbc4129dc71ca8cd55f0b" "Examples-CSharp-Outlook-MonthlyEndAfterNoccurrences-SetFixNumberOfOccurrences.cs" >}}

### **Ежемесячные рецидивы: тип повторения EndAfterDate**

Опция «End By» в задании Mapi достигается путем установки свойства OccurrenceCount, вычисляемого функцией getOccurrenceCount (). Эта функция принимает дату начала, дату окончания и строку RRULE. В следующем фрагменте кода показано, как создать повтор 15 числа каждого месяца между датой начала и концом.

{{< gist "aspose-email" "9e8fbeb51a8cbc4129dc71ca8cd55f0b" "Examples-CSharp-Outlook-SetMonthlyEndAfterDateRecurrence-SetMonthlyEndAfterDateRecurrence.cs" >}}

### **Ежемесячные рецидивы: тип повторения NeverEnd**

В следующем фрагменте кода показано, как задать конечный тип с помощью MapicaLendarRecurrenceEndType.Neverend.

{{< gist "aspose-email" "9e8fbeb51a8cbc4129dc71ca8cd55f0b" "Examples-CSharp-Outlook-SetMonthlyNeverEndRecurrence-SetMonthlyNeverEndRecurrence.cs" >}}

## **Работа с годовыми рецидивами**

Aspose.Email поддерживает создание ежегодных рецидивов с использованием шаблона MapicaLendarMonthlyRecurrencePattern. Установив для свойства периода значение 12, мы можем добиться ежегодной повторяемости. Можно использовать три разных типа окончания повторения в календаре Mapi, включая endAfterNoCcurrences, endAfterDate и NeverEnd. В этом разделе показано создание различных ежегодных закономерностей повторения.

### **Годовые рецидивы: тип повторения событий в конце дня**

В этом типе повторения количество рецидивов должно быть установлено вместе с другой информацией следующим образом:

1. Установите дату начала, окончания и срока.
1. Создайте задачу MapiTask.
1. Задайте для состояния задачи значение NotAssigned.
1. Создайте объект ежемесячного повторения, задав такие свойства, как PatternType, Period, WeekStartDay, endType и OccucenceCount.
1. Для достижения ежегодного повторения задайте свойству MapitAsk.Recrecurration этот объект ежемесячного повторения.
1. Сохраните это сообщение на диске.

В следующем фрагменте кода показано, как создать задачу с повторяющимся типом окончания EndAfterNOccurrence.

{{< gist "aspose-email" "9e8fbeb51a8cbc4129dc71ca8cd55f0b" "Examples-CSharp-Outlook-YearlyRecurrences-EndAfterNOccurrences.cs" >}}

### **Годовые рецидивы: тип повторения EndAfterDate**

Опция «End By» в задании Mapi достигается путем установки свойства OccurrenceCount, вычисляемого функцией getOccurrenceCount (). Эта функция принимает дату начала, дату окончания и строку RRULE. В следующем фрагменте кода показано, как создать повтор 15 числа каждого 7-го месяца между датой начала и концом.

{{< gist "aspose-email" "9e8fbeb51a8cbc4129dc71ca8cd55f0b" "Examples-CSharp-Outlook-YearlyEndAfterDate-YearlyEndAfterDate.cs" >}}

### **Годовые рецидивы: тип бесконечного повторения**

В следующем фрагменте кода показано, как задать конечный тип с помощью MapicaLendarRecurrenceEndType.Neverend.

{{< gist "aspose-email" "9e8fbeb51a8cbc4129dc71ca8cd55f0b" "Examples-CSharp-Outlook-SetYearlyNeverEndRecurrence-SetYearlyNeverEndRecurrence.cs" >}}

## **Создать повторение на основе правила повторения**

Aspose.Email API предоставляет возможность генерировать шаблон повторения на основе правила повторения (RRULE). Он анализирует информацию из RRULE в соответствии со спецификациями RFC 5545 iCal и генерирует шаблон повторения с помощью метода MapicaLendarRecurrencePatternFactory.fromString. В следующем фрагменте кода показано, как создать шаблон повторения на основе правила повторения.

{{< gist "aspose-email" "9e8fbeb51a8cbc4129dc71ca8cd55f0b" "Examples-CSharp-Outlook-GenerateRecurrenceFromRecurrenceRule-GenerateRecurrenceFromRecurrenceRule.cs" >}}

## **Добавить вложение к повторяющимся событиям календаря**

Aspose.Email API предоставляет возможность добавлять вложения к повторяющимся событиям календаря.

{{< gist "aspose-email" "9e8fbeb51a8cbc4129dc71ca8cd55f0b" "Examples-CSharp-Outlook-AddAttachmentToMapiExceptionInfo-AddAttachmentToMapiExceptionInfo.cs" >}}
