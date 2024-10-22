---
title: "Trabalhando com Compromissos"
url: /pt/net/trabalhando-com-compromissos/
weight: 20
type: docs
---
## **Criar um Compromisso**

A [Classe Appointment](https://reference.aspose.com/email/net/aspose.email.calendar/appointment/) no Aspose.Email para .NET pode ser usada para criar um novo compromisso. Neste artigo, primeiro criamos um compromisso e o salvamos em um disco no formato ICS.

### **Criar um Compromisso e Salvar em um Disco no Formato MSG ou ICS**

Os seguintes passos são necessários para criar um compromisso e salvá-lo em um disco.

1. Crie uma instância da [Classe Appointment](https://reference.aspose.com/email/net/aspose.email.calendar/appointment/) e inicialize-a com este construtor.
1. Passe os seguintes argumentos no construtor acima:
   1. Localização
   1. Resumo
   1. Descrição
   1. Data de Início
   1. Data de Término
   1. Organizador
   1. Participantes
1. Chame o [método Save()](https://reference.aspose.com/email/net/aspose.email.calendar/appointment/save/#save/) e especifique o nome do arquivo e o formato nos argumentos.

O compromisso pode ser aberto no Microsoft Outlook ou em qualquer programa que possa carregar um arquivo ICS. Se o arquivo for aberto no Microsoft Outlook, ele automaticamente adiciona o compromisso ao calendário do Outlook.

O seguinte trecho de código mostra como criar e salvar um compromisso em um disco no formato ICS ou MSG.

```cs
// Para exemplos completos e arquivos de dados, acesse https://github.com/aspose-email/Aspose.Email-for-.NET

// Criar e inicializar uma instância da classe Appointment
Appointment appointment = new Appointment(
    "Sala de Reuniões 3 na Sede", // Localização
    "Reunião Mensal",             // Resumo
    "Por favor, confirme sua disponibilidade.", // Descrição
    new DateTime(2015, 2, 8, 13, 0, 0), // Data de início
    new DateTime(2015, 2, 8, 14, 0, 0), // Data de término
    "from@domain.com", // Organizador
    "attendees@domain.com"); // Participantes

// Salvar o compromisso no disco em formato ICS            
appointment.Save(fileName + ".ics", new AppointmentIcsSaveOptions());
Console.WriteLine("Compromisso criado e salvo no disco com sucesso.");

// Salvar o compromisso no disco em formato MSG
appointment.Save(fileName + ".msg", new AppointmentMsgSaveOptions(););
Console.WriteLine("Compromisso criado e salvo no disco com sucesso.");
```

### **Criar um Compromisso com Conteúdo HTML**

Você pode especificar representações alternativas da descrição do evento em diferentes tipos de conteúdo usando o cabeçalho X-ALT-DESC. Isso permite que os destinatários do arquivo iCalendar escolham a representação que melhor atende às suas necessidades. Por exemplo, você pode incluir uma descrição em texto simples usando o tipo de conteúdo "text/plain" e uma descrição HTML usando o tipo de conteúdo "text/html". O cabeçalho X-ALT-DESC é adicionado para cada representação alternativa. Para criar um compromisso com conteúdo HTML, defina a propriedade [HtmlDescription](https://reference.aspose.com/email/net/aspose.email.calendar/appointment/htmldescription/#appointmenthtmldescription-property).

Experimente o seguinte exemplo de código para criar um compromisso com uma descrição HTML alternativa:

1. Crie uma nova instância da classe Appointment.
2. Forneça os parâmetros necessários ao construtor da Appointment:
   - Especifique a localização do compromisso.
   - Defina a data e hora de início.
   - Defina a data e hora de término.
   - Especifique o organizador.
   - Especifique o participante.
3. Defina a propriedade [HtmlDescription](https://reference.aspose.com/email/net/aspose.email.calendar/appointment/htmldescription/#appointmenthtmldescription-property) do objeto compromisso, indicando que a descrição está no formato HTML.
4. Defina a propriedade Description do objeto compromisso como uma string formatada em HTML, encerrada dentro de uma string multilinha:
   - A marcação HTML inclui um bloco `<style>` definindo uma classe CSS chamada "text" com estilos de fonte.
   - O corpo HTML contém uma tag de parágrafo `<p>` com a classe CSS "text" e a mensagem de convite real.
5. O objeto compromisso agora está pronto, e você pode realizar operações adicionais ou salvá-lo como um arquivo iCalendar.

```cs
var appointment = new Appointment("Bygget 83",
    DateTime.UtcNow, // data de início
    DateTime.UtcNow.AddHours(1), // data de término
    new MailAddress("TintinStrom@from.com", "Tintin Strom"), // organizador
    new MailAddress("AinaMartensson@to.com", "Aina Martensson")) // participante
{
    HtmlDescription = @"
    <html>
     <style type=""text/css"">
      .text {
             font-family:'Comic Sans MS';
             font-size:16px;
            }
     </style>
    <body>
     <p class=""text"">Oi, estou feliz em convidá-lo para a nossa festa.</p>
    </body>
    </html>"
};
```
### **Criar um Pedido de Compromisso em Rascunho**

Foi mostrado em nossos artigos anteriores como criar e salvar um compromisso no formato ICS. Muitas vezes é necessário criar um pedido de Compromisso em modo Rascunho, para que as informações básicas sejam adicionadas e então o mesmo compromisso em rascunho seja encaminhado para outros usuários para as alterações necessárias de acordo com usos individuais. Para salvar um compromisso em modo Rascunho, a propriedade [MethodType](https://reference.aspose.com/email/net/aspose.email.calendar/appointment/methodtype/) da classe Appointment deve ser configurada como [AppointmentMethodType.Publish](https://reference.aspose.com/email/net/aspose.email.calendar/appointmentmethodtype/). O seguinte trecho de código mostra como criar um pedido de compromisso em rascunho.

```cs
string sender = "test@gmail.com";
string recipient = "test@email.com";

MailMessage message = new MailMessage(sender, recipient, string.Empty, string.Empty);

Appointment app = new Appointment(string.Empty, DateTime.Now, DateTime.Now, sender, recipient)
{
    MethodType = AppointmentMethodType.Publish
};

message.AddAlternateView(app.RequestApointment());

MapiMessage msg = MapiMessage.FromMailMessage(message);

// Salvar o compromisso como rascunho.
msg.Save(dstDraft);

Console.WriteLine(Environment.NewLine + "Rascunho salvo em " + dstDraft);
```

### **Criação de Compromisso em Rascunho a Partir de Texto**

O seguinte trecho de código mostra como criar um compromisso em rascunho a partir de Texto. 

```cs
string ical = @"BEGIN:VCALENDAR
METHOD:PUBLISH
PRODID:-//Aspose Ltd//iCalender Builder (v3.0)//EN
VERSION:2.0
BEGIN:VEVENT
ATTENDEE;CN=test@gmail.com:mailto:test@gmail.com
DTSTART:20130220T171439
DTEND:20130220T174439
DTSTAMP:20130220T161439Z
END:VEVENT
END:VCALENDAR";

string sender = "test@gmail.com";
string recipient = "test@email.com";
MailMessage message = new MailMessage(sender, recipient, string.Empty, string.Empty);
AlternateView av = AlternateView.CreateAlternateViewFromString(ical, new ContentType("text/calendar"));
message.AlternateViews.Add(av);
MapiMessage msg = MapiMessage.FromMailMessage(message);
msg.Save(dataDir + "draft_out.msg");
```

### **Definir o Status dos Participantes dos Convidados do Compromisso**

A API Aspose.Email para .NET permite que você defina o status dos participantes do compromisso ao formular uma mensagem de resposta. Isso adiciona a propriedade PARTSTAT ao arquivo ICS.

```cs
DateTime startDate = new DateTime(2011, 12, 10, 10, 12, 11),
         endDate = new DateTime(2012, 11, 13, 13, 11, 12);
MailAddress organizer = new MailAddress("aaa@amail.com", "Organizador");
MailAddressCollection attendees = new MailAddressCollection();
MailAddress attendee1 = new MailAddress("bbb@bmail.com", "Primeiro participante");
MailAddress attendee2 = new MailAddress("ccc@cmail.com", "Segundo participante");

attendee1.ParticipationStatus = ParticipationStatus.Accepted;
attendee2.ParticipationStatus = ParticipationStatus.Declined;
attendees.Add(attendee1);
attendees.Add(attendee2);

Appointment target = new Appointment(location, startDate, endDate, organizer, attendees);
```

### **Personalizar o Identificador do Produto para iCalendar**

A API Aspose.Email para .NET permite obter ou definir o identificador do produto que criou o objeto iCalendar.

```cs
string description = "Descrição do Teste";
Appointment app = new Appointment("localização", "compromisso teste", description, DateTime.Today,
DateTime.Today.AddDays(1), "first@test.com", "second@test.com");

IcsSaveOptions saveOptions = IcsSaveOptions.Default;
saveOptions.ProductId = "Test Corporation";
app.Save(dataDir + "ChangeProdIdOfICS.ics", saveOptions);
```

## **Carregar e Salvar um Compromisso no Formato ICS**

Além disso, a [Classe Appointment](https://reference.aspose.com/email/net/aspose.email.calendar/appointment/) pode ser usada para carregar um compromisso de um arquivo ICS.

### **Carregar um Compromisso em Formato ICS**

Para carregar um compromisso em formato ICS, os seguintes passos são necessários:

1. Crie uma instância da [Classe Appointment](https://reference.aspose.com/email/net/aspose.email.calendar/appointment/).
1. Chame o [método Load()](https://reference.aspose.com/email/net/aspose.email.calendar/appointment/load/#load/) fornecendo o caminho do arquivo ICS.
1. Leia qualquer propriedade para obter qualquer informação do compromisso (arquivo ICS).

O seguinte trecho de código mostra como carregar um compromisso em formato ICS.

```cs
// Carregar um Compromisso que acabou de ser criado e salvo em disco e exibir seus detalhes.
Appointment loadedAppointment = Appointment.Load(dstEmail);
Console.WriteLine(Environment.NewLine + "Os detalhes do Compromisso carregado são os seguintes:");
// Exibir as informações do compromisso na tela
Console.WriteLine("Resumo: " + loadedAppointment.Summary);
Console.WriteLine("Localização: " + loadedAppointment.Location);
Console.WriteLine("Descrição: " + loadedAppointment.Description);
Console.WriteLine("Data de início: " + loadedAppointment.StartDate);
Console.WriteLine("Data de término: " + loadedAppointment.EndDate);
Console.WriteLine("Organizador: " + appointment.Organizer);
Console.WriteLine("Participantes: " + appointment.Attendees);
Console.WriteLine(Environment.NewLine + "Compromisso carregado com sucesso de " + dstEmail);
```

### **Carregar e Converter um Arquivo ICS em Formato de Mensagem**

A API permite que você converta facilmente um Compromisso em um objeto de mensagem. O seguinte exemplo de código mostra como converter um pedido de compromisso em um MailMessage ou MapiMessage:

```cs
var appointment = Appointment.Load("appRequest.ics");

var eml = appointment.ToMailMessage();
var msg = appointment.ToMapiMessage();
```

## **Ler Múltiplos Eventos do Arquivo ICS**

```cs
List<Appointment> appointments = new List<Appointment>();
CalendarReader reader = new CalendarReader(dataDir + "US-Holidays.ics");

while (reader.NextEvent())
{
    appointments.Add(reader.Current);
}
// trabalhando com compromissos...
```

## **Escrever Múltiplos Eventos em um Arquivo ICS**

```cs
IcsSaveOptions saveOptions = new IcsSaveOptions();
saveOptions.Action = AppointmentAction.Create;
using (CalendarWriter writer = new CalendarWriter(dataDir + "WriteMultipleEventsToICS_out.ics", saveOptions))
{
    for (int i = 0; i < 10; i++)
    {
        Appointment app = new Appointment(string.Empty, DateTime.Now, DateTime.Now, "sender@domain.com", "receiver@domain.com");
        app.Description = "Corpo de teste " + i;
        app.Summary = "Resumo de teste:" + i;
        writer.Write(app);
    }
}
```

## **Determinar a Versão do Compromisso**

Para determinar a versão de um compromisso, você pode usar a propriedade [Appointment.Version](https://reference.aspose.com/email/net/aspose.email.calendar/appointment/version/#appointmentversion-property) da classe [Appointment](https://reference.aspose.com/email/net/aspose.email.calendar/appointment/#appointment-class). Esta propriedade ajuda a determinar qual versão seus arquivos são baseados, garantindo a integração com outros sistemas e aplicativos.

O seguinte exemplo de código mostra como implementar esta propriedade em seu projeto:

```cs
var app = Appointment.Load("meeting.ics");

if (app.Version == 1.0)
{
    // faça algo
}
```