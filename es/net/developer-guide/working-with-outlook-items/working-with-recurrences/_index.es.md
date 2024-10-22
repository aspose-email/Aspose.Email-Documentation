---
title: "Trabajando con Recurrencias"
url: /es/net/trabajando-con-recurrencias/
weight: 140
type: docs
---


## **Trabajando con Recurrencias Diarias**

Aspose.Email soporta la creación de recurrencias diarias utilizando MapiCalendarDailyRecurrencePattern. Se pueden usar tres tipos diferentes de fin de recurrencia del calendario Mapi, incluyendo EndAfterNOccurrences, EndAfterDate y NeverEnd. Esta sección demuestra la creación de diferentes patrones de recurrencia diaria.

### **Recurrencias Diarias: Tipo de Recurrencia EndAfterNOccurrence**

En este tipo de recurrencia, se debe establecer el número de recurrencias junto con otra información de la siguiente manera:

1. Establecer la fecha de inicio, fin y fecha de vencimiento.
1. Crear una MapiTask.
1. Establecer el estado de la tarea a NotAssigned.
1. Crear el objeto de recurrencia diaria configurando propiedades como PatternType, Period, WeekStartDay, EndType y OccurenceCount.
1. Establecer la propiedad MapiTask.Recurrence a este objeto de recurrencia diaria.
1. Guardar este mensaje en disco.

El siguiente fragmento de código te muestra cómo crear una tarea con el tipo de fin de recurrencia como EndAfterNOccurrence.

{{< gist "aspose-email" "9e8fbeb51a8cbc4129dc71ca8cd55f0b" "Examples-CSharp-Outlook-EndAfterNoccurrences-EndAfterNoccurrences.cs" >}}

La siguiente función se puede usar para calcular el número de eventos entre las dos fechas:

{{< gist "aspose-email" "9e8fbeb51a8cbc4129dc71ca8cd55f0b" "Examples-CSharp-Outlook-GetOccurrenceCount-GetOccurrenceCount.cs" >}}

#### **Estableciendo el valor de cuenta de ocurrencias**

El siguiente fragmento de código te muestra cómo establecer el valor de cuenta de ocurrencias.

{{< gist "aspose-email" "9e8fbeb51a8cbc4129dc71ca8cd55f0b" "Examples-CSharp-Outlook-SetDailyOccurrenceCount-SetDailyOccurrenceCount.cs" >}}

### **Recurrencias Diarias: Tipo de Recurrencia EndAfterDate**

La opción "End By" en la tarea Mapi se logra estableciendo la propiedad OccurrenceCount calculada por la función GetOccurrenceCount(). Esta función toma la fecha de inicio, la fecha de fin y la cadena RRULE.

#### **Recurrencias Diarias: Estableciendo el valor de Every Day**

El siguiente fragmento de código te muestra cómo establecer el valor del período a 1 y el valor de INTERVAL a 1 en la cadena RRULE también.

{{< gist "aspose-email" "9e8fbeb51a8cbc4129dc71ca8cd55f0b" "Examples-CSharp-Outlook-SetRecurrenceEveryDay-SetRecurrenceEveryDay.cs" >}}

El valor de Every Day se puede establecer en cualquier valor apropiado como se muestra en el siguiente ejemplo:

{{< gist "aspose-email" "9e8fbeb51a8cbc4129dc71ca8cd55f0b" "Examples-CSharp-Outlook-DailyRecurrences-SetEveryDayValueInterval.cs" >}}

### **Recurrencias Diarias: Tipo de Recurrencia NeverEnd**

El tipo de fin se puede establecer utilizando MapiCalendarRecurrenceEndType.NeverEnd. El período o INTERVAL se puede establecer en el valor requerido, digamos 1 en el siguiente ejemplo.

{{< gist "aspose-email" "9e8fbeb51a8cbc4129dc71ca8cd55f0b" "Examples-CSharp-Outlook-SetDailyNeverEndRecurrence-SetDailyNeverEndRecurrence.cs" >}}

