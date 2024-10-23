---
title: "Detalhes Importantes do iCalendar RFC 2445"
url: /pt/java/detalhes-importantes-do-icalendar-rfc-2445/
weight: 70
type: docs
---


## **Sobre o Modelo de Objetos iCalendar da Aspose**
O Aspose.Email contém todas as classes fornecidas pelo componente Aspose [iCalendar](https://apireference.aspose.com/email/java/com.aspose.email/MapiCalendar). As classes [RecurrencePattern](https://apireference.aspose.com/email/java/com.aspose.email/RecurrencePattern) e [RecurrenceRule](https://apireference.aspose.com/email/java/com.aspose.email/RecurrenceRule) são as classes centrais do Aspose [iCalendar](https://apireference.aspose.com/email/java/com.aspose.email/MapiCalendar) e fornecem implementações concretas dos elementos correspondentes do RFC 2445.

A classe [RecurrencePattern](https://apireference.aspose.com/email/java/com.aspose.email/RecurrencePattern) representa todo o padrão de recorrência. Você pode criar um novo padrão de recorrência do zero usando o construtor padrão ou carregar um padrão existente em [CalendarRecurrence](https://apireference.aspose.com/email/java/com.aspose.email/CalendarRecurrence#CalendarRecurrence\(java.lang.String\)). A classe [RecurrenceRule](https://apireference.aspose.com/email/java/com.aspose.email/RecurrenceRule) representa a parte RRULE ou EXRULE de um padrão de recorrência. A [RecurrenceRule](https://apireference.aspose.com/email/java/com.aspose.email/RecurrenceRule) expõe várias propriedades que mapeiam diretamente para suas contrapartes no padrão iCalendar. Por exemplo, ByMonth mapeia para BYMONTH no iCalendar e assim por diante. Ao examinar ou definir valores das propriedades da [RecurrenceRule](https://apireference.aspose.com/email/java/com.aspose.email/RecurrenceRule), você pode analisar ou modificar uma regra de recorrência. Para mais informações e exemplos de código, consulte [RecurrencePattern](https://apireference.aspose.com/email/java/com.aspose.email/RecurrencePattern) e [RecurrenceRule](https://apireference.aspose.com/email/java/com.aspose.email/RecurrenceRule) na Referência da API.

## **Detalhes Importantes do iCalendar RFC 2445**
Esta seção inclui os seguintes tópicos:

- Formatos de Data e Hora.
- DATA.
- DATA-HORA com Hora Local.
- DATA-HORA com Hora UTC.
- DATA-HORA com Hora Local e Fuso Horário.
- BYWEEKNO Fornece Conformidade com o ISO 8601

### **Formatos de Data e Hora**
Datas, ou datas com horários associados, podem ser usadas nos elementos DTSTART, UNTIL, EXDATE e RDATE ao especificar um padrão de recorrência. O iCalendar define o tipo de valor DATE para identificar valores que contêm uma data do calendário e também define o tipo DATE-TIME para identificar valores que especificam uma data e hora do dia precisas. Os valores DATE-TIME podem ser especificados em três formas, com:

- Hora local.
- Hora UTC.
- Hora local e fuso horário.

### **DATA**
De acordo com o padrão iCalendar, os valores DATE devem seguir o formato yyyyMMdd. O seguinte exemplo representa 14 de julho de 1997: 19970714

### **DATA-HORA com Hora Local**
A forma de data com hora local é simplesmente um valor de data-hora que não contém o designador UTC e não faz referência a um fuso horário. Por exemplo, o seguinte representa 18 de janeiro de 1998, às 11 PM: DTSTART:19980118T230000. Valores de data-hora desse tipo são considerados "flutuantes" e não estão vinculados a nenhum fuso horário em particular. Eles são usados para representar o mesmo valor de hora, minuto e segundo, independentemente de qual fuso horário está sendo observado atualmente.

### **DATA-HORA com Hora UTC**
A data com hora UTC, ou hora absoluta, é identificada por um caractere sufixo de LETRA MAIÚSCULA LATINA Z, o designador UTC, acrescentado ao valor da hora. Por exemplo, o seguinte representa 19 de janeiro de 1998, às 0700 UTC: DTSTART:19980119T070000Z. Observe que o Aspose [iCalendar](https://apireference.aspose.com/email/java/com.aspose.email/MapiCalendar) ignora o sufixo Z do formato UTC e trata a hora como hora local. O padrão RFC2445 afirma que uma parte de hora especificada na regra UNTIL de um padrão de recorrência deve estar em formato UTC. Esta é uma afirmação muito estranha e, de fato, existem exemplos no padrão que são calculados incorretamente. O Aspose [iCalendar](https://apireference.aspose.com/email/java/com.aspose.email/MapiCalendar) aceita horas em qualquer formato na regra UNTIL.

### **DATA-HORA com Hora Local e Fuso Horário**
Para referenciar o fuso horário, a DATA-HORA é modificada com a propriedade TZID. Por exemplo, o seguinte representa 2 AM em Nova York em 19 de janeiro de 1998: DTSTART;TZID=US-Eastern:19980119T020000. Observe que o Aspose [iCalendar](https://apireference.aspose.com/email/java/com.aspose.email/MapiCalendar) no momento ignora o parâmetro TZID e trata a hora como hora local.

### **BYWEEKNO Fornece Conformidade com o ISO 8601**
Use BYWEEKNO apenas quando a conformidade com o [ISO 8601](https://en.wikipedia.org/wiki/ISO_8601) for necessária. Os números das semanas, conforme definidos pelo ISO 8601, são muito diferentes dos números das semanas no sentido normal. De acordo com o ISO 8601, o número da semana um do ano calendário é a primeira semana de um ano calendário que contém pelo menos quatro dias. Essa regra torna o algoritmo específico para aplicações que requerem conformidade com o ISO 8601 e torna-o quase inaplicável para outros usos. O ISO 8601 é suportado por algumas aplicações bancárias e financeiras europeias. É também usado na televisão para reserva de comerciais. A regra BYWEEKNO especifica uma lista de números delimitados por vírgulas identificando as semanas do ano. Valores válidos vão de 1 a 53 e de 1 a 53. Isso corresponde às semanas de acordo com a numeração das semanas conforme definido no ISO 8601. O BYWEEKNO é válido apenas para regras ANUAIS.