---
title: "Conectar-se ao Servidor POP3"
url: /pt/java/connect-to-pop3-server/
weight: 10
type: docs
---

A classe [Pop3Client](https://reference.aspose.com/email/java/com.aspose.email/pop3client/) permite que aplicativos gerenciem caixas de correio usando o Protocolo Post Office, versão 3 (POP3). Para conectar-se a um servidor, utilize a classe [Pop3Client](https://reference.aspose.com/email/java/com.aspose.email/pop3client/). A classe [Pop3Client](https://reference.aspose.com/email/java/com.aspose.email/pop3client/) é a principal entrada para desenvolvedores que desejam adicionar gerenciamento POP3 a suas aplicações .NET. Este artigo explica como usá-la. Para conectar-se a um servidor POP3:

1. Crie uma instância da classe [Pop3Client](https://reference.aspose.com/email/java/com.aspose.email/pop3client/).
1. Especifique o host, nome de usuário e senha na instância [Pop3Client](https://reference.aspose.com/email/java/com.aspose.email/pop3client/).

O seguinte trecho de código mostra como se conectar ao servidor POP3.

~~~Java
// Para exemplos completos e arquivos de dados, acesse https://github.com/aspose-email/Aspose.Email-for-Java

// Crie uma instância da classe Pop3Client
Pop3Client client = new Pop3Client();

// Especifique host, nome de usuário, senha, porta e opções de segurança para seu cliente
client.setHost("pop.gmail.com");
client.setUsername("seu.usuario@gmail.com");
client.setPassword("sua.senha");
client.setPort(995);
client.setSecurityOptions(SecurityOptions.Auto);
System.out.println("Conectado ao servidor POP3.");
~~~

## **Conectando-se ao Servidor SSL**

[Conectando-se a um Servidor POP3](#connecting-to-pop3-server) descreveu como se conectar a um servidor POP3 em três etapas simples:

1. Crie uma instância da classe [Pop3Client](https://reference.aspose.com/email/java/com.aspose.email/pop3client/).
1. Especifique o host, nome de usuário e senha.

O processo de conexão a um servidor POP3 habilitado para SSL é semelhante, mas requer que você defina mais algumas propriedades:

- [SecurityOptions](https://reference.aspose.com/email/java/com.aspose.email/securityoptions/)
- Porta

Para se conectar a um servidor POP3 habilitado para SSL, utilize a classe [Pop3Client](https://reference.aspose.com/email/java/com.aspose.email/pop3client/) e defina as propriedades [SecurityOptions](https://reference.aspose.com/email/java/com.aspose.email/securityoptions/) e Porta. O seguinte trecho de código mostra como se conectar a um servidor POP3 habilitado para SSL.

~~~Java
// Para exemplos completos e arquivos de dados, acesse https://github.com/aspose-email/Aspose.Email-for-Java

// Crie uma instância da classe Pop3Client
Pop3Client client = new Pop3Client();

// Especifique host, nome de usuário e senha, porta e opções de segurança para seu cliente
client.setHost("pop.gmail.com");
client.setUsername("seu.usuario@gmail.com");
client.setPassword("sua.senha");
client.setPort(995);
client.setSecurityOptions(SecurityOptions.Auto);
System.out.println("Conectando-se ao servidor POP3 usando SSL.");
~~~

## **Conectando-se com um Servidor APOP**

POP significa Protocolo Post Office. APOP significa Protocolo Post Office Autenticado. APOP é uma versão estendida da configuração do servidor POP3 que criptografa seu nome de usuário e senha e utiliza um mecanismo de autenticação projetado para proteger a senha da sua conta POP3 ao verificar emails. A autenticação APOP não exige que a senha da conta seja enviada como texto sem formatação para o servidor de email POP3.

## **Conectando-se a um Servidor via Proxy**

Servidores proxy são muito comuns para comunicação com o mundo exterior. Nesses casos, endereços proxy são usados para que os clientes de email acessem caixas de correio pela Internet. Aspose.Email fornece suporte para as versões 4, 4a e 5 do protocolo proxy SOCKS. Este artigo fornece um exemplo funcional de recuperação de email usando um servidor de email proxy. Para recuperar emails via um servidor proxy:

1. Inicialize [Proxy](https://reference.aspose.com/email/java/com.aspose.email/proxy/) com as informações necessárias, ou seja, endereço proxy, porta e versão SOCKS.
1. Inicialize [Pop3Client](https://reference.aspose.com/email/java/com.aspose.email/pop3client/) com o endereço do host, nome de usuário, senha e quaisquer outras configurações.
2. Defina a propriedade Proxy do cliente para o objeto [Proxy](https://reference.aspose.com/email/java/com.aspose.email/proxy/) criado acima.

O seguinte trecho de código mostra como recuperar emails via servidor proxy.

~~~Java
// Para exemplos completos e arquivos de dados, acesse https://github.com/aspose-email/Aspose.Email-for-Java

// Crie uma instância da classe Pop3Client
Pop3Client client = new Pop3Client("pop.domain.com", "username", "password");

// Defina o endereço proxy, porta e proxy
String proxyAddress = "192.168.203.142";
int proxyPort = 1080;
SocksProxy proxy = new SocksProxy(proxyAddress, proxyPort, SocksVersion.SocksV5);
client.setProxy(proxy);
Pop3MailboxInfo mailboxInfo = client.getMailboxInfo();
~~~

## **Conectando-se a um Servidor via Proxy HTTP**

~~~Java
// Para exemplos completos e arquivos de dados, acesse https://github.com/aspose-email/Aspose.Email-for-Java

HttpProxy proxy = new HttpProxy("18.222.124.59", 8080);
try (Pop3Client client = new Pop3Client("imap.domain.com", "username", "password")) {
    client.setProxy(proxy);
    Pop3MailboxInfo mailboxInfo = client.getMailboxInfo();
}
~~~

## **Personalizar Mecanismo de Autenticação**

Recupere a lista de mecanismos de autenticação que são suportados pelo servidor POP3 usando o método [getSupportedAuthentication](https://reference.aspose.com/email/java/com.aspose.email/pop3client/#getSupportedAuthentication--) da classe [Pop3Client](https://reference.aspose.com/email/java/com.aspose.email/pop3client/). Este método permite que o cliente determine quais métodos de autenticação estão disponíveis para estabelecer uma conexão segura com o servidor. Em seguida, utilizando o método [setAllowedAuthentication](https://reference.aspose.com/email/java/com.aspose.email/pop3client/#setAllowedAuthentication-long-), que obtém (ou define) a enumeração dos tipos de autenticação permitidos pelo usuário, escolha o mecanismo de autenticação mais apropriado para a comunicação cliente-servidor. Isso permite definir explicitamente o método de autenticação para o cliente de email.

O seguinte exemplo de código mostra como personalizar a autenticação do cliente de email:

```java
pop3Client.setAllowedAuthentication(Pop3KnownAuthenticationType.Plain);
```

## **Suporte ao protocolo OAuth 2.0 para autorização**

OAuth 2.0 fornece autorização 

O Pop3Client suporta OAuth 2.0, oferecendo formas específicas de autorização para aplicativos. Os seguintes construtores são usados para inicializar o POP3Client usando OAuth: 

```java
public Pop3Client(

            String host, /*O nome do host*/

            int port, /*O número da porta*/ 

            String username, /*O nome do usuário*/

            ITokenProvider tokenProvider, /*TokenProvider permitindo recuperar o token de acesso*/

            /*SecurityOptions*/int securityOptions) /*Modo de segurança para um cliente de email*/



public Pop3Client(

            String host, /*O nome do host*/

            int port, /*O número da porta*/

            String username, /*O nome do usuário*/

            String authInfo, /*A senha do usuário ou token de acesso XOAUTH2*/

            boolean useOAuth, /*Define se o mecanismo SASL XOAUTH2 é usado para fazer login no servidor*/

            /*SecurityOptions*/int securityOptions) /*Modo de segurança para um cliente de email*/
```

## **Validar Credenciais do Servidor de Email sem Enviar Email**

Às vezes, é necessário verificar credenciais sem enviar um email. Aspose.Email fornece o método [validateCredentials()](https://reference.aspose.com/email/java/com.aspose.email/pop3client/#validateCredentials--) para realizar essa operação. Se a validação for bem-sucedida, o código dentro da declaração if será executado, geralmente usado para realizar outras ações ou recuperar dados do servidor IMAP. O seguinte trecho de código demonstra a validação de credenciais sem enviar um email:

```java
try (Pop3Client pop3Client = new Pop3Client(
        server.Pop3Url, server.Pop3Port, "userName", "password", SecurityOptions.Auto)) {
    pop3Client.setTimeout(4000);

    if (pop3Client.validateCredentials()) {
        // para fazer algo
    }
}
```

## **Usando autenticação CRAM-MD5 para conectar-se a um servidor**

Para garantir autenticação e comunicação seguras com o servidor POP3, você pode especificar e impor o uso de CRAM-MD5 como o método de autenticação permitido para o cliente POP3. O seguinte trecho de código mostra como configurar o tipo de autenticação permitido para o [Pop3Client](https://reference.aspose.com/email/java/com.aspose.email/pop3client/):

```java
popClient.setAllowedAuthentication(Pop3KnownAuthenticationType.CramMD5);
```

## **Como definir timeout para operações de email**

Cada operação de email leva algum tempo, dependendo de muitos fatores (atrasos na rede, tamanho dos dados, desempenho do servidor, etc.). Você pode definir um timeout para todas as operações de email. O exemplo de código abaixo mostra como fazer isso usando a propriedade [Timeout](https://reference.aspose.com/email/java/com.aspose.email/emailclient/#setTimeout-int-). Nota: não deve-se definir valores grandes para evitar longas esperas em sua aplicação.

~~~Java
try (Pop3Client pop3Client = new Pop3Client("host", 995, "username", "password", SecurityOptions.Auto))
{
    pop3Client.setTimeout(60000); // 60 segundos

    // algum código...
}
~~~