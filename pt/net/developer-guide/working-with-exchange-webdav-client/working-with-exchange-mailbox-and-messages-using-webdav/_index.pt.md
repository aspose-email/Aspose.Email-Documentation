---
title: "Trabalhando com Caixa de Correio e Mensagens do Exchange usando WebDav"
url: /pt/net/trabalhando-com-caixa-de-correio-e-mensagens-do-exchange-usando-webdav/
weight: 20
type: docs
---


## **Obtendo Informações da Caixa de Correio usando WebDav**
A classe [ExchangeClient](https://apireference.aspose.com/net/email/aspose.email.clients.exchange.dav/exchangeclient) tem membros que podem ser usados para obter informações da caixa de correio de um servidor Exchange chamando o método [ExchangeClient.GetMailboxInfo()](https://apireference.aspose.com/net/email/aspose.email.clients.exchange.dav/exchangeclient/methods/getmailboxinfo/index). Ele retorna uma instância do tipo [ExchangeMailboxInfo](https://apireference.aspose.com/net/email/aspose.email.clients.exchange/exchangemailboxinfo). Obtenha informações da caixa de correio a partir de propriedades como [MailboxUri](https://apireference.aspose.com/net/email/aspose.email.clients.exchange/exchangemailboxinfo/properties/mailboxuri), [InboxUri](https://apireference.aspose.com/net/email/aspose.email.clients.exchange/exchangemailboxinfo/properties/inboxuri) e [DraftsUri](https://apireference.aspose.com/net/email/aspose.email.clients.exchange/exchangemailboxinfo/properties/draftsuri). Este artigo mostra como acessar informações da caixa de correio diretamente de um servidor Exchange.

Para obter as informações da caixa de correio do Exchange:

1. Crie uma instância da classe [ExchangeClient](https://apireference.aspose.com/net/email/aspose.email.clients.exchange.dav/exchangeclient).
1. Especifique o servidor Exchange, nome de usuário, senha e domínio no construtor da classe [ExchangeClient](https://apireference.aspose.com/net/email/aspose.email.clients.exchange.dav/exchangeclient).
1. Chame o método [ExchangeClient.GetMailboxSize()](https://apireference.aspose.com/net/email/aspose.email.clients.exchange.dav/exchangeclient/methods/getmailboxsize/index) para obter o tamanho da caixa de correio.
1. Chame o método [ExchangeClient.GetMailboxInfo()](https://apireference.aspose.com/net/email/aspose.email.clients.exchange.dav/exchangeclient/methods/getmailboxinfo/index) para obter uma instância da classe [ExchangeMailboxInfo](https://apireference.aspose.com/net/email/aspose.email.clients.exchange/exchangemailboxinfo).
1. Obtenha as informações da caixa de correio usando as diferentes propriedades da classe [ExchangeMailboxInfo](https://apireference.aspose.com/net/email/aspose.email.clients.exchange/exchangemailboxinfo).

O seguinte trecho de código mostra como obter informações da caixa de correio do Exchange.



{{< gist "aspose-com-gists" "6e5185a63aec6fd70d83098e82b06a32" "Examples-CSharp-Exchange_WebDav-GetMailboxInformationFromExchangeServer-GetMailboxInformationFromExchangeServer.cs" >}}
## **Enviando Mensagens de Email**
Você pode enviar mensagens de email usando um servidor Exchange com a ajuda das ferramentas do Aspose.Email.Exchange. O método [ExchangeClient.Send()](https://apireference.aspose.com/net/email/aspose.email.clients.exchange.dav/exchangeclient/methods/send) aceita uma instância de [MailMessage](https://apireference.aspose.com/net/email/aspose.email/mailmessage) como parâmetro e envia o email. Este artigo explica como enviar mensagens de email usando um servidor Exchange.
### **Enviando Mensagens de Email Usando o Servidor Exchange**
Para enviar emails usando um servidor Exchange:

1. Crie uma instância da classe [ExchangeClient](https://apireference.aspose.com/net/email/aspose.email.clients.exchange.dav/exchangeclient).
1. Especifique o nome do servidor, nome de usuário, senha e domínio.
1. Crie uma instância da classe [MailMessage](https://apireference.aspose.com/net/email/aspose.email/mailmessage).
1. Especifique os campos de de, para, assunto e outras propriedades da [MailMessage](https://apireference.aspose.com/net/email/aspose.email/mailmessage).
1. Chame o método [ExchangeClient.Send()](https://apireference.aspose.com/net/email/aspose.email.clients.exchange.dav/exchangeclient/methods/send) para enviar o email.

O seguinte trecho de código mostra como enviar mensagens de email usando o servidor Exchange.



{{< gist "aspose-com-gists" "6e5185a63aec6fd70d83098e82b06a32" "Examples-CSharp-Exchange_WebDav-SendEmailMessagesUsingExchangeServer-SendEmailMessagesUsingExchangeServer.cs" >}}
## **Lendo Emails da Caixa de Correio de Outro Usuário**
Algumas contas em servidores Exchange possuem o direito de acessar múltiplas caixas de correio, e alguns usuários têm múltiplas contas de email no mesmo servidor Exchange. Em ambos os casos, os usuários podem acessar as caixas de correio de outros usuários usando Aspose.Email para .NET. Esta API fornece um mecanismo para acessar pastas e emails de outras caixas de correio usando a classe [ExchangeClient](https://apireference.aspose.com/net/email/aspose.email.clients.exchange.dav/exchangeclient). Essa funcionalidade pode ser alcançada usando o método sobrecarregado [GetMailboxInfo()](https://apireference.aspose.com/net/email/aspose.email.clients.exchange.dav/exchangeclient/methods/getmailboxinfo/index) e fornecendo o endereço de email do usuário como parâmetro.

O seguinte trecho de código mostra como usar a classe [ExchangeClient](https://apireference.aspose.com/net/email/aspose.email.clients.exchange.dav/exchangeclient) para acessar outra caixa de correio.



{{< gist "aspose-com-gists" "6e5185a63aec6fd70d83098e82b06a32" "Examples-CSharp-Exchange_WebDav-AccessAnotherMailboxUsingExchangeClient-AccessAnotherMailboxUsingExchangeClient.cs" >}}
## **Listando Mensagens**
Uma lista das mensagens de email em uma caixa de correio do Exchange pode ser obtida chamando o método [ExchangeClient.ListMessages](https://apireference.aspose.com/net/email/aspose.email.clients.exchange.dav/exchangeclient/methods/listmessages/index). Obtenha as informações básicas sobre as mensagens, como assunto, de, para e ID da mensagem, usando o método [ListMessages](https://apireference.aspose.com/net/email/aspose.email.clients.exchange.dav/exchangeclient/methods/listmessages/index).
### **Listagem Simples de Mensagens**
Para listar as mensagens em uma caixa de correio do Exchange:

1. Crie uma instância da classe [ExchangeClient](https://apireference.aspose.com/net/email/aspose.email.clients.exchange.dav/exchangeclient).
1. Chame o método [ListMessages](https://apireference.aspose.com/net/email/aspose.email.clients.exchange.dav/exchangeclient/methods/listmessages/index) e crie uma coleção de mensagens.
1. Percorra a coleção e exiba as informações das mensagens.

O seguinte trecho de código mostra como se conectar à caixa de correio do Exchange e obter uma lista de mensagens da pasta de entrada.



{{< gist "aspose-com-gists" "6e5185a63aec6fd70d83098e82b06a32" "Examples-CSharp-Exchange_WebDav-ListExchangeServerMessages-ListExchangeServerMessages.cs" >}}
### **Listando Mensagens de Pastas Diferentes**
Os trechos de código acima listam todas as mensagens na pasta de Entrada. É possível obter a lista de mensagens de outras pastas também. O método [ExchangeClient.ListMessages()](https://apireference.aspose.com/net/email/aspose.email.clients.exchange.dav/exchangeclient/methods/listmessages/index) aceita um URI de pasta como parâmetro. Enquanto o URI da pasta for válido, você pode obter a lista de mensagens daquela pasta. Use a propriedade ExchangeClient.MailboxInfo.xxxFolderUri para obter o URI de diferentes pastas. O restante do código é o mesmo para obter uma lista de mensagens. O seguinte trecho de código mostra como listar mensagens de pastas diferentes usando [ExchangeClient](https://apireference.aspose.com/net/email/aspose.email.clients.exchange.dav/exchangeclient).



{{< gist "aspose-com-gists" "6e5185a63aec6fd70d83098e82b06a32" "Examples-CSharp-Exchange_WebDav-ListMessagesFromDifferentFolders-ListMessagesFromDifferentFolders.cs" >}}
### **Listando Mensagens por ID**
O trecho de código acima usou o método [ListMessages](https://apireference.aspose.com/net/email/aspose.email.clients.exchange.dav/exchangeclient/methods/listmessages/index) para listar todas as mensagens em uma pasta de caixa de correio do servidor Exchange especificada. Se você souber o ID da mensagem de antemão, pode obter a mensagem usando o método [ListMessagesbyId()](https://apireference.aspose.com/net/email/aspose.email.clients.exchange.dav/exchangeclient/methods/listmessagesbyid). Para obter a mensagem, passe o URI da pasta e o ID da mensagem. Esse cenário é útil quando você já conhece o ID da mensagem, por exemplo, quando os IDs das mensagens são salvos no banco de dados. O seguinte trecho de código mostra como listar mensagens por ID.



{{< gist "aspose-com-gists" "6e5185a63aec6fd70d83098e82b06a32" "Examples-CSharp-Exchange_WebDav-ListMessagesByID-ListMessagesByID.cs" >}}
## **Salvando Mensagens**
Este tópico mostra como obter mensagens de uma caixa de correio do servidor Exchange e salvá-las em disco nos formatos EML e MSG:

- Salvar como EML no disco.
- Salvar em um stream de memória.
- Salvar como MSG.
### **Salvando Mensagens em EML**
Para obter mensagens e salvar no formato EML:

1. Crie uma instância da classe [ExchangeClient](https://apireference.aspose.com/net/email/aspose.email.clients.exchange.dav/exchangeclient).
1. Forneça o nome do servidor, nome de usuário, senha e domínio.
1. Chame o método [ExchangeClient.ListMessages()](https://apireference.aspose.com/net/email/aspose.email.clients.exchange.dav/exchangeclient/methods/listmessages/index) para obter uma instância da coleção [ExchangeMessagesInfoCollection](https://apireference.aspose.com/net/email/aspose.email.clients.exchange/exchangemessageinfocollection).
1. Percorra a coleção [ExchangeMessagesInfoCollection](https://apireference.aspose.com/net/email/aspose.email.clients.exchange/exchangemessageinfocollection) para obter o URI exclusivo de cada mensagem.
1. Chame o método [ExchangeClient.SaveMessage()](https://apireference.aspose.com/net/email/aspose.email.clients.exchange.dav/exchangeclient/methods/savemessage/index) e passe o URI exclusivo como parâmetro.
1. Forneça ao método [SaveMessage()](https://apireference.aspose.com/net/email/aspose.email.clients.exchange.dav/exchangeclient/methods/savemessage/index) um caminho para onde você deseja salvar o arquivo.

O seguinte trecho de código mostra como salvar mensagens em EML.



{{< gist "aspose-com-gists" "6e5185a63aec6fd70d83098e82b06a32" "Examples-CSharp-Exchange_WebDav-ExchangeClientSaveMessagesInEMLFormat-ExchangeClientSaveMessagesInEMLFormat.cs" >}}
### **Salvando Mensagens em um Stream de Memória**
Em vez de salvar arquivos EML no disco, é possível salvá-los em um stream de memória. Isso é útil quando você deseja salvar o stream em algum local de armazenamento, como um banco de dados. Uma vez que o stream tenha sido salvo em um banco de dados, você pode recarregar o arquivo EML na classe [MailMessage](https://apireference.aspose.com/net/email/aspose.email/mailmessage). O seguinte trecho de código mostra como salvar mensagens de uma caixa de correio do servidor Exchange em um stream de memória.



{{< gist "aspose-com-gists" "6e5185a63aec6fd70d83098e82b06a32" "Examples-CSharp-Exchange_WebDav-SaveMessagesToMemoryStream-SaveMessagesToMemoryStream.cs" >}}
### **Salvando Mensagens em Formato MSG**
O método [ExchangeClient.SaveMessage()](https://apireference.aspose.com/email/net/aspose.email.clients.exchange.dav/exchangeclient/methods/savemessage/index) pode salvar diretamente a mensagem no formato EML. Para salvar as mensagens no formato MSG, primeiro, chame o método [ExchangeClient.fetchMessage()](https://apireference.aspose.com/email/net/aspose.email.clients.exchange.dav/exchangeclient/methods/fetchmessage) que retorna uma instância da classe [MailMessage](https://apireference.aspose.com/email/net/aspose.email/mailmessage). Em seguida, chame o método [MailMessage.Save()](https://apireference.aspose.com/email/net/aspose.email/mailmessage/methods/save/index) para salvar a mensagem como MSG. O seguinte trecho de código mostra como obter mensagens de uma caixa de correio do servidor Exchange e salvá-las no formato MSG.



{{< gist "aspose-com-gists" "6e5185a63aec6fd70d83098e82b06a32" "Examples-CSharp-Exchange_WebDav-SaveMessagesInMSGFormatExchangeClient-SaveMessagesInMSGFormatExchangeClient.cs" >}}
## **Buscar Mensagens de uma Caixa de Correio do Servidor Exchange**
Listar Mensagens em um servidor Exchange usou o método [ListMessages](https://apireference.aspose.com/net/email/aspose.email.clients.exchange.dav/exchangeclient/methods/listmessages/index) para obter uma lista de mensagens de uma caixa de correio do servidor Exchange. O método [ListMessages](https://apireference.aspose.com/net/email/aspose.email.clients.exchange.dav/exchangeclient/methods/listmessages/index) obtém informações básicas sobre as mensagens, por exemplo, o assunto, o ID da mensagem, de e para. Para obter os detalhes completos da mensagem, Aspose.Email.Exchange fornece o método [ExchangeClient.FetchMessage()](https://apireference.aspose.com/net/email/aspose.email.clients.exchange.dav/exchangeclient/methods/fetchmessage). Este método aceita o URI da mensagem como parâmetro e retorna uma instância da classe [MailMessage](https://apireference.aspose.com/email/net/aspose.email/mailmessage). A classe [MailMessage](https://apireference.aspose.com/email/net/aspose.email/mailmessage) fornece então detalhes da mensagem como corpo, cabeçalhos e anexos. Para buscar mensagens da Caixa de Correio do Servidor Exchange:

1. Crie uma instância do tipo [ExchangeClient](https://apireference.aspose.com/net/email/aspose.email.clients.exchange.dav/exchangeclient).
1. Especifique o mailboxUri, nome de usuário, senha e domínio.
1. Chame [ListMessages](https://apireference.aspose.com/net/email/aspose.email.clients.exchange.dav/exchangeclient/methods/listmessages/index) para obter a [ExchangeMessagesInfoCollection](https://apireference.aspose.com/net/email/aspose.email.clients.exchange/exchangemessageinfocollection).
1. Percorra a coleção [ExchangeMessagesInfoCollection](https://apireference.aspose.com/net/email/aspose.email.clients.exchange/exchangemessageinfocollection) para obter os valores de [ExchangeMessageInfo.UniqueURI](https://apireference.aspose.com/net/email/aspose.email.clients.exchange/exchangemessageinfo/properties/uniqueuri).
1. Chame [ExchangeClient.FetchMessage()](https://apireference.aspose.com/net/email/aspose.email.clients.exchange.dav/exchangeclient/methods/fetchmessage) e passe [ExchangeMessageInfo.UniqueURI](https://apireference.aspose.com/net/email/aspose.email.clients.exchange/exchangemessageinfo/properties/uniqueuri) como parâmetro.

O seguinte trecho de código mostra como se conectar à caixa de correio do servidor Exchange e buscar todas as mensagens.

{{< gist "aspose-com-gists" "6e5185a63aec6fd70d83098e82b06a32" "Examples-CSharp-Exchange_WebDav-FetchMessageUsingExchangeClient-FetchMessageUsingExchangeClient.cs" >}}
## **Pré-busca do Tamanho da Mensagem**
O Microsoft Outlook InterOp fornece o recurso de recuperar o tamanho da mensagem antes de realmente buscar a mensagem completa do servidor. No caso da API Aspose.Email, as informações resumidas recuperadas do servidor Exchange são representadas pela classe [ExchangeMessageInfo](https://apireference.aspose.com/net/email/aspose.email.clients.exchange/exchangemessageinfo). Ela fornece o mesmo recurso de recuperar o tamanho da mensagem usando a propriedade Size. Para recuperar o tamanho da mensagem, a chamada padrão ao método [ListMessages](https://apireference.aspose.com/net/email/aspose.email.clients.exchange.dav/exchangeclient/methods/listmessages/index) do ExchangeClient é usada para recuperar a coleção de [ExchangeMessageInfo](https://apireference.aspose.com/net/email/aspose.email.clients.exchange/exchangemessageinfo). O seguinte trecho de código mostra como exibir o tamanho da mensagem usando a classe [ExchangeMessageInfo](https://apireference.aspose.com/net/email/aspose.email.clients.exchange/exchangemessageinfo).

{{< gist "aspose-com-gists" "6e5185a63aec6fd70d83098e82b06a32" "Examples-CSharp-Exchange_WebDav-PreFetchMessageSizeUsingExchangeClient-PreFetchMessageSizeUsingExchangeClient.cs" >}}
## **Movendo Mensagens**
Você pode mover mensagens de email de uma pasta para outra com a ajuda do método [MoveItems](https://apireference.aspose.com/net/email/aspose.email.clients.exchange.dav/exchangeclient/methods/moveitems/index) da classe [ExchangeClient](https://apireference.aspose.com/net/email/aspose.email.clients.exchange.dav/exchangeclient). Ele aceita os parâmetros:

- O URI exclusivo da mensagem que deve ser movida.
- O URI exclusivo da pasta de destino.
### **Movendo Mensagens entre Pastas**
O seguinte trecho de código mostra como mover uma mensagem em uma caixa de correio da pasta de Entrada para uma pasta chamada Processada. Neste exemplo, o aplicativo:

1. Lê mensagens da pasta de Entrada.
1. Processa algumas das mensagens com base em alguns critérios (neste exemplo, encontramos uma palavra-chave no assunto da mensagem).
1. Move mensagens que cumprem a condição dada para a pasta processada.



{{< gist "aspose-com-gists" "6e5185a63aec6fd70d83098e82b06a32" "Examples-CSharp-Exchange_WebDav-MoveMessageFromOneFolderToAnotherUsingExchangeClient-MoveMessageFromOneFolderToAnotherUsingExchangeClient.cs" >}}
## **Excluindo Mensagens**
Você pode excluir mensagens de email de uma pasta com a ajuda do método [DeleteMessage](https://apireference.aspose.com/net/email/aspose.email.clients.exchange.dav/exchangeclient/methods/deletemessage/index) da classe [ExchangeClient](https://apireference.aspose.com/net/email/aspose.email.clients.exchange.dav/exchangeclient). Ele aceita o URI exclusivo da mensagem como parâmetro.
### **Excluindo Mensagens de um Servidor Exchange**
O seguinte trecho de código mostra como excluir uma mensagem da pasta de Entrada. Para o propósito deste exemplo, o código:

1. Lê mensagens da pasta de Entrada.
1. Processa mensagens com base em alguns critérios (neste exemplo, encontramos uma palavra-chave no assunto da mensagem).
1. Exclui a mensagem.



{{< gist "aspose-com-gists" "6e5185a63aec6fd70d83098e82b06a32" "Examples-CSharp-Exchange_WebDav-DeleteMessagesFromExchangeServer-DeleteMessagesFromExchangeServer.cs" >}}