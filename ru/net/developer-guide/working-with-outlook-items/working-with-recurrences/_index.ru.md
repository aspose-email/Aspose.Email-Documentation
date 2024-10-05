---
title: "Работа с Повторами"
url: /ru/net/working-with-recurrences/
weight: 140
type: docs
---


## **Работа с Ежедневными Повторами**

Aspose.Email поддерживает создание ежедневных повторов с использованием MapiCalendarDailyRecurrencePattern. Можно использовать три разных типа окончания повторов календаря Mapi, включая EndAfterNOccurrences, EndAfterDate и NeverEnd. Этот раздел демонстрирует создание различных типов ежедневного повтора.

### **Ежедневные Повторы: Тип Повтора EndAfterNOccurrence**

В этом типе повтора количество повторов устанавливается вместе с другой информацией следующим образом:

1. Установите дату начала, окончания и выполнения.
1. Создайте MapiTask.
1. Установите состояние задачи на NotAssigned.
1. Создайте объект ежедневного повтора, задав такие свойства, как PatternType, Period, WeekStartDay, EndType и OccurenceCount.
1. Установите свойство MapiTask.Recurrence на этот объект ежедневного повтора.
1. Сохраните это сообщение на диске.

Следующий фрагмент кода показывает, как создать задачу с типом окончания повтора EndAfterNOccurrence.

{{< gist "aspose-email" "9e8fbeb51a8cbc4129dc71ca8cd55f0b" "Examples-CSharp-Outlook-EndAfterNoccurrences-EndAfterNoccurrences.cs" >}}

Следующая функция может быть использована для вычисления количества событий между двумя датами:

{{< gist "aspose-email" "9e8fbeb51a8cbc4129dc71ca8cd55f0b" "Examples-CSharp-Outlook-GetOccurrenceCount-GetOccurrenceCount.cs" >}}

#### **Установка значения количества повторов**

Следующий фрагмент кода показывает, как установить значение количества повторов.

{{< gist "aspose-email" "9e8fbeb51a8cbc4129dc71ca8cd55f0b" "Examples-CSharp-Outlook-SetDailyOccurrenceCount-SetDailyOccurrenceCount.cs" >}}

### **Ежедневные Повторы: Тип Повтора EndAfterDate**

Опция "End By" в Mapi Task достигается путем установки свойства OccurrenceCount, рассчитанного с помощью функции GetOccurrenceCount(). Эта функция принимает дату начала, дату окончания и строку RRULE.

#### **Ежедневные Повторы: Установка значения Каждый День**

Следующий фрагмент кода показывает, как установить значение периода на 1 и значение INTERVAL на 1 в строке RRULE.

{{< gist "aspose-email" "9e8fbeb51a8cbc4129dc71ca8cd55f0b" "Examples-CSharp-Outlook-SetRecurrenceEveryDay-SetRecurrenceEveryDay.cs" >}}

Значение Каждый День можно установить на любое подходящее значение, как показано в следующем примере:

{{< gist "aspose-email" "9e8fbeb51a8cbc4129dc71ca8cd55f0b" "Examples-CSharp-Outlook-DailyRecurrences-SetEveryDayValueInterval.cs" >}}

### **Ежедневные Повторы: Тип Повтора NeverEnd**

Тип окончания можно установить, используя MapiCalendarRecurrenceEndType.NeverEnd. Период или INTERVAL можно установить на требуемое значение, скажем 1, в следующем примере.

{{< gist "aspose-email" "9e8fbeb51a8cbc4129dc71ca8cd55f0b" "Examples-CSharp-Outlook-SetDailyNeverEndRecurrence-SetDailyNeverEndRecurrence.cs" >}}

## **Работа с Еженедельными Повторами**

Aspose.Email предоставляет богатые возможности для создания еженедельных повторов с использованием MapiCalendarWeeklyRecurrencePattern. Можно использовать три разных типа окончания повторов календаря Mapi, включая EndAfterNOccurrences, EndAfterDate и NeverEnd. Этот раздел демонстрирует создание различных типов еженедельного повтора.

### **Еженедельные Повторы: Тип Повтора EndAfterNOccurrences**

В этом типе повтора количество повторов устанавливается вместе с другой информацией следующим образом:

1. Установите дату начала, окончания и выполнения.
1. Создайте MapiTask.
1. Установите состояние задачи на NotAssigned.
1. Создайте объект еженедельного повтора, задав такие свойства, как PatternType, Period, WeekStartDay, EndType и OccurenceCount.
1. Установите свойство MapiTask.Recurrence на этот объект еженедельного повтора.
1. Сохраните это сообщение на диске.

Следующий фрагмент кода показывает, как создать задачу с типом окончания повтора EndAfterNOccurrence.

