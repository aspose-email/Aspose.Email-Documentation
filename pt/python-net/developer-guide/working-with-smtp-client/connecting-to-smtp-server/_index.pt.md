---
title: "Conectando ao Servidor SMTP"
url: /pt/python-net/connecting-to-smtp-server/
weight: 10
type: docs
---


## **Conectando ao Servidor SMTP com SSL Ativado**
As seguintes propriedades precisam ser definidas ao se conectar a um servidor SMTP com suporte a SSL.

- SecurityOptions
- Port

Nos exemplos abaixo, mostramos como:

1. Definir um nome de usuário.
1. Definir uma senha.
1. Definir a porta.
1. Definir a opção de segurança.

O seguinte trecho de código mostra como conectar a um servidor SMTP com SSL ativado.

{{< gist "aspose-email" "356f0e128b9d45a7ee779fc813eb87e5" "Examples-SMTP-SSLEnabledSMTPServer-SSLEnabledSMTPServer.py" >}}

### **Definir um Tempo Limite para a Resposta de Saudação do Servidor**

Para aumentar a eficiência das operações do cliente de e-mail, os desenvolvedores frequentemente rely on the timeout property para limitar a duração de processos prolongados. No entanto, especificar intervalos excessivamente longos para essa propriedade pode dificultar operações que exigem tempos de processamento mais longos. Um cenário notável é durante o estabelecimento de uma conexão, onde confiar apenas na propriedade Timeout pode levar a tempos de conexão prolongados.

Em casos específicos, o cliente de e-mail pode empregar um modo automático para o estabelecimento da conexão, ciclamente sistematicamente através de vários parâmetros de conexão até que uma conexão bem-sucedida seja estabelecida. Servidores SMTP, IMAP e POP3, após a iniciação bem-sucedida da conexão, enviam uma string de saudação ao cliente. Notavelmente, os servidores podem empregar métodos de iniciação de conexão SSL/TLS implícitos ou explícitos (START TLS).

Um desafio potencial surge quando o modo de conexão não coincide entre o servidor e o cliente. Por exemplo, se o servidor espera uma conexão SSL implícita enquanto o cliente tenta estabelecer uma conexão não segura ou explicitamente SSL, o servidor se abstenha de enviar uma string de saudação. Consequentemente, os usuários experimentam tempos de espera prolongados até que o tempo limite seja alcançado, levando o cliente a seguir para a próxima opção de conexão.

