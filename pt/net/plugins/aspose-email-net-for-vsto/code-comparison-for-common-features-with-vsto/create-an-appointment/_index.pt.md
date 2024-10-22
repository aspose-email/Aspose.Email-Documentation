---
title: "Criar um Compromisso"
url: /pt/net/criar-um-compromisso/
weight: 20
type: docs
---


## **VSTO**
Abaixo está o trecho de código para criar e salvar um compromisso:

``` cs

   Outlook.AppointmentItem appt = Application.CreateItem(

  Outlook.OlItemType.olAppointmentItem) as Outlook.AppointmentItem;

  appt.Subject = "Conferência de Desenvolvedores";

  appt.AllDayEvent = true;

  appt.Start = DateTime.Parse("6/11/2007 12:00 AM");

  appt.End = DateTime.Parse("6/16/2007 12:00 AM");

  appt.Display(false);


```
## **Aspose.Email**
Os seguintes passos são necessários para criar um compromisso e salvá-lo no formato ICS.

1. Crie uma instância da classe Appointment e inicialize-a com este construtor.
1. Passe os seguintes argumentos no construtor acima 
   1. Participantes
   1. Descrição
   1. Data de Término
   1. Localização
   1. Organizador
   1. Data de Início
   1. Resumo
1. Chame o método Save() e especifique o nome do arquivo e o formato nos argumentos.

O compromisso pode ser aberto no Microsoft Outlook ou em qualquer programa que consiga carregar um arquivo ICS. Se o arquivo for aberto no Microsoft Outlook, ele adiciona automaticamente o compromisso no calendário do Outlook.

Os seguintes trechos de código criam e salvam um compromisso no disco no formato ICS.

``` cs

   string location = "Local do Encontro: Sala 5";

  DateTime startDate = new DateTime(1997, 3, 18, 18, 30, 00),

  endDate = new DateTime(1997, 3, 18, 19, 30, 00);

  MailAddress organizer = new MailAddress("aaa@amail.com", "Organizador");

  MailAddressCollection attendees = new MailAddressCollection();

  attendees.Add(new MailAddress("bbb@bmail.com", "Primeiro participante"));

  Appointment target = new Appointment(location, startDate, endDate, organizer, attendees);

  target.Save("savedFile.ics");


```
## **Baixar Código de Exemplo**
- [Codeplex](https://asposevsto.codeplex.com/releases/view/616980)
- [Github](https://github.com/aspose-email/Aspose.Email-for-.NET/releases/tag/AsposeEmailVsVSTOv1.1)
- [Code.MSDN](https://code.msdn.microsoft.com/AsposeEmail-Vs-VSTO-fa535977)
## **Baixar Código em Execução**
- [Codeplex](https://archive.codeplex.com/?p=asposevsto#Aspose.Email)
- [Github](https://github.com/aspose-email/Aspose.Email-for-.NET/tree/master/Plugins/Aspose.Email%20Vs%20VSTO%20Outlook/Code%20Comparison%20of%20Common%20Features/Criar%20um%20Compromisso)
- [Code.MSDN](https://code.msdn.microsoft.com/AsposeEmail-Vs-VSTO-fa535977/view/SourceCode#content)