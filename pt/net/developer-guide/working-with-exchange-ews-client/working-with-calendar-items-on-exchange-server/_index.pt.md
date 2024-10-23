---
title: "Trabalhando com Itens de Calendário no Exchange Server"
url: /pt/net/trabalhando-com-itens-de-calendario-no-exchange-server/
weight: 50
type: docs
---

## **Enviando Solicitações de Reunião**

Este artigo mostra como enviar uma solicitação de reunião para vários destinatários usando Exchange Web Services e Aspose.Email.

1. Crie uma solicitação de reunião usando a classe [Appointment](https://reference.aspose.com/email/net/aspose.email.calendar/appointment/) e defina a localização, horário e participantes.
2. Crie uma instância da classe [MailMessage](https://reference.aspose.com/email/net/aspose.email/mailmessage/) e defina a nomeação usando o método [MailMessage.AddAlternateView()](https://reference.aspose.com/email/net/aspose.email/mailmessage/addalternateview/#addalternateview).
3. Conecte-se ao Exchange Server e envie a solicitação de reunião usando o método [Send(MailMessage)](https://reference.aspose.com/email/net/aspose.email.clients.exchange.webservice/iewsclient/send/#send).

A classe [EWSClient](https://reference.aspose.com/email/net/aspose.email.clients.exchange.webservice/ewsclient/) pode ser usada para conectar-se a um Exchange Server com suporte a Exchange Web Services (EWS). Para que isso funcione, o servidor deve ser o Exchange Server 2007 ou posterior. O seguinte trecho de código mostra como usar EWS para enviar solicitações de reunião.

{{< gist "aspose-com-gists" "6e5185a63aec6fd70d83098e82b06a32" "Examples-CSharp-Exchange_EWS-SendMeetingRequestsUsingEWS-SendMeetingRequestsUsingEWS.cs" >}}

## **Trabalhando com Itens de Calendário usando EWS**

Aspose.Email fornece a capacidade de adicionar, atualizar e cancelar compromissos usando o cliente Exchange Web Service (EWS). Os métodos IEWSClient [CreateAppointment](https://reference.aspose.com/email/net/aspose.email.clients.exchange.webservice/iewsclient/createappointment/#createappointment/), [UpdateAppointment](https://reference.aspose.com/email/net/aspose.email.clients.exchange.webservice/iewsclient/updateappointment/#updateappointment/) e [CancelAppointment](https://reference.aspose.com/email/net/aspose.email.clients.exchange.webservice/iewsclient/cancelappointment/#cancelappointment/) permitem manipular itens de calendário usando EWS. Este artigo fornece um exemplo de código detalhado sobre como trabalhar com itens de calendário. O seguinte exemplo de código mostra como:

1. Criar um compromisso.
2. Atualizar um compromisso.
3. Excluir/Cancelar um compromisso.

{{< gist "aspose-com-gists" "6e5185a63aec6fd70d83098e82b06a32" "Examples-CSharp-Exchange_EWS-CreatingUpdatingAndDeletingCalendarItemsUsingEWS-CreatingUpdatingAndDeletingCalendarItemsUsingEWS.cs" >}}

## **Listando Compromissos com Suporte a Paginação**

O método ListAppointments exposto pela API [IEWSClient](https://reference.aspose.com/email/net/aspose.email.clients.exchange.webservice/iewsclient/) recupera a lista completa de compromissos do servidor Exchange. Isso pode demorar se houver um grande número de compromissos no Exchange Server. A API fornece métodos sobrecarregados do método [ListAppointments](https://reference.aspose.com/email/net/aspose.email.clients.exchange.webservice/iewsclient/listappointments/#listappointments/) que dão suporte à paginação da operação. Isso pode ser usado em diferentes combinações com o recurso de consulta também. Os seguintes métodos sobrecarregados estão disponíveis para listar compromissos do Exchange Server com suporte a paginação.

- `AppointmentCollection IEWSClient.ListAppointments(int itemsPerPage)`.
- `AppointmentCollection IEWSClient.ListAppointments(string folderUri, int itemsPerPage)`.
- `AppointmentCollection IEWSClient.ListAppointments(MailQuery query, int itemsPerPage)`.
- `AppointmentCollection IEWSClient.ListAppointments(string folderUri, MailQuery query, int itemsPerPage)`.
- `AppointmentCollection IEWSClient.ListAppointments(int itemsPerPage, int itemOffset)`.
- `AppointmentCollection IEWSClient.ListAppointments(string folderUri, int itemsPerPage, int itemOffset)`.
- `AppointmentCollection IEWSClient.ListAppointments(MailQuery query, int itemsPerPage, int itemOffset)`.
- `AppointmentCollection IEWSClient.ListAppointments(string folderUri, MailQuery query, int itemsPerPage, int itemOffset)`.

O seguinte trecho de código mostra como listar compromissos com suporte a paginação.

{{< gist "aspose-com-gists" "6e5185a63aec6fd70d83098e82b06a32" "Examples-CSharp-Exchange_EWS-PagingSupportForListingAppointments-PagingSupportForListingAppointments.cs" >}}

## **Adicionando Evento à Pasta de Calendário Secundária no Exchange Server**

A API Aspose.Email permite criar uma pasta de Calendário secundária no Exchange Server usando o [IEWSClient](https://reference.aspose.com/email/net/aspose.email.clients.exchange.webservice/iewsclient/). Em seguida, os compromissos podem ser adicionados, atualizados ou cancelados a partir do calendário secundário usando os métodos [CreateAppointment](https://reference.aspose.com/email/net/aspose.email.clients.exchange.webservice/iewsclient/createappointment/#createappointment/), [UpdateAppointment](https://reference.aspose.com/email/net/aspose.email.clients.exchange.webservice/iewsclient/updateappointment/#updateappointment/) e [CancelAppointment](https://reference.aspose.com/email/net/aspose.email.clients.exchange.webservice/iewsclient/cancelappointment/#cancelappointment/). Os seguintes métodos e propriedades da API são usados nos exemplos de código abaixo para mostrar a funcionalidade desse recurso. Observe que esse recurso é suportado pelo Aspose.Email para .NET 6.5.0 ou posterior.

- Método `IEWSClient.CancelAppointment(Appointment, String)`.
- Método `IEWSClient.CancelAppointment(String, String)`.
- Método `IEWSClient.CreateAppointment(Appointment, String)`.
- Método `IEWSClient.CreateFolder(String, String, ExchangeFolderPermissionCollection, String)`.
- Método `IEWSClient.FetchAppointment(String, String)`.
- Método `IEWSClient.UpdateAppointment(Appointment, String)`.
- Propriedade `IEWSClient.CurrentCalendarFolderUri`.

O seguinte trecho de código mostra como adicionar um evento à pasta de calendário secundária no servidor Exchange.

{{< gist "aspose-com-gists" "6e5185a63aec6fd70d83098e82b06a32" "Examples-CSharp-Exchange_EWS-SecondaryCalendarEvents-SecondaryCalendarEvents.cs" >}}

## **Compartilhando Convite de Calendário**

O servidor Microsoft Exchange fornece a capacidade de compartilhar calendários enviando convites de calendário para outros usuários, registrados no mesmo servidor Exchange. A API Aspose.Email fornece a mesma capacidade, permitindo compartilhar o calendário usando a API EWS.

{{< gist "aspose-com-gists" "6e5185a63aec6fd70d83098e82b06a32" "Examples-CSharp-Exchange_EWS-SendCalendarInvitation-SendCalendarInvitation.cs" >}}

## **Recuperando Informações de Atributos Estendidos de Itens de Calendário**

{{< gist "aspose-com-gists" "6e5185a63aec6fd70d83098e82b06a32" "Examples-CSharp-Exchange_EWS-RetreiveExtAttributesForCalendarItems-RetreiveExtAttributesForCalendarItems.cs" >}}

## **Retornando os Itens de Calendário Recorrentes Dentro do Intervalo de Datas Especificado**

O [EWSClient](https://reference.aspose.com/email/net/aspose.email.clients.exchange.webservice/ewsclient/) suporta o retorno dos itens de calendário recorrentes dentro do intervalo especificado por StartDate e EndDate. O método [AppointmentQueryBuilder.SetCalendarView](https://reference.aspose.com/email/net/aspose.email.clients.exchange/appointmentquerybuilder/setcalendarview/) é usado para definir um intervalo de datas específico e limitar o número de compromissos retornados para recuperar informações relevantes. Ao definir os seguintes parâmetros, você pode recuperar os compromissos correspondentes aos critérios especificados.

- startDate: A data de início da visualização do calendário. Compromissos iniciando a partir desta data serão incluídos no resultado da consulta.

- endDate: A data de término da visualização do calendário. Compromissos terminando antes ou nesta data serão incluídos no resultado da consulta.

- maxEntriesReturned: O número máximo de compromissos a serem retornados no resultado da consulta. O valor de -1 indica que não há limite específico.

```cs
ExchangeQueryBuilder builder = new ExchangeQueryBuilder();
builder.Appointment.SetCalendarView(DateTime.Now, DateTime.Now.AddMonths(1), -1);

Appointment[] appointments = client.ListAppointments(builder.GetQuery());
```