---
title: "Trabalhando com Itens de Calendário no Exchange Server"
url: /pt/cpp/trabalhando-com-itens-de-calendario-no-exchange-server/
weight: 50
type: docs
---

## **Enviando Solicitações de Reunião**
Este artigo mostra como enviar uma solicitação de reunião para múltiplos destinatários usando Exchange Web Services e Aspose.Email.

1. Crie uma solicitação de reunião usando a [Appointment](https://apireference.aspose.com/email/cpp/class/aspose.email.calendar.appointment) classe e defina o local, horário e participantes.
1. Crie uma instância da [MailMessage](https://apireference.aspose.com/email/cpp/class/aspose.email.mail_message) classe e defina a nomeação usando o [MailMessage->AddAlternateView()](https://docs.aspose.com/email/pt/cppfilter-messages-from-exchange-mailbox/) método.
1. Conecte-se ao Exchange Server e envie a solicitação de reunião usando o [IEWSClient->Send(MailMessage)](https://apireference.aspose.com/email/cpp/class/aspose.email.clients.exchange.web_service.i_e_w_s_client) método.

A classe [EWSClient](https://apireference.aspose.com/email/cpp/class/aspose.email.clients.exchange.web_service.e_w_s_client) pode ser usada para conectar-se a um servidor Exchange com suporte a Exchange Web Services (EWS). Para isso funcionar, o servidor deve ser Exchange Server 2007 ou posterior. O seguinte trecho de código mostra como usar o EWS para enviar as solicitações de reunião.

{{< gist "aspose-com-gists" "525dd06c8783ebb18fb75cfc4b31d1ef" "Examples-Cpp-source-Exchange_EWS-SendMeetingRequestsUsingEWS-SendMeetingRequestsUsingEWS.cpp" >}}
## **Trabalhando com Itens de Calendário usando EWS**
Aspose.Email fornece a capacidade de adicionar, atualizar e cancelar compromissos usando o cliente Exchange Web Service (EWS). Os métodos [IEWSClient->CreateAppointment](https://apireference.aspose.com/email/cpp/class/aspose.email.clients.exchange.web_service.i_e_w_s_client), [IEWSClient->UpdateAppointment](https://apireference.aspose.com/email/cpp/class/aspose.email.clients.exchange.web_service.i_e_w_s_client) e [IEWSClient->CancelAppointment](https://apireference.aspose.com/email/cpp/class/aspose.email.clients.exchange.web_service.i_e_w_s_client) permitem manipular itens de calendário usando EWS. Este artigo fornece um exemplo de código detalhado sobre como trabalhar com itens de calendário. O seguinte exemplo de código mostra como:

1. Criar um compromisso.
1. Atualizar um compromisso.
1. Excluir/Cancelar um compromisso.

{{< gist "aspose-com-gists" "525dd06c8783ebb18fb75cfc4b31d1ef" "Examples-Cpp-source-Exchange_EWS-CreatingUpdatingAndDeletingCalendarItemsUsingEWS-CreatingUpdatingAndDeletingCalendarItemsUsingEWS.cpp" >}}
## **Listando Compromissos com Suporte a Paginação**
O método [ListAppointments](https://apireference.aspose.com/email/cpp/class/aspose.email.clients.exchange.web_service.i_e_w_s_client) exposto pela API [IEWSClient](https://apireference.aspose.com/email/cpp/class/aspose.email.clients.exchange.web_service.i_e_w_s_client) recupera a lista completa de compromissos do servidor Exchange. Isso pode demorar se houver um grande número de compromissos no Exchange Server. A API fornece métodos sobrecarregados do método [ListAppointmentsByPage](https://apireference.aspose.com/email/cpp/class/aspose.email.clients.exchange.web_service.i_e_w_s_client) que oferece suporte à paginação para a operação. Isso pode ser usado em diferentes combinações com o recurso de consulta também. Os seguintes métodos sobrecarregados estão disponíveis para listar compromissos do Exchange Server com suporte à paginação.

- [`IEWSClient.ListAppointmentsByPage(int itemsPerPage)`](https://apireference.aspose.com/email/cpp/class/aspose.email.clients.exchange.web_service.i_e_w_s_client).
- [`IEWSClient.ListAppointmentsByPage(string folderUri, int itemsPerPage)`](https://apireference.aspose.com/email/cpp/class/aspose.email.clients.exchange.web_service.i_e_w_s_client).
- [`IEWSClient.ListAppointmentsByPage(MailQuery query, int itemsPerPage)`](https://apireference.aspose.com/email/cpp/class/aspose.email.clients.exchange.web_service.i_e_w_s_client).
- [`IEWSClient.ListAppointmentsByPage(string folderUri, MailQuery query, int itemsPerPage)`](https://apireference.aspose.com/email/cpp/class/aspose.email.clients.exchange.web_service.i_e_w_s_client).
- [`IEWSClient.ListAppointmentsByPage(int itemsPerPage, int itemOffset)`](https://apireference.aspose.com/email/cpp/class/aspose.email.clients.exchange.web_service.i_e_w_s_client).
- [`IEWSClient.ListAppointmentsByPage(string folderUri, int itemsPerPage, int itemOffset)`](https://apireference.aspose.com/email/cpp/class/aspose.email.clients.exchange.web_service.i_e_w_s_client).
- [`IEWSClient.ListAppointmentsByPage(MailQuery query, int itemsPerPage, int itemOffset)`](https://apireference.aspose.com/email/cpp/class/aspose.email.clients.exchange.web_service.i_e_w_s_client).
- [`IEWSClient.ListAppointmentsByPage(string folderUri, MailQuery query, int itemsPerPage, int itemOffset)`](https://apireference.aspose.com/email/cpp/class/aspose.email.clients.exchange.web_service.i_e_w_s_client).

O seguinte trecho de código mostra como listar compromissos com suporte à paginação.

{{< gist "aspose-com-gists" "525dd06c8783ebb18fb75cfc4b31d1ef" "Examples-Cpp-source-Exchange_EWS-PagingSupportForListingAppointments-PagingSupportForListingAppointments.cpp" >}}
## **Adicionando Evento a Pasta de Calendário Secundária no Exchange Server**
A API Aspose.Email permite criar uma pasta de calendário secundária no Exchange Server usando o [IEWSClient](https://apireference.aspose.com/email/cpp/class/aspose.email.clients.exchange.web_service.i_e_w_s_client). Compromissos podem ser adicionados, atualizados ou cancelados a partir do calendário secundário usando os métodos [IEWSClient->CreateAppointment](https://apireference.aspose.com/email/cpp/class/aspose.email.clients.exchange.web_service.i_e_w_s_client), [IEWSClient->UpdateAppointment](https://apireference.aspose.com/email/cpp/class/aspose.email.clients.exchange.web_service.i_e_w_s_client) e [IEWSClient->CancelAppointment](https://apireference.aspose.com/email/cpp/class/aspose.email.clients.exchange.web_service.i_e_w_s_client).

O seguinte trecho de código mostra como adicionar um evento a uma pasta de calendário secundária no servidor Exchange.

{{< gist "aspose-com-gists" "525dd06c8783ebb18fb75cfc4b31d1ef" "Examples-Cpp-source-Exchange_EWS-SecondaryCalendarEvents-SecondaryCalendarEvents.cpp" >}}
## **Compartilhando Convite de Calendário**
O servidor Microsoft Exchange fornece a capacidade de compartilhar calendários enviando convites de calendário para outros usuários, registrados no mesmo servidor Exchange. A API Aspose.Email fornece a mesma capacidade, permitindo compartilhar o calendário usando a API EWS.

{{< gist "aspose-com-gists" "525dd06c8783ebb18fb75cfc4b31d1ef" "Examples-Cpp-source-Exchange_EWS-SendCalendarInvitation-SendCalendarInvitation.cpp" >}}
## **Recuperando Informações de Atributos Estendidos de Itens de Calendário**
{{< gist "aspose-com-gists" "525dd06c8783ebb18fb75cfc4b31d1ef" "Examples-Cpp-source-Exchange_EWS-RetreiveExtAttributesForCalendarItems-RetreiveExtAttributesForCalendarItems.cpp" >}}