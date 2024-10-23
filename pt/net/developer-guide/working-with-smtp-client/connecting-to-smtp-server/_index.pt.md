---
title: "Conectando ao Servidor SMTP"
url: /pt/net/conectando-ao-servidor-smtp/
weight: 10
type: docs
---

Ao trabalhar com clientes de email, certas operações podem levar um tempo considerável para serem executadas. Para evitar que essas operações sejam executadas indefinidamente, os usuários podem utilizar a propriedade [EmailClient.Timeout](https://reference.aspose.com/email/net/aspose.email.clients/emailclient/timeout/). É importante notar que os valores atribuídos a esta propriedade devem ter intervalos longos o suficiente para acomodar operações extensas.

No entanto, confiar exclusivamente na propriedade Timeout pode fazer com que o estabelecimento da conexão demore mais do que o esperado. Isso pode ocorrer quando o cliente de email utiliza o modo automático para o estabelecimento de conexão. Nesse modo, o cliente passa por vários parâmetros de conexão até que uma conexão seja estabelecida.

Ao conectar a servidores SMTP, IMAP e POP3, uma string de saudação é enviada ao cliente quando a conexão é estabelecida com sucesso. Os servidores podem usar a inicialização de conexão SSL/TLS implícita ou explícita (START TLS). Em casos onde o modo de conexão está incompatível (por exemplo, o servidor espera uma conexão SSL implícita enquanto o cliente tenta estabelecer uma conexão não segura ou explícita em SSL), o servidor não enviará uma string de saudação.

Como resultado, o usuário pode esperar por um período prolongado até que o tempo limite seja alcançado e o cliente passe para a próxima opção de conexão.

Para resolver esse problema, a propriedade [GreetingTimeout](https://reference.aspose.com/email/net/aspose.email.clients/emailclient/greetingtimeout/) foi introduzida. Esta propriedade permite que os usuários definam um tempo limite para a string de saudação, reduzindo o tempo necessário para estabelecer uma conexão automática. Ao implementar a **propriedade GreetingTimeout**, os usuários podem otimizar o desempenho de seu cliente de email e evitar longos períodos de espera durante o estabelecimento de conexão.

O seguinte exemplo de código mostra como definir a propriedade [EmailClient.GreetingTimeout](https://reference.aspose.com/email/net/aspose.email.clients/emailclient/greetingtimeout/):

```cs
using (SmtpClient client = new SmtpClient("localhost", 25, "username", "password"))
{
    client.GreetingTimeout = 4000;
}
```

## **Conectando ao Servidor via Servidor Proxy Socks**

Às vezes usamos servidores proxy para comunicar com o mundo exterior. Nesses casos, os clientes de email não conseguem se comunicar pela Internet sem especificar o endereço do proxy. Aspose.Email fornece suporte para as versões 4, 4a e 5 do protocolo proxy SOCKS. Este artigo fornece um exemplo funcional de envio de email usando um servidor de correio proxy. Para enviar um email via um servidor proxy:

1. Inicialize o Proxy com as informações necessárias, ou seja, endereço do proxy, porta e versão do SOCKS.
1. Inicialize o [SmtpClient](https://reference.aspose.com/email/net/aspose.email.clients.smtp/smtpclient/) com o endereço do host, nome de usuário e senha, e quaisquer outras configurações.
1. Defina a propriedade Proxy do cliente para o objeto [Proxy](https://reference.aspose.com/email/net/aspose.email.clients/proxy/) criado anteriormente.

O seguinte trecho de código mostra como conectar a um servidor via servidor proxy.

{{< gist "aspose-com-gists" "6e5185a63aec6fd70d83098e82b06a32" "Examples-CSharp-SMTP-SendEmailViaProxyServer-SendEmailViaProxyServer.cs" >}}

## **Conectando ao Servidor via Servidor Proxy HTTP**

{{< gist "aspose-com-gists" "6e5185a63aec6fd70d83098e82b06a32" "Examples-CSharp-SMTP-SendEmailViaHttpProxy-SendEmailViaHttpProxy.cs" >}}

## **Conectando ao Servidor usando Método de Autenticação Suportado**

Aspose.Email para .NET oferece propriedades que permitem verificar quais métodos de autenticação podem ser utilizados para estabelecer uma conexão segura com o servidor SMTP antes de enviar um email:
- a propriedade [SmtpClient.SupportedAuthentication](https://reference.aspose.com/email/net/aspose.email.clients.smtp/smtpclient/supportedauthentication/) retorna uma lista de métodos de autenticação suportados pelo servidor SMTP. 
- a propriedade [SmtpClient.AllowedAuthentication](https://reference.aspose.com/email/net/aspose.email.clients.smtp/smtpclient/allowedauthentication/) retorna uma lista de métodos de autenticação definidos pelo usuário.

```cs
smtpClient.AllowedAuthentication = SmtpKnownAuthenticationType.Login;
```

## **Carregando Informações de Autenticação SMTP do Arquivo CONFIG**

A classe [SmtpClient](https://reference.aspose.com/email/net/aspose.email.clients.smtp/smtpclient/) permite que aplicativos leiam informações de autenticação como nome de usuário e senha e o endereço do host e número da porta diretamente de um arquivo de configuração. Usar a tag de configuração nativa do .NET, conforme mostrado abaixo, permite que a classe [SmtpClient](https://reference.aspose.com/email/net/aspose.email.clients.smtp/smtpclient/) leia essas informações através do Gerenciador de Configuração, também disponível no framework .NET. Para que Aspose.Email possa ler um arquivo de configuração, ele precisa estar no formato correto. Abaixo, mostramos um exemplo de arquivo de configuração XML seguido pelo código que o lê. O seguinte trecho de código mostra como carregar informações de autenticação SMTP do arquivo CONFIG.

{{< gist "aspose-com-gists" "6e5185a63aec6fd70d83098e82b06a32" "LoadingAuthenticationInformationFromAFile.xml" >}}

Uma vez que as configurações de configuração estão definidas, carregue essas configurações diretamente em uma instância da classe [SmtpClient](https://reference.aspose.com/email/net/aspose.email.clients.smtp/smtpclient/) usando um de seus construtores sobrecarregados. O seguinte trecho de código demonstra a leitura das configurações de configuração do arquivo de configuração e o carregamento delas diretamente na instância da classe [SmtpClient](https://reference.aspose.com/email/net/aspose.email.clients.smtp/smtpclient/).

{{< gist "aspose-com-gists" "6e5185a63aec6fd70d83098e82b06a32" "Examples-CSharp-SMTP-LoadSmtpConfigFile-LoadSmtpConfigFile.cs" >}}

## **Vinculando Cliente SMTP a Endereço IP Específico no Host**

A possibilidade de um host ter várias portas disponíveis para enviar emails não pode ser descartada. Nesses casos, pode surgir a necessidade de vincular o cliente de envio de emails a uma porta específica no host para enviar emails. Isso pode ser alcançado com a API Aspose.Email usando a propriedade [SmtpClient](https://reference.aspose.com/email/net/aspose.email.clients.smtp/smtpclient/) [BindIPEndPoint](https://apireference.aspose.com/email/net/aspose.email.clients/emailclient/events/bindipendpoint). O [SmtpClient](https://reference.aspose.com/email/net/aspose.email.clients.smtp/smtpclient/) da API pode ser configurado para usar um endereço IP específico no host especificando o Endpoint IP específico. O seguinte trecho de código mostra como vincular o Cliente SMTP a um Endereço IP Específico no Host.

{{< gist "aspose-com-gists" "6e5185a63aec6fd70d83098e82b06a32" "Examples-CSharp-SMTP-SetSpecificIpAddress-SetSpecificIpAddress.cs" >}}

## **Como Definir Timeout para Operações de Email**

Cada operação de email leva algum tempo dependendo de muitos fatores (atrasos de rede, tamanho dos dados, desempenho do servidor, etc.). Você pode definir um tempo limite para todas as operações de email. O exemplo de código abaixo mostra como fazer isso usando a propriedade [Timeout](https://reference.aspose.com/email/net/aspose.email.clients/emailclient/timeout/). Nota: você não deve definir valores grandes para evitar longas esperas em seu aplicativo.

```csharp
using (SmtpClient smtpClient = new SmtpClient("host", 587, "username", "password", SecurityOptions.SSLExplicit))
{
    smtpClient.Timeout = 60000; // 60 segundos

    // algum código...
}
```

## **Usando Protocolos Criptográficos com o Cliente SMTP**

Aspose.Email suporta SSL (obsoleto) e protocolos criptográficos TLS para fornecer segurança nas comunicações. Você pode habilitar a criptografia criptográfica para proteger a troca de dados entre seu aplicativo e os servidores de correio.

> **_NOTA:_** Você deve definir apenas aquelas versões do protocolo que são compatíveis com o .NET Framework. Se algumas versões do protocolo criptográfico não são suportadas pela sua versão atual do .NET Framework, elas serão ignoradas e puladas. Neste caso, exceções não serão geradas. Utilize o método [SetSupportedEncryptionUnsafe](https://reference.aspose.com/email/net/aspose.email.clients/emailclient/setsupportedencryptionunsafe/#setsupportedencryptionunsafe) se quiser definir os protocolos sem verificações de compatibilidade.

O exemplo de código abaixo mostra como definir TLS 1.3 para a instância da classe [SmtpClient](https://reference.aspose.com/email/net/aspose.email.clients.smtp/smtpclient/).

```csharp
using (SmtpClient smtpClient = new SmtpClient("host", 587, "username", "password", SecurityOptions.SSLExplicit))
{
    smtpClient.SupportedEncryption = EncryptionProtocols.Tls13;

    // algum código...
}
```

No caso do protocolo de criptografia especificado não ser suportado na versão atual do .NET Framework, a diferença de comportamento entre o método [SetSupportedEncryptionUnsafe](https://reference.aspose.com/email/net/aspose.email.clients/emailclient/setsupportedencryptionunsafe/#setsupportedencryptionunsafe) e a propriedade [SupportedEncryption](https://reference.aspose.com/email/net/aspose.email.clients/emailclient/supportedencryption/) é a seguinte:
- Se a propriedade [SupportedEncryption](https://reference.aspose.com/email/net/aspose.email.clients/emailclient/supportedencryption/) for usada, o cliente de email rebaixa o protocolo de criptografia para um nível suportado.
- Se o método [SetSupportedEncryptionUnsafe](https://reference.aspose.com/email/net/aspose.email.clients/emailclient/setsupportedencryptionunsafe/#setsupportedencryptionunsafe) for usado, o cliente de email lança exceções.

##  **Usando o Mecanismo CRAM-MD5 para Autenticação**

O mecanismo de autenticação CRAM-MD5 da Aspose.Email para .NET fornece uma camada adicional de segurança ao acessar o servidor. O seguinte trecho de código mostra como implementar esse recurso em seu projeto:

```cs
smtpClient.AllowedAuthentication = SmtpKnownAuthenticationType.CramMD5;
```