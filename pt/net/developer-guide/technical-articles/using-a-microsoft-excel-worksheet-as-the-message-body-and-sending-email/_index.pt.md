---
title: "Usando uma Planilha do Microsoft Excel como o Corpo da Mensagem e Enviando Email"
url: /pt/net/using-a-microsoft-excel-worksheet-as-the-message-body-and-sending-email/
weight: 160
type: docs
---

Este artigo usa uma pasta de trabalho do Microsoft Excel como o corpo do email e a envia para os destinatários. Aspose.Email para .NET lida com protocolos de rede e recursos do Microsoft Outlook e não consegue manipular pastas de trabalho do Microsoft Excel. Para superar isso, os exemplos neste artigo usam Aspose.Cells para .NET para carregar a pasta de trabalho do Excel e convertê-la em um fluxo HTML. Aspose.Email para .NET, então, utiliza o fluxo HTML no corpo do email. O exemplo de programação mostra como enviar uma planilha do Excel como corpo do email usando Aspose.Cells para .NET e Aspose.Email para .NET.

1. Carregar uma Pasta de Trabalho do Microsoft Excel usando a classe Workbook do Aspose.Cells
1. Salvar a pasta de trabalho carregada em MemoryStream no formato HTML
1. Obter o HTML do fluxo como String
1. Definir um novo objeto MailMessage e definir seu HtmlBody para o conteúdo HTML do passo 3
1. Enviar o email usando a classe SmtpClient do Aspose.Email para .NET

A pasta de trabalho do Excel de origem pode ser vista como segue:

![todo:image_alt_text](using-a-microsoft-excel-worksheet-as-the-message-body-and-sending-email_1.png)

Quando a mensagem foi enviada e recebida no Microsoft Outlook, ela se parece com a mensagem abaixo:

![todo:image_alt_text](using-a-microsoft-excel-worksheet-as-the-message-body-and-sending-email_2.png)

O seguinte trecho de código mostra como enviar uma Planilha do MS Excel como o Corpo da Mensagem e Enviar Email.

{{< gist "aspose-email" "9e8fbeb51a8cbc4129dc71ca8cd55f0b" "Examples-CSharp-Knowledge-Base-SendExcelWorksheetAsMessageBody-SendExcelWorksheetAsMessageBody.cs" >}}