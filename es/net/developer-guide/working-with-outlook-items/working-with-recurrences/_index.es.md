---
title: "Trabajando con recurrencias"
url: /es/net/working-with-recurrences/
weight: 140
type: docs
---


## **Trabajando con recurrencias diarias**

Aspose.Email admite la creación de recurrencias diarias mediante MapiCalendarDailyRecurrencePattern. Se pueden usar tres tipos diferentes de finales de recurrencia del calendario Mapi, incluidos EndAfterNoccurrences, EndAfterDate y NeverEnd. En esta sección se muestra la creación de diferentes patrones de recurrencia diarios.

### **Recurrencias diarias: tipo de recurrencia EndAfterNoccurrence**

En este tipo de recurrencia, el número de recurrencias se establecerá junto con otra información de la siguiente manera:

1. Establezca la fecha de inicio, finalización y vencimiento.
1. Crea una MapiTask.
1. Establece el estado de la tarea en NotAssigned.
1. Crea el objeto de periodicidad diaria estableciendo propiedades como PatternType, Period, WeekStartDay, EndType y OccurenceCount.
1. Establezca la propiedad mapitask.Recurrence en este objeto de recurrencia diaria.
1. Guarde este mensaje en el disco.

En el siguiente fragmento de código, se muestra cómo crear una tarea con un tipo de final recurrente como endAfternOcurrence.

{{< gist "aspose-email" "9e8fbeb51a8cbc4129dc71ca8cd55f0b" "Examples-CSharp-Outlook-EndAfterNoccurrences-EndAfterNoccurrences.cs" >}}

La siguiente función se puede utilizar para calcular el número de eventos entre las dos fechas:

{{< gist "aspose-email" "9e8fbeb51a8cbc4129dc71ca8cd55f0b" "Examples-CSharp-Outlook-GetOccurrenceCount-GetOccurrenceCount.cs" >}}

#### **Configuración del valor del recuento de ocurrencias**

El siguiente fragmento de código muestra cómo establecer el valor del recuento de ocurrencias.

{{< gist "aspose-email" "9e8fbeb51a8cbc4129dc71ca8cd55f0b" "Examples-CSharp-Outlook-SetDailyOccurrenceCount-SetDailyOccurrenceCount.cs" >}}

### **Recurrencias diarias: tipo de recurrencia EndAfterDate**

La opción «Finalizar por» de la tarea Mapi se logra estableciendo la propiedad OccurrenceCount calculada por la función getOccurrenceCount (). Esta función toma la fecha de inicio, la fecha de finalización y la cadena RRULE.

#### **Recurrencias diarias: configuración del valor diario**

En el siguiente fragmento de código, también se muestra cómo establecer el valor del período en 1 y el valor INTERVAL en 1 en la cadena RRULE.

{{< gist "aspose-email" "9e8fbeb51a8cbc4129dc71ca8cd55f0b" "Examples-CSharp-Outlook-SetRecurrenceEveryDay-SetRecurrenceEveryDay.cs" >}}

El valor de cada día se puede establecer en cualquier valor apropiado, como se muestra en el siguiente ejemplo:

{{< gist "aspose-email" "9e8fbeb51a8cbc4129dc71ca8cd55f0b" "Examples-CSharp-Outlook-DailyRecurrences-SetEveryDayValueInterval.cs" >}}

### **Recurrencias diarias: tipo de recurrencia sin fin**

El tipo de final se puede establecer mediante MapiCalendarRecurrenceEndType.NeverEnd. El período o el INTERVALO se pueden establecer en el valor requerido, por ejemplo, 1 en el siguiente ejemplo.

{{< gist "aspose-email" "9e8fbeb51a8cbc4129dc71ca8cd55f0b" "Examples-CSharp-Outlook-SetDailyNeverEndRecurrence-SetDailyNeverEndRecurrence.cs" >}}

## **Trabajando con recurrencias semanales**

Aspose.Email proporciona funciones completas para la creación de recurrencias semanales mediante MapiCalendarWeeklyRecurrencePattern. Se pueden usar tres tipos diferentes de finales de recurrencia del calendario Mapi, incluidos EndAfternOccurrences, EndAfterDate y NeverEnd. En esta sección se muestra la creación de diferentes patrones de recurrencia semanales.

### **Recurrencias semanales: tipo de recurrencia EndAfterNoccurrences**

En este tipo de recurrencia, el número de recurrencias se establecerá junto con otra información de la siguiente manera:

1. Establezca la fecha de inicio, finalización y vencimiento.
1. Crea una MapiTask.
1. Establece el estado de la tarea en NotAssigned.
1. Crea el objeto de periodicidad semanal estableciendo propiedades como PatternType, Period, WeekStartDay, EndType y OccurenceCount.
1. Establezca la propiedad mapitask.Recurrence en este objeto de periodicidad semanal.
1. Guarde este mensaje en el disco.

En el siguiente fragmento de código, se muestra cómo crear una tarea con un tipo de final recurrente como endAfternOcurrence.

