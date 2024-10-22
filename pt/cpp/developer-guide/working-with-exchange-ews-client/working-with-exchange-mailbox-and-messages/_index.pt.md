---
title: "Trabalhando com Caixa de Correio e Mensagens do Exchange"
url: /pt/cpp/trabalhando-com-caixa-de-correio-e-mensagens-do-exchange/
weight: 20
type: docs
---
  
## **Obtendo Informações da Caixa de Correio Usando EWS**  
Você pode obter informações da caixa de correio de um servidor Exchange chamando o método [GetMailboxInfo](https://apireference.aspose.com/email/cpp/class/aspose.email.clients.exchange.web_service.i_e_w_s_client#ab7a471f46b5ebe0e3bf2c7f9166e2927) da classe [IEWSClient](https://apireference.aspose.com/email/cpp/class/aspose.email.clients.exchange.web_service.i_e_w_s_client). Ele retorna uma instância do tipo [ExchangeMailboxInfo](https://apireference.aspose.com/email/cpp/class/aspose.email.clients.exchange.exchange_mailbox_info). Obtenha informações da caixa de correio a partir de propriedades como MailboxUri, InboxUri e DraftsUri. Este artigo mostra como acessar informações da caixa de correio usando os Serviços Web do Exchange.  
  
Para se conectar ao servidor Exchange usando os Serviços Web do Exchange (EWS), use a classe [IEWSClient](https://apireference.aspose.com/email/cpp/class/aspose.email.clients.exchange.web_service.i_e_w_s_client). Esta classe usa EWS para se conectar e gerenciar itens em um servidor Exchange. O seguinte trecho de código mostra como obter informações da caixa de correio usando os serviços web do exchange.  
  
  
{{< gist "aspose-com-gists" "525dd06c8783ebb18fb75cfc4b31d1ef" "Examples-Cpp-source-Exchange_EWS-GetMailboxInformationFromExchangeWebServices-GetMailboxInformationFromExchangeWebServices.cpp" >}}  
## **Enviando Mensagens de Email**  
Você pode enviar mensagens de email usando um servidor Exchange com o método [IEWSClient->Send()](https://apireference.aspose.com/email/cpp/class/aspose.email.clients.exchange.web_service.i_e_w_s_client#a02875ffd55c4033e7d88007a9ac2a83c) que aceita uma instância de [MailMessage](https://apireference.aspose.com/email/cpp/class/aspose.email.mail_message) como parâmetro e envia o email. Este artigo explica como enviar mensagens de email usando os Serviços Web do Exchange.  
  
O seguinte trecho de código mostra como enviar mensagens de email usando [IEWSClient](https://apireference.aspose.com/email/cpp/class/aspose.email.clients.exchange.web_service.i_e_w_s_client).  
  
  
{{< gist "aspose-com-gists" "525dd06c8783ebb18fb75cfc4b31d1ef" "Examples-Cpp-source-Exchange_EWS-SendEmailMessagesUsingExchangeWebServices-SendEmailMessagesUsingExchangeWebServices.cpp" >}}  
## **Lendo Emails da Caixa de Correio de Outro Usuário**  
Algumas contas em servidores Exchange têm o direito de acessar várias caixas de correio, e alguns usuários têm várias contas de email no mesmo servidor Exchange. Em ambos os casos, os usuários podem acessar as caixas de correio de outros usuários usando Aspose.Email. Esta API fornece um mecanismo para acessar pastas e emails de outras caixas de correio usando a classe [IEWSClient](https://apireference.aspose.com/email/cpp/class/aspose.email.clients.exchange.web_service.i_e_w_s_client). Essa funcionalidade pode ser alcançada usando o método sobrecarregado [GetMailboxInfo()](https://apireference.aspose.com/email/cpp/class/aspose.email.clients.exchange.web_service.i_e_w_s_client#ac95e7c7a5e8678b70b4f5c4356d88582) e fornecendo o endereço de email do usuário como parâmetro.  
  
O seguinte trecho de código mostra como ler emails usando a classe [IEWSClient](https://apireference.aspose.com/email/cpp/class/aspose.email.clients.exchange.web_service.i_e_w_s_client).  
  
  
{{< gist "aspose-com-gists" "525dd06c8783ebb18fb75cfc4b31d1ef" "Examples-Cpp-source-Exchange_EWS-AccessAnotherMailboxUsingExchangeWebServiceClient-1.cpp" >}}  
## **Listando Mensagens**  
Uma lista das mensagens de email em uma caixa de correio do Exchange pode ser obtida chamando o método [ListMessages](https://apireference.aspose.com/email/cpp/class/aspose.email.clients.exchange.web_service.i_e_w_s_client#a37cfefda7e1ab560a073b3e31f4d27ca). Obtenha as informações básicas sobre as mensagens, como assunto, de, para e ID da mensagem, usando o método [ListMessages](https://apireference.aspose.com/email/cpp/class/aspose.email.clients.exchange.web_service.i_e_w_s_client#a37cfefda7e1ab560a073b3e31f4d27ca).  
### **Listagem Simples de Mensagens**  
Para listar as mensagens em uma caixa de correio do Exchange:  
  
1. Crie uma instância da classe [IEWSClient](https://apireference.aspose.com/email/cpp/class/aspose.email.clients.exchange.web_service.i_e_w_s_client).  
1. Chame o método [ListMessages](https://apireference.aspose.com/email/cpp/class/aspose.email.clients.exchange.web_service.i_e_w_s_client#a37cfefda7e1ab560a073b3e31f4d27ca) para obter a coleção de mensagens.  
1. Percorra a coleção e exiba as informações da mensagem.  
  
O seguinte trecho de código mostra como se conectar a um servidor exchange usando EWS e listar mensagens da pasta de entrada.  
  
  
{{< gist "aspose-com-gists" "525dd06c8783ebb18fb75cfc4b31d1ef" "Examples-Cpp-source-Exchange_EWS-ListingMessagesUsingEWS-ListingMessagesUsingEWS.cpp" >}}  
### **Listando Mensagens de Pastas Diferentes**  
O trecho de código acima lista todas as mensagens na pasta de entrada. É possível obter a lista de mensagens de outras pastas também. O método [ListMessages](https://apireference.aspose.com/email/cpp/class/aspose.email.clients.exchange.web_service.i_e_w_s_client#a37cfefda7e1ab560a073b3e31f4d27ca) aceita uma URI de pasta como parâmetro. Desde que a URI da pasta seja válida, você pode obter a lista de mensagens dessa pasta. Use o [IEWSClient](https://apireference.aspose.com/email/cpp/class/aspose.email.clients.exchange.web_service.i_e_w_s_client)->[get_MailboxInfo](https://apireference.aspose.com/email/cpp/class/aspose.email.clients.exchange.web_service.i_e_w_s_client#a63b3972a738e652a9bab4e3fcfd23a26)->xxxFolderUri propriedade para obter a URI de diferentes pastas. O resto do código é o mesmo que para obter uma lista de mensagens. O seguinte trecho de código mostra como listar mensagens de pastas diferentes usando EWS.  
  
  
{{< gist "aspose-com-gists" "525dd06c8783ebb18fb75cfc4b31d1ef" "Examples-Cpp-source-Exchange_EWS-ListingMessagesFromFolders-ListingMessagesFromFolders.cpp" >}}  
### **Listando Mensagens com Suporte a Paginação**  
O seguinte trecho de código mostra como obter uma lista de mensagens com suporte a paginação.  
  
{{< gist "aspose-com-gists" "525dd06c8783ebb18fb75cfc4b31d1ef" "Examples-Cpp-source-Exchange_EWS-PagingSupportForListingMessages-PagingSupportForListingMessages.cpp" >}}  
### **Obtendo Informações do Tipo da Mensagem a partir do ExchangeMessageInfo**  
{{< gist "aspose-com-gists" "525dd06c8783ebb18fb75cfc4b31d1ef" "Examples-Cpp-source-Exchange_EWS-GetMessageTypeFromExchangeMessageInfo-GetMessageTypeFromExchangeMessageInfo.cpp" >}}  
## **Salvando Mensagens**  
Este artigo mostra como obter mensagens de uma caixa de correio de servidor Exchange e salvá-las no disco nos formatos EML e MSG:  
  
- Salvar como EML no disco.  
- Salvar em fluxo de memória.  
- Salvar como MSG.  
### **Salvando Mensagens em EML**  
Para obter mensagens e salvar em formato EML:  
  
1. Crie uma instância da classe [IEWSClient](https://apireference.aspose.com/email/cpp/class/aspose.email.clients.exchange.web_service.i_e_w_s_client).  
1. Forneça a mailboxUri, nome de usuário, senha e domínio.  
1. Chame o método [IEWSClient->ListMessages()](https://apireference.aspose.com/email/cpp/class/aspose.email.clients.exchange.web_service.i_e_w_s_client#a37cfefda7e1ab560a073b3e31f4d27ca) para obter uma instância da coleção [ExchangeMessagesInfoCollection](https://apireference.aspose.com/email/cpp/class/aspose.email.clients.exchange.exchange_message_info_collection).  
1. Percorra a coleção [ExchangeMessagesInfoCollection](https://apireference.aspose.com/email/cpp/class/aspose.email.clients.exchange.exchange_message_info_collection) para obter a URI única para cada mensagem.  
1. Chame o método [IEWSClient->SaveMessage()](https://apireference.aspose.com/email/cpp/class/aspose.email.clients.exchange.web_service.i_e_w_s_client#a1a735b25973171ac5111c3469a54f7fa) e passe a URI única e o local de salvamento como parâmetros.  
  
O seguinte trecho de código mostra como usar EWS para se conectar ao servidor Exchange e salvar mensagens como arquivos EML.  
  
  
{{< gist "aspose-com-gists" "525dd06c8783ebb18fb75cfc4b31d1ef" "Examples-Cpp-source-Exchange_EWS-SaveMessagesUsingExchangeWebServices-SaveMessagesUsingExchangeWebServices.cpp" >}}  
### **Salvando Mensagens em um Fluxo de Memória**  
Em vez de salvar arquivos EML no disco, é possível salvá-los em um fluxo de memória. Isso é útil quando você deseja salvar o fluxo em algum local de armazenamento, como um banco de dados. Uma vez que o fluxo foi salvo em um banco de dados, você pode recarregar o arquivo EML na classe [MailMessage](https://apireference.aspose.com/email/cpp/class/aspose.email.mail_message). O seguinte trecho de código mostra como salvar mensagens de uma caixa de correio de servidor Exchange em um fluxo de memória usando EWS.  
  
  
{{< gist "aspose-com-gists" "525dd06c8783ebb18fb75cfc4b31d1ef" "Examples-Cpp-source-Exchange_EWS-SaveMessagesToMemoryStreamUsingEWS-SaveMessagesToMemoryStream.cpp" >}}  
### **Salvando Mensagens em Formato MSG**  
O método [IEWSClient->SaveMessage()](https://apireference.aspose.com/email/cpp/class/aspose.email.clients.exchange.web_service.i_e_w_s_client#a1a735b25973171ac5111c3469a54f7fa) pode salvar diretamente a mensagem em formato EML. Para salvar as mensagens em formato MSG, primeiro, chame o método [IEWSClient->FetchMessage()](https://apireference.aspose.com/email/cpp/class/aspose.email.clients.exchange.web_service.i_e_w_s_client#ae0edf4afafbe6339541687aeacc84905) que retorna uma instância da classe [MailMessage](https://apireference.aspose.com/email/cpp/class/aspose.email.mail_message). Em seguida, chame o método [MailMessage->Save()](https://apireference.aspose.com/email/cpp/class/aspose.email.mail_message#a41d3ada3ca8b7ca8130629b616f0b91c) para salvar a mensagem em MSG. O seguinte trecho de código mostra como obter mensagens de uma caixa de correio de servidor Exchange e salvá-las no formato MSG usando EWS.  
  
  
{{< gist "aspose-com-gists" "525dd06c8783ebb18fb75cfc4b31d1ef" "Examples-Cpp-source-Exchange_EWS-SaveMessagesInMSGFormatExchangeEWS-SaveMessagesInMSGFormatExchangeEWS.cpp" >}}  
## **Obtendo ExchangeMessageInfo da URI da Mensagem**  
Uma mensagem de email é representada por seu identificador único, URI, e é uma parte integral do objeto ExchangeMessageInfo. No caso de apenas a URI da mensagem estar disponível, o objeto [ExchangeMessageInfo](https://apireference.aspose.com/email/cpp/class/aspose.email.clients.exchange.exchange_message_info) também pode ser recuperado usando essa informação disponível. A versão sobrecarregada de [ListMessages](https://apireference.aspose.com/email/cpp/class/aspose.email.clients.exchange.web_service.i_e_w_s_client#a2b3b4ebfdd9423eeb63d59b5e74cc53a) aceita uma lista de IDs e retorna uma coleção de [ExchangeMessageInfoCollection](https://apireference.aspose.com/email/cpp/class/aspose.email.clients.exchange.exchange_message_info_collection). O seguinte trecho de código mostra como obter [ExchangeMessageInfo](https://apireference.aspose.com/email/cpp/class/aspose.email.clients.exchange.exchange_message_info) da URI da mensagem.  
  
  
{{< gist "aspose-com-gists" "525dd06c8783ebb18fb75cfc4b31d1ef" "Examples-Cpp-source-Exchange_EWS-GetExchangeMessageInfoFromMessageURI-GetExchangeMessageInfoFromMessageURI.cpp" >}}  
## **Buscar Mensagens de uma Caixa de Correio do Servidor Exchange**  
O método [ListMessages()](https://apireference.aspose.com/email/cpp/class/aspose.email.clients.exchange.web_service.i_e_w_s_client#aad8420247acd17cb1d73303ed1982d1e) é usado para obter uma lista de mensagens de uma caixa de correio do servidor Exchange. O método [ListMessages()](https://apireference.aspose.com/email/cpp/class/aspose.email.clients.exchange.web_service.i_e_w_s_client#aad8420247acd17cb1d73303ed1982d1e) obtém informações básicas sobre as mensagens, como o assunto, o ID da mensagem, de e para. Para obter os detalhes completos da mensagem, Aspose.Email fornece o método [IEWSClient->FetchMessage()](https://apireference.aspose.com/email/cpp/class/aspose.email.clients.exchange.web_service.i_e_w_s_client#ae0edf4afafbe6339541687aeacc84905). Este método aceita a URI da mensagem como parâmetro e retorna uma instância da classe [MailMessage](https://apireference.aspose.com/email/cpp/class/aspose.email.mail_message). A classe [MailMessage](https://apireference.aspose.com/email/cpp/class/aspose.email.mail_message) fornece detalhes da mensagem, como o corpo, cabeçalhos e anexos. Para buscar mensagens da caixa de correio do servidor Exchange:  
  
1. Crie uma instância do tipo [IEWSClient](https://apireference.aspose.com/email/cpp/class/aspose.email.clients.exchange.web_service.i_e_w_s_client).  
1. Especifique o nome do servidor, nome de usuário, senha e domínio.  
1. Chame o método [IEWSClient->ListMessages()](https://apireference.aspose.com/email/cpp/class/aspose.email.clients.exchange.web_service.i_e_w_s_client#a37cfefda7e1ab560a073b3e31f4d27ca) para obter a [ExchangeMessagesInfoCollection](https://apireference.aspose.com/email/cpp/class/aspose.email.clients.exchange.exchange_message_info_collection).  
1. Percorra a coleção [ExchangeMessagesInfoCollection](https://apireference.aspose.com/email/cpp/class/aspose.email.clients.exchange.exchange_message_info_collection) para obter os valores de [ExchangeMessageInfo->get_UniqueUri()](https://apireference.aspose.com/email/cpp/class/aspose.email.clients.exchange.exchange_message_info#a3cb9feb99e2ac195529cf9e5e7867cb7).  
1. Chame [IEWSClient->FetchMessage()](https://apireference.aspose.com/email/cpp/class/aspose.email.clients.exchange.web_service.i_e_w_s_client#ae0edf4afafbe6339541687aeacc84905) e passe [ExchangeMessageInfo->get_UniqueUri()](https://apireference.aspose.com/email/cpp/class/aspose.email.clients.exchange.exchange_message_info#a3cb9feb99e2ac195529cf9e5e7867cb7) como parâmetro.  
  
O seguinte trecho de código demonstra como buscar todas as mensagens usando EWS.  
  
  
{{< gist "aspose-com-gists" "525dd06c8783ebb18fb75cfc4b31d1ef" "Examples-Cpp-source-Exchange_EWS-FetchMessageUsingEWS-FetchMessageUsingEWS.cpp" >}}  
## **Pré-Busca do Tamanho da Mensagem**  
O Microsoft Outlook InterOp fornece o recurso de recuperar o tamanho da mensagem antes de realmente buscar a mensagem completa do servidor. No caso da API Aspose.Email, as informações resumidas recuperadas do servidor Exchange são representadas pela classe [ExchangeMessageInfo](https://apireference.aspose.com/email/cpp/class/aspose.email.clients.exchange.exchange_message_info). Ela fornece o recurso de recuperar o tamanho da mensagem usando a propriedade [Size](https://apireference.aspose.com/email/cpp/class/aspose.email.clients.message_info_base#a04bc106203ed5cfec65f4d0320d14e8a). Para recuperar o tamanho da mensagem, a chamada padrão para [IEWSClient->ListMessages()](https://apireference.aspose.com/email/cpp/class/aspose.email.clients.exchange.web_service.i_e_w_s_client#a37cfefda7e1ab560a073b3e31f4d27ca) é usada para recuperar a [ExchangeMessagesInfoCollection](https://apireference.aspose.com/email/cpp/class/aspose.email.clients.exchange.exchange_message_info_collection). O seguinte trecho de código mostra como exibir o tamanho da mensagem usando a classe [ExchangeMessageInfo](https://apireference.aspose.com/email/cpp/class/aspose.email.clients.exchange.exchange_message_info).  
  
  
{{< gist "aspose-com-gists" "525dd06c8783ebb18fb75cfc4b31d1ef" "Examples-Cpp-source-Exchange_EWS-PreFetchMessageSizeUsingIEWSClient-PreFetchMessageSizeUsingIEWSClient.cpp" >}}  
## **Baixar Mensagens de Pastas Públicas**  
O Microsoft Exchange Server permite que os usuários criem pastas públicas e publiquem mensagens nelas. Para fazer isso por meio de seu aplicativo, use a classe [EWSClient](https://apireference.aspose.com/email/cpp/class/aspose.email.clients.exchange.web_service.e_w_s_client) do Aspose.Email para se conectar ao servidor Exchange e ler e baixar mensagens e postagens de pastas públicas. O seguinte trecho de código mostra como ler todas as pastas públicas e subpastas, e listar e baixar quaisquer mensagens encontradas nessas pastas. Este exemplo funciona apenas com o Microsoft Exchange Server 2007 ou superior, já que apenas esses suportam EWS.  
  
  
{{< gist "aspose-com-gists" "525dd06c8783ebb18fb75cfc4b31d1ef" "Examples-Cpp-source-Exchange_EWS-DownloadMessagesFromPublicFolders-DownloadMessagesFromPublicFolders.cpp" >}}  
## **Movendo Mensagens**  
Você pode mover mensagens de email de uma pasta para outra com a ajuda do método Move da classe [IEWSClient](https://apireference.aspose.com/email/cpp/class/aspose.email.clients.exchange.web_service.i_e_w_s_client). Ele aceita os seguintes parâmetros:  
  
- A URI única da mensagem que deve ser movida.  
- A URI única da pasta de destino.  
### **Movendo Mensagens entre Pastas**  
O seguinte trecho de código mostra como mover uma mensagem em uma caixa de correio da pasta de Entrada para uma pasta chamada Processada. Neste exemplo, o aplicativo:  
  
1. Lê mensagens da pasta de Entrada.  
1. Processa algumas das mensagens com base em alguns critérios (neste exemplo, encontramos uma palavra-chave no assunto da mensagem).  
1. Move mensagens que atendem à condição dada para a pasta processada.  
  
{{< gist "aspose-com-gists" "525dd06c8783ebb18fb75cfc4b31d1ef" "Examples-Cpp-source-Exchange_EWS-MoveMessageFromOneFolderToAnotherusingEWS-MoveMessageFromOneFolderToAnotherusingEWS.cpp" >}}  
## **Excluindo Mensagens**  
Você pode excluir mensagens de email de uma pasta com a ajuda do método [IEWSClient->DeleteMessage](https://apireference.aspose.com/email/cpp/class/aspose.email.clients.exchange.web_service.i_e_w_s_client#a576fb78dcbac3bdb8b2bb87cab5d33c1). Ele aceita a URI única da mensagem como parâmetro.  
  
O seguinte trecho de código mostra como excluir uma mensagem da pasta de Entrada. Para os propósitos deste exemplo, o código:  
  
1. Lê mensagens da pasta de Entrada.  
1. Processa mensagens com base em alguns critérios (neste exemplo, encontramos uma palavra-chave no assunto da mensagem).  
1. Exclui a mensagem.  
  
{{< gist "aspose-com-gists" "525dd06c8783ebb18fb75cfc4b31d1ef" "Examples-Cpp-source-Exchange_EWS-DeleteMessagesFromUsingEWS-DeleteMessagesFromusingEWS.cpp" >}}  
## **Copiando Mensagens**  
A API Aspose.Email permite copiar uma mensagem de uma pasta para outra usando o método [IEWSClient->CopyItem](https://apireference.aspose.com/email/cpp/class/aspose.email.clients.exchange.web_service.i_e_w_s_client#a6e340250e1e0f51d68d4ffe7727f4e7f). A versão sobrecarregada deste método retorna a URI única da mensagem copiada, conforme mostrado neste artigo.  
### **Copiando uma Mensagem para Outra Pasta**  
O seguinte trecho de código mostra como copiar uma mensagem para outra pasta.  
  
  
{{< gist "aspose-com-gists" "525dd06c8783ebb18fb75cfc4b31d1ef" "Examples-Cpp-source-Exchange_EWS-CopyingMessageToAnotherFolder-CopyingMessageToAnotherFolder.cpp" >}}  