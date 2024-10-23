---
title: "Trabalhando com Mensagens do Servidor IMAP"
url: /pt/net/trabalhando-com-mensagens-do-servidor-imap/
weight: 20
type: docs
---

## **Obtendo as informações de identificação para mensagens recebidas de uma caixa de correio**

Ao recuperar e processar mensagens de e-mail, você pode buscar os detalhes dessas mensagens usando seus números de sequência.
Os seguintes recursos são utilizados para interagir com uma caixa de correio IMAP:

- `Aspose.Email.MailboxInfo` class - Representa informações de identificação sobre a mensagem em uma caixa de correio.

    - `Aspose.Email.MailboxInfo.SequenceNumber` property - O número de sequência de uma mensagem.

    - `Aspose.Email.MailboxInfo.UniqueId` property - O id único de uma mensagem.

- `Aspose.Email.MailMessage.ItemId` property - Representa informações de identificação sobre a mensagem em uma caixa de correio.

O exemplo de código abaixo mostra como obter informações de identificação sobre mensagens:

```cs
using (var client = new ImapClient(imapHost, port, emailAddress, password, securityOption))
{
    var msgs = client.ListMessages("INBOX").Take(5);
    var seqIds = msgs.Select(t => t.SequenceNumber);
    var msgsViaFetch = client.FetchMessages(seqIds);
	
    for (var i = 0; i < 5; i++)
    {
        var thisMsg = msgsViaFetch[i];
        Console.WriteLine($"Message ID:{seqIds.ElementAt(i)} SequenceNumber: {thisMsg.ItemId.SequenceNumber} Subject:{thisMsg.Subject}");
    }
}
```

## **Listando IDs de Mensagens MIME do Servidor**

