---
title: "Lendo Mensagens de Email da Biblioteca de Documentos do Microsoft SharePoint"
url: /pt/net/lendo-mensagens-de-email-da-biblioteca-de-documentos-do-microsoft-sharepoint/
weight: 110
type: docs
---


Este artigo mostra como ler mensagens de email de uma biblioteca de documentos do Microsoft SharePoint. Para acessar arquivos em uma biblioteca de documentos do SharePoint, o SDK do SharePoint deve estar instalado no sistema. O SDK fornece a API necessária para fazer login e acessar arquivos da biblioteca de documentos.
## **Lendo Mensagens de Email do SharePoint**
Os exemplos de programação abaixo assumem que um arquivo de mensagem do Microsoft Outlook (.msg) já está armazenado na pasta SharedDocument da Biblioteca de Documentos do SharePoint. O SDK do SharePoint é usado para obter o arquivo de mensagem em um stream e, em seguida, passar esse stream para uma instância da classe [MailMessage](http://www.aspose.com/api/net/email/aspose.email/mailmessage) do Aspose.Email. A classe MailMessage carrega o stream e analisa o arquivo de mensagem do Outlook. Depois disso, acesse as propriedades da classe MailMessage, por exemplo, assunto, corpo do texto, corpo HTML etc., para usar as informações em um projeto do Visual Studio. Para informações sobre como instalar e configurar o Microsoft SharePoint Server e o SDK, consulte as seções respectivas na biblioteca MSDN. O seguinte trecho de código mostra como ler mensagens de email do SharePoint.



{{< gist "aspose-email" "9e8fbeb51a8cbc4129dc71ca8cd55f0b" "Examples-CSharp-LendoMensagensDeEmailDoSharePoint-LendoMensagensDeEmailDoSharePoint.cs" >}}