---
title: "Conectando-se ao Servidor IMAP"
url: /pt/java/connecting-to-imap-server/
weight: 10
type: docs
---


A classe [ImapClient](https://reference.aspose.com/email/java/com.aspose.email/imapclient/) permite que aplicativos gerenciem caixas de correio IMAP usando o protocolo IMAP. A classe [ImapClient](https://reference.aspose.com/email/java/com.aspose.email/imapclient/) é usada para se conectar a servidores de e-mail IMAP e gerenciar e-mails nas pastas de e-mail IMAP. Para se conectar a um servidor IMAP

1. Crie uma instância da classe [ImapClient](https://reference.aspose.com/email/java/com.aspose.email/imapclient/).
1. Especifique o hostname, nome de usuário e senha no [construtor do ImapClient](https://reference.aspose.com/email/java/com.aspose.email/imapclient/).

Uma vez que a instância [ImapClient](https://reference.aspose.com/email/java/com.aspose.email/imapclient/) é inicializada, a próxima chamada para qualquer operação usando esta instância se conectará ao servidor. O seguinte trecho de código mostra como se conectar a um servidor IMAP usando os passos acima.

~~~Java
// Para exemplos completos e arquivos de dados, acesse https://github.com/aspose-email/Aspose.Email-for-Java
// Crie um imapclient com host, usuário e senha
ImapClient client = new ImapClient("localhost", "user", "password");
~~~

## **Conectando-se a Servidor IMAP com SSL Habilitado**

[Conectando-se ao Servidor IMAP](/email/java/connecting-to-imap-server#connecting-with-imap-server) descreve como conectar-se a um servidor IMAP em quatro etapas simples:

1. Crie uma instância da classe [ImapClient](https://reference.aspose.com/email/java/com.aspose.email/imapclient/).
1. Especifique o hostname, nome de usuário e senha.
1. Especifique a porta.
1. Especifique as [Opções de Segurança](https://reference.aspose.com/email/java/com.aspose.email/securityoptions/).

O processo para conectar-se a um servidor IMAP habilitado para SSL é semelhante, mas requer que você defina mais algumas propriedades:

- Defina as [Opções de Segurança](https://reference.aspose.com/email/java/com.aspose.email/securityoptions/) para SSLImplicit.

O seguinte trecho de código mostra como

1. Definir um nome de usuário, senha e porta.
1. Definir a opção de segurança.

~~~Java
// Para exemplos completos e arquivos de dados, acesse https://github.com/aspose-email/Aspose.Email-for-Java
// Crie uma instância da classe ImapClient
ImapClient client = new ImapClient("imap.domain.com", 993, "user@domain.com", "pwd");

// Defina o modo de segurança como implícito
client.setSecurityOptions(SecurityOptions.SSLImplicit);
~~~

## **Conectando-se ao Servidor via Proxy**

Servidores proxy são comumente usados para se comunicar com o mundo externo. Nesses casos, os clientes de e-mail não conseguem se comunicar pela Internet sem especificar o endereço do proxy. Aspose.Email fornece suporte para as versões 4, 4a e 5 do protocolo SOCKS. Este artigo fornece um exemplo funcional de acesso à caixa de correio usando um servidor de e-mail proxy. Para acessar a caixa de correio via um servidor proxy:

1. Inicialize [SocksProxy](https://reference.aspose.com/email/java/com.aspose.email/socksproxy/) com as informações necessárias, ou seja, endereço do proxy, porta e versão do SOCKS.
1. Inicialize [ImapClient](https://reference.aspose.com/email/java/com.aspose.email/imapclient/) com o endereço do host, nome de usuário, senha e quaisquer outras configurações.
1. Defina a propriedade [SocksProxy](https://reference.aspose.com/email/java/com.aspose.email/socksproxy/) do cliente para o objeto [SocksProxy](https://reference.aspose.com/email/java/com.aspose.email/socksproxy/) criado acima.

O seguinte trecho de código mostra como recuperar a caixa de correio via um servidor proxy.

~~~Java
// Para exemplos completos e arquivos de dados, acesse https://github.com/aspose-email/Aspose.Email-for-Java
// Conectar e fazer login no IMAP e definir SecurityOptions
ImapClient client = new ImapClient("imap.domain.com", "username", "password");
client.setSecurityOptions(SecurityOptions.Auto);

String proxyAddress = "192.168.203.142"; // endereço do proxy
int proxyPort = 1080; // porta do proxy
SocksProxy proxy = new SocksProxy(proxyAddress, proxyPort, SocksVersion.SocksV5);

// Defina o proxy
client.setProxy(proxy);

try {
    client.selectFolder("Inbox");
} catch (java.lang.RuntimeException ex) {
    System.out.println(ex.getMessage());
}
~~~

## **Conectando-se ao Servidor via Proxy HTTP**

~~~Java
// Para exemplos completos e arquivos de dados, acesse https://github.com/aspose-email/Aspose.Email-for-Java
HttpProxy proxy = new HttpProxy("18.222.124.59", 8080);
final ImapClient client = new ImapClient("imap.domain.com", "username", "password");
try {
    client.setProxy(proxy);
    client.selectFolder("Inbox");
} finally {
    if (client != null)
        client.dispose();
}
~~~

## **Personalizar Mecanismo de Autenticação**

Recupere a lista de mecanismos de autenticação que são suportados pelo servidor IMAP usando o método [getSupportedAuthentication](https://reference.aspose.com/email/java/com.aspose.email/imapclient/#getSupportedAuthentication--) da classe [ImapClient](https://reference.aspose.com/email/java/com.aspose.email/imapclient/). Este método permite que o cliente determine quais métodos de autenticação estão disponíveis para estabelecer uma conexão segura com o servidor. Em seguida, utilizando o método [setAllowedAuthentication](https://reference.aspose.com/email/java/com.aspose.email/imapclient/#setAllowedAuthentication-long-) que obtém (ou define) a enumeração dos tipos de autenticação permitidos pelo usuário, escolha o mecanismo de autenticação mais apropriado para a comunicação cliente-servidor. Isso permite que você defina o método de autenticação para o cliente de e-mail explicitamente.

O seguinte trecho de código mostra como personalizar a autenticação do cliente de e-mail:

```java
imapClient.setAllowedAuthentication(ImapKnownAuthenticationType.Plain);
```

## **Conectando-se ao Servidor em Modo Somente Leitura**

A classe [ImapClient](https://reference.aspose.com/email/java/com.aspose.email/imapclient/) fornece uma propriedade [ReadOnly](https://reference.aspose.com/email/java/com.aspose.email/imapclient/#setReadOnly-boolean-) que, quando definida como **true**, indica que nenhuma alteração deve ser feita no estado permanente da caixa de correio. O seguinte trecho de código demonstra o uso da propriedade [ImapClient.ReadOnly](https://reference.aspose.com/email/java/com.aspose.email/imapclient/#setReadOnly-boolean-). Ele obtém a contagem de mensagens não lidas, depois busca uma mensagem e depois obtém a contagem de mensagens não lidas novamente em modo somente leitura. A contagem de mensagens não lidas permanece a mesma, indicando que o estado permanente da caixa de correio não foi alterado.

~~~Java
// Para exemplos completos e arquivos de dados, acesse https://github.com/aspose-email/Aspose.Email-for-Java
ImapClient imapClient = new ImapClient();
imapClient.setHost("<HOST>");
imapClient.setPort(993);
imapClient.setUsername("<USERNAME>");
imapClient.setPassword("<PASSWORD>");
imapClient.setSupportedEncryption(EncryptionProtocols.Tls);
imapClient.setSecurityOptions(SecurityOptions.SSLImplicit);

ImapQueryBuilder imapQueryBuilder = new ImapQueryBuilder();
imapQueryBuilder.hasNoFlags(ImapMessageFlags.isRead()); /* obter mensagens não lidas. */
MailQuery query = imapQueryBuilder.getQuery();

imapClient.setReadOnly(true);
imapClient.selectFolder("Inbox");
ImapMessageInfoCollection messageInfoCol = imapClient.listMessages(query);
System.out.println("Contagem Inicial de Não Lidas: " + messageInfoCol.size());
if (messageInfoCol.size() > 0) {
    imapClient.fetchMessage(messageInfoCol.get_Item(0).getSequenceNumber());

    messageInfoCol = imapClient.listMessages(query);
    // Esta contagem será igual à contagem inicial
    System.out.println("Contagem Atualizada de Não Lidas: " + messageInfoCol.size());
} else {
    System.out.println("Nenhuma mensagem não lida encontrada");
}
~~~

## **Usando autenticação CRAM-MD5 para Conectar-se a um Servidor**

Para garantir autenticação e comunicação seguras com o servidor IMAP, você pode especificar e impor o uso de CRAM-MD5 como o método de autenticação permitido para o cliente IMAP. O seguinte trecho de código mostra como configurar o tipo de autenticação permitido para o [ImapClient](https://reference.aspose.com/email/java/com.aspose.email/imapclient/):

```java
imapClient.setAllowedAuthentication(ImapKnownAuthenticationType.CramMD5);
```
## **Validar Credenciais do Servidor de E-mail Sem Enviar E-mail**

Às vezes, é necessário verificar credenciais sem enviar um e-mail. Aspose.Email fornece o método [validateCredentials()](https://reference.aspose.com/email/java/com.aspose.email/imapclient/#validateCredentials--) para realizar essa operação. Se a validação for bem-sucedida, o código dentro da instrução if é executado, normalmente usado para realizar ações adicionais ou recuperar dados do servidor IMAP. O seguinte trecho de código demonstra a validação de credenciais sem enviar um e-mail:

```java
try (ImapClient imapClient = new ImapClient(
        server.ImapUrl, server.ImapPort, "username", "password", SecurityOptions.Auto)) {
    imapClient.setTimeout(4000);

    if (imapClient.validateCredentials()) {
        // fazer algo
    }
}
```

## **Como Definir Timeout para Operações de E-mail**

Cada operação de e-mail leva algum tempo dependendo de muitos fatores (atrasos na rede, tamanho dos dados, desempenho do servidor, etc.). Você pode definir um timeout para todas as operações de e-mail. O exemplo de código abaixo mostra como fazer isso usando a propriedade [Timeout](https://reference.aspose.com/email/java/com.aspose.email/imapclient/#setTimeout-int-). Nota: você não deve definir valores grandes para evitar longas esperas em seu aplicativo.

~~~Java
try (ImapClient imapClient = new ImapClient("host", 993, "username", "password", SecurityOptions.SSLImplicit))
{
    imapClient.setTimeout(60000); // 60 segundos

    // algum código...
}
~~~

## **Como Restringir o Timeout de Saudação**

O cliente IMAP pode usar o modo automático para estabelecer uma conexão. Nesse modo, o cliente IMAP passa por todos os parâmetros de conexão possíveis até que a conexão seja estabelecida. Um servidor IMAP, em caso de conexão correta, envia uma string de saudação ao cliente. Os servidores podem usar a iniciação de conexão SSL/TLS implícita ou explícita (START TLS). Se o modo de conexão estiver desalinhado (por exemplo, o servidor espera uma conexão SSL implícita, mas o cliente tenta estabelecer uma conexão não segura ou uma conexão SSL explícita), o servidor não enviará uma string de saudação e o usuário aguardará um longo tempo até que o timeout alcance uma string de saudação, e o cliente irá para a próxima opção de conexão. Para evitar esse problema, o GreetingTimeout foi introduzido. Esta propriedade permite que você defina o timeout para a string de saudação e reduza o tempo de estabelecimento automático da conexão.

```java
ImapClient imapClient = new ImapClient();
imapClient.setGreetingTimeout(4000);
```