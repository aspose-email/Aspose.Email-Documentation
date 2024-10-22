---
title: "Detalhes Importantes do iCalendar RFC 2445"
url: /pt/net/detalhes-importantes-do-icalendar-rfc-2445/
weight: 70
type: docs
---


## **Sobre o Modelo de Objeto Aspose.iCalendar**
O namespace [Aspose.iCalendar](https://apireference.aspose.com/email/net/aspose.email.calendar) contém todas as classes fornecidas pelo componente Aspose.iCalendar. RecurrencePattern e RecurrenceRule são as classes centrais do Aspose.iCalendar e fornecem implementações concretas dos elementos correspondentes do RFC 2445.

A classe RecurrencePattern representa todo o padrão de recorrência. Você pode criar um novo padrão de recorrência do zero usando o construtor padrão ou carregar um padrão existente em formato iCalendar usando o método estático FromiCalendar. A classe RecurrenceRule representa a parte RRULE ou EXRULE de um padrão de recorrência. A RecurrenceRule expõe uma série de propriedades que mapeiam diretamente para suas contrapartes no padrão iCalendar. Por exemplo, ByMonth mapeia para BYMONTH no iCalendar e assim por diante. Ao examinar ou definir valores das propriedades da RecurrenceRule, você pode analisar ou modificar uma regra de recorrência. Para mais informações e exemplos de código, veja RecurrencePattern e RecurrenceRule na Referência da API.
## **Detalhes Importantes do iCalendar RFC 2445**
Esta seção inclui os seguintes tópicos:

- Formatos de Data e Hora.
- DATA.
- DATA-HORA com Hora Local.
- DATA-HORA com Hora UTC.
- DATA-HORA com Hora Local e Fuso Horário.
- BYWEEKNO Fornece Conformidade com ISO 8601
### **Formatos de Data e Hora**
Datas, ou datas com horários associados, podem ser usadas nos elementos DTSTART, UNTIL, EXDATE e RDATE ao especificar um padrão de recorrência. O iCalendar define o tipo de valor DATE para identificar valores que contêm uma data do calendário e também define o tipo DATE-TIME para identificar valores que especificam uma data e hora do dia precisas. Os valores de DATE-TIME podem ser especificados em três formas, com:

- Hora local.
- Hora UTC.
- Hora local e fuso horário.
### **DATA**
De acordo com o padrão iCalendar, os valores de DATA devem seguir o formato yyyyMMdd. O seguinte exemplo representa 14 de julho de 1997: 19970714
### **DATA-HORA com Hora Local**
A forma de data com hora local é simplesmente um valor de data-hora que não contém o modificador UTC e não referencia um fuso horário. Por exemplo, o seguinte representa 18 de janeiro de 1998, às 23h: DTSTART:19980118T230000. Os valores de data-hora deste tipo são ditos "flutuantes" e não estão vinculados a nenhum fuso horário em particular. Eles são usados para representar o mesmo valor de hora, minuto e segundo, independentemente de qual fuso horário esteja sendo observado atualmente.
### **DATA-HORA com Hora UTC**
A data com hora UTC, ou hora absoluta, é identificada por um caractere de sufixo Z em letra maiúscula latina, o designador UTC, anexado ao valor da hora. Por exemplo, o seguinte representa 19 de janeiro de 1998, às 07h UTC: DTSTART:19980119T070000Z. Por favor, note que o Aspose.iCalendar ignora o sufixo Z do formato UTC e trata a hora como hora local. O padrão RFC2445 afirma que uma parte de hora especificada na regra UNTIL de um padrão de recorrência deve estar no formato UTC. Esta é uma declaração muito estranha e, de fato, existem exemplos no padrão que são calculados incorretamente. O Aspose.iCalendar aceita hora em qualquer formato na regra UNTIL.
### **DATA-HORA com Hora Local e Fuso Horário**
Para referenciar o fuso horário, a DATA-HORA é modificada com a propriedade TZID. Por exemplo, o seguinte representa 2h em Nova Iorque em 19 de janeiro de 1998: DTSTART;TZID=US-Eastern:19980119T020000. Por favor, note que o Aspose.iCalendar, no momento, ignora o parâmetro TZID e trata a hora como hora local.
### **BYWEEKNO Fornece Conformidade com ISO 8601**
Use BYWEEKNO apenas quando a conformidade com [ISO 8601](https://en.wikipedia.org/wiki/ISO_8601) for necessária. Os números das semanas definidos pela ISO 8601 são muito diferentes dos números das semanas no sentido normal. De acordo com a ISO 8601, a semana número um do ano civil é a primeira semana de um ano civil que contém pelo menos quatro dias. Esta regra torna o algoritmo específico para aplicações que exigem conformidade com a ISO 8601 e torna-o quase inaplicável a outros usos. A ISO 8601 é suportada por algumas aplicações bancárias e financeiras europeias. Também é utilizada na televisão para a reserva de comerciais. A regra BYWEEKNO especifica uma lista de números delimitados por vírgula que identificam as semanas do ano. Os valores válidos são de 1 a 53 e de 1 a 53. Isso corresponde às semanas de acordo com a numeração das semanas conforme definido na ISO 8601. BYWEEKNO é válido apenas para regras ANUAIS.