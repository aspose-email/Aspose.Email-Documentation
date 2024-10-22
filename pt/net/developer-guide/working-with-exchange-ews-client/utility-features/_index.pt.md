---
title: "Recursos de Utilidade"
url: /pt/net/utility-features/
weight: 120
type: docs
---

## **Enviando uma Mensagem com Opção de Votação**

Microsoft Outlook permite que os usuários criem uma enquete ao compor uma nova mensagem. Isso é feito incluindo opções de votação como Sim, Não, Talvez, etc. A classe FollowUpOptions oferecida pelo Aspose.Email, fornece a propriedade VotingButtons que pode ser usada para definir ou obter o valor das opções de votação. Este artigo fornece um exemplo detalhado de como criar um MapiMessage com opções de votação para criar uma enquete e, em seguida, enviar a mensagem utilizando o cliente Exchange Web Service (EWS).

### **Criando e Enviando uma Mensagem com Opções de Votação**

O seguinte trecho de código mostra como criar uma nova mensagem e, em seguida, enviá-la com opções de votação.

{{< gist "aspose-email" "9e8fbeb51a8cbc4129dc71ca8cd55f0b" "Examples-CSharp-Exchange_EWS-CreateAndSendingMessageWithVotingOptions-CreateAndSendingMessageWithVotingOptions.cs" >}}

### **Métodos de Exemplo Usados nos Exemplos**

O seguinte trecho de código mostra como usar os métodos utilizados no exemplo acima.

{{< gist "aspose-email" "9e8fbeb51a8cbc4129dc71ca8cd55f0b" "Examples-CSharp-Exchange_EWS-CreateAndSendingMessageWithVotingOptions-CreateTestMessage.cs" >}}

## **Ignorar ou Contornar Certificado SSL Inválido ou Expirado**

