---
title: "Trabalhando com Calendários do Gmail"
url: /pt/java/trabalhando-com-calendarios-do-gmail/
weight: 20
type: docs
---


## **Adicionar, Editar e Excluir um Calendário**
Aspose.Email permite que aplicações gerenciem os calendários do Gmail usando [IGmailClient](https://apireference.aspose.com/email/java/com.aspose.email/IGmailClient), que oferece recursos como adição, exclusão e atualização de calendários do Gmail. Esta classe de cliente retorna uma lista de objetos do tipo ExtendedCalendar que contêm informações sobre os itens do calendário do Gmail. A classe [IGmailClient](https://apireference.aspose.com/email/java/com.aspose.email/IGmailClient) expõe as seguintes funções para os calendários:

- [createCalendar](https://apireference.aspose.com/email/java/com.aspose.email/IGmailClient#createCalendar\(com.aspose.email.Calendar\))
  Para inserir um novo calendário
- [listCalendars](https://apireference.aspose.com/email/java/com.aspose.email/IGmailClient#listCalendars\(\))

Obter a lista de todos os calendários de um cliente

- [deleteCalendar](https://apireference.aspose.com/email/java/com.aspose.email/IGmailClient#deleteCalendar\(java.lang.String\))
  Pode ser usado para excluir um calendário
- [fetchCalendar](https://apireference.aspose.com/email/java/com.aspose.email/IGmailClient#fetchCalendar\(java.lang.String\))
  Pode ser usado para buscar um calendário específico de um cliente
- [updateCalendar](https://apireference.aspose.com/email/java/com.aspose.email/IGmailClient#updateCalendar\(com.aspose.email.Calendar\))
  Esta função é usada para reinserir um calendário modificado de um cliente

Para acessar os calendários, GoogleTestUser é inicializado usando as credenciais da conta gmail. GoogleOAuthHelper é usado para obter o token de acesso para o usuário, que é então usado para inicializar [IGmailClient](https://apireference.aspose.com/email/java/com.aspose.email/IGmailClient).
### **Inserir, Buscar e Atualizar**
Para inserir um calendário, inicialize um objeto do tipo [Calendar](https://apireference.aspose.com/email/java/com.aspose.email/Calendar) e insira-o usando a função [createCalendar](https://apireference.aspose.com/email/java/com.aspose.email/IGmailClient#createCalendar\(com.aspose.email.Calendar\)). [createCalendar](https://apireference.aspose.com/email/java/com.aspose.email/IGmailClient#createCalendar\(com.aspose.email.Calendar\)) retorna o id do calendário inserido recentemente. Este id pode ser usado para buscar o calendário do servidor. O seguinte trecho de código mostra como inserir, buscar e atualizar um calendário.



~~~Java
try (IGmailClient client = GmailClient.getInstance(accessToken, email)) {
    // Inserir, obter e atualizar calendário
    Calendar calendar = new Calendar("Resumo", "Descrição", "Localização", "America/Los_Angeles");

    // Inserir calendário e recuperar o mesmo calendário usando o id
    String id = client.createCalendar(calendar);
    Calendar cal = client.fetchCalendar(id);

    // Mudar informações no calendário buscado e atualizar calendário
    cal.setDescription("Nova Descrição");
    cal.setLocation("Novo Local");
    client.updateCalendar(cal);
}
~~~
### **Excluir Calendário Particular**
Para excluir um calendário particular, precisamos obter a lista de todos os calendários de um cliente e então excluir conforme necessário. [listCalendars](https://apireference.aspose.com/email/java/com.aspose.email/IGmailClient#listCalendars\(\)) retorna a lista de [ExtendedCalendar](https://apireference.aspose.com/email/java/com.aspose.email/ExtendedCalendar) que contém calendários do Gmail. O seguinte trecho de código mostra como excluir um calendário particular.



~~~Java
try (IGmailClient client = GmailClient.getInstance(accessToken, email)) {
    // Acessar e excluir calendário com resumo começando por "Resumo do calendário"
    String summary = "Resumo do calendário";

    // Obter lista de calendários
    ExtendedCalendar[] lst = client.listCalendars();

    for (ExtendedCalendar extCal : lst) {
        // Excluir calendários selecionados
        if (extCal.getSummary().startsWith(summary))
            client.deleteCalendar(extCal.getId());
    }
}
~~~
## **Trabalhando com Controle de Acesso ao Calendário**
Aspose.Email fornece controle total sobre o controle de acesso aos itens do calendário. A função [listAccessRules](https://apireference.aspose.com/email/java/com.aspose.email/IGmailClient#listAccessRules\(java.lang.String\)) é exposta pelo [IGmailClient](https://apireference.aspose.com/email/java/com.aspose.email/IGmailClient), que retorna uma lista de [AccessControlRule](https://apireference.aspose.com/email/java/com.aspose.email/AccessControlRule). Informações sobre regras individuais podem ser recuperadas, modificadas e salvas novamente para o calendário de um cliente. [IGmailClient](https://apireference.aspose.com/email/java/com.aspose.email/IGmailClient) contém as seguintes funções para gerenciar as regras de controle de acesso.

- [listAccessRules](https://apireference.aspose.com/email/java/com.aspose.email/IGmailClient#listAccessRules\(java.lang.String\))
  Esta função fornece uma lista de [AccessControlRule](https://apireference.aspose.com/email/java/com.aspose.email/AccessControlRule)
- [createAccessRule](https://apireference.aspose.com/email/java/com.aspose.email/IGmailClient#createAccessRule\(java.lang.String,%20com.aspose.email.AccessControlRule\))
  Esta função cria uma nova regra de acesso para um calendário.
- [updateAccessRule](https://apireference.aspose.com/email/java/com.aspose.email/IGmailClient#updateAccessRule\(java.lang.String,%20com.aspose.email.AccessControlRule\))
  Esta função é usada para atualizar uma regra de acesso.
- [fetchAccessRule](https://apireference.aspose.com/email/java/com.aspose.email/IGmailClient#fetchAccessRule\(java.lang.String,%20java.lang.String\))
  Pode ser usado para buscar uma regra de acesso específica para o calendário de um cliente
- [deleteAccessRule](https://apireference.aspose.com/email/java/com.aspose.email/IGmailClient#deleteAccessRule\(java.lang.String,%20java.lang.String\))
  Esta função é usada para excluir uma regra de acesso.

O seguinte trecho de código mostra como as funções são usadas para gerenciar as regras de acesso:


~~~Java
try (IGmailClient client = GmailClient.getInstance(accessToken, email)) {
    // Recuperar lista de calendários para o cliente atual
    ExtendedCalendar[] calendarList = client.listCalendars();

    // Obter o primeiro id de calendário e recuperar a lista de AccessControlRule para o primeiro calendário
    String calendarId = calendarList[0].getId();
    AccessControlRule[] roles1 = client.listAccessRules(calendarId);

    // Criar uma regra de controle de acesso local e definir propriedades da regra
    AccessControlRule rule = new AccessControlRule();
    rule.setRole(AccessRole.reader);
    rule.setScope(new AclScope(AclScopeType.user, email2));

    // Inserir nova regra para o calendário. Isso retorna a regra criada recentemente
    AccessControlRule createdRule = client.createAccessRule(calendarId, rule);

    // Obter lista de regras
    AccessControlRule[] roles2 = client.listAccessRules(calendarId);

    // O comprimento atual da lista deve ser 1 a mais do que o anterior
    if (roles1.length + 1 == roles2.length) {
        System.out.println("Os comprimentos das listas estão ok");
    } else {
        System.out.println("Os comprimentos das listas não estão ok");
        return;
    }

    // Mudar a regra e atualizar a regra para o calendário selecionado
    createdRule.setRole(AccessRole.writer);
    AccessControlRule updatedRule = client.updateAccessRule(calendarId, createdRule);

    // Recuperar regra individual contra um calendário
    AccessControlRule fetchedRule = client.fetchAccessRule(calendarId, createdRule.getId());

    // Excluir regra particular contra um determinado calendário e recuperar toda a lista de regras para o mesmo calendário
    client.deleteAccessRule(calendarId, createdRule.getId());
    AccessControlRule[] roles3 = client.listAccessRules(calendarId);

    // Verificar se o comprimento da lista atual de regras deve ser igual ao comprimento da lista original antes de adicionar e excluir a regra
    if (roles1.length == roles3.length) {
        System.out.println("Os comprimentos das listas são iguais");
    } else {
        System.out.println("Os comprimentos das listas não são iguais");
        return;
    }
}
~~~
## **Trabalhando com Configurações do Cliente e Informações de Cor**
Aspose.Email suporta o acesso às configurações do cliente usando [IGmailClient.getSettings](https://apireference.aspose.com/email/java/com.aspose.email/IGmailClient#getSettings\(\)). Ele retorna uma lista de configurações conforme dado abaixo:

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

Da mesma forma, as informações de cor para os clientes também podem ser recuperadas usando [IGmailClient.getColors](https://apireference.aspose.com/email/java/com.aspose.email/IGmailClient#getColors\(\)). Este objeto de informação de cor retorna a lista de cores de primeiro plano, cores de fundo e data e hora da atualização.
### **Acessar Configurações do Cliente**
O seguinte trecho de código mostra como as funções são utilizadas para acessar as configurações do cliente:


~~~Java
try (IGmailClient client = GmailClient.getInstance(accessToken, email)) {
    // Recuperar configurações do cliente
    Dictionary<String, String> settings = client.getSettings();
    if (settings.size() < 1) {
        System.out.println("Nenhuma configuração disponível.");
        return;
    }

    // Percorrer a lista de configurações
    for (KeyValuePair<String, String> pair : settings) {
        // Obter o valor da configuração e testar se as configurações estão ok
        String value = client.getSetting(pair.getKey());
        if (pair.getValue().equals(value)) {
            System.out.println("Chave = " + pair.getKey() + ", Valor = " + pair.getValue());
        } else {
            System.out.println("As configurações não puderam ser recuperadas");
        }
    }
}
~~~
### **Acessar Informações de Cor**
O seguinte trecho de código mostra como as funções são usadas para acessar as configurações de cor do cliente.


~~~Java
try (IGmailClient client = GmailClient.getInstance(accessToken, email)) {
    ColorsInfo colors = client.getColors();
    Dictionary<String, Colors> palettes = colors.getCalendar();

    // Percorrer a lista de configurações
    for (KeyValuePair<String, Colors> pair : palettes) {
        System.out.println("Chave = " + pair.getKey() + ", Cor = " + pair.getValue());
    }
    System.out.println("Data de Atualização = " + colors.getUpdated());
}
~~~
## **Trabalhando com Compromissos**
Aspose.Email fornece recursos para trabalhar com [Compromissos](https://apireference.aspose.com/email/java/com.aspose.email/Appointment) em calendários do Google. A seguir está a lista de tarefas que podem ser realizadas em compromissos no calendário do Google:

1. Adicionar Compromissos - [createAppointment](https://apireference.aspose.com/email/java/com.aspose.email/IGmailClient#createAppointment\(java.lang.String,%20com.aspose.email.Appointment\)), [importAppointment](https://apireference.aspose.com/email/java/com.aspose.email/IGmailClient#importAppointment\(java.lang.String,%20com.aspose.email.Appointment\))
1. Recuperar lista de compromissos - [listAppointments](https://apireference.aspose.com/email/java/com.aspose.email/IGmailClient#listAppointments\(java.lang.String\))
1. Recuperar compromisso específico - [fetchAppointment](https://apireference.aspose.com/email/java/com.aspose.email/IGmailClient#fetchAppointment\(java.lang.String,%20java.lang.String\)), [listAppointmentInstances](https://apireference.aspose.com/email/java/com.aspose.email/IGmailClient#listAppointmentInstances\(java.lang.String,%20java.lang.String\))
1. Atualizar um compromisso - [updateAppointment](https://apireference.aspose.com/email/java/com.aspose.email/IGmailClient#updateAppointment\(java.lang.String,%20com.aspose.email.Appointment\))
1. Mover compromisso de um calendário para outro - [moveAppointment](https://apireference.aspose.com/email/java/com.aspose.email/IGmailClient#moveAppointment\(java.lang.String,%20java.lang.String,%20java.lang.String\))
1. Excluir compromisso - [deleteAppointment](https://apireference.aspose.com/email/java/com.aspose.email/IGmailClient#deleteAppointment\(java.lang.String,%20java.lang.String\))

### **Adicionando um Compromisso**
O seguinte trecho de código demonstra o recurso de adicionar um compromisso em um calendário. Neste exemplo, os seguintes passos são seguidos:

1. Criar e inserir um calendário.
1. Recuperar lista de compromissos de um novo calendário.
1. Criar um compromisso.
1. Inserir compromisso.


~~~Java
try (IGmailClient client = GmailClient.getInstance(accessToken, email)) {
    // Criar calendário local
    Calendar calendar1 = new Calendar("Resumo", null, null, "Europe/Kiev");

    // Inserir calendário e obter id do calendário inserido e recuperar o calendário usando um id
    String id = client.createCalendar(calendar1);
    Calendar cal1 = client.fetchCalendar(id);
    String calendarId1 = cal1.getId();

    try {
        // Recuperar lista de compromissos do primeiro calendário
        Appointment[] appointments = client.listAppointments(calendarId1);
        if (appointments.length > 0) {
            System.out.println("Número incorreto de compromissos");
            return;
        }

        // Obter hora atual e calcular a hora após uma hora a partir de agora
        java.util.Calendar c = java.util.Calendar.getInstance();
        Date startDate = c.getTime();
        c.add(java.util.Calendar.HOUR_OF_DAY, 1);
        Date endDate = c.getTime();

        // Inicializar uma coleção de endereços de e-mail e definir os endereços de e-mail dos participantes
        MailAddressCollection attendees = new MailAddressCollection();
        attendees.add("User1.EMail@domain.com");
        attendees.add("User3.EMail@domain.com");

        // Criar um compromisso com os participantes acima
        Appointment app1 = new Appointment("Localização", startDate, endDate, MailAddress.to_MailAddress(email2), attendees);

        // Definir resumo do compromisso, descrição, fuso horário de início/fim
        app1.setSummary("Novo Resumo");
        app1.setDescription("Nova Descrição");
        app1.setStartTimeZone("Europe/Kiev");
        app1.setEndTimeZone("Europe/Kiev");

        // Inserir compromisso no primeiro calendário inserido acima e obter o compromisso inserido
        Appointment app2 = client.createAppointment(calendarId1, app1);

        // Recuperar compromisso usando id único
        Appointment app3 = client.fetchAppointment(calendarId1, app2.getUniqueId());
    } catch (Exception ex) {
        System.err.println(ex);
    }
    
}
~~~
### **Recuperar e Atualizar Compromisso**
Aqui, a recuperação e atualização de um calendário são demonstradas da seguinte forma:

1. Recuperar compromisso particular.
1. Modificar o compromisso.
1. Atualizar o compromisso no calendário.

Supõe-se que um calendário com id "calendarId" e id único do compromisso "AppointmentUniqueId" já foram extraídos. O seguinte trecho de código mostra como recuperar e atualizar um compromisso.



~~~Java
try (IGmailClient client = GmailClient.getInstance(accessToken, email)) {
    String calendarId = client.listCalendars()[0].getId();
    String AppointmentUniqueId = client.listAppointments(calendarId)[0].getUniqueId();

    // Recuperar Compromisso
    Appointment app3 = client.fetchAppointment(calendarId, AppointmentUniqueId);
    // Mudar as informações do compromisso
    app3.setSummary("Novo Resumo");
    app3.setDescription("Nova Descrição");
    app3.setLocation("Novo Local");
    app3.setFlags(AppointmentFlags.AllDayEvent);
    java.util.Calendar c = java.util.Calendar.getInstance();
    c.add(java.util.Calendar.HOUR_OF_DAY, 2);
    app3.setStartDate(c.getTime());
    c.add(java.util.Calendar.HOUR_OF_DAY, 1);
    app3.setEndDate(c.getTime());
    app3.setStartTimeZone("Europe/Kiev");
    app3.setEndTimeZone("Europe/Kiev");
    // Atualizar o compromisso e obter o compromisso atualizado
    Appointment app4 = client.updateAppointment(calendarId, app3);
}
~~~
### **Mover e Excluir Compromisso**
[Appointment](https://apireference.aspose.com/email/java/com.aspose.email/Appointment) pode ser movido fornecendo o calendário de origem, calendário de destino e id único do compromisso no calendário de origem. O seguinte trecho de código mostra como mover e excluir um compromisso.


~~~Java
try (IGmailClient client = GmailClient.getInstance(accessToken, email)) {
    String SourceCalendarId = client.listCalendars()[0].getId();
    String DestinationCalendarId = client.listCalendars()[1].getId();
    String TargetAppUniqueId = client.listAppointments(SourceCalendarId)[0].getUniqueId();

    // Recuperar a lista de compromissos no calendário de destino antes de mover o compromisso
    Appointment[] appointments = client.listAppointments(DestinationCalendarId);
    System.out.println("Antes da contagem de movimento = " + appointments.length);
    Appointment Movedapp = client.moveAppointment(SourceCalendarId, DestinationCalendarId, TargetAppUniqueId);

    // Recuperar a lista de compromissos no calendário de destino após mover o compromisso
    appointments = client.listAppointments(DestinationCalendarId);
    System.out.println("Após a contagem de movimento = " + appointments.length);

    // Excluir compromisso particular de um calendário usando id único
    client.deleteAppointment(DestinationCalendarId, Movedapp.getUniqueId());

    // Recuperar a lista de compromissos. Deve ser um a menos do que os compromissos anteriores no calendário de destino
    appointments = client.listAppointments(DestinationCalendarId);
    System.out.println("Após a contagem de exclusão = " + appointments.length);
}
~~~