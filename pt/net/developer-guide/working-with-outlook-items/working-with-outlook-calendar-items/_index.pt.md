---
title: "Trabalhando com Itens do Calendário do Outlook"
url: /pt/net/trabalhando-com-itens-do-calendario-do-outlook/
weight: 120
type: docs
---

## **Trabalhando com MapiCalendar**

A classe MapiCalendar do Aspose.Email fornece métodos e atributos para definir várias propriedades de um item de calendário. Este artigo fornece amostras de código para:

- [**Trabalhando com MapiCalendar**](#trabalhando-com-mapicalendar)
  - [**Criando e Salvando Itens de Calendário**](#criando-e-salvando-itens-de-calendario)
  - [**Salvando o Item do Calendário como MSG**](#salvando-o-item-do-calendario-como-msg)
  - [**Adicionando lembrete de exibição a um Calendário**](#adicionando-lembrete-de-exibicao-a-um-calendario)
  - [**Adicionando lembrete de áudio a um Calendário**](#adicionando-lembrete-de-audio-a-um-calendario)
  - [**Adicionar/Recuperar anexos de arquivos do Calendário**](#adicionarrecuperar-anexos-de-arquivos-do-calendario)
  - [**Status dos Recipientes de um Pedido de Reunião**](#status-dos-recipientes-de-um-pedido-de-reuniao)
  - [**Criar MapiCalendarTimeZone a partir do Fuso Horário Padrão**](#criar-mapicalendartimezone-a-partir-do-fuso-horario-padrao)
- [**Definindo Lembrete com o Compromisso Criado**](#definindo-lembrete-com-o-compromisso-criado)
  - [**Definindo um Lembrete Adicionando Tags**](#definindo-um-lembrete-adicionando-tags)
- [**Converter Compromisso EML para MSG com Corpo HTML**](#converter-compromisso-eml-para-msg-com-corpo-html)

### **Criando e Salvando Itens de Calendário**

O seguinte trecho de código mostra como criar e salvar um item de calendário no formato ICS.

{{< gist "aspose-com-gists" "6e5185a63aec6fd70d83098e82b06a32" "Examples-CSharp-Outlook-CreateAndSaveCalendaritems-CreateAndSaveCalendaritems.cs" >}}

### **Salvando o Item do Calendário como MSG**

O seguinte trecho de código mostra como salvar o item do calendário como MSG.

{{< gist "aspose-com-gists" "6e5185a63aec6fd70d83098e82b06a32" "Examples-CSharp-Outlook-SavingTheCalendarItemAsMSG-SavingTheCalendarItemAsMSG.cs" >}}

### **Definindo um Produto ID ao Salvar MapiCalendar para ICS**

A propriedade [ProductIdentifier](https://reference.aspose.com/email/net/aspose.email.mapi/mapicalendaricssaveoptions/productidentifier/) da classe [MapiCalendarIcsSaveOptions](https://reference.aspose.com/email/net/aspose.email.mapi/mapicalendaricssaveoptions/#mapicalendaricssaveoptions-class) é usada para salvar um item de calendário MAPI em um arquivo iCalendar (ICS) preservando as informações originais de data e hora, bem como um identificador de produto personalizado. A propriedade especifica o identificador para o produto que criou o objeto iCalendar.

O seguinte exemplo de código mostra como trabalhar com dados iCalendar (ICS) dentro de um objeto de calendário MAPI:

```cs
var icsSaveOptions = new MapiCalendarIcsSaveOptions
{
    KeepOriginalDateTimeStamp = true,
    ProductIdentifier = "Foo Ltd"
};

mapiCalendar.Save("my.ics", icsSaveOptions);
```

### **Obtendo o número total de eventos**

A classe CalendarReader permite lidar com eventos de calendário sem esforço. As seguintes propriedades e um método permitem que você trabalhe com múltiplos eventos:

- **CalendarReader.Count** - A propriedade Count da classe CalendarReader permite recuperar o número de componentes Vevent (eventos) presentes no calendário, facilitando o rastreamento do número total de eventos.
- **CalendarReader.IsMultiEvents** - Esta propriedade determina se o calendário contém múltiplos eventos. Ela fornece um valor booleano indicando se o calendário contém mais de um evento, ajudando a identificar calendários com eventos únicos ou múltiplos.
- **CalendarReader.Method** - A propriedade Method obtém o tipo de método iCalendar associado ao objeto de calendário. Ela retorna o tipo de método, como “REQUEST,” “PUBLISH,” ou “CANCEL,” fornecendo informações valiosas sobre o propósito do calendário.
- **CalendarReader.Version** - Obtém a versão do iCalendar.
- **CalendarReader.LoadAsMultiple()** Este método permite carregar uma lista de eventos de um calendário contendo múltiplos eventos. Ele retorna uma lista de objetos Appointment, permitindo fácil acesso e processamento de cada evento individualmente.

O seguinte exemplo de código demonstra como você pode implementar essas capacidades em seu projeto:

```cs
var reader = new CalendarReader(fileName);
Console.WriteLine("O calendário contém " + reader.Count + " eventos");
Console.WriteLine("A versão do calendário é " + reader.Version);
Console.WriteLine("O método do calendário é " + reader.Method);
Console.WriteLine("O calendário contém múltiplos eventos? - " + reader.IsMultiEvents);
List<Appointment> appointments = reader.LoadAsMultiple();
```

### **Adicionando lembrete de exibição a um Calendário**

O seguinte trecho de código mostra como adicionar um lembrete de exibição a um calendário.

{{< gist "aspose-com-gists" "6e5185a63aec6fd70d83098e82b06a32" "Examples-CSharp-Outlook-AddDisplayReminderToACalendar-AddDisplayReminderToACalendar.cs" >}}

### **Adicionando lembrete de áudio a um Calendário**

O seguinte trecho de código mostra como adicionar um lembrete de áudio a um calendário.

{{< gist "aspose-com-gists" "6e5185a63aec6fd70d83098e82b06a32" "Examples-CSharp-Outlook-AddAudioReminderToCalendar-AddAudioReminderToCalendar.cs" >}}

### **Adicionar/Recuperar anexos de arquivos do Calendário**

O seguinte trecho de código mostra como adicionar/recuperar anexos de arquivos do calendário.

{{< gist "aspose-com-gists" "6e5185a63aec6fd70d83098e82b06a32" "Examples-CSharp-Outlook-ManageAttachmentsFromCalendarFiles-GetAttachmentsFromCalendar.cs" >}}

### **Status dos Recipientes de um Pedido de Reunião**

O seguinte trecho de código mostra como exibir o status dos recipientes de um pedido de reunião.

{{< gist "aspose-com-gists" "6e5185a63aec6fd70d83098e82b06a32" "Examples-CSharp-Outlook-DisplayRecipientsStatusFromMeetingRequest-DisplayRecipientsStatusFromMeetingRequest.cs" >}}

### **Criar MapiCalendarTimeZone a partir do Fuso Horário Padrão**

O seguinte trecho de código mostra como criar MapiCalendarTimeZone a partir do fuso horário padrão.

{{< gist "aspose-com-gists" "6e5185a63aec6fd70d83098e82b06a32" "Examples-CSharp-Outlook-CreateMapiCalendarTimeZoneFromStandardTimezone-CreateMapiCalendarTimeZoneFromStandardTimezone.cs" >}}

## **Definindo Lembrete com o Compromisso Criado**

Um lembrete pode ser adicionado quando um compromisso é criado. Esses alarmes podem ser acionados com base em diferentes critérios, como n minutos antes do agendamento começar, repetir n vezes em n intervalos. Diferentes tags podem ser usadas para criar esses gatilhos no script delimitado por BEGIN:VALARM e END:VALARM dentro de um compromisso. Existem várias variantes nas quais o lembrete pode ser definido em um compromisso.

### **Definindo um Lembrete Adicionando Tags**

O seguinte trecho de código mostra como definir um lembrete adicionando tags.

{{< gist "aspose-com-gists" "6e5185a63aec6fd70d83098e82b06a32" "Examples-CSharp-Outlook-SetReminderByAddingTags-SetReminderByAddingTags.cs" >}}

## **Converter Compromisso EML para MSG com Corpo HTML**

Desde a versão 19.3, o Aspose.Email fornece a capacidade de converter Compromisso EML para MSG enquanto retém o corpo HTML do compromisso. O Aspose.Email fornece uma propriedade [MapiConversionOptions.ForcedRtfBodyForAppointment](https://reference.aspose.com/email/net/aspose.email.mapi/mapiconversionoptions/forcedrtfbodyforappointment/) que tem um valor padrão de **true.** Quando o valor de [MapiConversionOptions.ForcedRtfBodyForAppointment](https://reference.aspose.com/email/net/aspose.email.mapi/mapiconversionoptions/forcedrtfbodyforappointment/) é definido como **true**, o corpo do compromisso é convertido para o formato RTF. Para manter o formato do corpo do compromisso em HTML, defina o valor de [MapiConversionOptions.ForcedRtfBodyForAppointment](https://reference.aspose.com/email/net/aspose.email.mapi/mapiconversionoptions/forcedrtfbodyforappointment/) como **false.**

O seguinte exemplo demonstra o uso da propriedade [MapiConversionOptions.ForcedRtfBodyForAppointment](https://reference.aspose.com/email/net/aspose.email.mapi/mapiconversionoptions/forcedrtfbodyforappointment/) para manter o formato do corpo do compromisso em HTML.

{{< gist "aspose-com-gists" "522d47278b8ca448dc1d7eb97193322c" "Examples-CSharp-Outlook-ConvertAppointmentEMLToMSGWithHTMLBody-1.cs" >}}