{{< gist "aspose-email" "9e8fbeb51a8cbc4129dc71ca8cd55f0b" "Examples-CSharp-Outlook-WeeklyEndAfterNoccurrences-WeeklyEndAfterNoccurrences.cs" >}}

La siguiente función se puede utilizar para calcular el número de eventos entre las dos fechas:

{{< gist "aspose-email" "9e8fbeb51a8cbc4129dc71ca8cd55f0b" "Examples-CSharp-Outlook-WeeklyEndAfterNoccurrences-EventsBetweenTheTwoDates.cs" >}}

#### **Selección de varios días en una semana**

En el siguiente fragmento de código, se muestra cómo seleccionar varios días de la semana.

{{< gist "aspose-email" "9e8fbeb51a8cbc4129dc71ca8cd55f0b" "Examples-CSharp-Outlook-EndAfterNoccurrenceSelectMultipleDaysInweek-EndAfterNoccurrenceSelectMultipleDaysInweek.cs" >}}

#### **Selección de varios días en una semana y configuración de intervalos**

El siguiente fragmento de código muestra cómo seleccionar varios días de una semana y establecer intervalos.

{{< gist "aspose-email" "9e8fbeb51a8cbc4129dc71ca8cd55f0b" "Examples-CSharp-Outlook-SetWeeklyRecurrenceMultipleDaysInWeekWithInterval-SetWeeklyRecurrenceMultipleDaysInWeekWithInterval.cs" >}}

### **Recurrencias semanales: tipo de recurrencia EndAfterDate**

La opción «Finalizar por» de la tarea Mapi se logra estableciendo la propiedad OccurrenceCount calculada por la función getOccurrenceCount (). Esta función toma la fecha de inicio, la fecha de finalización y la cadena RRULE.

#### **Recurrencias semanales: configuración del valor diario**

En el siguiente fragmento de código, también se muestra cómo establecer el valor del período en 1 y el valor INTERVAL en 1 en la cadena RRULE.

{{< gist "aspose-email" "9e8fbeb51a8cbc4129dc71ca8cd55f0b" "Examples-CSharp-Outlook-SetWeeklyEndAfterDateRecurrence-SetWeeklyEndAfterDateEveryDayRecurrence.cs" >}}

El valor de cada día se puede establecer en cualquier valor apropiado y se pueden seleccionar varios días como se muestra en el siguiente ejemplo:

{{< gist "aspose-email" "9e8fbeb51a8cbc4129dc71ca8cd55f0b" "Examples-CSharp-Outlook-SetWeeklyEndAfterDateRecurrence-SetWeeklyEndAfterDateMultipleDaysRecurrence.cs" >}}

### **Recurrencias semanales: tipo de recurrencia sin fin**

El tipo de final se puede establecer mediante MapiCalendarRecurrenceEndType.NeverEnd. El período o el INTERVALO se pueden establecer en el valor requerido, por ejemplo, 1 en el siguiente ejemplo.

{{< gist "aspose-email" "9e8fbeb51a8cbc4129dc71ca8cd55f0b" "Examples-CSharp-Outlook-SetWeeklyNeverEndRecurrence-SetWeeklyNeverEndRecurrence.cs" >}}

## **Trabajando con recurrencias mensuales**

Aspose.Email admite la creación de recurrencias mensuales mediante MapiCalendarMonthlyRecurrencePattern. Se pueden usar tres tipos diferentes de finales de recurrencia del calendario Mapi, incluidos EndAfterNoccurrences, EndAfterDate y NeverEnd. En esta sección se muestra la creación de diferentes patrones de recurrencia mensual.

### **Recurrencias mensuales: tipo de recurrencia de EndAfternoCurrences**

En este tipo de recurrencia, el número de recurrencias se establecerá junto con otra información de la siguiente manera:

1. Establezca la fecha de inicio, finalización y vencimiento.
1. Crea una MapiTask.
1. Establece el estado de la tarea en NotAssigned.
1. Crea el objeto de periodicidad mensual estableciendo propiedades como PatternType, Period, WeekStartDay, EndType y OccurenceCount.
1. Establezca la propiedad mapitask.Recurrence en este objeto de periodicidad mensual.
1. Guarde este mensaje en el disco.

En el siguiente fragmento de código, se muestra cómo crear una tarea con un tipo de final recurrente como endAfternOcurrence.

{{< gist "aspose-email" "9e8fbeb51a8cbc4129dc71ca8cd55f0b" "Examples-CSharp-Outlook-MonthlyEndAfterNoccurrences-MonthlyEndAfterNoccurrences.cs" >}}

La siguiente función se puede utilizar para calcular el número de eventos entre las dos fechas:

{{< gist "aspose-email" "9e8fbeb51a8cbc4129dc71ca8cd55f0b" "Examples-CSharp-Outlook-MonthlyEndAfterNoccurrences-EventsBetweenTheTwoDates.cs" >}}

#### **Establecer el número fijo de ocurrencias**

El siguiente fragmento de código muestra cómo establecer el número fijo de ocurrencias.

