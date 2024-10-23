---
title: "Trabalhando com Itens de Calendário do Outlook usando a Biblioteca de Email C++"
description: "Usando a API da Biblioteca de Email C++, você pode criar e salvar itens de calendário do Outlook como MSG, adicionar e recuperar anexos de arquivos de calendário, e configurar lembretes para compromissos adicionando tags."
url: /pt/cpp/trabalhando-com-itens-de-calendario-do-outlook/
weight: 80
type: docs
linktitle: "Trabalhando com Itens de Calendário do Outlook"
---

## **Trabalhando com MapiCalendar**
A classe MapiCalendar da Aspose.Email fornece métodos e atributos para definir várias propriedades de um item de calendário. Este artigo fornece exemplos de código para:

- Criar e salvar itens de calendário
- Definir lembretes para itens MapiCalendar
- Adicionar/Recuperar Anexos de Calendário
- Recuperar Status dos Destinatários de Solicitações de Reunião
- Criar objeto MapiCalendar TimeZone a partir de Fuso Horário Padrão

### **Criando e Salvando Itens de Calendário**
O seguinte trecho de código mostra como criar e salvar um item de calendário no formato ICS usando a Biblioteca ou API de Análise de Email C++.

{{< gist "aspose-email" "ef0db907527892c88c557bb418093cee" "Examples-EmailCPP-Outlook-CreateAndSaveCalendaritems-CreateAndSaveCalendaritems.cpp" >}}

### **Salvando o Item de Calendário como MSG**
O seguinte trecho de código mostra como salvar o item de calendário como MSG.

{{< gist "aspose-email" "ef0db907527892c88c557bb418093cee" "Examples-EmailCPP-Outlook-SavingTheCalendarItemAsMSG-SavingTheCalendarItemAsMSG.cpp" >}}

### **Adicionando lembrete visual a um Calendário**
O seguinte trecho de código mostra como adicionar um lembrete visual a um calendário.

{{< gist "aspose-email" "ef0db907527892c88c557bb418093cee" "Examples-EmailCPP-Outlook-AddDisplayReminderToACalendar-AddDisplayReminderToACalendar.cpp" >}}

### **Adicionando lembrete de áudio a um Calendário**
O seguinte trecho de código mostra como adicionar um lembrete de áudio a um calendário.

{{< gist "aspose-email" "ef0db907527892c88c557bb418093cee" "Examples-EmailCPP-Outlook-AddAudioReminderToCalendar-AddAudioReminderToCalendar.cpp" >}}

### **Adicionar/Recuperar anexos de arquivos de Calendário**
O seguinte trecho de código mostra como adicionar/recuperar anexos de arquivos de calendário.

{{< gist "aspose-email" "ef0db907527892c88c557bb418093cee" "Examples-EmailCPP-Outlook-ManageAttachmentsFromCalendarFiles-GetAttachmentsFromCalendar.cpp" >}}

### **Status dos Destinatários de uma Solicitação de Reunião**
O seguinte trecho de código mostra como obter o status dos destinatários de uma solicitação de reunião.

{{< gist "aspose-email" "ef0db907527892c88c557bb418093cee" "Examples-EmailCPP-Outlook-DisplayRecipientsStatusFromMeetingRequest-DisplayRecipientsStatusFromMeetingRequest.cpp" >}}

### **Criar MapiCalendarTimeZone a partir de Fuso Horário Padrão**
O seguinte trecho de código mostra como criar MapiCalendarTimeZone a partir de um fuso horário padrão.

{{< gist "aspose-email" "ef0db907527892c88c557bb418093cee" "Examples-EmailCPP-Outlook-CreateMapiCalendarTimeZoneFromStandardTimezone-CreateMapiCalendarTimeZoneFromStandardTimezone.cpp" >}}

## **Definindo Lembrete com o Compromisso Criado**
Um lembrete pode ser adicionado quando um compromisso é criado. Esses alarmes podem ser acionados com base em diferentes critérios, como n minutos antes do horário programado, repetir n vezes em n intervalos. Diferentes tags podem ser usadas para criar esses gatilhos no script delimitado por BEGIN:VALARM e END:VALARM dentro de um compromisso. Existem várias variantes nas quais o lembrete pode ser definido em um compromisso.

### **Definindo um Lembrete Adicionando Tags**
O seguinte trecho de código mostra como definir um lembrete adicionando tags.

{{< gist "aspose-email" "ef0db907527892c88c557bb418093cee" "Examples-EmailCPP-Outlook-SetReminderByAddingTags-SetReminderByAddingTags.cpp" >}}