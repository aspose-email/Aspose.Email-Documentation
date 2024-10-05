---
title: "Важные детали iCalendar RFC 2445"
url: /ru/net/important-icalendar-rfc-2445-details/
weight: 70
type: docs
---


## **О модели объектов Aspose.iCalendar**
Пространство имен [Aspose.iCalendar](https://apireference.aspose.com/email/net/aspose.email.calendar) содержит все классы, предоставляемые компонентом Aspose.iCalendar. RecurrencePattern и RecurrenceRule являются центральными классами Aspose.iCalendar и предоставляют конкретные реализации соответствующих элементов RFC 2445. 

Класс RecurrencePattern представляет собой весь шаблон повторения. Вы можете создать новый шаблон повторения с нуля, используя конструктор по умолчанию, или загрузить существующий шаблон в формате iCalendar, используя статический метод FromiCalendar. Класс RecurrenceRule представляет собой часть RRULE или EXRULE шаблона повторения. RecurrenceRule предоставляет ряд свойств, которые напрямую соответствуют их аналогам в стандарте iCalendar. Например, ByMonth соответствует BYMONTH в iCalendar и так далее. Изучая или устанавливая значения свойств RecurrenceRule, вы можете анализировать или изменять правило повторения. Для получения дополнительной информации и примеров кода смотрите RecurrencePattern и RecurrenceRule в API Reference.
## **Важные детали iCalendar RFC 2445**
В этом разделе рассматриваются следующие темы: 

- Форматы даты и времени.
- DATE.
- DATE-TIME с местным временем.
- DATE-TIME с UTC временем.
- DATE-TIME с местным временем и временной зоной.
- BYWEEKNO обеспечивает соответствие ISO 8601
### **Форматы даты и времени**
Даты, или даты с связанными временными значениями, могут использоваться в элементах DTSTART, UNTIL, EXDATE и RDATE при указании шаблона повторения. iCalendar определяет тип значения DATE для обозначения значений, содержащих календарную дату, а также определяет тип DATE-TIME для обозначения значений, которые указывают на точную календарную дату и время суток. Значения DATE-TIME могут быть указаны в трех формах:

- Местное время.
- UTC время.
- Местное время и временная зона.
### **DATE**
Согласно стандарту iCalendar, значения DATE должны следовать формату yyyyMMdd. Следующий пример представляет 14 июля 1997 года: 19970714 
### **DATE-TIME с местным временем**
Форма даты с местным временем представляет собой значение даты-времени, которое не содержит обозначения UTC и не ссылается на временную зону. Например, следующее представляет 18 января 1998 года в 23:00: DTSTART:19980118T230000. Значения даты-времени этого типа называются "плавающими" и не привязаны к какой-либо конкретной временной зоне. Их используют для представления одного и того же часа, минуты и секунды независимо от текущей наблюдаемой временной зоны. 
### **DATE-TIME с UTC временем**
Дата с UTC временем или абсолютным временем определяется суффиксом латинской заглавной буквы Z, обозначающим UTC, добавленным к значению времени. Например, следующее представляет 19 января 1998 года в 07:00 UTC: DTSTART:19980119T070000Z Пожалуйста, обратите внимание, что Aspose.iCalendar игнорирует суффикс формата UTC Z и рассматривает время как местное время. Стандарт RFC2445 утверждает, что часть времени, указанная в правиле UNTIL шаблона повторения, должна быть в формате UTC. Это очень странное утверждение, и, на самом деле, в стандарте есть примеры, которые рассчитаны неверно. Aspose.iCalendar принимает время в любом формате в правиле UNTIL. 
### **DATE-TIME с местным временем и временной зоной**
Чтобы ссылаться на временную зону, DATE-TIME модифицируется с помощью свойства TZID. Например, следующее представляет 2 ночи в Нью-Йорке 19 января 1998 года: DTSTART;TZID=US-Eastern:19980119T020000. Пожалуйста, обратите внимание, что в данный момент Aspose.iCalendar игнорирует параметр TZID и рассматривает время как местное время. 
### **BYWEEKNO обеспечивает соответствие ISO 8601**
Используйте BYWEEKNO только тогда, когда требуется соответствие [ISO 8601](https://en.wikipedia.org/wiki/ISO_8601). Номера недель, определенные ISO 8601, очень отличаются от номеров недель в обычном понимании. Согласно ISO 8601, номер недели один календарного года - это первая неделя календарного года, которая содержит не менее четырех дней. Это правило делает алгоритм специфичным для приложений, требующих соответствия ISO 8601, и делает его практически неприменимым для других задач. ISO 8601 поддерживается некоторыми европейскими банковскими и финансовыми приложениями. Он также используется на телевидении для бронирования рекламного времени. Правило BYWEEKNO задает список номеров, разделенных запятыми, идентифицирующих недели года. Допустимые значения - от 1 до 53 и от 1 до 53. Это соответствует неделям в соответствии с номерованием недель, определенным в ISO 8601. BYWEEKNO действительно только для годовых правил.