## **Trabajando con Recurrencias Semanales**

Aspose.Email proporciona características ricas para la creación de recurrencias semanales utilizando MapiCalendarWeeklyRecurrencePattern. Se pueden usar tres tipos diferentes de fin de recurrencia del calendario Mapi, incluyendo EndAfterNOccurrences, EndAfterDate y NeverEnd. Esta sección demuestra la creación de diferentes patrones de recurrencia semanal.

### **Recurrencias Semanales: Tipo de Recurrencia EndAfterNOccurrences**

En este tipo de recurrencia, se debe establecer el número de recurrencias junto con otra información de la siguiente manera:

1. Establecer la fecha de inicio, fin y fecha de vencimiento.
1. Crear una MapiTask.
1. Establecer el estado de la tarea a NotAssigned.
1. Crear el objeto de recurrencia semanal configurando propiedades como PatternType, Period, WeekStartDay, EndType y OccurenceCount.
1. Establecer la propiedad MapiTask.Recurrence a este objeto de recurrencia semanal.
1. Guardar este mensaje en disco.

El siguiente fragmento de código te muestra cómo crear una tarea con el tipo de fin de recurrencia como EndAfterNOccurrence.

{{< gist "aspose-email" "9e8fbeb51a8cbc4129dc71ca8cd55f0b" "Examples-CSharp-Outlook-WeeklyEndAfterNoccurrences-WeeklyEndAfterNoccurrences.cs" >}}

La siguiente función se puede usar para calcular el número de eventos entre las dos fechas:

{{< gist "aspose-email" "9e8fbeb51a8cbc4129dc71ca8cd55f0b" "Examples-CSharp-Outlook-WeeklyEndAfterNoccurrences-EventsBetweenTheTwoDates.cs" >}}

#### **Seleccionando múltiples días en una semana**

El siguiente fragmento de código te muestra cómo seleccionar múltiples días en una semana.

{{< gist "aspose-email" "9e8fbeb51a8cbc4129dc71ca8cd55f0b" "Examples-CSharp-Outlook-EndAfterNoccurrenceSelectMultipleDaysInweek-EndAfterNoccurrenceSelectMultipleDaysInweek.cs" >}}

#### **Seleccionando múltiples días en una semana y estableciendo intervalos**

El siguiente fragmento de código te muestra cómo seleccionar múltiples días en una semana y establecer intervalos.

{{< gist "aspose-email" "9e8fbeb51a8cbc4129dc71ca8cd55f0b" "Examples-CSharp-Outlook-SetWeeklyRecurrenceMultipleDaysInWeekWithInterval-SetWeeklyRecurrenceMultipleDaysInWeekWithInterval.cs" >}}

### **Recurrencias Semanales: Tipo de Recurrencia EndAfterDate**

La opción "End By" en la tarea Mapi se logra estableciendo la propiedad OccurrenceCount calculada por la función GetOccurrenceCount(). Esta función toma la fecha de inicio, la fecha de fin y la cadena RRULE.

#### **Recurrencias Semanales: Estableciendo el valor de Every Day**

El siguiente fragmento de código te muestra cómo establecer el valor del período a 1 y el valor de INTERVAL a 1 en la cadena RRULE también.

{{< gist "aspose-email" "9e8fbeb51a8cbc4129dc71ca8cd55f0b" "Examples-CSharp-Outlook-SetWeeklyEndAfterDateRecurrence-SetWeeklyEndAfterDateEveryDayRecurrence.cs" >}}

El valor de Every Day se puede establecer en cualquier valor apropiado y se pueden seleccionar múltiples días como se muestra en el siguiente ejemplo:

{{< gist "aspose-email" "9e8fbeb51a8cbc4129dc71ca8cd55f0b" "Examples-CSharp-Outlook-SetWeeklyEndAfterDateRecurrence-SetWeeklyEndAfterDateMultipleDaysRecurrence.cs" >}}

