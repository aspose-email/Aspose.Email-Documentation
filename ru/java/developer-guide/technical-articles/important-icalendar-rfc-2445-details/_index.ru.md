---
title: "Важные детали iCalendar RFC 2445"
url: /ru/java/important-icalendar-rfc-2445-details/
weight: 70
type: docs
---


## **Об объектной модели Aspose iCalendar**
Aspose.Email содержит все классы, предоставляемые компонентом Aspose [iCalendar](https://apireference.aspose.com/email/java/com.aspose.email/MapiCalendar). Классы [RecurrencePattern](https://apireference.aspose.com/email/java/com.aspose.email/RecurrencePattern) и [RecurrenceRule](https://apireference.aspose.com/email/java/com.aspose.email/RecurrenceRule) являются центральными классами Aspose [iCalendar](https://apireference.aspose.com/email/java/com.aspose.email/MapiCalendar) и предоставляют конкретные реализации соответствующих элементов RFC 2445.

Класс [RecurrencePattern](https://apireference.aspose.com/email/java/com.aspose.email/RecurrencePattern) представляет собой весь шаблон повторения. Вы можете создать новый шаблон повторения с нуля, используя конструктор по умолчанию, или загрузить существующий шаблон в [CalendarRecurrence](https://apireference.aspose.com/email/java/com.aspose.email/CalendarRecurrence#CalendarRecurrence\(java.lang.String\)). Класс [RecurrenceRule](https://apireference.aspose.com/email/java/com.aspose.email/RecurrenceRule) представляет собой часть RRULE или EXRULE шаблона повторения. [RecurrenceRule](https://apireference.aspose.com/email/java/com.aspose.email/RecurrenceRule) предоставляет ряд свойств, которые напрямую соответствуют их аналогам в стандарте iCalendar. Например, ByMonth соответствует BYMONTH в iCalendar и так далее. Изучая или устанавливая значения свойств [RecurrenceRule](https://apireference.aspose.com/email/java/com.aspose.email/RecurrenceRule), вы можете анализировать или изменять правило повторения. Для получения дополнительной информации и примеров кода смотрите [RecurrencePattern](https://apireference.aspose.com/email/java/com.aspose.email/RecurrencePattern) и [RecurrenceRule](https://apireference.aspose.com/email/java/com.aspose.email/RecurrenceRule) в API Reference.

## **Важные детали iCalendar RFC 2445**
В этом разделе рассматриваются следующие темы:

- Форматы даты и времени.
- DATE.
- DATE-TIME с местным временем.
- DATE-TIME с UTC-временем.
- DATE-TIME с местным временем и часовым поясом.
- BYWEEKNO обеспечивает соответствие ISO 8601.

### **Форматы даты и времени**
Даты или даты с указанным временем могут использоваться в элементах DTSTART, UNTIL, EXDATE и RDATE при указании шаблона повторения. iCalendar определяет тип значения DATE для идентификации значений, содержащих календарную дату, и также определяет тип DATE-TIME для идентификации значений, которые указывают точную календарную дату и время суток. Значения DATE-TIME могут быть указаны в трех формах:

- Местное время.
- UTC-время.
- Местное время и часовой пояс.

### **DATE**
Согласно стандарту iCalendar, значения DATE должны следовать формату yyyyMMdd. Следующий пример представляет 14 июля 1997 года: 19970714

### **DATE-TIME с местным временем**
Форма даты с местным временем представляет собой просто значение даты-времени, которое не содержит обозначение UTC и не ссылается на часовой пояс. Например, следующее представляет 18 января 1998 года в 23:00: DTSTART:19980118T230000. Значения даты-времени этого типа считаются "плавающими" и не привязаны к какому-либо конкретному часовому поясу. Они используются для представления одного и того же значения часа, минуты и секунды независимо от того, какой часовой пояс в данный момент наблюдается.

### **DATE-TIME с UTC-временем**
Дата с UTC-временем, или абсолютное время, определяется суффиксом латинской ЗАГЛАВНОЙ БУКВЫ Z, обозначающим UTC, который добавляется к значению времени. Например, следующее представляет 19 января 1998 года в 07:00 UTC: DTSTART:19980119T070000Z. Обратите внимание, что Aspose [iCalendar](https://apireference.aspose.com/email/java/com.aspose.email/MapiCalendar) игнорирует суффикс формата UTC Z и рассматривает время как местное. Стандарт RFC2445 утверждает, что часть времени, указанная в правиле UNTIL шаблона повторения, должна быть в формате UTC. Это очень странное утверждение, и на самом деле в стандарте есть примеры, рассчитанные неправильно. Aspose [iCalendar](https://apireference.aspose.com/email/java/com.aspose.email/MapiCalendar) принимает время в любом формате в правиле UNTIL.

### **DATE-TIME с местным временем и часовым поясом**
Чтобы сослаться на часовой пояс, DATE-TIME модифицируется свойством TZID. Например, следующее представляет 2:00 ночи в Нью-Йорке 19 января 1998 года: DTSTART;TZID=US-Eastern:19980119T020000. Обратите внимание, что на данный момент Aspose [iCalendar](https://apireference.aspose.com/email/java/com.aspose.email/MapiCalendar) игнорирует параметр TZID и рассматривает время как местное.

### **BYWEEKNO обеспечивает соответствие ISO 8601**
Используйте BYWEEKNO только тогда, когда требуется соблюдение [ISO 8601](https://en.wikipedia.org/wiki/ISO_8601). Номера недель, определенные ISO 8601, очень отличаются от номеров недель в обычном смысле. Согласно ISO 8601, номер недели один календарного года — это первая неделя календарного года, которая содержит как минимум четыре дня. Це правило делает алгоритм специфичным для приложений, требующих соответствия ISO 8601, и делает его почти неприменимым для других целей. ISO 8601 поддерживается некоторыми европейскими банковскими и финансовыми приложениями. Он также используется на телевидении для бронирования рекламы. Правило BYWEEKNO указывает список чисел, разделенных запятыми, идентифицирующих недели года. Допустимые значения — от 1 до 53. Это соответствует номерам недель согласно нумерации недель, как определено в ISO 8601. BYWEEKNO действительно только для ГОДОВЫХ правил.