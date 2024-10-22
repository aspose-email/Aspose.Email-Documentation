---
title: "Conectar ao Servidor POP3"
url: /pt/python-net/connect-to-pop3-server/
weight: 10
type: docs
---

## **Conectando ao Servidor POP3**
A classe Pop3Client permite que aplicativos gerenciem caixas de e-mail usando o Protocolo Post Office, Versão 3 (POP3). Para se conectar a um servidor, use a classe Pop3Client. A classe Pop3Client é a principal entrada para desenvolvedores que desejam adicionar gerenciamento POP3 a suas aplicações .NET. Este artigo explica como usá-la. Para se conectar a um servidor POP3:

1. Crie uma instância da classe Pop3Client como client.
1. Especifique o host, nome de usuário e senha na instância Pop3Client.

O seguinte trecho de código mostra como se conectar ao servidor POP3.



{{< gist "aspose-email" "356f0e128b9d45a7ee779fc813eb87e5" "Examples-POP3-ConnectingToPOP3-ConnectingToPOP3.py" >}}
## **Conectando ao servidor SSL**
Conectar-se a um servidor POP3 descreve como se conectar a um servidor POP3 em três etapas simples:

1. Crie uma instância da classe Pop3Client.
1. Especifique o host, nome de usuário e senha.

O processo para se conectar a um servidor POP3 habilitado para SSL é semelhante, mas requer que você defina algumas outras propriedades:

- SecurityOptions
- Port

Para se conectar a um servidor POP3 habilitado para SSL, use a classe Aspose.Email.Pop3.Pop3Client e defina as propriedades SecurityOptions e Port. O seguinte trecho de código mostra como se conectar a um servidor POP3 habilitado para SSL.



{{< gist "aspose-email" "356f0e128b9d45a7ee779fc813eb87e5" "Examples-POP3-SSLEnabledPOP3Server-SSLEnabledPOP3Server.py" >}}

## **Conectando com um Servidor APOP**

APOP ou Protocolo de Correio Autenticado é uma extensão do tradicional Protocolo Post Office (POP), que fornece um método seguro para autenticação do cliente durante o processo de recuperação de e-mails. A principal vantagem do APOP é que a senha real nunca é transmitida pela rede. O acesso à caixa de correio do usuário é concedido como resultado de uma troca bem-sucedida do valor hash entre um servidor e um cliente.

### **Conectando ao servidor via Proxy**

Servidores proxy são muito comuns para se comunicar com o mundo exterior. Nesses casos, endereços de proxy são usados para clientes de e-mail acessarem caixas de e-mail pela Internet. Aspose.Email fornece suporte para as versões 4, 4a e 5 do protocolo de proxy SOCKS. Sua classe [Pop3Client](https://reference.aspose.com/email/python-net/aspose.email.clients.pop3/pop3client/#pop3client-class) permite que os aplicativos acessem e manipulem mensagens usando o Protocolo Post Office Versão 3 (POP3). O método 'get_mailbox_info()' da classe recupera informações sobre a caixa de correio, como o número de mensagens, tamanho total, etc. O seguinte exemplo de código demonstra o processo de recuperação de e-mail usando um servidor de correio proxy:

```py
import aspose.email as ae

client = ae.clients.pop3.Pop3Client("pop.domain.com", "username", "password")
# Definir endereço proxy, Port e Proxy
proxy_address = "192.168.203.142"
proxy_port = 1080
proxy = ae.clients.SocksProxy(proxy_address, proxy_port, ae.clients.SocksVersion.SOCKS_V5)
client.socks_proxy = proxy
mailboxInfo = client.get_mailbox_info()
```
### **Conectando ao servidor via Proxy HTTP**

Existem vários tipos de proxies, incluindo proxies HTTP, proxies SOCKS e outros, cada um servindo a diferentes propósitos e fornecendo diferentes níveis de funcionalidade. As etapas e configurações específicas podem variar com base no tipo de proxy sendo usado. O exemplo de código abaixo demonstra como configurar o POP3Client com a configuração adicional de um proxy HTTP e buscar informações sobre a caixa de correio:

```py
import aspose.email as ae

proxy = ae.clients.HttpProxy("18.222.124.59", 8080)
client = ae.clients.pop3.Pop3Client("pop.domain.com", "username", "password")
client.socks_proxy = proxy
mailboxInfo = client.get_mailbox_info()
```
### **Conectando ao servidor via mecanismo de autenticação CRAM-MD5**

CRAM-MD5 (Desafio-Resposta Mecanismo de Autenticação com MD5) é comumente usado em protocolos de e-mail, como POP3 e IMAP, onde a autenticação segura é importante. Ele fornece um nível mais forte de segurança em comparação com a transmissão de senha em texto claro. Aspose.Email para .NET permite que os usuários autentiquem e acessem servidores de e-mail que oferecem suporte a este método de autenticação.

```py
client.allowed_authentication = ae.clients.pop3.Pop3KnownAuthenticationType.CRAM_MD5
```
## **Como Definir o Tempo Limite para Operações de E-mail**

Aspose.Email fornece a propriedade 'timeout' da classe [Pop3Client](https://reference.aspose.com/email/python-net/aspose.email.clients.pop3/pop3client/#pop3client-class) para obter ou definir o tempo limite para operações de e-mail a fim de evitar travamentos ou bloqueios, lidar com problemas de rede ou servidor, melhorar a capacidade de resposta e garantir uma gestão eficiente dos recursos. O seguinte exemplo de código mostra como implementar a propriedade em um projeto:

```py
import aspose.email as ae

client = ae.clients.pop3.Pop3Client("host", 995, "username", "password", ae.clients.SecurityOptions.AUTO)
#  60 segundos
client.timeout = 60000
```
## **Usando Protocolos Criptográficos com o Cliente POP3**

Aspose.Email suporta SSL (obsoleto) e protocolos criptográficos TLS para fornecer segurança nas comunicações. Você pode ativar a criptografia criptográfica para proteger a troca de dados entre sua aplicação e servidores de e-mail.

```
NOTA: É importante saber que você pode configurar apenas as versões de protocolo suportadas pelo .NET Framework. Se a versão atual do .NET Framework não suportar certas versões de protocolo, essas versões não suportadas serão desconsideradas e ignoradas. Isso pode resultar em uma possível redução no nível de segurança TLS, e é crucial estar ciente de que nenhuma exceção será levantada nessa situação. Os desenvolvedores devem ter cautela para garantir que o nível de segurança TLS desejado seja mantido com base nos protocolos suportados em seu ambiente .NET Framework.
```
O seguinte exemplo de código demonstra como configurar um cliente POP3 com configurações para o protocolo de criptografia TLS 1.3 para comunicação segura:

```py
import aspose.email as ae

client = ae.clients.pop3.Pop3Client("host", 995, "username", "password", ae.clients.SecurityOptions.AUTO)
client.supported_encryption = ae.clients.base.EncryptionProtocols.TLS13
```
No caso de um protocolo de criptografia especificado não ser suportado na versão atual do .NET Framework, a diferença de comportamento entre o método 'SetSupportedEncryptionUnsafe' e a propriedade 'SupportedEncryption' é a seguinte:

Se a propriedade 'SupportedEncryption' for usada, o cliente de e-mail reduz o protocolo de criptografia para um nível suportado.

Se o método 'SetSupportedEncryptionUnsafe' for usado, o cliente de e-mail gera exceções.