---
title: "Conectar ao Servidor POP3"
url: /pt/net/connect-to-pop3-server/
weight: 10
type: docs
---

## Conectando a um Servidor POP3

A classe [Pop3Client](https://reference.aspose.com/email/net/aspose.email.clients.pop3/pop3client/) permite que aplicativos gerenciem caixas de e-mail usando o Protocolo de Postagem, Versão 3 (POP3). Para se conectar a um servidor, use a classe [Pop3Client](https://reference.aspose.com/email/net/aspose.email.clients.pop3/pop3client/). A classe [Pop3Client](https://reference.aspose.com/email/net/aspose.email.clients.pop3/pop3client/) é a principal entrada para desenvolvedores que desejam adicionar gerenciamento POP3 às suas aplicações .NET. Este artigo explica como usá-la. Para se conectar a um servidor POP3:

1. Crie uma instância da classe [Pop3Client](https://reference.aspose.com/email/net/aspose.email.clients.pop3/pop3client/).
2. Especifique o host, nome de usuário e senha na instância [Pop3Client](https://reference.aspose.com/email/net/aspose.email.clients.pop3/pop3client/).

O seguinte trecho de código mostra como se conectar ao servidor POP3.

{{< gist "aspose-com-gists" "6e5185a63aec6fd70d83098e82b06a32" "Examples-CSharp-POP3-ConnectingToPOP3-ConnectingToPOP3.cs" >}}

## **Conectando ao servidor SSL**

[Conectar a um Servidor POP3](#connecting-to-a-pop3-server) descreve como se conectar a um servidor POP3 em dois passos simples:

1. Crie uma instância da classe [Pop3Client](https://reference.aspose.com/email/net/aspose.email.clients.pop3/pop3client/).
1. Especifique o host, nome de usuário e senha.

O processo para se conectar a um servidor POP3 habilitado para SSL é semelhante, mas requer que você defina mais algumas propriedades:

- [SecurityOptions](https://reference.aspose.com/email/net/aspose.email.clients/securityoptions/)
- Porta

Para se conectar a um servidor POP3 habilitado para SSL, use a classe [Pop3Client](https://reference.aspose.com/email/net/aspose.email.clients.pop3/pop3client/) e defina as propriedades [SecurityOptions](https://reference.aspose.com/email/net/aspose.email.clients/securityoptions/) e Porta. O seguinte trecho de código mostra como se conectar a um servidor POP3 habilitado para SSL.

{{< gist "aspose-com-gists" "6e5185a63aec6fd70d83098e82b06a32" "Examples-CSharp-POP3-SSLEnabledPOP3Server-SSLEnabledPOP3Server.cs" >}}

## **Conectando com um Servidor APOP**

POP significa Protocolo de Postagem. APOP significa Protocolo de Postagem Autenticada. APOP é uma versão estendida da configuração do servidor POP3 que criptografa seu nome de usuário e senha e usa um mecanismo de autenticação projetado para proteger a senha da sua conta POP3 ao verificar e-mails. A autenticação APOP não requer que a senha da conta seja enviada como texto simples para o servidor de correio POP3.

## **Conectando ao Servidor via Proxy**

Servidores proxy são muito comuns para se comunicar com o mundo exterior. Em tais casos, endereços de proxy são usados para que clientes de e-mail acessem caixas de entrada pela Internet. Aspose.Email oferece suporte para as versões 4, 4a e 5 do protocolo de proxy SOCKS. Este artigo fornece um exemplo funcional de recuperação de e-mail usando um servidor de e-mail proxy. Para recuperar e-mail através de um servidor proxy:

1. Inicialize [Proxy](https://reference.aspose.com/email/net/aspose.email.clients/proxy/) com as informações necessárias, ou seja, endereço do proxy, porta e versão do SOCKS.
1. Inicialize [Pop3Client](https://reference.aspose.com/email/net/aspose.email.clients.pop3/pop3client/) com o endereço do host, nome de usuário, senha e qualquer outra configuração.
1. Defina a propriedade Proxy de um cliente para o objeto [Proxy](https://reference.aspose.com/email/net/aspose.email.clients/proxy/) criado acima.

O seguinte trecho de código mostra como recuperar e-mail através de um servidor proxy.

{{< gist "aspose-com-gists" "6e5185a63aec6fd70d83098e82b06a32" "Examples-CSharp-POP3-RetrieveEmailViaProxyServer-RetrieveEmailViaProxyServer.cs" >}}

## **Conectando ao servidor via Proxy HTTP**

{{< gist "aspose-com-gists" "6e5185a63aec6fd70d83098e82b06a32" "Examples-CSharp-POP3-AccessMailboxViaHttpProxy-AccessPOP3MailboxViaHttpProxy.cs" >}}

## **Conectando ao servidor via mecanismo de autenticação CRAM-MD5**

Usando a autenticação CRAM-MD5, Aspose.Email para .NET permite que os usuários autentiquem-se de forma segura e acessem servidores de e-mail que suportam este método de autenticação. O exemplo de código abaixo mostra como usar o mecanismo em seu projeto:

```cs
popClient.AllowedAuthentication = Pop3KnownAuthenticationType.CramMD5;
```

## **Como Configurar Timeout para Operações de E-mail**

Cada operação de e-mail leva algum tempo dependendo de muitos fatores (atrasos de rede, tamanho dos dados, desempenho do servidor, etc.). Você pode definir um tempo limite para todas as operações de e-mail. O exemplo de código abaixo mostra como fazer isso usando a propriedade [Timeout](https://reference.aspose.com/email/net/aspose.email.clients/emailclient/timeout/). Nota: você não deve definir valores grandes para evitar longas esperas em sua aplicação.

```csharp
using (Pop3Client pop3Client = new Pop3Client("host", 995, "username", "password", SecurityOptions.Auto))
{
    pop3Client.Timeout = 60000; // 60 segundos

    // algum código...
}
```

## **Usando Protocolos Criptográficos com o Cliente POP3**

Aspose.Email suporta SSL (obsoleto) e protocolos criptográficos TLS para proporcionar segurança nas comunicações. Você pode habilitar a criptografia criptográfica para proteger a troca de dados entre seu aplicativo e os servidores de e-mail.

> **_NOTA:_**  Você deve definir apenas aquelas versões do protocolo que são suportadas pelo .NET Framework. Se algumas versões do protocolo criptográfico não forem suportadas pela sua versão atual do .NET Framework, elas serão ignoradas e puladas. Neste caso, exceções não serão geradas. Use o método [SetSupportedEncryptionUnsafe](https://reference.aspose.com/email/net/aspose.email.clients/emailclient/setsupportedencryptionunsafe/#setsupportedencryptionunsafe) se você quiser definir os protocolos sem verificações de compatibilidade.

O exemplo de código abaixo mostra como definir TLS 1.3 para a instância da classe [Pop3Client](https://reference.aspose.com/email/net/aspose.email.clients.pop3/pop3client/).

```csharp
using (Pop3Client pop3Client = new Pop3Client("host", 995, "username", "password", SecurityOptions.Auto))
{
    pop3Client.SupportedEncryption = EncryptionProtocols.Tls13;

    // algum código...
}
```

Caso um protocolo de criptografia especificado não seja suportado na versão atual do .NET Framework, a diferença de comportamento entre o método [SetSupportedEncryptionUnsafe](https://reference.aspose.com/email/net/aspose.email.clients/emailclient/setsupportedencryptionunsafe/#setsupportedencryptionunsafe) e a propriedade [SupportedEncryption](https://reference.aspose.com/email/net/aspose.email.clients/emailclient/supportedencryption/) é a seguinte:

- Se a propriedade [SupportedEncryption](https://reference.aspose.com/email/net/aspose.email.clients/emailclient/supportedencryption/) for usada, o cliente de e-mail rebaixará o protocolo de criptografia para um nível suportado.
  
- Se o método [SetSupportedEncryptionUnsafe](https://reference.aspose.com/email/net/aspose.email.clients/emailclient/setsupportedencryptionunsafe/#setsupportedencryptionunsafe) for usado, o cliente de e-mail lançará exceções.