{{< gist "aspose-email" "9e8fbeb51a8cbc4129dc71ca8cd55f0b" "Examples-CSharp-Outlook-MonthlyEndAfterNoccurrences-SetFixNumberOfOccurrences.cs" >}}

### **Recurrencias mensuales: tipo de recurrencia EndAfterDate**

La opción «Finalizar por» de la tarea Mapi se logra estableciendo la propiedad OccurrenceCount calculada por la función getOccurrenceCount (). Esta función toma la fecha de inicio, la fecha de finalización y la cadena RRULE. El siguiente fragmento de código muestra cómo crear una repetición el 15 de cada mes entre la fecha de inicio y la fecha de finalización.

{{< gist "aspose-email" "9e8fbeb51a8cbc4129dc71ca8cd55f0b" "Examples-CSharp-Outlook-SetMonthlyEndAfterDateRecurrence-SetMonthlyEndAfterDateRecurrence.cs" >}}

### **Recurrencias mensuales: tipo de recurrencia sin fin**

En el siguiente fragmento de código, se muestra cómo establecer el tipo de finalización mediante MapiCalendarRecurrenceEndType.NeverEnd.

{{< gist "aspose-email" "9e8fbeb51a8cbc4129dc71ca8cd55f0b" "Examples-CSharp-Outlook-SetMonthlyNeverEndRecurrence-SetMonthlyNeverEndRecurrence.cs" >}}

## **Trabajando con recurrencias anuales**

Aspose.Email admite la creación de recurrencias anuales mediante MapiCalendarMonthlyRecurrencePattern. Al establecer la propiedad del período en 12, podemos lograr el patrón de recurrencia anual. Se pueden usar tres tipos diferentes de finales de recurrencia del calendario Mapi, incluidos EndAfterNoccurrences, EndAfterDate y NeverEnd. En esta sección se muestra la creación de diferentes patrones de recurrencia anual.

### **Recurrencias anuales: tipo de recurrencia EndAfterNoccurrences**

En este tipo de recurrencia, el número de recurrencias se establecerá junto con otra información de la siguiente manera:

1. Establezca la fecha de inicio, finalización y vencimiento.
1. Crea una MapiTask.
1. Establece el estado de la tarea en NotAssigned.
1. Crea el objeto de periodicidad mensual estableciendo propiedades como PatternType, Period, WeekStartDay, EndType y OccurenceCount.
1. Establezca la propiedad mapitask.Recurrence en este objeto de periodicidad mensual para lograr la periodicidad anual.
1. Guarde este mensaje en el disco.

En el siguiente fragmento de código, se muestra cómo crear una tarea con un tipo de final recurrente como endAfternOcurrence.

{{< gist "aspose-email" "9e8fbeb51a8cbc4129dc71ca8cd55f0b" "Examples-CSharp-Outlook-YearlyRecurrences-EndAfterNOccurrences.cs" >}}

### **Recurrencias anuales: tipo de recurrencia EndAfterDate**

La opción «Finalizar por» de la tarea Mapi se logra estableciendo la propiedad OccurrenceCount calculada por la función getOccurrenceCount (). Esta función toma la fecha de inicio, la fecha de finalización y la cadena RRULE. El siguiente fragmento de código muestra cómo crear una repetición el 15 de cada séptimo mes entre la fecha de inicio y la fecha de caducidad.

{{< gist "aspose-email" "9e8fbeb51a8cbc4129dc71ca8cd55f0b" "Examples-CSharp-Outlook-YearlyEndAfterDate-YearlyEndAfterDate.cs" >}}

### **Recurrencias anuales: tipo de recurrencia sin fin**

En el siguiente fragmento de código, se muestra cómo establecer el tipo de finalización mediante MapiCalendarRecurrenceEndType.NeverEnd.

{{< gist "aspose-email" "9e8fbeb51a8cbc4129dc71ca8cd55f0b" "Examples-CSharp-Outlook-SetYearlyNeverEndRecurrence-SetYearlyNeverEndRecurrence.cs" >}}

## **Generar repetición a partir de la regla de recurrencia**

La API Aspose.Email brinda la capacidad de generar un patrón de recurrencia a partir de la regla de recurrencia (RRULE). Analiza la información de la RRULE según las especificaciones de iCal en el RFC 5545 y genera el patrón de recurrencia mediante el método MapiCalendarRecurrencePatternFactory.fromString. El siguiente fragmento de código muestra cómo generar un patrón de recurrencia a partir de la regla de recurrencia.

{{< gist "aspose-email" "9e8fbeb51a8cbc4129dc71ca8cd55f0b" "Examples-CSharp-Outlook-GenerateRecurrenceFromRecurrenceRule-GenerateRecurrenceFromRecurrenceRule.cs" >}}

## **Agregar un archivo adjunto a los eventos periódicos del calendario**

La API Aspose.Email ofrece la capacidad de agregar archivos adjuntos a los eventos periódicos del calendario.

{{< gist "aspose-email" "9e8fbeb51a8cbc4129dc71ca8cd55f0b" "Examples-CSharp-Outlook-AddAttachmentToMapiExceptionInfo-AddAttachmentToMapiExceptionInfo.cs" >}}