[ImapMessageInfo](https://reference.aspose.com/email/net/aspose.email.clients.imap/imapmessageinfo/) fornece o MIME [MessageId](https://reference.aspose.com/email/net/aspose.email.clients/messageinfobase/messageid/) para identificação de mensagens sem extrair a mensagem completa. O seguinte exemplo de código mostra como listar o messageId MIME.

{{< gist "aspose-com-gists" "6e5185a63aec6fd70d83098e82b06a32" "Examples-CSharp-IMAP-ListingMIMEMessageIdInImapMessageInfo-ListingMIMEMessageIdInImapMessageInfo.cs" >}}

## **Listando Mensagens do Servidor**

Aspose.Email fornece uma variante sobrecarregada de 2 membros do [ListMessages()](https://reference.aspose.com/email/net/aspose.email.clients.imap/imapclient/listmessages/#listmessages_12) para recuperar um número específico de mensagens com base em uma consulta. O seguinte exemplo de código mostra como listar Mensagens.

{{< gist "aspose-com-gists" "6e5185a63aec6fd70d83098e82b06a32" "Examples-CSharp-ListMessagesWithMaximumNumberOfMessages-ListMessagesWithMaximumNumberOfMessages.cs" >}}

## **Listando Mensagens do Servidor Recursivamente**

O protocolo IMAP suporta listar mensagens recursivamente de uma pasta de caixa de correio. Isso ajuda a listar mensagens de subpastas de uma pasta também. O seguinte exemplo de código mostra como listar mensagens recursivamente.

{{< gist "aspose-com-gists" "6e5185a63aec6fd70d83098e82b06a32" "Examples-CSharp-IMAP-ListingMessagesRecursively-ListingMessagesRecursively.cs" >}}

## **Listando Mensagens com MultiConnection**

[ImapClient](https://reference.aspose.com/email/net/aspose.email.clients.imap/imapclient/) fornece uma propriedade [UseMultiConnection](https://reference.aspose.com/email/net/aspose.email.clients/emailclient/usemulticonnection/) que pode ser usada para criar várias conexões para operações pesadas. Você também pode definir o número de conexões a serem usadas durante o modo de multi-conexão usando [ImapClient.ConnectionsQuantity](https://reference.aspose.com/email/net/aspose.email.clients/emailclient/connectionsquantity/). O seguinte exemplo de código demonstra o uso do modo multi-conexão para listar mensagens e compara seu desempenho com o modo de conexão única.

{{< gist "aspose-com-gists" "522d47278b8ca448dc1d7eb97193322c" "Examples-CSharp-IMAP-ImapListMessagesWithMultiConnection-1.cs" >}}

{{% alert color="primary" %}} 

Por favor, note que o uso do modo de multi-conexão não garante aumento de desempenho.

{{% /alert %}} 

## **Obter Mensagens em ordem decrescente**

Aspose.Email fornece o método [`ImapClient.ListMessagesByPage`](https://reference.aspose.com/email/net/aspose.email.clients.imap/imapclient/listmessagesbypage/#listmessagesbypage/) que lista mensagens com suporte para paginação. Algumas sobrecargas de [`ImapClient.ListMessagesByPage`](https://reference.aspose.com/email/net/aspose.email.clients.imap/imapclient/listmessagesbypage/#listmessagesbypage/) aceitam [`PageSettings`](https://reference.aspose.com/email/net/aspose.email.clients.imap/pagesettings/) como parâmetro. [`PageSettings`](https://reference.aspose.com/email/net/aspose.email.clients.imap/pagesettings/) fornece uma propriedade [`AscendingSorting`](https://reference.aspose.com/email/net/aspose.email.clients.imap/pagesettings/ascendingsorting/) que, quando definida como **false**, retorna e-mails em ordem decrescente.

O seguinte código de exemplo demonstra o uso da propriedade [AscendingSorting](https://reference.aspose.com/email/net/aspose.email.clients.imap/pagesettings/ascendingsorting/) da classe [PageSettings](https://reference.aspose.com/email/net/aspose.email.clients.imap/pagesettings/) para alterar a ordem dos e-mails.

{{< gist "aspose-com-gists" "522d47278b8ca448dc1d7eb97193322c" "Examples-CSharp-IMAP-ChangeOrderOfEmails-1.cs" >}}

## **Buscar Mensagens do Servidor e Salvar no disco**

A classe [ImapClient](https://reference.aspose.com/email/net/aspose.email.clients.imap/imapclient/) pode buscar mensagens de um servidor IMAP e salvar as mensagens no formato EML em um disco local. Os seguintes passos são necessários para salvar as mensagens no disco:

1. Crie uma instância da classe [ImapClient](https://reference.aspose.com/email/net/aspose.email.clients.imap/imapclient/).
2. Especifique um hostname, porta, nome de usuário e senha no construtor do ImapClient [constructor](https://reference.aspose.com/email/net/aspose.email.clients.imap/imapclient/imapclient/#constructor).
3. Selecione a pasta usando o método [SelectFolder()](https://reference.aspose.com/email/net/aspose.email.clients.imap/imapclient/selectfolder/#selectfolder/).
4. Chame o método [ListMessages](https://reference.aspose.com/email/net/aspose.email.clients.imap/imapclient/listmessages/#listmessages) para obter o objeto [ImapMessageInfoCollection](https://reference.aspose.com/email/net/aspose.email.clients.imap/imapmessageinfocollection/).
5. Itere pela coleção [ImapMessageInfoCollection](https://reference.aspose.com/email/net/aspose.email.clients.imap/imapmessageinfocollection/), chame o método [SaveMessage()](https://reference.aspose.com/email/net/aspose.email.clients.imap/imapclient/savemessage/#savemessage/) e forneça o caminho de saída e o nome do arquivo.

O seguinte exemplo de código mostra como buscar mensagens de e-mail de um servidor e salvá-las.

{{< gist "aspose-com-gists" "6e5185a63aec6fd70d83098e82b06a32" "Examples-CSharp-IMAP-FetchEmailMessagesFromIMAPServer-FetchEmailMessagesFromIMAPServer.cs" >}}

## **Salvando Mensagens no Formato MSG**

[No exemplo acima](#fetch-messages-from-server-and-save-to-disc), os e-mails são salvos no formato EML. Para salvar e-mails no formato MSG, o método [ImapClient.FetchMessage()](https://reference.aspose.com/email/net/aspose.email.clients.imap/imapclient/fetchmessage/#fetchmessage/) precisa ser chamado. Ele retorna a mensagem em uma instância da classe [MailMessage](https://reference.aspose.com/email/net/aspose.email/mailmessage/). O método [MailMessage.Save()](https://reference.aspose.com/email/net/aspose.email/mailmessage/save/#save/) pode então ser chamado para salvar a mensagem em MSG. O seguinte exemplo de código mostra como salvar mensagens no formato MSG.

{{< gist "aspose-com-gists" "6e5185a63aec6fd70d83098e82b06a32" "Examples-CSharp-IMAP-SavingMessagesFromIMAPServer-SavingMessagesFromIMAPServer.cs" >}}

## **Busca em Grupo de Mensagens**

[ImapClient](https://reference.aspose.com/email/net/aspose.email.clients.imap/imapclient/) fornece um método [FetchMessages](https://reference.aspose.com/email/net/aspose.email.clients.imap/imapclient/fetchmessages/#fetchmessages/) que aceita um iterável de Números de Sequência ou ID Único e retorna uma lista de [MailMessage](https://reference.aspose.com/email/net/aspose.email/mailmessage/). O seguinte exemplo de código demonstra o uso do método [FetchMessages](https://reference.aspose.com/email/net/aspose.email.clients.imap/imapclient/fetchmessages/#fetchmessages/) para buscar mensagens por Números de Sequência e ID Único.

{{< gist "aspose-com-gists" "522d47278b8ca448dc1d7eb97193322c" "Examples-CSharp-IMAP-ImapFetchGroupMessages-1.cs" >}}


## **Listando Mensagens com Suporte a Paginação**

Em cenários onde o servidor de e-mail contém um grande número de mensagens na caixa de correio, muitas vezes é desejado listar ou recuperar as mensagens com suporte a paginação. A API Aspose.Email [ImapClient](https://reference.aspose.com/email/net/aspose.email.clients.imap/imapclient/) permite recuperar as mensagens do servidor com suporte a paginação.

{{< gist "aspose-com-gists" "6e5185a63aec6fd70d83098e82b06a32" "Examples-CSharp-IMAP-ListingMessagesWithPagingSupport-ListingMessagesWithPagingSupport.cs" >}}

## **Listando os Anexos da Mensagem** 

Para obter informações sobre anexos, como nome e tamanho, sem buscar os dados do anexo, tente as seguintes APIs:

- *Aspose.Email.Clients.Imap.ImapAttachmentInfo* - Representa informações de um anexo. 
- *Aspose.Email.Clients.Imap.ImapAttachmentInfoCollection* - Representa uma coleção da classe [ImapAttachmentInfo](https://reference.aspose.com/email/net/aspose.email.clients.imap/imapattachmentinfo/). 
- *Aspose.Email.Clients.Imap.ListAttachments(int sequenceNumber)* - Obtém informações para cada anexo em uma mensagem.

O exemplo de código com os passos abaixo mostrará como usar as APIs:

1. Chame o método [ListMessages()](https://reference.aspose.com/email/net/aspose.email.clients.imap/imapclient/listmessages/) no objeto imapClient. Este método retornará um ImapMessageInfoCollection contendo informações sobre as mensagens na caixa de correio.
2. Itere através de cada mensagem na messageInfoCollection usando um loop foreach.
3. Chame o método [ListAttachments()](https://reference.aspose.com/email/net/aspose.email.clients.imap/imapclient/listattachments/#imapclientlistattachments-method) no objeto imapClient, passando a propriedade SequenceNumber do objeto de mensagem como parâmetro. Este método retornará uma ImapAttachmentInfoCollection contendo informações sobre os anexos na mensagem.
4. Itere através de cada anexo na attachmentInfoCollection usando um loop foreach.
5. Dentro do loop interno, você pode acessar as informações sobre cada anexo usando as propriedades do objeto attachmentInfo. Neste exemplo, o nome e o tamanho de cada anexo são registrados no console usando `Console.WriteLine()`.
   
   `Console.WriteLine("Attachment: {0} (size: {1})", attachmentInfo.Name, attachmentInfo.Size);`
```cs
var messageInfoCollection = imapClient.ListMessages();
    
foreach (var message in messageInfoCollection)
{
    var attachmentInfoCollection = imapClient.ListAttachments(message.SequenceNumber);

    foreach (var attachmentInfo in attachmentInfoCollection)
    {
        Console.WriteLine("Attachment: {0} (size: {1})", attachmentInfo.Name, attachmentInfo.Size);
    }
}
```

## **Obtendo Pastas e Lendo Mensagens Recursivamente**

Neste artigo, a maioria dos recursos do [ImapClient](https://reference.aspose.com/email/net/aspose.email.clients.imap/imapclient/) são usados para criar um aplicativo que lista todas as pastas e subpastas recursivamente de um servidor IMAP. Ele também salva as mensagens em cada pasta e subpasta em formato MSG em um disco local. No disco, pastas e mensagens são criadas e salvas na mesma estrutura hierárquica que no servidor IMAP. O seguinte exemplo de código mostra como obter as mensagens e as informações das subpastas recursivamente.

{{< gist "aspose-com-gists" "6e5185a63aec6fd70d83098e82b06a32" "Examples-CSharp-IMAP-ReadMessagesRecursively-ReadMessagesRecursively.cs" >}}

## **Recuperando Parâmetros Extras como Informações Resumidas**

{{< gist "aspose-com-gists" "6e5185a63aec6fd70d83098e82b06a32" "Examples-CSharp-IMAP-RetrieveExtraParameters-RetrieveExtraParametersAsSummaryInformation.cs" >}}

## **Obtendo Informações do Cabeçalho List-Unsubscribe**

O cabeçalho List-Unsubscribe contém a URL para se descadastrar de listas de e-mail, como anúncios, boletins informativos, etc. Para obter o cabeçalho List-Unsubscribe, use a propriedade [ListUnsubscribe](https://reference.aspose.com/email/net/aspose.email.clients/messageinfobase/listunsubscribe/) da classe [ImapMessageInfo](https://reference.aspose.com/email/net/aspose.email.clients.imap/imapmessageinfo/). O seguinte exemplo mostra o uso da propriedade [ListUnsubscribe](https://reference.aspose.com/email/net/aspose.email.clients/messageinfobase/listunsubscribe/) para obter o cabeçalho List-Unsubscribe.

{{< gist "aspose-com-gists" "522d47278b8ca448dc1d7eb97193322c" "Examples-CSharp-IMAP-GetListUnsubscribeHeader-1.cs" >}}