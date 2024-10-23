---
title: "Trabalhando com Itens de Calendário no Exchange Server"
url: /pt/java/trabalhando-com-itens-de-calendario-no-exchange-server/
weight: 50
type: docs
---


## **Enviando Solicitações de Reunião**
Este artigo mostra como enviar uma solicitação de reunião para múltiplos destinatários usando o Exchange Web Services e o Aspose.Email.

1. Crie uma solicitação de reunião usando a classe Appointment e defina o local, horário e participantes.
1. Crie uma instância da classe MailMessage e defina a consulta usando o método MailMessage.addAlternateView().
1. Conecte-se ao Exchange Server e envie a solicitação de reunião usando o método send(MailMessage).

A classe [EWSClient](https://apireference.aspose.com/email/java/com.aspose.email/ewsclient) pode ser usada para conectar-se a servidores Exchange com suporte a Exchange Web Services (EWS). Para que isso funcione, o servidor deve ser Exchange Server 2007 ou posterior. O seguinte trecho de código mostra como usar o EWS para enviar as solicitações de reunião.



~~~Java
try {
    // Crie uma instância da classe IEWSClient fornecendo credenciais
    IEWSClient client = EWSClient.getEWSClient("https://outlook.office365.com/ews/exchange.asmx", "testUser", "pwd", "domain");

    Calendar c = Calendar.getInstance();
    c.add(Calendar.HOUR_OF_DAY, 1);
    Date startTime = c.getTime();
    c.add(Calendar.MINUTE, 90);
    Date endTime = c.getTime();

    // Crie a solicitação de reunião
    Appointment app = new Appointment("solicitação de reunião", startTime, endTime, MailAddress.to_MailAddress("administrator@test.com"),
            MailAddressCollection.to_MailAddressCollection("bob@test.com"));
    app.setSummary("resumo da solicitação de reunião");
    app.setDescription("descrição");

    c = Calendar.getInstance();
    c.add(Calendar.DATE, 5);
    RecurrencePattern pattern = new DailyRecurrencePattern(c.getTime());
    app.setRecurrence(pattern);

    // Crie a mensagem e defina a solicitação de reunião
    MailMessage msg = new MailMessage();
    msg.setFrom(MailAddress.to_MailAddress("administrator@test.com"));
    msg.setTo(MailAddressCollection.to_MailAddressCollection("bob@test.com"));
    msg.isBodyHtml(true);
    msg.setHtmlBody("<h3>HTML Heading</h3><p>Detalhe da Mensagem de Email</p>");
    msg.setSubject("solicitação de reunião");
    msg.addAlternateView(app.requestApointment(0));

    // envie a consulta
    client.send(msg);
    System.out.println("Solicitação de reunião enviada");
} catch (java.lang.RuntimeException ex) {
    System.out.println(ex.getMessage());
}
~~~  
## **Trabalhando com Itens de Calendário usando EWS**
Aspose.Email fornece a capacidade de adicionar, atualizar e cancelar compromissos usando o cliente Exchange Web Service (EWS). Os métodos IEWSClients [createAppointment](https://apireference.aspose.com/email/java/com.aspose.email/IEWSClient#createAppointment\(com.aspose.email.Appointment\)), [updateAppointment](https://apireference.aspose.com/email/java/com.aspose.email/IEWSClient#updateAppointment\(com.aspose.email.Appointment\)), e [cancelAppointment](https://apireference.aspose.com/email/java/com.aspose.email/IEWSClient#cancelAppointment\(com.aspose.email.Appointment\)) permitem manipular itens de calendário usando EWS. Este artigo fornece um exemplo de código detalhado sobre como trabalhar com itens de calendário. O seguinte exemplo de código mostra como:

1. Criar um compromisso.
1. Atualizar um compromisso.
1. Excluir/Cancelar um compromisso.



~~~Java
IEWSClient client = EWSClient.getEWSClient("https://outlook.office365.com/ews/exchange.asmx", "your.username", "your.Password");
Calendar c = Calendar.getInstance();
c.set(Calendar.MINUTE, 0);
c.set(Calendar.SECOND, 0);
c.set(Calendar.MILLISECOND, 0);
Date startTime = c.getTime();
c.add(Calendar.HOUR_OF_DAY, 1);
Date endTime = c.getTime();
String timeZone = "America/New_York";

Appointment app = new Appointment("Sala 112", startTime, endTime, MailAddress.to_MailAddress("organizeraspose-email.test3@domain.com"),
        MailAddressCollection.to_MailAddressCollection("attendee@gmail.com"));
app.setTimeZone(timeZone);
app.setSummary("NETWORKNET-34136" + UUID.randomUUID().toString());
app.setDescription("NETWORKNET-34136 Exchange 2007/EWS: Prover suporte para Adicionar/Atualizar/Excluir itens de calendário");

String uid = client.createAppointment(app);
Appointment fetchedAppointment1 = client.fetchAppointment(uid);
app.setLocation("Sala 115");
app.setSummary("Novo resumo para " + app.getSummary());
app.setDescription("Nova Descrição");
client.updateAppointment(app);

Appointment[] appointments1 = client.listAppointments();
System.out.println("Total de Compromissos: " + appointments1.length);
Appointment fetchedAppointment2 = client.fetchAppointment(uid);
System.out.println("Resumo: " + fetchedAppointment2.getSummary());
System.out.println("Localização: " + fetchedAppointment2.getLocation());
System.out.println("Descrição: " + fetchedAppointment2.getDescription());
client.cancelAppointment(app);
Appointment[] appointments2 = client.listAppointments();
System.out.println("Total de Compromissos: " + appointments2.length);
~~~  

### **Retornar os Itens de Calendário Recorrentes Dentro da Faixa de Datas Especificada**

Aspose.Email EWSClient suporta o retorno dos itens de calendário recorrentes dentro da faixa especificada por StartDate e EndDate. O método [AppointmentQueryBuilder.setCalendarView(Date startDate, Date endDate, int maxEntriesReturned)](https://reference.aspose.com/email/java/com.aspose.email/appointmentquerybuilder/#setCalendarView-java.util.Date-java.util.Date-int-) retorna uma lista de itens de calendário únicos e ocorrências de itens de calendário recorrentes dentro da faixa especificada por StartDate e EndDate, se a CalendarView for especificada. O parâmetro *maxEntriesReturned* descreve o número máximo de resultados. (Valor <= 0 para todos os resultados).

```java
ExchangeQueryBuilder builder = new ExchangeQueryBuilder();
builder.getAppointment().setCalendarView(startDate, endDate, -1);

Appointment[] appointments = client.listAppointments(builder.getQuery());
```
## **Listando Compromissos com Suporte a Paginação**
O método ListAppointments exposto pela API [IEWSClient](https://apireference.aspose.com/email/java/com.aspose.email/IEWSClient) recupera a lista completa de compromissos do servidor Exchange. Isso pode levar tempo se houver um grande número de compromissos no Server Exchange. A API fornece métodos sobrecarregados do método [listAppointments](https://apireference.aspose.com/email/java/com.aspose.email/IEWSClient#listAppointments\(\)) que oferecem suporte à paginação para a operação. Isso pode ser usado em diferentes combinações com o recurso de consulta também. Os seguintes métodos sobrecarregados estão disponíveis para listar compromissos do Exchange Server com suporte à paginação.

- `AppointmentCollection IEWSClient.listAppointments(int itemsPerPage)`.
- `AppointmentCollection IEWSClient.listAppointments(String folderUri, int itemsPerPage)`.
- `AppointmentCollection IEWSClient.listAppointments(MailQuery query, int itemsPerPage)`.
- `AppointmentCollection IEWSClient.listAppointments(String folderUri, MailQuery query, int itemsPerPage)` .
- `AppointmentCollection IEWSClient.listAppointments(int itemsPerPage, int itemOffset)` .
- `AppointmentCollection IEWSClient.listAppointments(String folderUri, int itemsPerPage, int itemOffset)` .
- `AppointmentCollection IEWSClient.listAppointments(MailQuery query, int itemsPerPage, int itemOffset)` .
- `AppointmentCollection IEWSClient.listAppointments(String folderUri, MailQuery query, int itemsPerPage, int itemOffset)`.

O seguinte trecho de código mostra como listar compromissos com suporte à paginação.



~~~Java
        IEWSClient client = EWSClient.getEWSClient("exchange.domain.com", "username", "password");
        try {
            try {
                Appointment[] appts = client.listAppointments();
                System.out.println(appts.length);

                Calendar c = Calendar.getInstance();
                c.set(Calendar.MINUTE, 0);
                c.set(Calendar.SECOND, 0);
                c.set(Calendar.MILLISECOND, 0);

                int appNumber = 10;
                Map<String, Appointment> appointmentsDict = new HashMap<String, Appointment>();
                for (int i = 0; i < appNumber; i++) {
                    c.set(Calendar.HOUR_OF_DAY, i + 1);
                    Date startTime = c.getTime();
                    c.set(Calendar.HOUR_OF_DAY, i + 2);
                    Date endTime = c.getTime();

                    String timeZone = "America/New_York";
                    Appointment appointment = new Appointment("Sala 112", startTime, endTime, MailAddress.to_MailAddress("from@domain.com"),
                            MailAddressCollection.to_MailAddressCollection("to@domain.com"));
                    appointment.setTimeZone(timeZone);
                    appointment.setSummary("NETWORKNET-35157_3 - " + UUID.randomUUID().toString());
                    appointment.setDescription("EMAILNET-35157 Mover parâmetros de paginação para classe separada");
                    String uid = client.createAppointment(appointment);
                    appointmentsDict.put(uid, appointment);
                }
                AppointmentCollection totalAppointmentCol = AppointmentCollection.to_AppointmentCollection(client.listAppointments());

                ///// LISTANDO COMPROMISSOS COM SUPORTE À PAGINAÇÃO ///////
                int itemsPerPage = 2;
                List<AppointmentPageInfo> pages = new ArrayList<AppointmentPageInfo>();
                AppointmentPageInfo pagedAppointmentCol = client.listAppointmentsByPage(itemsPerPage);
                System.out.println(pagedAppointmentCol.getItems().size());
                pages.add(pagedAppointmentCol);
                while (!pagedAppointmentCol.getLastPage()) {
                    pagedAppointmentCol = client.listAppointmentsByPage(itemsPerPage, pagedAppointmentCol.getPageOffset() + 1);
                    pages.add(pagedAppointmentCol);
                }
                int retrievedItems = 0;
                // conversão de foreach para while
                for (AppointmentPageInfo folderCol : pages) {
                    retrievedItems += folderCol.getItems().size();
                }
            } finally {
            }
        } finally {
            client.dispose();
        }
~~~  
## **Adicionando Evento à Pasta de Calendário Secundária no Exchange Server**
A API Aspose.Email permite que você crie uma pasta de Calendário secundário no Exchange Server usando o [IEWSClient](https://apireference.aspose.com/email/java/com.aspose.email/IEWSClient). Compromissos podem então ser adicionados, atualizados ou cancelados dessa pasta de calendário secundária usando os métodos [createAppointment](https://apireference.aspose.com/email/java/com.aspose.email/IEWSClient#createAppointment\(com.aspose.email.Appointment\)), [updateAppointment](https://apireference.aspose.com/email/java/com.aspose.email/IEWSClient#updateAppointment\(com.aspose.email.Appointment\)) e [cancelAppointment](https://apireference.aspose.com/email/java/com.aspose.email/IEWSClient#cancelAppointment\(com.aspose.email.Appointment\)). Os seguintes métodos e propriedades da API são usados nos exemplos de código abaixo para mostrar a funcionalidade deste recurso. Observe que este recurso é suportado pelo Aspose.Email para Java 6.5.0 ou posterior.

- Método `IEWSClient.cancelAppointment(Appointment, String)` .
- Método `IEWSClient.cancelAppointment(String, String)` .
- Método `IEWSClient.createAppointment(Appointment, String)` .
- Método `IEWSClient.createFolder(String, String, ExchangeFolderPermissionCollection, String)` .
- Método `IEWSClient.fetchAppointment(String, String)` .
- Método `IEWSClient.updateAppointment(Appointment, String)` .
- Propriedade `IEWSClient.CurrentCalendarFolderUri` .

O seguinte trecho de código mostra como adicionar um evento à pasta de calendário secundária no servidor exchange.



~~~Java
IEWSClient client = EWSClient.getEWSClient("https://outlook.office365.com/ews/exchange.asmx", "your.username", "your.Password");
try {
    try {
        // Crie um compromisso que será adicionado à pasta de calendário secundária

        Calendar c = Calendar.getInstance();
        c.set(Calendar.MINUTE, 0);
        c.set(Calendar.SECOND, 0);
        c.set(Calendar.MILLISECOND, 0);
        Date startTime = c.getTime();
        c.add(Calendar.HOUR_OF_DAY, 1);
        Date endTime = c.getTime();

        String timeZone = "America/New_York";

        Appointment[] listAppointments;
        Appointment appointment = new Appointment("Sala 121", startTime, endTime, MailAddress.to_MailAddress("from@domain.com"),
                MailAddressCollection.to_MailAddressCollection("attendee@domain.com"));
        appointment.setTimeZone(timeZone);
        appointment.setSummary("EMAILNET-35198 - " + UUID.randomUUID().toString());
        appointment.setDescription("EMAILNET-35198 Capacidade de adicionar evento ao Calendário Secundário do Office 365");

        // Verifique se a nova pasta foi criada
        ExchangeFolderInfoCollection calendarSubFolders = client.listSubFolders(client.getMailboxInfo().getCalendarUri());

        String getfolderName;
        String setFolderName = "Novo Calendário";
        boolean alreadyExits = false;

        // Verifique se a nova pasta foi criada, já existe ou não

        for (int i = 0; i < calendarSubFolders.size(); i++) {
            getfolderName = calendarSubFolders.get_Item(i).getDisplayName();

            if (getfolderName.equals(setFolderName)) {
                alreadyExits = true;
            }
        }

        if (alreadyExits) {
            System.out.println("Pasta Já Existe");
        } else {
            // Crie nova pasta de calendário
            client.createFolder(client.getMailboxInfo().getCalendarUri(), setFolderName, null, "IPF.Appointment");

            System.out.println(calendarSubFolders.size());

            // Obtenha o URI da pasta criada
            String newCalendarFolderUri = calendarSubFolders.get_Item(0).getUri();

            // api de compromisso com o uri da pasta de calendário
            // Criar
            client.createAppointment(appointment, newCalendarFolderUri);
            appointment.setLocation("Sala 122");
            // atualizar
            client.updateAppointment(appointment, newCalendarFolderUri);
            // listar
            listAppointments = client.listAppointments(newCalendarFolderUri);

            // listar pasta de calendário padrão
            listAppointments = client.listAppointments(client.getMailboxInfo().getCalendarUri());

            // Cancelar
            client.cancelAppointment(appointment, newCalendarFolderUri);
            listAppointments = client.listAppointments(newCalendarFolderUri);

            // api de compromisso com o contexto do uri atual da pasta de calendário
            client.setCurrentCalendarFolderUri(newCalendarFolderUri);
            // Criar
            client.createAppointment(appointment);
            appointment.setLocation("Sala 122");
            // atualizar
            client.updateAppointment(appointment);
            // listar
            listAppointments = client.listAppointments();

            // listar pasta de calendário padrão
            listAppointments = client.listAppointments(client.getMailboxInfo().getCalendarUri());

            // Cancelar
            client.cancelAppointment(appointment);
            listAppointments = client.listAppointments();

        }
    } finally {
    }
} finally {
    client.dispose();
}
~~~  
## **Compartilhando Convite de Calendário**
O servidor Microsoft Exchange fornece a capacidade de compartilhar calendários enviando convites de calendário para outros usuários, registrados no mesmo servidor Exchange. A API Aspose.Email fornece a mesma capacidade permitindo compartilhar o calendário usando a API EWS.



~~~Java
final IEWSClient client = EWSClient.getEWSClient("https://outlook.office365.com/ews/exchange.asmx", "testUser", "pwd", "domain");
try {
    // delegar permissão de acesso ao calendário
    ExchangeDelegateUser delegateUser = new ExchangeDelegateUser("sharingfrom@domain.com", ExchangeDelegateFolderPermissionLevel.NotSpecified);
    delegateUser.getFolderPermissions().setCalendarFolderPermissionLevel(ExchangeDelegateFolderPermissionLevel.Reviewer);
    client.delegateAccess(delegateUser, "sharingfrom@domain.com");

    // Criar convite
    MapiMessage mapiMessage = client.createCalendarSharingInvitationMessage("sharingfrom@domain.com");
    MailConversionOptions options = new MailConversionOptions();
    options.setConvertAsTnef(true);
    MailMessage mail = mapiMessage.toMailMessage(options);
    client.send(mail);
} finally {
    client.dispose();
}
~~~  
## **Recuperando Informações de Atributos Estendidos dos Itens do Calendário**
~~~Java
IEWSClient client = EWSClient.getEWSClient("https://exchange.office365.com/Exchange.asmx", "username", "password");

java.util.List<String> uriList = java.util.Arrays.asList(client.listItems(client.getMailboxInfo().getCalendarUri()));

// Defina o Descritor de Propriedade de Atributo Estendido para fins de pesquisa
// Neste caso, temos uma propriedade nomeada K1 Long para item de Calendário
UUID uuid = UUID.fromString("00020329-0000-0000-C000-000000000046");
PropertyDescriptor propertyDescriptor = new PidNamePropertyDescriptor("K1", PropertyDataType.Integer32, uuid);

java.util.List<PropertyDescriptor> propertyDescriptors = java.util.Arrays.asList(new PropertyDescriptor[] { propertyDescriptor });
IGenericList<MapiCalendar> mapiCalendarList = client.fetchMapiCalendar(uriList, propertyDescriptors);

for (MapiCalendar cal : mapiCalendarList) {
    for (MapiNamedProperty namedProperty : (Iterable<MapiNamedProperty>) cal.getNamedProperties().getValues()) {
        System.out.println(namedProperty.getNameId() + " = " + namedProperty.getInt32());
    }
}
~~~  