{{< gist "aspose-email" "9e8fbeb51a8cbc4129dc71ca8cd55f0b" "Examples-CSharp-Outlook-WeeklyEndAfterNoccurrences-WeeklyEndAfterNoccurrences.cs" >}}

Следующая функция может быть использована для вычисления количества событий между двумя датами:

{{< gist "aspose-email" "9e8fbeb51a8cbc4129dc71ca8cd55f0b" "Examples-CSharp-Outlook-WeeklyEndAfterNoccurrences-EventsBetweenTheTwoDates.cs" >}}

#### **Выбор нескольких дней в неделю**

Следующий фрагмент кода показывает, как выбрать несколько дней в неделю.

{{< gist "aspose-email" "9e8fbeb51a8cbc4129dc71ca8cd55f0b" "Examples-CSharp-Outlook-EndAfterNoccurrenceSelectMultipleDaysInweek-EndAfterNoccurrenceSelectMultipleDaysInweek.cs" >}}

#### **Выбор нескольких дней в неделю и установка интервалов**

Следующий фрагмент кода показывает, как выбрать несколько дней в неделю и установить интервалы.

{{< gist "aspose-email" "9e8fbeb51a8cbc4129dc71ca8cd55f0b" "Examples-CSharp-Outlook-SetWeeklyRecurrenceMultipleDaysInWeekWithInterval-SetWeeklyRecurrenceMultipleDaysInWeekWithInterval.cs" >}}

### **Еженедельные Повторы: Тип Повтора EndAfterDate**

Опция "End By" в Mapi Task достигается путем установки свойства OccurrenceCount, рассчитанного с помощью функции GetOccurrenceCount(). Эта функция принимает дату начала, дату окончания и строку RRULE.

#### **Еженедельные Повторы: Установка значения Каждый День**

Следующий фрагмент кода показывает, как установить значение периода на 1 и значение INTERVAL на 1 в строке RRULE.

{{< gist "aspose-email" "9e8fbeb51a8cbc4129dc71ca8cd55f0b" "Examples-CSharp-Outlook-SetWeeklyEndAfterDateRecurrence-SetWeeklyEndAfterDateEveryDayRecurrence.cs" >}}

Значение Каждый День можно установить на любое подходящее значение, и можно выбрать несколько дней, как показано в следующем примере:

{{< gist "aspose-email" "9e8fbeb51a8cbc4129dc71ca8cd55f0b" "Examples-CSharp-Outlook-SetWeeklyEndAfterDateRecurrence-SetWeeklyEndAfterDateMultipleDaysRecurrence.cs" >}}

### **Еженедельные Повторы: Тип Повтора NeverEnd**

Тип окончания можно установить, используя MapiCalendarRecurrenceEndType.NeverEnd. Период или INTERVAL можно установить на требуемое значение, скажем 1, в следующем примере.

{{< gist "aspose-email" "9e8fbeb51a8cbc4129dc71ca8cd55f0b" "Examples-CSharp-Outlook-SetWeeklyNeverEndRecurrence-SetWeeklyNeverEndRecurrence.cs" >}}

## **Работа с Ежемесячными Повторами**

Aspose.Email поддерживает создание ежемесячных повторов с использованием MapiCalendarMonthlyRecurrencePattern. Можно использовать три разных типа окончания повторов календаря Mapi, включая EndAfterNOccurrences, EndAfterDate и NeverEnd. Этот раздел демонстрирует создание различных типов ежемесячного повтора.

### **Ежемесячные Повторы: Тип Повтора EndAfterNOccurrences**

В этом типе повтора количество повторов устанавливается вместе с другой информацией следующим образом:

1. Установите дату начала, окончания и выполнения.
1. Создайте MapiTask.
1. Установите состояние задачи на NotAssigned.
1. Создайте объект ежемесячного повтора, задав такие свойства, как PatternType, Period, WeekStartDay, EndType и OccurenceCount.
1. Установите свойство MapiTask.Recurrence на этот объект ежемесячного повтора.
1. Сохраните это сообщение на диске.

Следующий фрагмент кода показывает, как создать задачу с типом окончания повтора EndAfterNOccurrence.

{{< gist "aspose-email" "9e8fbeb51a8cbc4129dc71ca8cd55f0b" "Examples-CSharp-Outlook-MonthlyEndAfterNoccurrences-MonthlyEndAfterNoccurrences.cs" >}}

Следующая функция может быть использована для вычисления количества событий между двумя датами:

{{< gist "aspose-email" "9e8fbeb51a8cbc4129dc71ca8cd55f0b" "Examples-CSharp-Outlook-MonthlyEndAfterNoccurrences-EventsBetweenTheTwoDates.cs" >}}

#### **Установка фиксированного количества повторений**

Следующий фрагмент кода показывает, как установить фиксированное количество повторений.

