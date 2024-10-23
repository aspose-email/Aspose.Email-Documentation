---
title: "Trabalhando com Calendários do Gmail"
url: /pt/net/trabalhando-com-calendarios-do-gmail/
weight: 20
type: docs
---


## **Adicionar, Editar e Excluir um Calendário**

Aspose.Email permite que aplicativos gerenciem os calendários do Gmail usando [IGmailClient](https://reference.aspose.com/email/net/aspose.email.clients.google/igmailclient/), que fornece recursos como adicionar, excluir e atualizar calendários do Gmail. Esta classe cliente retorna uma lista de objetos do tipo ExtendedCalendar, que contêm informações sobre os itens do calendário do Gmail. A classe [IGmailClient](https://reference.aspose.com/email/net/aspose.email.clients.google/igmailclient/) expõe as seguintes funções para calendários:

- [CreateCalendar](https://reference.aspose.com/email/net/aspose.email.clients.google/igmailclient/createcalendar/#createcalendar) 
  Pode ser usada para inserir um novo calendário
- [ListCalendars](https://reference.aspose.com/email/net/aspose.email.clients.google/igmailclient/listcalendars/)
  Pode ser usada para obter a lista de todos os calendários de um cliente
- [DeleteCalendar](https://reference.aspose.com/email/net/aspose.email.clients.google/igmailclient/deletecalendar/)
  Pode ser usada para excluir um calendário
- [FetchCalendar](https://reference.aspose.com/email/net/aspose.email.clients.google/igmailclient/fetchcalendar/)
  Pode ser usada para buscar um calendário específico de um cliente
- [UpdateCalendar](https://reference.aspose.com/email/net/aspose.email.clients.google/igmailclient/updatecalendar/)
  Esta função é usada para reinserir um calendário modificado de um cliente

Para acessar os calendários, GoogleTestUser é inicializado usando as credenciais da conta gmail. GoogleOAuthHelper é usado para obter o token de acesso para o usuário, que é posteriormente utilizado para inicializar o IGmailClient.

### **Inserir, Buscar e Atualizar**

Para inserir um calendário, inicialize um objeto do tipo Calendar e insira-o usando a função [CreateCalendar()](https://reference.aspose.com/email/net/aspose.email.clients.google/igmailclient/createcalendar/#createcalendar). A função [CreateCalendar()](https://reference.aspose.com/email/net/aspose.email.clients.google/igmailclient/createcalendar/#createcalendar) retorna o id do calendário recém-inserido. Este id pode ser usado para buscar o calendário do servidor. O seguinte trecho de código mostra como inserir, buscar e atualizar um calendário.

{{< gist "aspose-email" "9e8fbeb51a8cbc4129dc71ca8cd55f0b" "Examples-CSharp-Gmail-InsertFetchAndUpdateCalendar-InsertFetchAndUpdateCalendar.cs" >}}

### **Excluir calendário específico**

Para excluir um calendário específico, precisamos obter a lista de todos os calendários de um cliente e, em seguida, excluir conforme necessário. A função [ListCalendars()](https://reference.aspose.com/email/net/aspose.email.clients.google/igmailclient/listcalendars/#listcalendars) retorna a lista de [ExtendedCalendar](https://reference.aspose.com/email/net/aspose.email.clients.google/extendedcalendar/) que contém os calendários do Gmail. O seguinte trecho de código mostra como excluir um calendário específico.

{{< gist "aspose-email" "9e8fbeb51a8cbc4129dc71ca8cd55f0b" "Examples-CSharp-Gmail-DeleteParticularCalendar-DeleteParticularCalendar.cs" >}}

## **Trabalhando com Controle de Acesso ao Calendário**

Aspose.Email fornece controle total sobre o acesso aos itens do calendário. A função [ListAccessRules()](https://reference.aspose.com/email/net/aspose.email.clients.google/igmailclient/listaccessrules/) é exposta pelo [IGmailClient](https://reference.aspose.com/email/net/aspose.email.clients.google/igmailclient/) e retorna a lista de [AccessControlRule](https://reference.aspose.com/email/net/aspose.email.clients.google/accesscontrolrule/). Informações sobre regras individuais podem ser recuperadas, modificadas e salvas novamente para o calendário de um cliente. O [IGmailClient](https://reference.aspose.com/email/net/aspose.email.clients.google/igmailclient/) contém as seguintes funções para gerenciar as regras de controle de acesso.

- [ListAccessRules](https://reference.aspose.com/email/net/aspose.email.clients.google/igmailclient/listaccessrules/)
  Esta função fornece a lista de AccessControlRule
- [CreateAccessRule](https://reference.aspose.com/email/net/aspose.email.clients.google/igmailclient/createaccessrule/)
  Esta função cria uma nova regra de acesso para um calendário.
- [UpdateAccessRule](https://reference.aspose.com/email/net/aspose.email.clients.google/igmailclient/updateaccessrule/)
  Esta função é usada para atualizar uma regra de acesso.
- [FetchAccessRule](https://reference.aspose.com/email/net/aspose.email.clients.google/igmailclient/fetchaccessrule/)
  Pode ser usada para buscar uma regra de acesso específica para o calendário de um cliente
- [DeleteAccessRule](https://search.aspose.com/q/deleteaccessrule.html)
  Esta função é usada para excluir uma regra de acesso.

O seguinte trecho de código mostra como usar funções para gerenciar as regras de acesso:

{{< gist "aspose-email" "9e8fbeb51a8cbc4129dc71ca8cd55f0b" "Examples-CSharp-Gmail-ManageAccessRule-ManageAccessRule.cs" >}}

## **Trabalhando com Configurações do Cliente e Informações de Cor**

Aspose.Email suporta o acesso às configurações do Cliente usando [IGmailClient.GetSettings()](https://reference.aspose.com/email/net/aspose.email.clients.google/igmailclient/getsettings/#igmailclientgetsettings-method). Ele retorna a lista de configurações conforme listado abaixo:

1. dateFieldOrder
1. displayAllTimezones
1. hideInvitations
1. format24HourTime
1. defaultCalendarMode
1. defaultEventLength
1. locale
1. remindOnRespondedEventsOnly
1. alternateCalendar
1. userLocation
1. hideWeekends
1. showDeclinedEvents
1. weekStart
1. weather
1. customCalendarMode
1. timezoneLabel
1. timezone
1. useKeyboardShortcuts
1. country

Da mesma forma, informações de cor para clientes também podem ser recuperadas usando [IGmailClient.GetColors()](https://reference.aspose.com/email/net/aspose.email.clients.google/igmailclient/getcolors/#igmailclientgetcolors-method). Este objeto de informações de cor retorna a lista de cores de primeiro plano, cores de fundo e data e hora da atualização.

### **Acessar configurações do cliente**

O seguinte trecho de código mostra como as funções podem ser usadas para acessar as configurações do cliente:

{{< gist "aspose-email" "9e8fbeb51a8cbc4129dc71ca8cd55f0b" "Examples-CSharp-Gmail-AccessClientSettings-AccessClientSettings.cs" >}}

### **Acessar informações de cor**

O seguinte trecho de código mostra como as funções podem ser usadas para acessar as configurações de cor do cliente.

{{< gist "aspose-email" "9e8fbeb51a8cbc4129dc71ca8cd55f0b" "Examples-CSharp-Gmail-AccessColorInfo-AccessColorInfo.cs" >}}

## **Trabalhando com Compromissos**

Aspose.Email fornece recursos para trabalhar com compromissos em calendários do Google. A seguir está a lista de tarefas que podem ser realizadas em compromissos no calendário do Google:

1. Adicionar Compromissos.
1. Recuperar lista de compromissos.
1. Recuperar compromisso específico.
1. Atualizar um compromisso.
1. Mover compromisso de um calendário para outro.
1. Excluir compromisso.

[IGmailClient](https://reference.aspose.com/email/net/aspose.email.clients.google/igmailclient/) fornece funções como [CreateAppointment](https://reference.aspose.com/email/net/aspose.email.clients.google/igmailclient/createappointment/#igmailclientcreateappointment-method), [FetchAppointment](https://reference.aspose.com/email/net/aspose.email.clients.google/igmailclient/fetchappointment/#igmailclientfetchappointment-method), [UpdateAppointment](https://reference.aspose.com/email/net/aspose.email.clients.google/igmailclient/updateappointment/#igmailclientupdateappointment-method), [ListAppointments](https://reference.aspose.com/email/net/aspose.email.clients.google/igmailclient/listappointments/#igmailclientlistappointments-method), [MoveAppointment](https://reference.aspose.com/email/net/aspose.email.clients.google/igmailclient/moveappointment/#moveappointment) e [DeleteAppointment](https://reference.aspose.com/email/net/aspose.email.clients.google/igmailclient/deleteappointment/#igmailclientdeleteappointment-method).

### **Adicionando um compromisso**

O seguinte exemplo de código demonstra o recurso de adicionar um compromisso em um calendário. Para conseguir isso, siga os passos:

1. Criar e inserir um calendário.
1. Recuperar a lista de compromissos de um novo calendário.
1. Criar um compromisso.
1. Inserir um compromisso.

{{< gist "aspose-email" "9e8fbeb51a8cbc4129dc71ca8cd55f0b" "Examples-CSharp-Gmail-AddingAnAppointment-AddingAnAppointment.cs" >}}

### **Recuperar e atualizar um compromisso**

Aqui a recuperação e atualização de um calendário são demonstradas da seguinte forma:

1. Recuperar compromisso específico.
1. Modificar o compromisso.
1. Atualizar o compromisso no calendário.

Assume-se que um calendário com id "calendarId" e id único de compromisso "AppointmentUniqueId" já foram extraídos. O seguinte trecho de código mostra como recuperar e atualizar um compromisso.

{{< gist "aspose-email" "9e8fbeb51a8cbc4129dc71ca8cd55f0b" "Examples-CSharp-Gmail-RetrieveUpdateAppointment-RetrieveUpdateAppointment.cs" >}}

### **Mover e Excluir um compromisso**

Um compromisso pode ser movido fornecendo o calendário de origem, o calendário de destino e o id único de um compromisso no calendário de origem. O seguinte trecho de código mostra como mover e excluir um compromisso.

{{< gist "aspose-email" "9e8fbeb51a8cbc4129dc71ca8cd55f0b" "Examples-CSharp-Gmail-MoveAndDeleteAppointment-MoveAndDeleteAppointment.cs" >}}