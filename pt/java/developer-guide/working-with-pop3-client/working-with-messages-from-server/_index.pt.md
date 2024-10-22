---
title: "Trabalhando com Mensagens do Servidor"
url: /pt/java/trabalhando-com-mensagens-do-servidor/
weight: 50
type: docs
---


## **Obtendo Informações da Caixa de Correio**

Podemos obter informações sobre a caixa de correio, como o número de mensagens e o tamanho da caixa de correio, utilizando os métodos [getMailBoxSize](https://reference.aspose.com/email/java/com.aspose.email/pop3client/#getMailboxSize--) e [getMailBoxInfo](https://reference.aspose.com/email/java/com.aspose.email/pop3client/#getMailboxInfo--) da classe [Pop3Client](https://reference.aspose.com/email/java/com.aspose.email/pop3client/).

- O método [getMailBoxSize](https://reference.aspose.com/email/java/com.aspose.email/pop3client/#getMailboxSize--) retorna o tamanho da caixa de correio em bytes.
- O método [getMailBoxInfo](https://reference.aspose.com/email/java/com.aspose.email/pop3client/#getMailboxInfo--) retorna um objeto do tipo [Pop3MailBoxInfo](https://reference.aspose.com/email/java/com.aspose.email/pop3mailboxinfo/).

Também é possível obter o número de mensagens utilizando a propriedade [MessageCount](https://reference.aspose.com/email/java/com.aspose.email/pop3mailboxinfo/#getMessageCount--) e o tamanho utilizando a propriedade [OccupiedSize](https://reference.aspose.com/email/java/com.aspose.email/pop3mailboxinfo/#getOccupiedSize--) da classe [Pop3MailBoxInfo](https://reference.aspose.com/email/java/com.aspose.email/pop3mailboxinfo/). O seguinte código de exemplo mostra como obter informações sobre a caixa de correio. Ele mostra como:

1. Criar um [Pop3Client](https://reference.aspose.com/email/java/com.aspose.email/pop3client/).
1. Conectar a um servidor POP3.
1. Obter o tamanho da caixa de correio.
1. Obter informações da caixa de correio.
1. Obter o número de mensagens na caixa de correio.
1. Obter o tamanho ocupado.

~~~Java
// Para exemplos completos e arquivos de dados, acesse https://github.com/aspose-email/Aspose.Email-for-Java

Pop3Client client = new Pop3Client();
// Especifique host, nome de usuário, senha, porta e opções de segurança para seu cliente
client.setHost("pop.gmail.com");
client.setUsername("your.username@gmail.com");
client.setPassword("your.password");
client.setPort(995);
client.setSecurityOptions(SecurityOptions.Auto);

// Obter o tamanho da caixa de correio, Obter informações da caixa de correio, número de mensagens na caixa de correio
long nSize = client.getMailboxSize();
System.out.println("O tamanho da caixa de correio é " + nSize + " bytes.");
Pop3MailboxInfo info = client.getMailboxInfo();
int nMessageCount = info.getMessageCount();
System.out.println("O número de mensagens na caixa de correio é " + nMessageCount);
long nOccupiedSize = info.getOccupiedSize();
System.out.println("O tamanho ocupado é " + nOccupiedSize);
~~~

## **Obtendo a Contagem de Emails na Caixa de Correio**

O seguinte trecho de código mostra como contar as mensagens de email em uma caixa de correio.

~~~Java
// Para exemplos completos e arquivos de dados, acesse https://github.com/aspose-email/Aspose.Email-for-Java
Pop3Client client = new Pop3Client("pop3.server.com", "username", "password");
try {
    client.setSecurityOptions(SecurityOptions.Auto);
    int i = client.getMessageCount();
    System.out.println("Contagem de mensagens: " + i);
} catch (Pop3Exception ex) {
    System.out.println("Erro:" + ex.toString());
}
~~~

Aspose.Email permite que os desenvolvedores trabalhem com emails de várias maneiras diferentes. Por exemplo, eles podem recuperar informações do cabeçalho antes de decidir se devem ou não baixar um email. Ou eles podem recuperar emails de um servidor e salvá-los sem analisá-los (mais rápido) ou após analisá-los (mais lento). Este artigo mostra como recuperar e converter emails.

## **Recuperando Informações dos Cabeçalhos de Email**

Os cabeçalhos de email podem nos fornecer informações sobre uma mensagem de email que podemos usar para decidir se devemos ou não recuperar a mensagem de email completa. Normalmente, as informações do cabeçalho contêm remetente, assunto, data de recebimento, etc. (Os cabeçalhos de email são descritos em detalhes em [Personalizando Cabeçalhos de Email](/email/java/creating-and-setting-contents-of-emails/#set-email-headers). Esse assunto é especificamente sobre enviar um email com SMTP, mas as informações do conteúdo do cabeçalho de email permanecem válidas para emails POP3). Os seguintes exemplos mostram como recuperar cabeçalhos de email de um servidor POP3 pelo número de sequência da mensagem.

~~~Java
// Para exemplos completos e arquivos de dados, acesse https://github.com/aspose-email/Aspose.Email-for-Java
// Crie uma instância da classe Pop3Client
Pop3Client client = new Pop3Client();

// Especifique host, nome de usuário, senha, porta e opções de segurança para seu cliente
client.setHost("pop.gmail.com");
client.setUsername("your.username@gmail.com");
client.setPassword("your.password");
client.setPort(995);
client.setSecurityOptions(SecurityOptions.Auto);
try {
    HeaderCollection headers = client.getMessageHeaders(1);
    for (int i = 0; i < headers.size(); i++) {
        // Exibir chave e valor na coleção de cabeçalho
        System.out.print(headers.getKey(i));
        System.out.print(" : ");
        System.out.println(headers.get(i));
    }
} catch (Exception ex) {
    System.out.println(ex.getMessage());
} finally {
    client.dispose();
}
~~~

## **Recuperando Mensagens de Email**

A classe [Pop3Client](https://reference.aspose.com/email/java/com.aspose.email/pop3client/) proporciona a capacidade de recuperar mensagens de email do servidor POP3 e analisá-las em uma instância de [MailMessage](https://reference.aspose.com/email/java/com.aspose.email/mailmessage/) com a ajuda dos componentes [MailMessage](https://reference.aspose.com/email/java/com.aspose.email/mailmessage/). A classe [MailMessage](https://reference.aspose.com/email/java/com.aspose.email/mailmessage/) contém várias propriedades e métodos para manipular o conteúdo do email. Usando o método [fetchMessage](https://reference.aspose.com/email/java/com.aspose.email/pop3client/#fetchMessage-int-) da classe [Pop3Client](https://reference.aspose.com/email/java/com.aspose.email/pop3client/), você pode obter uma instância de [MailMessage](https://reference.aspose.com/email/java/com.aspose.email/mailmessage/) diretamente do servidor POP3. O seguinte trecho de código mostra como recuperar uma mensagem de email completa do servidor POP3.

~~~Java
// Para exemplos completos e arquivos de dados, acesse https://github.com/aspose-email/Aspose.Email-for-Java
// Crie uma instância da classe Pop3Client
Pop3Client client = new Pop3Client();

// Especifique host, nome de usuário, senha, porta e opções de segurança para seu cliente
client.setHost("pop.gmail.com");
client.setUsername("your.username@gmail.com");
client.setPassword("your.password");
client.setPort(995);
client.setSecurityOptions(SecurityOptions.Auto);
try {
    int messageCount = client.getMessageCount();
    // Crie uma instância da classe MailMessage e recupere a mensagem
    MailMessage message;
    for (int i = 1; i <= messageCount; i++) {
        message = client.fetchMessage(i);
        System.out.println("De:" + message.getFrom());
        System.out.println("Assunto:" + message.getSubject());
        System.out.println(message.getHtmlBody());
    }
} catch (Exception ex) {
    System.out.println(ex.getMessage());
} finally {
    client.dispose();
}
~~~

## **Recuperando Informações Resumidas de Mensagens Usando ID Único**

O Cliente POP3 da API pode recuperar informações resumidas da mensagem do servidor usando o ID único da mensagem. Isso fornece acesso rápido às informações resumidas da mensagem sem primeiro recuperar a mensagem completa do servidor. O seguinte trecho de código mostra como recuperar informações resumidas da mensagem.

~~~Java
// Para exemplos completos e arquivos de dados, acesse https://github.com/aspose-email/Aspose.Email-for-Java
String uniqueId = "id único de uma mensagem do servidor";
Pop3Client client = new Pop3Client("host.domain.com", 456, "username", "password");
client.setSecurityOptions(SecurityOptions.Auto);
Pop3MessageInfo messageInfo = client.getMessageInfo(uniqueId);

if (messageInfo != null) {
    System.out.println(messageInfo.getSubject());
    System.out.println(messageInfo.getDate());
}
~~~ 

## **Listando Mensagens com MultiConnection**

[Pop3Client](https://reference.aspose.com/email/java/com.aspose.email/pop3client/) fornece uma propriedade [UseMultiConnection](https://reference.aspose.com/email/java/com.aspose.email/pop3client/#setUseMultiConnection-int-) que pode ser usada para criar várias conexões para operações pesadas. Você também pode definir o número de conexões a serem usadas durante o modo de multiconexão usando [Pop3Client.ConnectionsQuantity](https://reference.aspose.com/email/java/com.aspose.email/pop3client/#setConnectionsQuantity-int-). O seguinte trecho de código demonstra o uso do modo de multiconexão para listar mensagens e compara seu desempenho com o modo de conexão única.

~~~Java
// Para exemplos completos e arquivos de dados, acesse https://github.com/aspose-email/Aspose.Email-for-Java
// Crie uma instância da classe Pop3Client
Pop3Client pop3Client = new Pop3Client();
pop3Client.setHost("<HOST>");
pop3Client.setPort(995);
pop3Client.setUsername("<USERNAME>");
pop3Client.setPassword("<PASSWORD>");

pop3Client.setConnectionsQuantity(5);
pop3Client.setUseMultiConnection(MultiConnectionMode.Enable);
long multiConnectionModeStartTime = System.currentTimeMillis();
Pop3MessageInfoCollection messageInfoCol1 = pop3Client.listMessages();
long multiConnectionModeTimeSpan = System.currentTimeMillis() - multiConnectionModeStartTime;

pop3Client.setUseMultiConnection(MultiConnectionMode.Disable);
long singleConnectionModeStartTime = System.currentTimeMillis();
Pop3MessageInfoCollection messageInfoCol2 = pop3Client.listMessages();
long singleConnectionModeTimeSpan = System.currentTimeMillis() - singleConnectionModeStartTime;

System.out.println("multiConnectionModeTimeSpan: " + multiConnectionModeTimeSpan);
System.out.println("singleConnectionModeTimeSpan: " + singleConnectionModeTimeSpan);
double performanceRelation = singleConnectionModeTimeSpan / multiConnectionModeTimeSpan;
System.out.println("Relação de Desempenho: " + performanceRelation);
~~~ 

{{% alert color="primary" %}} 

Por favor, note que o uso do modo de multiconexão não garante aumento de desempenho.

{{% /alert %}} 

## **Buscando Mensagens do Servidor e Salvando no Disco**

### **Salvar Mensagem no Disco sem Análise**

Se você deseja baixar mensagens de email do servidor POP3 sem analisá-las, use a função [saveMessage](https://reference.aspose.com/email/java/com.aspose.email/pop3client/#saveMessage\(java.lang.String,%20java.io.OutputStream\)) da classe [Pop3Client](https://reference.aspose.com/email/java/com.aspose.email/pop3client/). A função [saveMessage](https://reference.aspose.com/email/java/com.aspose.email/pop3client/#saveMessage-com.aspose.email.IConnection-java.lang.String-java.io.OutputStream-) não analisa a mensagem de email, portanto, é mais rápida que a função [fetchMessage](https://reference.aspose.com/email/java/com.aspose.email/pop3client/#fetchMessage-int-). O seguinte trecho de código mostra como salvar uma mensagem pelo seu número de sequência, neste caso, o número 1. O método [saveMessage](https://reference.aspose.com/email/java/com.aspose.email/pop3client/#saveMessage-com.aspose.email.IConnection-java.lang.String-java.io.OutputStream-) salva a mensagem no formato EML original sem analisá-la.

~~~Java
// Para exemplos completos e arquivos de dados, acesse https://github.com/aspose-email/Aspose.Email-for-Java
// O caminho para o diretório de arquivos.
String dataDir = "pop3/";
String dstEmail = dataDir + "InsertHeaders.eml";

// Crie uma instância da classe Pop3Client
Pop3Client client = new Pop3Client();

// Especifique host, nome de usuário, senha, porta e opções de segurança para seu cliente
client.setHost("pop.gmail.com");
client.setUsername("your.username@gmail.com");
client.setPassword("your.password");
client.setPort(995);
client.setSecurityOptions(SecurityOptions.Auto);

try {
    // Salvar mensagem no disco pelo número de sequência da mensagem
    client.saveMessage(1, dstEmail);
    client.dispose();
} catch (Exception ex) {
    System.out.println(ex.getMessage());
}
System.out.println("Mensagens de email recuperadas usando POP3 ");
~~~ 

### **Analisar Mensagem Antes de Salvar**

O seguinte trecho de código utiliza o método [fetchMessage](https://reference.aspose.com/email/java/com.aspose.email/pop3client/#fetchMessage-int-) da classe [Pop3Client](https://reference.aspose.com/email/java/com.aspose.email/pop3client/) para recuperar uma mensagem de um servidor POP3 pelo seu número de sequência e, em seguida, salvar a mensagem no disco utilizando o assunto como nome do arquivo.

~~~Java
// Para exemplos completos e arquivos de dados, acesse https://github.com/aspose-email/Aspose.Email-for-Java
// O caminho para o diretório de arquivos.
String dataDir = "pop3/";

// Crie uma instância da classe Pop3Client
Pop3Client client = new Pop3Client();

// Especifique host, nome de usuário, senha, porta e opções de segurança para seu cliente
client.setHost("pop.gmail.com");
client.setUsername("your.username@gmail.com");
client.setPassword("your.password");
client.setPort(995);
client.setSecurityOptions(SecurityOptions.Auto);

try {
    // Buscar a mensagem pelo seu número de sequência e salvar a mensagem usando seu assunto como nome do arquivo
    MailMessage msg = client.fetchMessage(1);
    msg.save(dataDir + "first-message_out.eml", SaveOptions.getDefaultEml());
    client.dispose();
} catch (Exception ex) {
    System.out.println(ex.getMessage());
} finally {
    client.dispose();
}
~~~ 

## **Grupo de Mensagens**

[Pop3Client](https://reference.aspose.com/email/java/com.aspose.email/pop3client/) fornece um método [fetchMessages](https://reference.aspose.com/email/java/com.aspose.email/pop3client/#fetchMessagesBySequences-com.aspose.email.IConnection-java.lang.Iterable-java.lang.Integer--) que aceita um iterável de números de sequência ou ID únicos e retorna uma lista de [MailMessage](https://reference.aspose.com/email/java/com.aspose.email/mailmessage/). O seguinte trecho de código demonstra o uso do método [fetchMessages](https://reference.aspose.com/email/java/com.aspose.email/pop3client/#fetchMessagesBySequences-com.aspose.email.IConnection-java.lang.Iterable-java.lang.Integer--) para buscar mensagens por números de sequência e ID únicos.

~~~Java
// Para exemplos completos e arquivos de dados, acesse https://github.com/aspose-email/Aspose.Email-for-Java
// Crie uma instância da classe Pop3Client
Pop3Client pop3Client = new Pop3Client();
pop3Client.setHost("<HOST>");
pop3Client.setPort(995);
pop3Client.setUsername("<USERNAME>");
pop3Client.setPassword("<PASSWORD>");

Pop3MessageInfoCollection messageInfoCol = pop3Client.listMessages();
System.out.println("Contagem do ListMessages: " + messageInfoCol.size());

List<Integer> sequenceNumberAr = new ArrayList<Integer>();
List<String> uniqueIdAr = new ArrayList<String>();
for (Pop3MessageInfo mi : messageInfoCol) {
    sequenceNumberAr.add(mi.getSequenceNumber());
    uniqueIdAr.add(mi.getUniqueId());
}

for (MailMessage m : pop3Client.fetchMessagesBySequences(sequenceNumberAr)) {
    System.out.println("FetchMessages-sequenceNumberAr : " + m.getSubject());
}

for (MailMessage m : pop3Client.fetchMessagesByUids(uniqueIdAr)) {
    System.out.println("FetchMessages-uniqueIdAr : " + m.getSubject());
}
~~~ 

## **Filtrando Mensagens por Remetente, Destinatário ou Data**

A classe [Pop3Client](https://reference.aspose.com/email/java/com.aspose.email/pop3client/), descrita em [Conectando a um Servidor POP3](/email/java/connect-to-pop3-server/#connecting-to-pop3-server), fornece o método [listMessages](https://reference.aspose.com/email/java/com.aspose.email/pop3client/#listMessages--) que obtém todas as mensagens de uma caixa de correio. Para obter apenas mensagens que correspondem a alguma condição, use o método sobrecarregado [listMessages](https://reference.aspose.com/email/java/com.aspose.email/pop3client/#listMessages--) que aceita [MailQuery](https://reference.aspose.com/email/java/com.aspose.email/mailquery/) como argumento. A classe [MailQuery](https://reference.aspose.com/email/java/com.aspose.email/mailquery/) fornece várias propriedades para especificar as condições da consulta, como data, assunto, remetente, destinatário, etc. A classe [MailQueryBuilder](https://reference.aspose.com/email/java/com.aspose.email/mailquerybuilder/) é utilizada para construir a expressão de pesquisa. Primeiro, todas as condições e restrições são definidas e depois [MailQuery](https://reference.aspose.com/email/java/com.aspose.email/mailquery/) é preenchido com a consulta desenvolvida pelo [MailQueryBuilder](https://reference.aspose.com/email/java/com.aspose.email/mailquerybuilder/). O objeto da classe [MailQuery](https://reference.aspose.com/email/java/com.aspose.email/mailquery/) é utilizado pelo [Pop3Client](https://reference.aspose.com/email/java/com.aspose.email/pop3client/) para extrair as informações filtradas do servidor. Este artigo mostra como filtrar mensagens de email a partir de uma caixa de correio. O primeiro exemplo ilustra como filtrar mensagens com base em uma data e um assunto. Também mostramos como filtrar por outros critérios e como construir consultas mais complexas. Também demonstra a aplicação de filtro de Data e Hora para recuperar emails específicos da caixa de correio. Além disso, também mostra como aplicar filtragem que diferencia maiúsculas de minúsculas.

### **Filtrando Mensagens da Caixa de Correio**

Para filtrar mensagens de uma caixa de correio:

1. [Conecte-se e faça login em um servidor POP3](/email/java/connect-to-pop3-server#connecting-to-pop3-server).
1. Crie uma instância de [MailQuery](https://reference.aspose.com/email/java/com.aspose.email/mailquery/) e defina as propriedades desejadas.
1. Chame o método [Pop3Client.listMessages(MailQuery query)](https://reference.aspose.com/email/java/com.aspose.email/pop3client/#listMessages-com.aspose.email.MailQuery-) e passe o [MailQuery](https://reference.aspose.com/email/java/com.aspose.email/mailquery/) como parâmetro para obter apenas as mensagens filtradas.

O seguinte trecho de código mostra como conectar a uma caixa de correio POP3 e obter mensagens que chegaram hoje e possuem a palavra "newsletter" no assunto.

~~~Java
// Para exemplos completos e arquivos de dados, acesse https://github.com/aspose-email/Aspose.Email-for-Java
// Conecte-se e faça login no POP3
String host = "host";
int port = 110;
String username = "user@host.com";
String password = "password";
Pop3Client client = new Pop3Client(host, port, username, password);

// Defina condições, Assunto contém "Newsletter", Emails que chegaram hoje
MailQueryBuilder builder = new MailQueryBuilder();
builder.getSubject().contains("Newsletter");
builder.getInternalDate().on(new Date());
// Construa a consulta e obtenha a lista de mensagens
MailQuery query = builder.getQuery();
Pop3MessageInfoCollection messages = client.listMessages(query);
System.out.println("Pop3: " + messages.size() + " mensagem(s) encontrada(s).");
~~~ 

### **Obtendo Mensagens que Atendam a Critérios Específicos**

[Os exemplos de código acima](/email/java/working-with-messages-from-server/#filtering-messages-from-mailbox) filtram mensagens com base no assunto do email e na data. Podemos usar outras propriedades para definir outras condições suportadas também. Abaixo estão alguns exemplos de como definir as condições usando [MailQuery](https://reference.aspose.com/email/java/com.aspose.email/mailquery/).

Os trechos de código que seguem mostram como filtrar emails por outros critérios:

- Encontrar emails entregues hoje.
- Encontrar emails recebidos dentro de um intervalo.
- Encontrar emails de um remetente específico.
- Encontrar emails enviados de um domínio específico.
- Encontrar emails enviados para um destinatário específico.

#### **Data de Hoje**

O seguinte trecho de código mostra como encontrar emails entregues hoje.

~~~Java
// Para exemplos completos e arquivos de dados, acesse https://github.com/aspose-email/Aspose.Email-for-Java
// Emails que chegaram hoje
MailQueryBuilder builder = new MailQueryBuilder();
builder.getInternalDate().on(new Date());
~~~ 

#### **Intervalo de Datas**

O seguinte trecho de código mostra como encontrar emails recebidos dentro de um intervalo.

~~~Java
// Para exemplos completos e arquivos de dados, acesse https://github.com/aspose-email/Aspose.Email-for-Java
// Emails que chegaram nos últimos 7 dias
Calendar calendar = Calendar.getInstance();

builder.getInternalDate().before(calendar.getTime());
calendar.add(Calendar.DATE, -7);
builder.getInternalDate().since(calendar.getTime());
~~~ 

#### **Remetente Específico**

O seguinte trecho de código mostra como encontrar emails de um remetente específico.

~~~Java
// Para exemplos completos e arquivos de dados, acesse https://github.com/aspose-email/Aspose.Email-for-Java
// Obter emails de remetente específico
builder.getFrom().contains("saqib.razzaq@127.0.0.1");
~~~ 

#### **Domínio Específico**

O seguinte trecho de código mostra como encontrar emails enviados de um domínio específico.

~~~Java
// Para exemplos completos e arquivos de dados, acesse https://github.com/aspose-email/Aspose.Email-for-Java
// Obter emails de domínio específico
builder.getFrom().contains("SpecificHost.com");
~~~ 

#### **Destinatário Específico**

O seguinte trecho de código mostra como encontrar emails enviados para um destinatário específico.

~~~Java
// Para exemplos completos e arquivos de dados, acesse https://github.com/aspose-email/Aspose.Email-for-Java
// Obter emails enviados para destinatário específico
builder.getTo().contains("recipient");
~~~ 

### **Construindo Consultas Complexas**

Se diferentes propriedades do [MailQueryBuilder](https://reference.aspose.com/email/java/com.aspose.email/mailquerybuilder/) forem definidas em declarações separadas, todas as condições serão correspondidas. Por exemplo, se quisermos obter mensagens entre um intervalo de datas e de um host específico, precisamos escrever três declarações.

#### **Combinando Consultas com AND**

O seguinte trecho de código mostra como combinar consultas com AND.

~~~Java
// Para exemplos completos e arquivos de dados, acesse https://github.com/aspose-email/Aspose.Email-for-Java
// Emails de host específico, obter todos os emails que chegaram antes de hoje e todos os emails que chegaram desde 7 dias atrás
builder.getFrom().contains("SpecificHost.com");

Calendar calendar = Calendar.getInstance();

builder.getInternalDate().before(calendar.getTime());
calendar.add(Calendar.DATE, -7);
builder.getInternalDate().since(calendar.getTime());
~~~ 

#### **Combinando Consultas com OR**

[MailQueryBuilder](https://reference.aspose.com/email/java/com.aspose.email/mailquerybuilder/) fornece o método [or](https://reference.aspose.com/email/java/com.aspose.email/mailquerybuilder/#or-com.aspose.email.MailQuery-com.aspose.email.MailQuery-) que aceita duas instâncias de [MailQuery](https://reference.aspose.com/email/java/com.aspose.email/mailquery/) como parâmetros. Ele obtém as mensagens que correspondem a qualquer uma das duas condições especificadas. O seguinte trecho de código mostra como filtrar mensagens que têm "teste" no assunto ou "noreply@host.com" como remetente. O seguinte trecho de código mostra como combinar consultas com OR.

~~~Java
// Para exemplos completos e arquivos de dados, acesse https://github.com/aspose-email/Aspose.Email-for-Java
// Especifique condição OR
builder.or(builder.getSubject().contains("test"), builder.getFrom().contains("noreply@host.com"));
~~~ 

#### **Aplicando Filtros que Diferenciam Maiúsculas de Minúsculas**

A API também fornece a capacidade de filtrar emails da caixa de correio com base em um critério sensível a maiúsculas e minúsculas. Os seguintes métodos fornecem a capacidade de pesquisar emails especificando o sinalizador de sensibilidade a maiúsculas e minúsculas.

- Método StringComparisonField.contains(String value, boolean ignoreCase)
- Método StringComparisonField.equals(String value, boolean ignoreCase)
- Método StringComparisonField.notContains(String boolean, bool ignoreCase)
- Método StringComparisonField.notEquals(String boolean, bool ignoreCase)

~~~Java
// Para exemplos completos e arquivos de dados, acesse https://github.com/aspose-email/Aspose.Email-for-Java
// IgnoreCase é True
MailQueryBuilder builder1 = new MailQueryBuilder();
builder1.getFrom().contains("tesT", true);
MailQuery query1 = builder1.getQuery();
Pop3MessageInfoCollection messageInfoCol1 = client.listMessages(query1);
~~~