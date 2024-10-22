---
title: "Trabalhando com Mensagens do Servidor"
url: /pt/net/trabalhando-com-mensagens-do-servidor/
weight: 50
type: docs
---

## **Obtendo Informações da Caixa de Correio**

Podemos obter informações sobre a caixa de correio, como o número de mensagens e o tamanho da caixa de correio, usando os métodos [GetMailBoxSize](https://reference.aspose.com/email/net/aspose.email.clients.pop3/pop3client/getmailboxsize/#getmailboxsize/v) e [GetMailBoxInfo](https://reference.aspose.com/email/net/aspose.email.clients.pop3/pop3client/getmailboxinfo/#getmailboxinfo/) da classe [Pop3Client](https://reference.aspose.com/email/net/aspose.email.clients.pop3/pop3client/).

- O método [GetMailBoxSize](https://reference.aspose.com/email/net/aspose.email.clients.pop3/pop3client/getmailboxsize/#getmailboxsize/) retorna o tamanho da caixa de correio em bytes.
- O método [GetMailBoxInfo](https://reference.aspose.com/email/net/aspose.email.clients.pop3/pop3client/getmailboxinfo/#getmailboxinfo/) retorna um objeto do tipo [Pop3MailBoxInfo](https://reference.aspose.com/email/net/aspose.email.clients.pop3/pop3mailboxinfo/).

É também possível obter o número de mensagens usando a propriedade [MessageCount](https://reference.aspose.com/email/net/aspose.email.clients.pop3/pop3mailboxinfo/messagecount/) e o tamanho usando a propriedade [OccupiedSize](https://reference.aspose.com/email/net/aspose.email.clients.pop3/pop3mailboxinfo/occupiedsize/) da classe [Pop3MailBoxInfo](https://reference.aspose.com/email/net/aspose.email.clients.pop3/pop3mailboxinfo/). O seguinte código de exemplo mostra como obter informações sobre a caixa de correio. Ele mostra como:

1. Criar um [Pop3Client](https://reference.aspose.com/email/net/aspose.email.clients.pop3/pop3client/).
1. Conectar-se a um servidor POP3.
1. Obter o tamanho da caixa de correio.
1. Obter informações da caixa de correio.
1. Obter o número de mensagens na caixa de correio.
1. Obter o tamanho ocupado.

{{< gist "aspose-com-gists" "6e5185a63aec6fd70d83098e82b06a32" "Examples-CSharp-POP3-GettingMailboxInfo-GettingMailboxInfo.cs" >}}

## **Obtendo a Contagem de Emails na Caixa de Correio**

O seguinte código de exemplo mostra como contar as mensagens de email em uma caixa de correio.

{{< gist "aspose-com-gists" "6e5185a63aec6fd70d83098e82b06a32" "Examples-CSharp-POP3-GetEmailCountIntheMailbox-GetEmailCountIntheMailbox.cs" >}}

Aspose.Email permite que os desenvolvedores trabalhem com emails de muitas maneiras diferentes. Por exemplo, eles podem recuperar informações do cabeçalho antes de decidir se devem baixar um email. Ou eles podem recuperar emails de um servidor e salvá-los sem analisá-los (mais rápido) ou após analisá-los (mais devagar). Este artigo mostra como recuperar e converter emails.

## **Recuperando Informações dos Cabeçalhos de Email**

Os cabeçalhos de email podem nos fornecer informações sobre uma mensagem de email que podemos usar para decidir se devemos ou não recuperar toda a mensagem de email. Normalmente, as informações do cabeçalho contêm remetente, assunto, data de recebimento, etc. (Os cabeçalhos de email são descritos em detalhes em [Personalizando Cabeçalhos de Email](https://docs.aspose.com/email/pt/net/creating-and-setting-contents-of-emails/#set-email-headers). Esse tópico é especificamente sobre o envio de um email com SMTP, mas as informações do conteúdo do cabeçalho de email permanecem válidas para emails POP3). Os seguintes exemplos mostram como recuperar cabeçalhos de email de um servidor POP3 pelo número de sequência da mensagem.

{{< gist "aspose-com-gists" "6e5185a63aec6fd70d83098e82b06a32" "Examples-CSharp-POP3-RetrievingEmailHeaders-RetrievingEmailHeaders.cs" >}}

## **Recuperando Mensagens de Email**

A classe [Pop3Client](https://reference.aspose.com/email/net/aspose.email.clients.pop3/pop3client/) fornece a capacidade de recuperar mensagens de email do servidor POP3 e analisá-las em uma instância de [MailMessage](https://reference.aspose.com/email/net/aspose.email/mailmessage/) com a ajuda dos componentes [MailMessage](https://reference.aspose.com/email/net/aspose.email/mailmessage/). A classe [MailMessage](https://reference.aspose.com/email/net/aspose.email/mailmessage/) contém várias propriedades e métodos para manipulação do conteúdo do email. Usando o método [FetchMessage](https://reference.aspose.com/email/net/aspose.email.clients.pop3/pop3client/fetchmessage/#fetchmessage/) da classe [Pop3Client](https://reference.aspose.com/email/net/aspose.email.clients.pop3/pop3client/), você pode obter uma instância de [MailMessage](https://reference.aspose.com/email/net/aspose.email/mailmessage/) diretamente do servidor POP3. O seguinte código de exemplo mostra como recuperar uma mensagem de email completa do servidor POP3.

{{< gist "aspose-com-gists" "6e5185a63aec6fd70d83098e82b06a32" "Examples-CSharp-POP3-RetrievingEmailMessages-RetrievingEmailMessages.cs" >}}

## **Recuperando Informações Resumidas da Mensagem Usando ID Único**

O Cliente POP3 da API pode recuperar informações resumidas da mensagem do servidor usando o ID único da mensagem. Isso fornece acesso rápido às informações resumidas da mensagem sem primeiro recuperar a mensagem completa do servidor. O seguinte código de exemplo mostra como recuperar informações resumidas da mensagem.

{{< gist "aspose-com-gists" "6e5185a63aec6fd70d83098e82b06a32" "Examples-CSharp-POP3-RetrieveMessageSummaryInformationUsingUniqueId-RetrieveMessageSummaryInformationUsingUniqueId.cs" >}}

## **Listando Mensagens com MultiConnection**

O [Pop3Client](https://reference.aspose.com/email/net/aspose.email.clients.pop3/pop3client/) fornece uma propriedade [UseMultiConnection](https://reference.aspose.com/email/net/aspose.email.clients/emailclient/usemulticonnection/) que pode ser usada para criar várias conexões para operações pesadas. Você também pode definir o número de conexões a serem usadas durante o modo de multiconexão usando [Pop3Client.ConnectionsQuantity](https://reference.aspose.com/email/net/aspose.email.clients/emailclient/connectionsquantity/). O seguinte código de exemplo demonstra o uso do modo de multiconexão para listar mensagens e compara seu desempenho com o modo de conexão única.

{{< gist "aspose-com-gists" "522d47278b8ca448dc1d7eb97193322c" "Examples-CSharp-POP3-Pop3ListMessagesWithMultiConnection-1.cs" >}}

{{% alert color="primary" %}} 

Por favor, note que o uso do modo de multiconexão não garante aumento de desempenho.

{{% /alert %}} 

## **Buscando Mensagens do Servidor e Salvando no Disco**

### **Salvar Mensagem no Disco Sem Analisar**

Se você deseja baixar mensagens de email do servidor POP3 sem analisá-las, use a função [SaveMessage](https://reference.aspose.com/email/net/aspose.email.clients.pop3/pop3client/savemessage/#savemessage/) da classe [Pop3Client](https://reference.aspose.com/email/net/aspose.email.clients.pop3/pop3client/). A função [SaveMessage](https://reference.aspose.com/email/net/aspose.email.clients.pop3/pop3client/savemessage/#savemessage/) não analisa a mensagem de email, portanto, é mais rápida do que a função [FetchMessage](https://reference.aspose.com/email/net/aspose.email.clients.pop3/pop3client/fetchmessage/#fetchmessage/). O seguinte código de exemplo mostra como salvar uma mensagem pelo seu número de sequência. Nesse caso, o método [SaveMessage](https://reference.aspose.com/email/net/aspose.email.clients.pop3/pop3client/savemessage/#savemessage/) salva a mensagem no formato EML original sem analisá-la.

{{< gist "aspose-com-gists" "6e5185a63aec6fd70d83098e82b06a32" "Examples-CSharp-POP3-SaveToDiskWithoutParsing-SaveToDiskWithoutParsing.cs" >}}

### **Analisar Mensagem Antes de Salvar**

O seguinte código de exemplo usa o método [FetchMessage](https://reference.aspose.com/email/net/aspose.email.clients.pop3/pop3client/fetchmessage/#fetchmessage/) da classe [Pop3Client](https://reference.aspose.com/email/net/aspose.email.clients.pop3/pop3client/) para recuperar uma mensagem de um servidor POP3 pelo seu número de sequência e, em seguida, salvar a mensagem no disco usando o assunto como nome do arquivo.

{{< gist "aspose-com-gists" "6e5185a63aec6fd70d83098e82b06a32" "Examples-CSharp-POP3-ParseMessageAndSave-ParseMessageAndSave.cs" >}}

## **Busca em Grupo de Mensagens**

O [Pop3Client](https://reference.aspose.com/email/net/aspose.email.clients.pop3/pop3client/) fornece um método [FetchMessages](https://docs.aspose.com/email/pt/net/working-with-messages-from-server/) que aceita um iterável de Números de Sequência ou ID Únicos e retorna uma lista de [MailMessage](https://reference.aspose.com/email/net/aspose.email/mailmessage/). O seguinte código de exemplo demonstra o uso do método [FetchMessages](https://docs.aspose.com/email/pt/net/working-with-messages-from-server/) para buscar mensagens por Números de Sequência e ID Único.

{{< gist "aspose-com-gists" "522d47278b8ca448dc1d7eb97193322c" "Examples-CSharp-POP3-Pop3FetchGroupMessages-1.cs" >}}

## **Filtrando Mensagens por Remetente, Destinatário ou Data**

A classe [Pop3Client](https://reference.aspose.com/email/net/aspose.email.clients.pop3/pop3client/), descrita em [Conectando-se a um Servidor POP3](https://docs.aspose.com/email/pt/net/connect-to-pop3-server/), fornece o método [ListMessages()](https://reference.aspose.com/email/net/aspose.email.clients.pop3/pop3client/listmessages/#listmessages/) que obtém todas as mensagens de uma caixa de correio. Para obter apenas mensagens que atendem a alguma condição, use o método sobrecarregado [ListMessages()](https://reference.aspose.com/email/net/aspose.email.clients.pop3/pop3client/listmessages/#listmessages/) que aceita [MailQuery](https://reference.aspose.com/email/net/aspose.email.tools.search/mailquery/) como argumento. A classe [MailQuery](https://reference.aspose.com/email/net/aspose.email.tools.search/mailquery/) fornece várias propriedades para especificar as condições da consulta, por exemplo, data, assunto, remetente, destinatário e assim por diante. A classe [MailQueryBuilder](https://reference.aspose.com/email/net/aspose.email.tools.search/mailquerybuilder/) é usada para construir a expressão de busca. Primeiro, todas as condições e restrições são definidas e, em seguida, [MailQuery](https://reference.aspose.com/email/net/aspose.email.tools.search/mailquery/) é preenchido com a consulta desenvolvida por [MailQueryBuilder](https://reference.aspose.com/email/net/aspose.email.tools.search/mailquerybuilder/). O objeto da classe [MailQuery](https://reference.aspose.com/email/net/aspose.email.tools.search/mailquery/) é usado pelo [Pop3Client](https://reference.aspose.com/email/net/aspose.email.clients.pop3/pop3client/) para extrair as informações filtradas do servidor. Este artigo mostra como filtrar mensagens de email de uma caixa de correio. O primeiro exemplo ilustra como filtrar mensagens com base na data e no assunto. Também mostramos como filtrar por outros critérios e como construir consultas mais complexas. Também mostra a aplicação do filtro de Data e Hora para recuperar emails específicos da caixa de correio. Além disso, também mostra como aplicar filtragem com diferenciação entre maiúsculas e minúsculas.

### **Filtrando Mensagens da Caixa de Correio**

Para filtrar mensagens de uma caixa de correio:

1. [Conecte-se e faça login em um servidor POP3](https://docs.aspose.com/email/pt/net/connect-to-pop3-server/#connecting-to-pop3-server).
2. Crie uma instância de [MailQuery](https://reference.aspose.com/email/net/aspose.email.tools.search/mailquery/) e defina as propriedades desejadas.
3. Chame o método [`Pop3Client.ListMessages(MailQuery query)`](https://reference.aspose.com/email/net/aspose.email.clients.pop3/pop3client/listmessages/#listmessages_8) e passe o [MailQuery](https://reference.aspose.com/email/net/aspose.email.tools.search/mailquery/) como parâmetro para obter somente as mensagens filtradas.

O seguinte código de exemplo mostra como conectar-se a uma caixa de correio POP3 e obter mensagens que chegaram hoje e têm a palavra "newsletter" no assunto.

{{< gist "aspose-com-gists" "6e5185a63aec6fd70d83098e82b06a32" "Examples-CSharp-POP3-FilterMessagesFromPOP3Mailbox-FilterMessagesFromPOP3Mailbox.cs" >}}

### **Obtendo Mensagens que Atendem a Critérios Específicos**

[Os exemplos de código acima](https://docs.aspose.com/email/pt/net/working-with-messages-from-server/#filtering-messages-from-mailbox) mostram como você pode filtrar mensagens com base no assunto do email e na data. Podemos usar outras propriedades para definir outras condições suportadas também. Abaixo estão alguns exemplos de como definir as condições usando [MailQuery](https://reference.aspose.com/email/net/aspose.email.tools.search/mailquery/).

Os trechos de código a seguir mostram como filtrar emails com base em outros critérios:

- Encontrar emails entregues hoje.
- Encontrar emails recebidos dentro de um intervalo.
- Encontrar emails de um remetente específico.
- Encontrar emails enviados de um domínio específico.
- Encontrar emails enviados para um destinatário específico.
  
#### **Data de Hoje**

O seguinte código de exemplo mostra como encontrar emails entregues hoje.

{{< gist "aspose-com-gists" "6e5185a63aec6fd70d83098e82b06a32" "Examples-CSharp-POP3-GetMessagesUsingSpecificCriteria-GetEmailsWithTodayDate.cs" >}}

#### **Intervalo de Datas**

O seguinte código de exemplo mostra como encontrar emails recebidos dentro de um intervalo.

{{< gist "aspose-com-gists" "6e5185a63aec6fd70d83098e82b06a32" "Examples-CSharp-POP3-GetMessagesUsingSpecificCriteria-GetEmailsOverDateRange.cs" >}}

#### **Remetente Específico**

O seguinte código de exemplo mostra como encontrar emails de um remetente específico.

{{< gist "aspose-com-gists" "6e5185a63aec6fd70d83098e82b06a32" "Examples-CSharp-POP3-GetMessagesUsingSpecificCriteria-GetSpecificSenderEmails.cs" >}}

#### **Domínio Específico**

O seguinte código de exemplo mostra como encontrar emails enviados de um domínio específico.

{{< gist "aspose-com-gists" "6e5185a63aec6fd70d83098e82b06a32" "Examples-CSharp-POP3-GetMessagesUsingSpecificCriteria-GetSpecificDomainEmails.cs" >}}

#### **Destinatário Específico**

O seguinte código de exemplo mostra como encontrar emails enviados para um destinatário específico.

{{< gist "aspose-com-gists" "6e5185a63aec6fd70d83098e82b06a32" "Examples-CSharp-POP3-GetMessagesUsingSpecificCriteria-GetSpecificRecipientEmails.cs" >}}

### **Construindo Consultas Complexas**

Se diferentes propriedades do [MailQueryBuilder](https://reference.aspose.com/email/net/aspose.email.tools.search/mailquerybuilder/) forem definidas em declarações separadas, então todas as condições devem ser atendidas. Por exemplo, se quisermos obter mensagens dentro de um intervalo de datas e de um host específico, precisamos escrever três declarações.

#### **Combinando Consultas com AND**

O seguinte código de exemplo mostra como combinar consultas com AND.

{{< gist "aspose-com-gists" "6e5185a63aec6fd70d83098e82b06a32" "Examples-CSharp-POP3-BuildComplexQueries-CombineQueriesWithAND.cs" >}}

#### **Combinando Consultas com OR**

O [MailQueryBuilder](https://reference.aspose.com/email/net/aspose.email.tools.search/mailquerybuilder/) fornece o método [Or()](https://reference.aspose.com/email/net/aspose.email.tools.search/mailquerybuilder/or/#or) que aceita duas instâncias de [MailQuery](https://reference.aspose.com/email/net/aspose.email.tools.search/mailquery/) como parâmetros. Ele obtém as mensagens que atendem a qualquer uma das duas condições especificadas. O seguinte código de exemplo mostra como filtrar mensagens que possuem “teste” no assunto ou “noreply@host.com” como remetente. O seguinte código de exemplo mostra como combinar consultas com OR.

{{< gist "aspose-com-gists" "6e5185a63aec6fd70d83098e82b06a32" "Examples-CSharp-POP3-BuildComplexQueries-CombiningQueriesWithOR.cs" >}}

#### **Aplicando Filtros Sensíveis a Maiúsculas e Minúsculas**

A API também fornece a capacidade de filtrar emails da caixa de correio com base em um critério sensível a maiúsculas e minúsculas. Os seguintes métodos fornecem a capacidade de pesquisar emails especificando um sinalizador sensível a maiúsculas.

- Método `Aspose.Email.StringComparisonField.Contains(string value, bool ignoreCase)`
- Método `Aspose.Email.StringComparisonField.Equals(string value, bool ignoreCase)`
- Método `Aspose.Email.StringComparisonField.NotContains(string value, bool ignoreCase)`
- Método `Aspose.Email.StringComparisonField.NotEquals(string value, bool ignoreCase)`

{{< gist "aspose-com-gists" "6e5185a63aec6fd70d83098e82b06a32" "Examples-CSharp-POP3-ApplyCaseSensitiveFilters-ApplyCaseSensitiveFilters.cs" >}}