---
title: "Criar Solicitação de Compromisso em Rascunho"
url: /pt/java/create-draft-appointment-request/
weight: 40
type: docs
---

## **Aspose.Email - Criar Solicitação de Compromisso em Rascunho**  
Pode ser útil criar uma solicitação de compromisso no modo rascunho, de modo que as informações básicas sejam adicionadas e, em seguida, o mesmo compromisso em rascunho possa ser encaminhado para outros usuários que podem fazer alterações. Aspose.Email para Java oferece a flexibilidade de criar e salvar um compromisso em modo rascunho para uso posterior.  

Para salvar um compromisso em modo rascunho, a propriedade Method da classe Appointment deve ser definida como **Publish**.  

**Java**  

``` java  

 String sender = "test@gmail.com";  

String recipient = "test@email.com";  

MailMessage message = new MailMessage(sender, recipient, "", "");  

Calendar calendar = Calendar.getInstance(TimeZone.getTimeZone("GMT"));  

calendar.set(2012, Calendar.NOVEMBER, 1, 0, 0, 0);  

Date startDate = calendar.getTime();  

calendar.set(2012, Calendar.DECEMBER, 1);  

Date endDate = calendar.getTime();  

MailAddressCollection attendees = new MailAddressCollection();  

attendees.addMailAddress(new MailAddress("attendee_address@aspose.com", "Participante"));  

WeeklyRecurrencePattern expected = new WeeklyRecurrencePattern(3);  

Appointment app = new Appointment("Local do Compromisso", "Resumo do Compromisso", "Descrição do Compromisso",  

        startDate, endDate,  

        new MailAddress("organizer_address@aspose.com", "Organizador"), attendees, expected);  

//Definir o Compromisso como Rascunho  

app.setMethod(AppointmentMethodType.Publish);//.Method = AppointmentMethodType.Publish;  

message.addAlternateView(app.requestApointment());  

MapiMessage msg = MapiMessage.fromMailMessage(message);  

// Salvar o compromisso como rascunho.  

msg.save("data/AsposeDraft.msg");  

```  
## **Baixar Código em Execução**  
Baixe **Criar Solicitação de Compromisso em Rascunho** de qualquer um dos sites de codificação social mencionados abaixo:  

- [CodePlex](https://asposeapachepoi.codeplex.com/downloads/get/1381615)  
- [SourceForge](http://sourceforge.net/projects/asposeforapachepoi/files/Aspose.Email%20Features%20Not%20in%20Apache%20POI%20HSMF%20for%20Outlook/Create%20Draft%20Appointment%20Request%20%28Aspose.Email%29.zip/download)  
- [GitHub](https://github.com/asposemarketplace/Aspose_for_Apache_POI/releases/download/More-Features-in-Aspose.Email-v1.1/Create.Draft.Appointment.Request.Aspose.Email.zip)  
- [BitBucket](https://bitbucket.org/asposemarketplace/aspose-for-apache-poi/downloads/Create%20Draft%20Appointment%20Request%20\(Aspose.Email\).zip)  

{{% alert color="primary" %}}  

Para mais detalhes, visite [Criar uma Solicitação de Compromisso em Rascunho](/email/java/working-with-appointments/).  

{{% /alert %}}  