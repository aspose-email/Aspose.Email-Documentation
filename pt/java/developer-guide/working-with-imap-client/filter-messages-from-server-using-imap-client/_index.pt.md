---
title: "Filtrar Mensagens do Servidor Usando Cliente IMAP"
url: /pt/java/filter-messages-from-server-using-imap-client/
weight: 40
type: docs
---

A classe [ImapClient](https://reference.aspose.com/email/java/com.aspose.email/imapclient/) fornece o método [listMessages()](https://reference.aspose.com/email/java/com.aspose.email/imapclient/#listMessages--) que obtém todas as mensagens de uma caixa de entrada. Para obter apenas as mensagens que correspondem a alguma condição, use o método sobrecarregado [listMessages()](https://reference.aspose.com/email/java/com.aspose.email/imapclient/#listMessages--) que recebe [MailQuery](https://reference.aspose.com/email/java/com.aspose.email/mailquery/) como argumento. A classe [MailQuery](https://reference.aspose.com/email/java/com.aspose.email/mailquery/) fornece várias propriedades para especificar as condições, por exemplo, data, assunto, remetente, destinatário e assim por diante. O primeiro exemplo ilustra como filtrar mensagens com base na data e no assunto. Também mostramos como filtrar por outros critérios e como construir consultas mais complexas. A API também oferece a capacidade de aplicar critérios de pesquisa que diferenciam maiúsculas de minúsculas para corresponder a critérios de filtragem exatos. A API também permite especificar a codificação da string de pesquisa para filtrar mensagens da caixa de entrada.

## **Filtrando Mensagens da Caixa de Entrada**

1. [Conectar e fazer login em um servidor IMAP](/email/java/connecting-to-imap-server#connecting-with-imap-server)
1. Crie uma instância de [MailQuery](https://reference.aspose.com/email/java/com.aspose.email/mailquery/) e defina as propriedades
1. Chame o método [ImapClient.listMessages(MailQuery query)](https://reference.aspose.com/email/java/com.aspose.email/imapclient/#listMessages-com.aspose.email.MailQuery-) e passe o [MailQuery](https://reference.aspose.com/email/java/com.aspose.email/mailquery/) com os parâmetros para obter apenas as mensagens filtradas.

O seguinte trecho de código mostra como se conectar a uma caixa de entrada IMAP e obter mensagens que chegaram hoje e têm a palavra "newsletter" no assunto.

~~~Java
// Para exemplos completos e arquivos de dados, acesse https://github.com/aspose-email/Aspose.Email-for-Java
// Conectar e fazer login no IMAP
final String host = "host";
final int port = 143;
final String username = "user@host.com";
final String password = "password";
ImapClient client = new ImapClient(host, port, username, password);
client.selectFolder("Inbox");
// Definir condições, Assunto contém "Newsletter", Emails que chegaram hoje
ImapQueryBuilder builder = new ImapQueryBuilder();
builder.getSubject().contains("Newsletter");
builder.getInternalDate().on(new Date());
// Construir a consulta e obter a lista de mensagens
MailQuery query = builder.getQuery();
ImapMessageInfoCollection messages = client.listMessages(query);
System.out.println("Imap: " + messages.size() + " mensagem(ns) encontrada(s).");
// Desconectar do IMAP
client.dispose();
~~~

## **Obter Mensagens que Atendam a Critérios Específicos**

[Os exemplos de código acima](#filtering-messages-from-mailbox) filtram mensagens com base no assunto e na data do email. Podemos usar outras propriedades para definir outras condições suportadas também. Abaixo estão alguns exemplos de como definir as condições usando [MailQuery](https://reference.aspose.com/email/java/com.aspose.email/mailquery/). Os trechos de código a seguir mostram como filtrar emails em:

1. Data de hoje.
1. Um intervalo de datas.
1. De um remetente específico.
1. De um domínio específico.
1. De um destinatário específico.

### **Data de Hoje**

O seguinte trecho de código mostra como filtrar emails na Data de Hoje.

~~~Java
// Para exemplos completos e arquivos de dados, acesse https://github.com/aspose-email/Aspose.Email-for-Java
// Emails que chegaram hoje
MailQueryBuilder builder = new MailQueryBuilder();
builder.getInternalDate().on(new Date());
~~
### **Intervalo de Datas**
O seguinte trecho de código mostra como filtrar emails no intervalo de datas.

~~~Java
// Para exemplos completos e arquivos de dados, acesse https://github.com/aspose-email/Aspose.Email-for-Java
// Emails que chegaram nos últimos 7 dias
Calendar cal = Calendar.getInstance();
builder.getInternalDate().before(cal.getTime());
cal.add(Calendar.DATE, -7);
builder.getInternalDate().since(cal.getTime());
~~~

### **Remetente Específico**

O seguinte trecho de código mostra como filtrar emails de um remetente específico.

~~~Java
// Para exemplos completos e arquivos de dados, acesse https://github.com/aspose-email/Aspose.Email-for-Java
// Obter emails de remetente específico
builder.getFrom().contains("saqib.razzaq@127.0.0.1");
~~~

### **Domínio Específico**

O seguinte trecho de código mostra como filtrar emails de um domínio específico.

~~~Java
// Para exemplos completos e arquivos de dados, acesse https://github.com/aspose-email/Aspose.Email-for-Java
// Obter emails de domínio específico
builder.getFrom().contains("SpecificHost.com");
~~~

### **Destinatário Específico**

O seguinte trecho de código mostra como filtrar emails para um destinatário específico.

~~~Java
// Para exemplos completos e arquivos de dados, acesse https://github.com/aspose-email/Aspose.Email-for-Java
// Obter emails enviados para destinatário específico
builder.getTo().contains("recipient");
~~~

## **Construindo Consultas Complexas**

Se diferentes propriedades de [MailQueryBuilder](https://reference.aspose.com/email/java/com.aspose.email/mailquerybuilder/) forem definidas em declarações separadas, todas as condições serão correspondidas. Por exemplo, se quisermos obter mensagens entre um intervalo de datas e de um host específico, precisaremos escrever três declarações.

### **Combinando Consultas com AND**

O seguinte trecho de código mostra como combinar consultas com AND.

~~~Java
// Para exemplos completos e arquivos de dados, acesse https://github.com/aspose-email/Aspose.Email-for-Java
// Emails de host específico, obter todos os emails que chegaram antes de hoje e todos os emails que chegaram desde 7 dias atrás
builder.getFrom().contains("SpecificHost.com");

Calendar cal = Calendar.getInstance();
builder.getInternalDate().before(cal.getTime());
cal.add(Calendar.DATE, -7);
builder.getInternalDate().since(cal.getTime());
~~~

### **Combinando Consultas com OR**

[MailQueryBuilder](https://reference.aspose.com/email/java/com.aspose.email/mailquerybuilder/) fornece o método [or()](https://reference.aspose.com/email/java/com.aspose.email/mailquerybuilder/#or-com.aspose.email.MailQuery-com.aspose.email.MailQuery-) que recebe duas instâncias de [MailQuery](https://reference.aspose.com/email/java/com.aspose.email/mailquery/) como parâmetros. Ele obtém as mensagens que correspondem a qualquer uma das duas condições especificadas. O seguinte trecho de código mostra como filtrar mensagens que têm “test” no assunto ou “noreply@host.com” como remetente. O seguinte trecho de código mostra como combinar consultas com OR.

~~~Java
// Para exemplos completos e arquivos de dados, acesse https://github.com/aspose-email/Aspose.Email-for-Java
// Especificar condição OR
builder.or(builder.getSubject().contains("test"), builder.getFrom().contains("noreply@host.com"));
~~~

## **Filtragem pelo InternalDate**

As mensagens podem ser extraídas do servidor com base no InternalDate, no entanto, às vezes o servidor não retorna todas as mensagens visíveis na caixa de entrada. O motivo pode ser o fuso horário do servidor porque pode não ser UTC para todos os servidores como [Gmail](https://www.google.com.ua/search?client=opera&q=timezone+gmail&sourceid=opera&ie=utf-8&oe=utf-8&channel=suggest#channel=suggest&q=gmail+server+timezone++). Aspose envia comandos como 008 SEARCH ON 4-May-2014 de acordo com o [protocolo IMAP](https://datatracker.ietf.org/doc/html/rfc1730), no entanto, o resultado pode diferir devido às configurações de fuso horário do servidor. Um novo membro é adicionado em [ImapMessageInfo](https://reference.aspose.com/email/java/com.aspose.email/imapmessageinfo/) como [InternalDate](https://reference.aspose.com/email/java/com.aspose.email/imapmessageinfo/#getInternalDate--) que ajuda ainda mais na filtragem das mensagens. O seguinte trecho de código mostra o uso de [InternalDate](https://reference.aspose.com/email/java/com.aspose.email/imapmessageinfo/#getInternalDate--) para filtrar mensagens.

~~~Java
// Para exemplos completos e arquivos de dados, acesse https://github.com/aspose-email/Aspose.Email-for-Java
// Conectar e fazer login no IMAP
final String host = "host";
final int port = 143;
final String username = "user@host.com";
final String password = "password";
ImapClient client = new ImapClient(host, port, username, password);
client.selectFolder("Inbox");

// Definir condições, Assunto contém "Newsletter", Emails que chegaram hoje
ImapQueryBuilder builder = new ImapQueryBuilder();
builder.getSubject().contains("Newsletter");
builder.getInternalDate().on(new Date());

// Construir a consulta e obter a lista de mensagens
MailQuery query = builder.getQuery();
ImapMessageInfoCollection messages = client.listMessages(query);
for (ImapMessageInfo info : messages) {
    System.out.println("Data Interna: " + info.getInternalDate());
}

// Desconectar do IMAP
client.dispose();
~~~

### **Filtragem de Emails Sensível a Maiúsculas e Minúsculas**

O seguinte trecho de código mostra como usar a filtragem de emails sensível a maiúsculas e minúsculas.

~~~Java
// Para exemplos completos e arquivos de dados, acesse https://github.com/aspose-email/Aspose.Email-for-Java
// Definir condições, Assunto contém "Newsletter", Emails que chegaram hoje
ImapQueryBuilder builder = new ImapQueryBuilder();
builder.getSubject().contains("Newsletter", true);
builder.getInternalDate().on(new Date());
MailQuery query = builder.getQuery();
~~~

### **Especificar Codificação para o Construtor de Consultas**

O construtor de [ImapQueryBuilder](https://reference.aspose.com/email/java/com.aspose.email/imapquerybuilder/) da API pode ser usado para especificar a codificação para a string de pesquisa. Isso também pode ser definido usando a propriedade [DefaultEncoding](https://reference.aspose.com/email/java/com.aspose.email/mailquerybuilder/#getDefaultEncoding--) do MailQueryBuilder. O seguinte trecho de código mostra como especificar a codificação para o construtor de consultas.

~~~Java
// Para exemplos completos e arquivos de dados, acesse https://github.com/aspose-email/Aspose.Email-for-Java
// Definir condições
ImapQueryBuilder builder = new ImapQueryBuilder(Charset.forName("utf-8"));
builder.getSubject().contains("ğüşıöç", true);
MailQuery query = builder.getQuery();
~~~

### **Filtrar Mensagens com Suporte a Paginação**

O [ImapClient](https://reference.aspose.com/email/java/com.aspose.email/imapclient/) fornece a capacidade de pesquisar mensagens da caixa de entrada e listá-las com suporte a paginação. O seguinte trecho de código mostra como filtrar mensagens com suporte a paginação.

~~~Java
// Para exemplos completos e arquivos de dados, acesse https://github.com/aspose-email/Aspose.Email-for-Java
/// <summary>
/// Este exemplo mostra como pesquisar mensagens usando o ImapClient da API com suporte a paginação
/// Introduzido no Aspose.Email para .NET 6.4.0
/// </summary>
final ImapClient client = new ImapClient("host.domain.com", 84, "username", "password");
try {
    try {
        // Adicionar algumas mensagens de teste
        int messagesNum = 12;
        int itemsPerPage = 5;
        MailMessage message = null;
        for (int i = 0; i < messagesNum; i++) {
            message = new MailMessage("from@domain.com", "to@domain.com", "EMAILNET-35128 - " + UUID.randomUUID(), "111111111111111");
            client.appendMessage(ImapFolderInfo.IN_BOX, message);
        }
        String body = "2222222222222";
        for (int i = 0; i < messagesNum; i++) {
            message = new MailMessage("from@domain.com", "to@domain.com", "EMAILNET-35128 - " + UUID.randomUUID(), body);
            client.appendMessage(ImapFolderInfo.IN_BOX, message);
        }

        client.selectFolder("Inbox");
        ImapQueryBuilder iqb = new ImapQueryBuilder();
        iqb.getBody().contains(body);
        MailQuery query = iqb.getQuery();

        client.selectFolder(ImapFolderInfo.IN_BOX);
        ImapMessageInfoCollection totalMessageInfoCol = client.listMessages(query);
        System.out.println(totalMessageInfoCol.size());

        //////////////////////////////////////////////////////

        List<ImapPageInfo> pages = new ArrayList<ImapPageInfo>();

        PageSettings ps = new PageSettings();
        ps.setFolderName(ImapFolderInfo.IN_BOX);
        PageInfo pi = new PageInfo(itemsPerPage);
        ImapPageInfo pageInfo = client.listMessagesByPage(query, pi, ps);

        pages.add(pageInfo);
        while (!pageInfo.getLastPage()) {
            pageInfo = client.listMessagesByPage(query, pageInfo.getNextPage(), ps);
            pages.add(pageInfo);
        }
        int retrievedItems = 0;
        // conversão de foreach para while
        for (ImapPageInfo folderCol : pages) {
            retrievedItems += folderCol.getItems().size();
        }
    } finally {
    }
} finally {
    if (client != null)
        client.dispose();
}
~~~

## **Filtrar Mensagens com Sinalizador Personalizado**

~~~Java
// Para exemplos completos e arquivos de dados, acesse https://github.com/aspose-email/Aspose.Email-for-Java
ImapQueryBuilder queryBuilder = new ImapQueryBuilder();

queryBuilder.hasFlags(ImapMessageFlags.keyword("custom1"));

queryBuilder.hasNoFlags(ImapMessageFlags.keyword("custom2"));
~~~

## **Filtrar Mensagens Usando Pesquisa Personalizada**

Por exemplo, o padrão RFC 3501 não permite que uma pesquisa de mensagens seja feita com base na existência de anexos nas mensagens. Mas o **Gmail** oferece [Extensões IMAP](https://developers.google.com/gmail/imap/imap-extensions) que permitem realizar esse tipo de pesquisa. Aspose.Email fornece o método [customSearch](https://reference.aspose.com/email/java/com.aspose.email/imapquerybuilder/#customSearch-java.lang.String-) da classe [ImapQueryBuilder](https://reference.aspose.com/email/java/com.aspose.email/imapquerybuilder/) para fazer a consulta correspondente. 

O exemplo de código abaixo mostra como recuperar uma lista de mensagens de email do servidor que possuem anexos, usando o protocolo IMAP e um critério de pesquisa personalizado:

```java
ImapQueryBuilder builder = new ImapQueryBuilder();
builder.customSearch("X-GM-RAW \"has:attachment\"");
MailQuery query = builder.getQuery();
messageInfoCol = client.listMessages(query);
```