### **Recurrencias Semanales: Tipo de Recurrencia NeverEnd**

El tipo de fin se puede establecer utilizando MapiCalendarRecurrenceEndType.NeverEnd. El período o INTERVAL se puede establecer en el valor requerido, digamos 1 en el siguiente ejemplo.

{{< gist "aspose-email" "9e8fbeb51a8cbc4129dc71ca8cd55f0b" "Examples-CSharp-Outlook-SetWeeklyNeverEndRecurrence-SetWeeklyNeverEndRecurrence.cs" >}}

## **Trabajando con Recurrencias Mensuales**

Aspose.Email soporta la creación de recurrencias mensuales utilizando MapiCalendarMonthlyRecurrencePattern. Se pueden usar tres tipos diferentes de fin de recurrencia del calendario Mapi, incluyendo EndAfterNOccurrences, EndAfterDate y NeverEnd. Esta sección demuestra la creación de diferentes patrones de recurrencia mensual.

### **Recurrencias Mensuales: Tipo de Recurrencia EndAfterNOccurrences**

En este tipo de recurrencia, se debe establecer el número de recurrencias junto con otra información de la siguiente manera:

1. Establecer la fecha de inicio, fin y fecha de vencimiento.
1. Crear una MapiTask.
1. Establecer el estado de la tarea a NotAssigned.
1. Crear el objeto de recurrencia mensual configurando propiedades como PatternType, Period, WeekStartDay, EndType y OccurenceCount.
1. Establecer la propiedad MapiTask.Recurrence a este objeto de recurrencia mensual.
1. Guardar este mensaje en disco.

El siguiente fragmento de código te muestra cómo crear una tarea con el tipo de fin de recurrencia como EndAfterNOccurrence.

{{< gist "aspose-email" "9e8fbeb51a8cbc4129dc71ca8cd55f0b" "Examples-CSharp-Outlook-MonthlyEndAfterNoccurrences-MonthlyEndAfterNoccurrences.cs" >}}

La siguiente función se puede usar para calcular el número de eventos entre las dos fechas:

{{< gist "aspose-email" "9e8fbeb51a8cbc4129dc71ca8cd55f0b" "Examples-CSharp-Outlook-MonthlyEndAfterNoccurrences-EventsBetweenTheTwoDates.cs" >}}

#### **Establecer un número fijo de ocurrencias**

El siguiente fragmento de código te muestra cómo establecer un número fijo de ocurrencias.

{{< gist "aspose-email" "9e8fbeb51a8cbc4129dc71ca8cd55f0b" "Examples-CSharp-Outlook-MonthlyEndAfterNoccurrences-SetFixNumberOfOccurrences.cs" >}}

### **Recurrencias Mensuales: Tipo de Recurrencia EndAfterDate**

La opción "End By" en la tarea Mapi se logra estableciendo la propiedad OccurrenceCount calculada por la función GetOccurrenceCount(). Esta función toma la fecha de inicio, la fecha de fin y la cadena RRULE. El siguiente fragmento de código te muestra cómo crear una recurrencia el día 15 de cada mes entre la fecha de inicio y la fecha de fin.

{{< gist "aspose-email" "9e8fbeb51a8cbc4129dc71ca8cd55f0b" "Examples-CSharp-Outlook-SetMonthlyEndAfterDateRecurrence-SetMonthlyEndAfterDateRecurrence.cs" >}}

### **Recurrencias Mensuales: Tipo de Recurrencia NeverEnd**

El siguiente fragmento de código te muestra cómo establecer el tipo de fin utilizando MapiCalendarRecurrenceEndType.NeverEnd.

{{< gist "aspose-email" "9e8fbeb51a8cbc4129dc71ca8cd55f0b" "Examples-CSharp-Outlook-SetMonthlyNeverEndRecurrence-SetMonthlyNeverEndRecurrence.cs" >}}