{{< gist "aspose-email" "9e8fbeb51a8cbc4129dc71ca8cd55f0b" "Examples-CSharp-Outlook-MonthlyEndAfterNoccurrences-SetFixNumberOfOccurrences.cs" >}}

### **Ежемесячные Повторы: Тип Повтора EndAfterDate**

Опция "End By" в Mapi Task достигается путем установки свойства OccurrenceCount, рассчитанного с помощью функции GetOccurrenceCount(). Эта функция принимает дату начала, дату окончания и строку RRULE. Следующий фрагмент кода показывает, как создать повтор 15-го числа каждого месяца между начальной и конечной датами.

{{< gist "aspose-email" "9e8fbeb51a8cbc4129dc71ca8cd55f0b" "Examples-CSharp-Outlook-SetMonthlyEndAfterDateRecurrence-SetMonthlyEndAfterDateRecurrence.cs" >}}

### **Ежемесячные Повторы: Тип Повтора NeverEnd**

Следующий фрагмент кода показывает, как установить тип окончания, используя MapiCalendarRecurrenceEndType.NeverEnd.

{{< gist "aspose-email" "9e8fbeb51a8cbc4129dc71ca8cd55f0b" "Examples-CSharp-Outlook-SetMonthlyNeverEndRecurrence-SetMonthlyNeverEndRecurrence.cs" >}}

## **Работа с Ежегодными Повторами**

Aspose.Email поддерживает создание ежегодных повторов с использованием MapiCalendarMonthlyRecurrencePattern. Установив свойство периода на 12, мы можем достичь шаблона ежегодного повтора. Можно использовать три разных типа окончания повторов календаря Mapi, включая EndAfterNOccurrences, EndAfterDate и NeverEnd. Этот раздел демонстрирует создание различных типов ежегодного повтора.

### **Ежегодные Повторы: Тип Повтора EndAfterNOccurrences**

В этом типе повтора количество повторов устанавливается вместе с другой информацией следующим образом:

1. Установите дату начала, окончания и выполнения.
1. Создайте MapiTask.
1. Установите состояние задачи на NotAssigned.
1. Создайте объект ежемесячного повтора, задав такие свойства, как PatternType, Period, WeekStartDay, EndType и OccurenceCount.
1. Установите свойство MapiTask.Recurrence на этот объект ежемесячного повтора для достижения ежегодного повтора.
1. Сохраните это сообщение на диске.

Следующий фрагмент кода показывает, как создать задачу с типом окончания повтора EndAfterNOccurrence.

{{< gist "aspose-email" "9e8fbeb51a8cbc4129dc71ca8cd55f0b" "Examples-CSharp-Outlook-YearlyRecurrences-EndAfterNOccurrences.cs" >}}

### **Ежегодные Повторы: Тип Повтора EndAfterDate**

Опция "End By" в Mapi Task достигается путем установки свойства OccurrenceCount, рассчитанного с помощью функции GetOccurrenceCount(). Эта функция принимает дату начала, дату окончания и строку RRULE. Следующий фрагмент кода показывает, как создать повтор 15-го числа каждого 7-го месяца между начальной и конечной датами.

{{< gist "aspose-email" "9e8fbeb51a8cbc4129dc71ca8cd55f0b" "Examples-CSharp-Outlook-YearlyEndAfterDate-YearlyEndAfterDate.cs" >}}

### **Ежегодные Повторы: Тип Повтора NeverEnd**

Следующий фрагмент кода показывает, как установить тип окончания, используя MapiCalendarRecurrenceEndType.NeverEnd.

{{< gist "aspose-email" "9e8fbeb51a8cbc4129dc71ca8cd55f0b" "Examples-CSharp-Outlook-SetYearlyNeverEndRecurrence-SetYearlyNeverEndRecurrence.cs" >}}

## **Генерация Повтора из Правила Повтора**

API Aspose.Email предоставляет возможность генерировать Шаблон Повтора из Правила Повтора (RRULE). Он анализирует информацию из RRULE в соответствии со спецификациями iCal RFC 5545 и генерирует шаблон повтора с использованием метода MapiCalendarRecurrencePatternFactory.FromString. Следующий фрагмент кода показывает, как сгенерировать шаблон повтора из правила повтора.

{{< gist "aspose-email" "9e8fbeb51a8cbc4129dc71ca8cd55f0b" "Examples-CSharp-Outlook-GenerateRecurrenceFromRecurrenceRule-GenerateRecurrenceFromRecurrenceRule.cs" >}}

## **Добавление Вложений к Повторяющимся Календарным Событиям**

API Aspose.Email предоставляет возможность добавлять вложения к повторяющимся календарным событиям.

{{< gist "aspose-email" "9e8fbeb51a8cbc4129dc71ca8cd55f0b" "Examples-CSharp-Outlook-AddAttachmentToMapiExceptionInfo-AddAttachmentToMapiExceptionInfo.cs" >}}