Aspose.Email pode lidar com certificados SSL no Exchange Server usando tanto as classes [ExchangeClient](https://reference.aspose.com/email/net/aspose.email.clients.exchange.dav/exchangeclient/) quanto [EWSClient](https://reference.aspose.com/email/net/aspose.email.clients.exchange.webservice/ewsclient/). Se o certificado SSL estiver expirado ou se tornar inválido, Aspose.Email lança uma exceção devido ao certificado SSL inválido. Evite tais erros de certificado SSL ignorando-os usando o método utilizado no código abaixo. Registre o manipulador de callback em seu método main() ou init() e adicione o método abaixo como membro da classe.

{{< gist "aspose-email" "9e8fbeb51a8cbc4129dc71ca8cd55f0b" "Examples-CSharp-Exchange_EWS-IgnoringInvalidSSLCertificates-IgnoringInvalidSSLCertificates.cs" >}}

## **Criando Mensagens RE e FW a partir de arquivos MSG**

[IEWSClient](https://reference.aspose.com/email/net/aspose.email.clients.exchange.webservice/iewsclient/) permite que os desenvolvedores criem mensagens RE (Responder/Responder a Todos) e FW (Encaminhar) a partir de uma mensagem fonte. A mensagem fonte é identificada selecionando uma [ExchangeMessageInfo](https://reference.aspose.com/email/net/aspose.email.clients.exchange/exchangemessageinfo/) específica da [ExchangeMessageInfoCollection](https://reference.aspose.com/email/net/aspose.email.clients.exchange/exchangemessageinfocollection/exchangemessageinfocollection/) obtida por [IEWSClient.ListMessages()](https://reference.aspose.com/email/net/aspose.email.clients.exchange.webservice/iewsclient/listmessages/). O outro argumento é o [MailMessage](https://reference.aspose.com/email/net/aspose.email/mailmessage/) que deve ser enviado como mensagem RE ou FW. O seguinte trecho de código mostra como criar uma conta de exemplo que é usada para enviar uma mensagem e, em seguida, as funcionalidades de Responder e Encaminhar são demonstradas contra essa mensagem de exemplo. Para realizar esta tarefa:

1. Inicialize o objeto [IEWSClient](https://reference.aspose.com/email/net/aspose.email.clients.exchange.webservice/iewsclient/) fornecendo credenciais válidas.
2. Envie algumas mensagens de exemplo.
3. Chame as funções [IEWSClient.Reply()](https://reference.aspose.com/email/net/aspose.email.clients.exchange.webservice/iewsclient/reply/), [IEWSClient.ReplyAll()](https://reference.aspose.com/email/net/aspose.email.clients.exchange.webservice/iewsclient/replyall/) e [IEWSClient.Forward()](https://reference.aspose.com/email/net/aspose.email.clients.exchange.webservice/iewsclient/forward/) para enviar mensagens.

{{< gist "aspose-email" "9e8fbeb51a8cbc4129dc71ca8cd55f0b" "Examples-CSharp-Exchange_EWS-CreateREAndFWMessages-CreateREAndFWMessages.cs" >}}

## **Suporte para Rastreamento de Email**

A API Aspose.Email fornece suporte para rastreamento de email usando Notificação de Disposição de Mensagem (MDN). Isso é alcançado ao solicitar os recibos de leitura e criar as informações necessárias. A propriedade [MailMessage.ReadReceiptTo](https://reference.aspose.com/email/net/aspose.email/mailmessage/readreceiptto/) obtém ou define o endereço do recibo de leitura configurado. Os métodos [CreateReadReceipt](https://reference.aspose.com/email/net/aspose.email/mailmessage/createreadreceipt/) e [ReadReceiptRequested](https://reference.aspose.com/email/net/aspose.email.mapi/mapimessage/readreceiptrequested/) são usados para criar e recuperar informações sobre se os recibos de leitura foram solicitados. O seguinte trecho de código mostra como rastrear emails usando a API Aspose.Email.

{{< gist "aspose-email" "9e8fbeb51a8cbc4129dc71ca8cd55f0b" "Examples-CSharp-Exchange-EmailTracking-EmailTracking.cs" >}}

## **Suporte para Registro em Clientes Exchange**

A API Aspose.Email fornece a capacidade de fornecer um recurso de registro para o cliente do Exchange Web Service. Isso pode ser alcançado configurando o arquivo App.config.

### **Registro para Cliente EWS**

{{< gist "aspose-email" "9e8fbeb51a8cbc4129dc71ca8cd55f0b" "LoggingForEWSClient.xml" >}}

## **Adicionando Cabeçalhos em Solicitações EWS**

A API Aspose.Email permite adicionar cabeçalhos às solicitações do Exchange. Isso pode ser usado para adicionar cabeçalhos às solicitações EWS para diferentes cabeçalhos que podem ser usados para diferentes fins. Um exemplo poderia ser adicionar o cabeçalho X-AnchorMailbox que é usado para gerenciar problemas de limitação no servidor Exchange. O método [AddHeader](https://reference.aspose.com/email/net/aspose.email.clients.exchange.webservice/iewsclient/addheader/) da classe [IEWSClient](https://reference.aspose.com/email/net/aspose.email.clients.exchange.webservice/iewsclient/) é usado para adicionar cabeçalhos às solicitações EWS, conforme mostrado no seguinte trecho de código.

{{< gist "aspose-email" "9e8fbeb51a8cbc4129dc71ca8cd55f0b" "Examples-CSharp-Exchange_EWS-AddingHeadersToEWSRequests-AddingHeadersToEWSRequests.cs" >}}

## **Trabalhando com Mensagens Unificadas**

Aspose.Email pode recuperar informações de mensagens unificadas do Exchange Server 2010. Mensagens unificadas como obter informações de configuração, iniciar uma chamada externa, recuperar informações de chamada telefonando pelo ID e desconectar uma chamada telefônica pelo ID são suportadas atualmente. O seguinte exemplo de código mostra como recuperar informações de configuração de mensagens unificadas do Microsoft Exchange Server 2010.

{{< gist "aspose-email" "9e8fbeb51a8cbc4129dc71ca8cd55f0b" "Examples-CSharp-Exchange_EWS-GettingUnifiedMessagingConfigurationInformation-GettingUnifiedMessagingConfigurationInformation.cs" >}}

## **Obtendo Dicas de Email**

O Microsoft Exchange Server adicionou vários novos recursos com o Exchange Server 2010 e 2013. Um deles permite que os usuários obtenham dicas de email ao compor uma mensagem de email. Essas dicas são muito úteis, pois fornecem informações antes que o email seja enviado. Por exemplo, se um endereço de email estiver errado na lista de destinatários, uma dica é exibida para informar que o endereço de email é inválido. As dicas de email também permitem que você veja respostas de fora do escritório antes de enviar um email: o Exchange Server (2010 e 2013) envia a dica de email quando o email está sendo composto se um ou mais dos destinatários tiverem configurado respostas de fora do escritório. O Microsoft Exchange Server 2010 Service Pack 1 é necessário para todos os recursos demonstrados neste artigo. O seguinte trecho de código mostra como usar a classe [EWSClient](https://reference.aspose.com/email/net/aspose.email.clients.exchange.webservice/ewsclient/) que usa os Serviços Web do Exchange, disponíveis no Microsoft Exchange Server 2007 e versões posteriores.

{{< gist "aspose-email" "9e8fbeb51a8cbc4129dc71ca8cd55f0b" "Examples-CSharp-Exchange_EWS-GetMailTips-GetMailTips.cs" >}}

## **Impersonação do Exchange**

A impersonação do Exchange permite que alguém impersonifique outra conta e realize tarefas e operações usando as permissões da conta impersonificada em vez de suas próprias. Enquanto a delegação permite que os usuários atuem em nome de outros usuários, a impersonação permite que eles atuem como outros usuários. Aspose.Email suporta a impersonação do Exchange. A classe [EWSClient](https://reference.aspose.com/email/net/aspose.email.clients.exchange.webservice/ewsclient/) fornece os métodos [ImpersonateUser](https://reference.aspose.com/email/net/aspose.email.clients.exchange.webservice/iewsclient/impersonateuser/) e [ResetImpersonation](https://reference.aspose.com/email/net/aspose.email.clients.exchange.webservice/iewsclient/resetimpersonation/) para facilitar esse recurso.

Para realizar esta tarefa:

1. Inicialize o ExchangeWebServiceClient para o usuário 1.
2. Inicialize o ExchangeWebServiceClient para o usuário 2.
3. Anexe mensagens de teste às contas.
4. Habilite a Impersonação.
5. Redefina a Impersonação.

O seguinte trecho de código mostra como usar a classe [EWSClient](https://reference.aspose.com/email/net/aspose.email.clients.exchange.webservice/ewsclient/) para implementar o recurso de Impersonação.

{{< gist "aspose-email" "9e8fbeb51a8cbc4129dc71ca8cd55f0b" "Examples-CSharp-Exchange_EWS-ExchangeImpersonationUsingEWS-ExchangeImpersonationUsingEWS.cs" >}}

## **Recurso de Descoberta Automática usando EWS**

A API Aspose.Email permite descobrir as configurações do Exchange Server usando o Cliente EWS.

{{< gist "aspose-email" "9e8fbeb51a8cbc4129dc71ca8cd55f0b" "Examples-CSharp-Exchange_EWS-AutoDiscoverUsingEWS-AutoDiscoverUsingEWS.cs" >}}

## **Abortar Restauração de PST para a Operação do Exchange Server**

A API Aspose.Email permite restaurar um arquivo PST para o Exchange Server. No entanto, se a operação estiver demorando muito devido ao tamanho grande do arquivo PST, pode ser necessário especificar critérios para abortar a operação. Isso pode ser alcançado usando a API conforme mostrado no seguinte exemplo de código.

**Nota:** O exemplo precisa que a seguinte classe seja adicionada também.

``` cs
 public class CustomAbortRestoreException : Exception { }
```

{{< gist "aspose-email" "9e8fbeb51a8cbc4129dc71ca8cd55f0b" "Examples-CSharp-Exchange_EWS-AbortPSTToExchangeServerOperation-AbortPSTToExchangeServerOperation.cs" >}}