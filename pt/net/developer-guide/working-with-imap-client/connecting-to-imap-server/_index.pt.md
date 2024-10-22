---
title: "Conectando ao Servidor IMAP"
url: /pt/net/conectando-ao-servidor-imap/
weight: 10
type: docs
---

A classe [ImapClient](https://reference.aspose.com/email/net/aspose.email.clients.imap/imapclient/) permite que aplicativos gerenciem caixas de correio IMAP usando o protocolo IMAP. A classe [ImapClient](https://reference.aspose.com/email/net/aspose.email.clients.imap/imapclient/) é usada para se conectar a servidores de e-mail IMAP e gerenciar e-mails nas pastas de e-mail IMAP. Para se conectar a um servidor IMAP

1. Crie uma instância da classe [ImapClient](https://reference.aspose.com/email/net/aspose.email.clients.imap/imapclient/).
1. Especifique o nome do host, nome de usuário e senha no [construtor ImapClient](https://reference.aspose.com/email/net/aspose.email.clients.imap/imapclient/imapclient/#constructor_8).

**Nota: as restrições de senha devem cumprir os requisitos do servidor. O cliente de e-mail não adiciona restrições de senha.**

Uma vez que a instância da [ImapClient](https://reference.aspose.com/email/net/aspose.email.clients.imap/imapclient/) é iniciada, a próxima chamada a qualquer operação usando essa instância se conectará ao servidor. O seguinte trecho de código mostra como se conectar a um servidor IMAP usando os passos acima.

```csharp
// Para exemplos completos e arquivos de dados, por favor, acesse https://github.com/aspose-email/Aspose.Email-for-.NET
// Crie um imapclient com host, usuário e senha
ImapClient client = new ImapClient("localhost", "user", "password");
```

## **Conectando com o Servidor IMAP com SSL Ativado**

[Conectando com Servidor IMAP](/email/net/connecting-to-imap-server#connecting-with-imap-server) descreveu como se conectar a um servidor IMAP em quatro passos simples:

1. Crie uma instância da classe [ImapClient](https://reference.aspose.com/email/net/aspose.email.clients.imap/imapclient/).
1. Especifique o nome do host, nome de usuário e senha.
1. Especifique a porta.
1. Especifique as Opções de Segurança.

O processo para se conectar a um servidor IMAP com SSL é semelhante, mas requer que você defina mais algumas propriedades:

- Defina Opções de Segurança para SSLImplicit.

O seguinte trecho de código mostra como

1. Definir um nome de usuário, senha e porta.
1. Definir a opção de segurança.

```csharp
// Para exemplos completos e arquivos de dados, por favor, acesse https://github.com/aspose-email/Aspose.Email-for-.NET
// Crie uma instância da classe ImapClient
ImapClient client = new ImapClient("imap.domain.com", 993, "user@domain.com", "pwd");
            
// Defina o modo de segurança como implícito
client.SecurityOptions = SecurityOptions.SSLImplicit;
```

## **Conectando ao Servidor via Proxy**

Servidores proxy são comumente usados para se comunicar com o mundo exterior. Em tais casos, os clientes de e-mail não conseguem se comunicar pela Internet sem especificar o endereço do proxy. Aspose.Email fornece suporte para as versões 4, 4a e 5 do protocolo proxy SOCKS. Este artigo fornece um exemplo funcional de acesso à caixa de correio usando um servidor de e-mail proxy. Para acessar a caixa de correio através de um servidor proxy:

1. Inicialize [SocksProxy](https://reference.aspose.com/email/net/aspose.email.clients/socksproxy/) com as informações necessárias, ou seja, endereço do proxy, porta e versão SOCKS.
1. Inicialize [ImapClient](https://reference.aspose.com/email/net/aspose.email.clients.imap/imapclient/) com o endereço do host, nome de usuário, senha e qualquer outra configuração.
1. Defina a propriedade [SocksProxy](https://reference.aspose.com/email/net/aspose.email.clients/socksproxy/) do cliente para o objeto [SocksProxy](https://reference.aspose.com/email/net/aspose.email.clients/socksproxy/) criado acima.

O seguinte trecho de código mostra como recuperar a caixa de correio via um servidor proxy.

```csharp
// Para exemplos completos e arquivos de dados, por favor, acesse https://github.com/aspose-email/Aspose.Email-for-.NET
// Conecte e faça login no IMAP e defina SecurityOptions
ImapClient client = new ImapClient("imap.domain.com", "username", "password");
client.SecurityOptions = SecurityOptions.Auto;
            
string proxyAddress = "192.168.203.142"; // endereço do proxy
int proxyPort = 1080; // porta do proxy
SocksProxy proxy = new SocksProxy(proxyAddress, proxyPort, SocksVersion.SocksV5);

// Defina o proxy
client.Proxy = proxy;
           
try
{
    client.SelectFolder("Inbox");
}
catch (Exception ex)
{
    Console.WriteLine(ex.Message);
}
```

## **Conectando ao Servidor via Proxy HTTP**

```csharp
// Para exemplos completos e arquivos de dados, por favor, acesse https://github.com/aspose-email/Aspose.Email-for-.NET
HttpProxy proxy = new HttpProxy("18.222.124.59", 8080);
using (ImapClient client = new ImapClient("imap.domain.com", "username", "password"))
{
    client.Proxy = proxy;
    client.SelectFolder("Inbox");
}
```

## **Conectando ao Servidor em Modo Somente Leitura**

A classe [ImapClient](https://reference.aspose.com/email/net/aspose.email.clients.imap/imapclient/) fornece uma propriedade [ReadOnly](https://reference.aspose.com/email/net/aspose.email.clients.imap/imapclient/readonly/) que quando definida como **true**, indica que nenhuma alteração deve ser feita ao estado permanente da caixa de correio. O seguinte exemplo de código demonstra o uso da propriedade [ImapClient.ReadOnly](https://reference.aspose.com/email/net/aspose.email.clients.imap/imapclient/readonly/). Ele obtém a contagem de mensagens não lidas, depois busca uma mensagem e então obtém a contagem de mensagens não lidas novamente em modo somente leitura. A contagem das mensagens não lidas permanece a mesma, indicando que o estado permanente da caixa de correio não foi alterado.

```csharp
// Para exemplos completos e arquivos de dados, por favor, acesse https://github.com/aspose-email/Aspose.Email-for-.NET
ImapClient imapClient = new ImapClient();
imapClient.Host = "<HOST>";
imapClient.Port = 993;
imapClient.Username = "<USERNAME>";
imapClient.Password = "<PASSWORD>";
imapClient.SupportedEncryption = EncryptionProtocols.Tls;
imapClient.SecurityOptions = SecurityOptions.SSLImplicit;

ImapQueryBuilder imapQueryBuilder = new ImapQueryBuilder();
imapQueryBuilder.HasNoFlags(ImapMessageFlags.IsRead); /* obter mensagens não lidas. */
MailQuery query = imapQueryBuilder.GetQuery();

imapClient.ReadOnly = true;
imapClient.SelectFolder("Inbox");
ImapMessageInfoCollection messageInfoCol = imapClient.ListMessages(query);
Console.WriteLine("Contagem Inicial de Não Lidas: " + messageInfoCol.Count());
if (messageInfoCol.Count() > 0)
{
    imapClient.FetchMessage(messageInfoCol[0].SequenceNumber);

    messageInfoCol = imapClient.ListMessages(query);
    // Esta contagem será igual à contagem inicial
    Console.WriteLine("Contagem Atualizada de Não Lidas: " + messageInfoCol.Count());
}
else
{
    Console.WriteLine("Nenhuma mensagem não lida encontrada");
}
```
## **Conectando ao Servidor usando autenticação CRAM-MD5**

Para autenticação segura e acesso ao servidor de e-mail, o Aspose.Email para .NET oferece um método de autenticação CRAM-MD5.
O seguinte trecho de código mostrará como funciona com o ImapClient:

```cs
imapClient.AllowedAuthentication = ImapKnownAuthenticationType.CramMD5;
```

## **Como Definir Tempo Limite para Operações de E-mail**

Cada operação de e-mail leva algum tempo, dependendo de muitos fatores (atrasos de rede, tamanho dos dados, desempenho do servidor, etc.). Você pode definir um tempo limite para todas as operações de e-mail. O exemplo de código abaixo mostra como fazer isso usando a propriedade [Timeout](https://reference.aspose.com/email/net/aspose.email.clients/emailclient/timeout/). Nota: você não deve definir valores grandes para evitar longas esperas em sua aplicação.

```csharp
using (ImapClient imapClient = new ImapClient("host", 993, "username", "password", SecurityOptions.SSLImplicit))
{
    imapClient.Timeout = 60000; // 60 segundos

    // algum código...
}
```

## **Como Restringir o Tempo Limite de Saudação**

O cliente IMAP pode usar o modo automático para estabelecer uma conexão. Nesse modo, o cliente IMAP passa por todos os possíveis parâmetros de conexão até que a conexão seja estabelecida. Um servidor IMAP em caso de conexão correta envia uma string de saudação ao cliente. Os servidores podem usar a inicialização de conexão SSL/TLS implícita ou explícita (START TLS). Se o modo de conexão estiver incorreto (por exemplo, o servidor aguarda uma conexão SSL implícita, mas o cliente tenta estabelecer uma conexão não segura ou explícita SSL), o servidor não enviará uma string de saudação e o usuário aguardará muito tempo até que o tempo limite chegue a uma string de saudação, e o cliente passe para a próxima opção de conexão. Para evitar esse problema, a propriedade GreetingTimeout foi introduzida. Esta propriedade permite que você defina o tempo limite para a string de saudação e reduza o tempo de estabelecimento automático da conexão.

```cs
using (ImapClient client = new ImapClient("localhost", 993, "username", "password"))
{
    client.GreetingTimeout = 4000;
    client.SelectFolder(ImapFolderInfo.InBox);
}
```

## **Usando Protocolos Criptográficos com o Cliente IMAP**

O Aspose.Email suporta protocolos criptográficos SSL (obsoleto) e TLS para fornecer segurança nas comunicações. Você pode ativar a criptografia criptográfica para proteger a troca de dados entre seu aplicativo e servidores de e-mail.

> **_NOTA:_** Você deve definir apenas aquelas versões do protocolo que são suportadas pelo .NET Framework. Se algumas versões do protocolo criptográfico não forem suportadas pela sua versão atual do .NET Framework, elas serão ignoradas e puladas. Nesse caso, exceções não serão geradas. Por favor, use o método [SetSupportedEncryptionUnsafe](https://reference.aspose.com/email/net/aspose.email.clients/emailclient/setsupportedencryptionunsafe/#setsupportedencryptionunsafe) se você quiser definir os protocolos sem verificações de compatibilidade.

O exemplo de código abaixo mostra como definir TLS 1.3 para a instância da classe [ImapClient](https://reference.aspose.com/email/net/aspose.email.clients.imap/imapclient/).

```csharp
using (ImapClient imapClient = new ImapClient("host", 993, "username", "password", SecurityOptions.SSLImplicit))
{
    imapClient.SupportedEncryption = EncryptionProtocols.Tls13;

    // algum código...
}
```

No caso de um protocolo de criptografia especificado não ser suportado na versão atual do .NET Framework, a diferença de comportamento entre o método [SetSupportedEncryptionUnsafe](https://reference.aspose.com/email/net/aspose.email.clients/emailclient/setsupportedencryptionunsafe/#setsupportedencryptionunsafe) e a propriedade [SupportedEncryption](https://reference.aspose.com/email/net/aspose.email.clients/emailclient/supportedencryption/) é a seguinte:
- Se a propriedade [SupportedEncryption](https://reference.aspose.com/email/net/aspose.email.clients/emailclient/supportedencryption/) for usada, o cliente de e-mail rebaixa o protocolo de criptografia para um nível suportado.
- Se o método [SetSupportedEncryptionUnsafe](https://reference.aspose.com/email/net/aspose.email.clients/emailclient/setsupportedencryptionunsafe/#setsupportedencryptionunsafe) for usado, o cliente de e-mail lança exceções.