## **Trabajando con Recurrencias Anuales**

Aspose.Email soporta la creación de recurrencias anuales utilizando MapiCalendarMonthlyRecurrencePattern. Al establecer la propiedad de período en 12, podemos lograr el patrón de recurrencia anual. Se pueden usar tres tipos diferentes de fin de recurrencia del calendario Mapi, incluyendo EndAfterNOccurrences, EndAfterDate y NeverEnd. Esta sección demuestra la creación de diferentes patrones de recurrencia anual.

### **Recurrencias Anuales: Tipo de Recurrencia EndAfterNOccurrences**

En este tipo de recurrencia, se debe establecer el número de recurrencias junto con otra información de la siguiente manera:

1. Establecer la fecha de inicio, fin y fecha de vencimiento.
1. Crear una MapiTask.
1. Establecer el estado de la tarea a NotAssigned.
1. Crear el objeto de recurrencia mensual configurando propiedades como PatternType, Period, WeekStartDay, EndType y OccurenceCount.
1. Establecer la propiedad MapiTask.Recurrence a este objeto de recurrencia mensual para lograr la recurrencia anual.
1. Guardar este mensaje en disco.

El siguiente fragmento de código te muestra cómo crear una tarea con el tipo de fin de recurrencia como EndAfterNOccurrence.

{{< gist "aspose-email" "9e8fbeb51a8cbc4129dc71ca8cd55f0b" "Examples-CSharp-Outlook-YearlyRecurrences-EndAfterNOccurrences.cs" >}}

### **Recurrencias Anuales: Tipo de Recurrencia EndAfterDate**

La opción "End By" en la tarea Mapi se logra estableciendo la propiedad OccurrenceCount calculada por la función GetOccurrenceCount(). Esta función toma la fecha de inicio, la fecha de fin y la cadena RRULE. El siguiente fragmento de código te muestra cómo crear una recurrencia el día 15 de cada 7º mes entre la fecha de inicio y la fecha de fin.

{{< gist "aspose-email" "9e8fbeb51a8cbc4129dc71ca8cd55f0b" "Examples-CSharp-Outlook-YearlyEndAfterDate-YearlyEndAfterDate.cs" >}}

### **Recurrencias Anuales: Tipo de Recurrencia NeverEnd**

El siguiente fragmento de código te muestra cómo establecer el tipo de fin utilizando MapiCalendarRecurrenceEndType.NeverEnd.

{{< gist "aspose-email" "9e8fbeb51a8cbc4129dc71ca8cd55f0b" "Examples-CSharp-Outlook-SetYearlyNeverEndRecurrence-SetYearlyNeverEndRecurrence.cs" >}}

## **Generar Recurrencia a partir de Regla de Recurrencia**

La API Aspose.Email proporciona la capacidad de generar un Patrón de Recurrencia a partir de una Regla de Recurrencia (RRULE). Analiza la información de la RRULE según las especificaciones iCal de RFC 5545 y genera el patrón de recurrencia utilizando el método MapiCalendarRecurrencePatternFactory.FromString. El siguiente fragmento de código te muestra cómo generar el patrón de recurrencia a partir de la regla de recurrencia.

{{< gist "aspose-email" "9e8fbeb51a8cbc4129dc71ca8cd55f0b" "Examples-CSharp-Outlook-GenerateRecurrenceFromRecurrenceRule-GenerateRecurrenceFromRecurrenceRule.cs" >}}

## **Añadir un Archivo Adjunto a Eventos de Calendario Recurrentes**

La API Aspose.Email proporciona la capacidad de agregar archivos adjuntos a eventos de calendario recurrentes.

{{< gist "aspose-email" "9e8fbeb51a8cbc4129dc71ca8cd55f0b" "Examples-CSharp-Outlook-AddAttachmentToMapiExceptionInfo-AddAttachmentToMapiExceptionInfo.cs" >}}