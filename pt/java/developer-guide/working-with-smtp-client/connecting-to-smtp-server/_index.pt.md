---
title: "Conectando ao Servidor SMTP"
url: /pt/java/conectando-ao-servidor-smtp/
weight: 10
type: docs
---


As seguintes propriedades precisam ser configuradas ao conectar-se a um servidor SMTP com suporte a SSL.

- [SecurityOptions](https://reference.aspose.com/email/java/com.aspose.email/securityoptions/)
- Porta

Nos exemplos abaixo, mostramos como:

1. Definir um nome de usuário.
1. Definir uma senha.
1. Definir a porta.
1. Definir a opção de segurança.

O seguinte trecho de código mostra como conectar-se a um servidor SMTP com SSL habilitado.

~~~Java
// Para exemplos completos e arquivos de dados, acesse https://github.com/aspose-email/Aspose.Email-for-Java

SmtpClient client = new SmtpClient("smtp.gmail.com");

// Defina o nome de usuário, senha, porta e opções de segurança
client.setUsername("seu.email@gmail.com");
client.setPassword("sua.senha");
client.setPort(587);
client.setSecurityOptions(SecurityOptions.SSLExplicit);
~~~ 

## **Conectando ao Servidor via Servidor Proxy Socks**

Às vezes, usamos servidores proxy para comunicar com o mundo externo. Nesses casos, os clientes de email não conseguem se comunicar pela Internet sem especificar o endereço do proxy. Aspose.Email oferece suporte para as versões 4, 4a e 5 do protocolo SOCKS. Este artigo fornece um exemplo funcional de envio de email usando um servidor de email proxy. Para enviar um email via um servidor proxy:

1. Inicialize o Proxy com as informações necessárias, ou seja, endereço do proxy, porta e versão do SOCKS.
1. Inicialize [SmtpClient](https://reference.aspose.com/email/java/com.aspose.email/smtpclient/) com o endereço do host, nome de usuário e senha, e quaisquer outras configurações.
1. Defina a propriedade Proxy do cliente para o objeto [Proxy](https://reference.aspose.com/email/java/com.aspose.email/emailclient/#getProxy--) criado anteriormente.

O seguinte trecho de código mostra como conectar-se a um servidor via servidor proxy.

~~~Java
// Para exemplos completos e arquivos de dados, acesse https://github.com/aspose-email/Aspose.Email-for-Java

SmtpClient client = new SmtpClient("smtp.domain.com", "username", "password");
client.setSecurityOptions(SecurityOptions.SSLImplicit);
String proxyAddress = "192.168.203.142"; // endereço do proxy
int proxyPort = 1080; // porta do proxy
SocksProxy proxy = new SocksProxy(proxyAddress, proxyPort, SocksVersion.SocksV5);
client.setProxy(proxy);
client.send(new MailMessage("sender@domain.com", "receiver@domain.com", "Enviando Email via proxy",
        "Implementar protocolo proxy socks para versões 4, 4a, 5 (apenas autenticação Nome de Usuário/Senha)"));
~~~ 

## **Conectando ao Servidor via Servidor Proxy HTTP**

~~~Java
// Para exemplos completos e arquivos de dados, acesse https://github.com/aspose-email/Aspose.Email-for-Java

HttpProxy proxy = new HttpProxy("18.222.124.59", 8080);
try (SmtpClient client = new SmtpClient("host", 587, "username", "password")) {
    client.setProxy(proxy);
    client.send(new MailMessage("sender@domain.com", "receiver@domain.com", "Enviando Email via proxy",
            "Implementar protocolo proxy socks para versões 4, 4a, 5 (apenas autenticação Nome de Usuário/Senha)"));
}
~~~ 

## **Personalizar o Mecanismo de Autenticação**

Recupere a lista de mecanismos de autenticação que são suportados pelo servidor SMTP usando o método [getSupportedAuthentication](https://reference.aspose.com/email/java/com.aspose.email/smtpclient/#getSupportedAuthentication--) da classe [SmtpClient](https://reference.aspose.com/email/java/com.aspose.email/smtpclient/). Este método permite ao cliente determinar quais métodos de autenticação estão disponíveis para estabelecer uma conexão segura com o servidor. Em seguida, usando o método [setAllowedAuthentication](https://reference.aspose.com/email/java/com.aspose.email/smtpclient/#setAllowedAuthentication-long-) que obtém (ou define) a enumeração dos tipos de autenticação permitidos pelo usuário, escolha o mecanismo de autenticação mais apropriado para a comunicação cliente-servidor. Isso permite que você defina explicitamente o método de autenticação para o cliente de email.

O seguinte exemplo de código mostra como personalizar a autenticação do cliente de email:

```java
smtpClient.setAllowedAuthentication(SmtpKnownAuthenticationType.Login);
```
## **Usando autenticação CRAM-MD5 para conectar-se a um servidor**

Para garantir a autenticação e comunicação seguras com o servidor SMTP, você pode especificar e impor o uso de CRAM-MD5 como o método de autenticação permitido para o cliente SMTP. O seguinte trecho de código mostra como configurar o tipo de autenticação permitida para o [SmtpClient](https://reference.aspose.com/email/java/com.aspose.email/smtpclient/):

```java
smtpClient.setAllowedAuthentication(SmtpKnownAuthenticationType.CramMD5);
```

## **Vincular o Cliente SMTP a um Endereço IP Específico no Host**

A possibilidade de um host ter várias portas disponíveis para enviar emails não pode ser descartada. Nesses casos, pode surgir a necessidade de vincular o cliente de envio de email a uma porta específica no host para enviar emails. Isso pode ser alcançado com a API Aspose.Email usando a propriedade [SmtpClient](https://reference.aspose.com/email/java/com.aspose.email/smtpclient/) [bindIPEndPoint](https://reference.aspose.com/email/java/com.aspose.email/smtpclient/#bindIPEndPoint-com.aspose.email.BindIPEndPointHandler-). A API [SmtpClient](https://reference.aspose.com/email/java/com.aspose.email/smtpclient/) pode ser configurada para usar um endereço IP específico no host especificando o Endpoint IP específico. O seguinte trecho de código mostra como vincular o Cliente SMTP a um Endereço IP Específico no Host.

~~~Java
// Para exemplos completos e arquivos de dados, acesse https://github.com/aspose-email/Aspose.Email-for-Java

SmtpClient client = new SmtpClient("smtp.domain.com", // host
        587, // porta
        "username", // nome de usuário
        "password", // senha
        SecurityOptions.Auto // Opções de Segurança
);
try {
    client.bindIPEndPoint(new BindIPEndPointHandler() {
        public InetSocketAddress invoke(InetSocketAddress remoteEndPoint) {
            return new InetSocketAddress(0);
        }
    });
    client.noop();
} finally {
    client.dispose();
}
~~~ 

## **Validar Credenciais do Servidor de Email sem Enviar Email**

Às vezes, é necessário verificar credenciais sem enviar um email. Aspose.Email fornece o método [validateCredentials()](https://reference.aspose.com/email/java/com.aspose.email/smtpclient/#validateCredentials--) para realizar essa operação. Se a validação for bem-sucedida, o código dentro da declaração if é executado, geralmente usado para executar ações adicionais ou recuperar dados do servidor IMAP. O seguinte trecho de código demonstra a validação de credenciais sem enviar um email:

```java
try (SmtpClient smtpClient = new SmtpClient(
        server.SmtpUrl, server.SmtpPort, "username", "password", SecurityOptions.Auto)) {
    smtpClient.setTimeout(4000);

    if (smtpClient.validateCredentials()) {
        // fazer algo
    }
}
``` 

## **Como Definir Timeout para Operações de Email**

Cada operação de email leva algum tempo, dependendo de muitos fatores (atrasos na rede, tamanho dos dados, desempenho do servidor, etc.). Você pode definir um timeout para todas as operações de email. O exemplo de código abaixo mostra como fazer isso usando a propriedade [Timeout](https://reference.aspose.com/email/java/com.aspose.email/emailclient/#getTimeout--). Nota: você não deve definir valores grandes para evitar longas esperas em sua aplicação.

~~~Java
try (SmtpClient smtpClient = new SmtpClient("host", 587, "username", "password", SecurityOptions.SSLExplicit))
{
    smtpClient.setTimeout(60000); // 60 segundos

    // algum código...
}
~~~