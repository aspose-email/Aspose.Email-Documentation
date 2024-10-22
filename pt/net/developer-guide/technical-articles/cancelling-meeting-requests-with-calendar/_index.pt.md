---
title: "Cancelando Solicitações de Reunião com o Calendário"
url: /pt/net/cancelling-meeting-requests-with-calendar/
weight: 270
type: docs
---


Você pode enviar uma solicitação de cancelamento de reunião com Aspose.Email usando o objeto da classe Appointment. Você precisa ter as informações da solicitação de reunião original para cancelar a solicitação. O exemplo deste artigo primeiro envia uma solicitação de reunião, salva as informações em um banco de dados e, em seguida, cancela a solicitação com base no ID da mensagem.
## **Enviando Solicitações de Reunião**
Antes que possamos [cancelar solicitações de reunião](#cancelling-meeting-request), precisamos enviar algumas:

1. Primeiro, crie uma instância do tipo SmtpClient para enviar a mensagem.
1. Para reunir informações dos participantes, criamos uma grade de dados para que os usuários possam inserir os nomes e endereços das pessoas para as quais o convite deve ser enviado.
1. Depois de fazer um loop for-each na coleção Rows da grade, salve todas as informações dos participantes na coleção MailAddressCollection.
1. Crie uma instância da classe MailMessage e as propriedades necessárias, como De, Para e Assunto.
1. Crie uma instância do tipo Appointment e forneça informações sobre o local, hora de início, hora de término, organizadores e participantes.
1. Salve todas as informações em um banco de dados SQL Server. O trabalho relacionado ao DB está sendo feito no método SaveIntoDB.

O seguinte trecho de código mostra como enviar solicitações de reunião.



{{< gist "aspose-email" "9e8fbeb51a8cbc4129dc71ca8cd55f0b" "Examples-CSharp-Knowledge-Base-SendMeetingRequests-SendMeetingRequests.cs" >}}
## **Cancelando Solicitação de Reunião**
Para cancelar uma solicitação de reunião, primeiro obtenha o ID da mensagem de email. Como salvamos essa informação em um banco de dados para este exemplo, podemos facilmente obtê-la novamente. Usamos uma grade para carregar todas as mensagens enviadas. A captura de tela do formulário é a seguinte: 

![todo:image_alt_text](cancelling-meeting-requests-with-calendar_1.png)

1. Selecionando a linha para a qual enviar a solicitação de cancelamento.
1. Clique em **Enviar Solicitação de Cancelamento** para enviar a solicitação.
1. O código obtém o ID da linha selecionada da grade e consulta o banco de dados para obter as informações relacionadas aos participantes, mensagem e calendário.
1. Crie instâncias da classe Calendar e da classe [MailMessage](https://apireference.aspose.com/email/net/aspose.email/mailmessage) usando as informações recuperadas do banco de dados.
1. Use o método Appointment.CancelAppointment() para enviar a solicitação de cancelamento.
1. Envie o email usando o [SMTP](https://apireference.aspose.com/email/net/aspose.email.clients.smtp/smtpclient).

O seguinte trecho de código mostra como cancelar a solicitação de reunião.



{{< gist "aspose-email" "9e8fbeb51a8cbc4129dc71ca8cd55f0b" "Examples-CSharp-Knowledge-Base-CancelMeetingRequest-CancelMeetingRequest.cs" >}}