Para resolver esse problema, os desenvolvedores podem aproveitar a propriedade 'greeting_timeout' da classe [SmtpClient](https://reference.aspose.com/email/python-net/aspose.email.clients.smtp/smtpclient/#smtpclient-class). Essa propriedade permite especificar um tempo limite (em milissegundos) especificamente para a string de saudação, minimizando o tempo necessário para o estabelecimento automático da conexão. Ao incorporar a propriedade 'greeting_timeout', os desenvolvedores podem otimizar os processos de conexão e garantir uma experiência de cliente de e-mail mais responsiva e eficiente.

O seguinte exemplo de código demonstra como implementar a propriedade em um projeto:

```py
import aspose.email as ae

client = ae.clients.smtp.SmtpClient("localhost", 25, "username", "password")
client.greeting_timeout = 4000
```
## **Enviar um E-mail via Servidor Proxy Socks**

Aspose.Email fornece suporte para as versões 4, 4a e 5 do protocolo de proxy SOCKS. O seguinte exemplo de código demonstra como enviar um e-mail usando SMTP com proxy SOCKS:

```py
import aspose.email as ae

client = ae.clients.smtp.SmtpClient("smtp.domain.com", "username", "password")

client.security_options = ae.clients.SecurityOptions.SSL_IMPLICIT
# endereço do proxy
proxy_address = "192.168.203.142"
#porta do proxy
proxy_port = 1080
socks_proxy = ae.clients.SocksProxy(proxy_address, proxy_port, ae.clients.SocksVersion.SOCKS_V5)
client.proxy = socks_proxy
client.send(ae.MailMessage("sender@domain.com", "receiver@domain.com", "Enviando E-mail via proxy", "Implementar o protocolo proxy socks para as versões 4, 4a, 5 (apenas autenticação por Nome de Usuário/Senha)"))
```

## **Conectando ao Servidor via Servidor Proxy HTTP**

O exemplo de código abaixo demonstra o uso de um proxy HTTP para enviar um e-mail via um servidor SMTP:

```py
import aspose.email as ae

http_proxy = ae.clients.HttpProxy("18.222.124.59", 8080)
client = ae.clients.smtp.SmtpClient("host", 587, "username", "password")
client.proxy = http_proxy
client.send(ae.MailMessage("sender@domain.com", "receiver@domain.com", "Enviando E-mail via proxy", "Corpo"))
```

## **Conectando ao Servidor usando Método de Autenticação Suportado**

Para estabelecer uma conexão segura e bem-sucedida com o servidor para enviar e-mails, um cliente pode selecionar um método de autenticação suportado com base nas capacidades do servidor. Aspose.Email fornece propriedades que retornam listas de métodos de autenticação suportados:

- A propriedade 'supported_authentication' obtém a enumeração dos tipos de autenticação suportados pelo servidor
- A propriedade 'allowed_authentication' obtém ou define a enumeração dos tipos de autenticação permitidos pelo usuário

Usando essas propriedades, os desenvolvedores podem garantir que o cliente SMTP e o servidor sejam compatíveis em termos de métodos de autenticação suportados e estabelecer uma conexão com um servidor SMTP. O seguinte trecho de código fornece um exemplo do uso da propriedade 'allowed_authentication' em um projeto:

```py
client.allowed_authentication = ae.clients.smtp.SmtpKnownAuthenticationType.LOGIN
```

## **Como Definir Tempo Limite para Operações de E-mail**

Definir um tempo limite pode ser importante para lidar com a comunicação em rede de forma eficiente. A propriedade 'timeout' da classe [SmtpClient](https://reference.aspose.com/email/python-net/aspose.email.clients.smtp/smtpclient/#smtpclient-class) é usada para especificar o tempo máximo (em milissegundos) a esperar por uma resposta do servidor SMTP. Esta propriedade permite que o usuário controle a duração que o cliente esperará pela resposta do servidor a uma operação específica, como uma conexão ou o envio de um comando. Se o servidor demorar mais do que o tempo especificado para responder, o cliente lançará uma exceção, indicando um erro de tempo limite. Isso ajuda a gerenciar o comportamento do cliente ao interagir com o servidor, garantindo que o cliente não fique travado indefinidamente se o servidor não responder em tempo hábil. Use o seguinte trecho de código para definir o tempo limite para a resposta do servidor:

```py
import aspose.email as ae

client = ae.clients.smtp.SmtpClient("host", 587, "username", "password", ae.clients.SecurityOptions.SSL_EXPLICIT)
# 60 segundos
client.timeout = 60000
```

## **Usando Protocolos Criptográficos com o Cliente SMTP**

Aspose.Email suporta protocolos criptográficos SSL (obsoleto) e TLS para fornecer segurança nas comunicações. Você pode habilitar a criptografia criptográfica para proteger a troca de dados entre sua aplicação e servidores de e-mail.

```
NOTA: Você deve definir apenas aquelas versões do protocolo que são suportadas pelo Framework Python. Se algumas versões do protocolo criptográfico não forem suportadas pela sua versão atual do Framework Python, elas serão ignoradas e puladas. Nesse caso, exceções não serão geradas. Por favor, use o método 'set_supported_encryption_unsafe(value)' da classe SmtpClient se você quiser definir os protocolos sem quaisquer verificações de compatibilidade.
```
O exemplo de código abaixo mostra como definir TLS 1.3 para a instância da classe SmtpClient.

```py
import aspose.email as ae

client = ae.clients.smtp.SmtpClient("host", 587, "username", "password", ae.clients.SecurityOptions.SSL_EXPLICIT)
client.supported_encryption = ae.clients.base.EncryptionProtocols.TLS13
```

## **Usando o Mecanismo CRAM-MD5 para Autenticação**

O mecanismo de autenticação CRAM-MD5 da Aspose.Email para Python fornece uma camada adicional de segurança ao acessar o servidor. O seguinte trecho de código mostra como implementar esse recurso em seu projeto:

```py
client.allowed_authentication = ae.clients.smtp.SmtpKnownAuthenticationType.CRAM_MD5
```