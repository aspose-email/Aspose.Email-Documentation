---
title: "Conectando ao Servidor IMAP"
url: /pt/python-net/connecting-to-imap-server/
weight: 10
type: docs
---

A classe [ImapClient](https://reference.aspose.com/email/python-net/aspose.email.clients.imap/imapclient/#imapclient-class) no Aspose.Email para Python serve como um componente para interagir com contas de email usando o protocolo IMAP. IMAP (Protocolo de Acesso a Mensagens da Internet) é um protocolo padrão para acessar e gerenciar mensagens de email armazenadas em um servidor de email.

A classe [ImapClient](https://reference.aspose.com/email/python-net/aspose.email.clients.imap/imapclient/#imapclient-class) fornece funcionalidades para se conectar a um servidor de email via IMAP, autenticar usuários, recuperar emails, gerenciar pastas e realizar várias operações, como ler, mover, excluir ou atualizar mensagens de email. Essa classe essencialmente permite que os desenvolvedores integrem a funcionalidade IMAP em suas aplicações Python, permitindo que interajam com contas de email de uma maneira padronizada e compatível com o protocolo.

Para se conectar ao servidor IMAP, siga três etapas simples. O exemplo de código abaixo mostra como se conectar ao servidor IMAP programaticamente.

1. Crie uma instância da classe ImapClient.
2. Especifique o hostname, porta, nome de usuário e senha.
3. Especifique as Opções de Segurança.

```py
import aspose.email as ae

client = ae.clients.imap.ImapClient("imap.domain.com", 993, "user@domain.com", "pwd")
```
## **Conectando ao Servidor IMAP com SSL Habilitado**

O processo para conectar-se a um servidor IMAP habilitado para SSL é semelhante ao descrito acima, mas requer que você defina outra propriedade:

- Defina as Opções de Segurança como SSLImplicit.

```py
import aspose.email as ae

client = ae.clients.imap.ImapClient("imap.domain.com", 993, "user@domain.com", "pwd")

# Defina o modo de segurança como implícito
client.security_options = ae.clients.SecurityOptions.SSL_EXPLICIT
```
## **Conectando ao Servidor via Proxy**

Um servidor proxy atua como um intermediário entre o dispositivo de um usuário e a internet. Ele pode ser utilizado por várias razões, como melhorar o desempenho da rede, aumentar a segurança e a privacidade, contornar restrições geográficas e armazenar em cache conteúdo da web para reduzir o uso de largura de banda. Servidores proxy também podem ser usados para filtrar e monitorar o uso da internet em uma organização ou fornecer anonimato para os usuários. O Aspose.Email fornece suporte para as versões 4, 4a e 5 do protocolo proxy SOCKS. O seguinte exemplo de código e passos demonstram como configurar um cliente IMAP para se conectar a um servidor IMAP através de um servidor proxy SOCKS para comunicação segura e privada com o servidor de email.

1. Crie uma instância da classe [ImapClient](https://reference.aspose.com/email/python-net/aspose.email.clients.imap/imapclient/#imapclient-class) e defina os detalhes do servidor IMAP.
2. Defina as opções de segurança como automáticas para o cliente IMAP.
3. Defina os detalhes do servidor proxy, como o endereço IP e a porta.
4. Crie um objeto SocksProxy com o endereço e a porta do proxy definidos, usando a versão SOCKS 5.
5. Defina o proxy criado como o proxy para o cliente IMAP.
6. Conecte-se ao servidor IMAP e selecione a pasta "Inbox" usando o proxy para a comunicação.

```py
import aspose.email as ae

client = ae.clients.imap.ImapClient("imap.domain.com", "username", "password")

client.security_options = ae.clients.SecurityOptions.AUTO
proxy_address = "192.168.203.142"
proxy_port = 1080

proxy = ae.clients.SocksProxy(proxy_address, proxy_port, ae.clients.SocksVersion.SOCKS_V5)
client.proxy = proxy
client.select_folder("Inbox")
```
## **Conectando ao Servidor via Proxy HTTP**

O Aspose.Email também fornece a funcionalidade de acessar uma caixa de correio usando o proxy HTTP. O exemplo de código abaixo demonstra como configurar um cliente IMAP para se conectar a um servidor IMAP através de um servidor proxy HTTP para comunicação segura e privada com o servidor de email.

```py
import aspose.email as ae

client = ae.clients.imap.ImapClient("imap.domain.com", "username", "password")
client.proxy = ae.clients.HttpProxy("18.222.124.59", 8080)
client.select_folder("Inbox")
```
## **Conectando ao Servidor em Modo Somente Leitura**

Implementar uma funcionalidade de modo somente leitura para uma caixa de correio envolve fornecer a capacidade de controlar e restringir modificações ao estado permanente da caixa de correio, garantindo integridade dos dados, conformidade e experiência do usuário. Um valor True atribuído a esta propriedade indica que alterações não são permitidas. O exemplo de código a seguir mostra como usar essa propriedade em um projeto:

```py
import aspose.email as ae

client = ae.clients.imap.ImapClient("imap.domain.com", 993, "user@domain.com", "pwd")
client.security_options = ae.clients.SecurityOptions.SSL_EXPLICIT
client.read_only = True
```
## **Conectando ao Servidor usando Autenticação CRAM-MD5**

Usar autenticação CRAM-MD5 fornece uma maneira segura de autenticar com um servidor de email. Com o Aspose.Email você pode implementar essa capacidade em seu projeto Python facilmente.

O exemplo de código abaixo demonstra como configurar o cliente para aceitar CRAM-MD5 como um dos métodos de autenticação suportados para se conectar a um servidor IMAP:

```py
import aspose.email as ae

client = ae.clients.imap.ImapClient("imap.domain.com", 993, "user@domain.com", "pwd")
client.allowed_authentication = ae.clients.imap.ImapKnownAuthenticationType.CRAM_MD5
```
## **Como Definir Timeout para Operações de Email**

A propriedade 'timeout' da classe [ImapClient](https://reference.aspose.com/email/python-net/aspose.email.clients.imap/imapclient/#imapclient-class) evita que o cliente aguarde indefinidamente por uma resposta ao se comunicar com o servidor de email e permite lidar com atrasos de conexão potenciais, problemas de rede ou latência. O timeout é calculado em milissegundos. O seguinte trecho de código mostra como definir um período de timeout de 60.000 milissegundos (60 segundos) para o cliente esperar pela resposta do servidor:

```py
import aspose.email as ae

client = ae.clients.imap.ImapClient("imap.domain.com", 993, "user@domain.com", "pwd", ae.clients.SecurityOptions.SSL_IMPLICIT)
#  60 segundos
client.timeout = 60000
```
## **Como Restringir o Timeout de Saudação**

Definir um timeout na operação de saudação entre um cliente e um servidor permite que o cliente limite a quantidade de tempo que espera por uma resposta do servidor durante o processo inicial de handshake. Isso é importante porque se o servidor não responder ou houver problemas de rede, o cliente não deve esperar indefinidamente por uma resposta.

A API fornece a propriedade 'greeting_timeout' da classe [ImapClient](https://reference.aspose.com/email/python-net/aspose.email.clients.imap/imapclient/#imapclient-class) para definir um timeout na operação de saudação. O seguinte trecho de código mostra como restringir o timeout de saudação:

```py
import aspose.email as ae

client = ae.clients.imap.ImapClient("imap.domain.com", 993, "user@domain.com", "pwd")

client.greeting_timeout = 4000
client.select_folder(ae.clients.imap.ImapFolderInfo.IN_BOX)
```
## **Usando Protocolos Criptográficos com o Cliente IMAP**

O Aspose.Email suporta SSL (obsoleto) e protocolos criptográficos TLS para fornecer segurança nas comunicações. A propriedade 'supported_encryption' da classe [EmailClient](https://reference.aspose.com/email/python-net/aspose.email.clients/emailclient/#emailclient-class) define as versões dos protocolos de criptografia SSL/TLS a serem utilizados.

> **_NOTA:_** você pode definir apenas aquelas versões de protocolo que são suportadas pelo .NET framework. Se algumas versões de protocolo não forem suportadas pela sua versão atual do .NET framework, elas serão ignoradas e puladas. Isso pode levar a uma degradação do nível de segurança do TLS. Nesse caso, exceções não serão geradas. Por favor, use o método 'set_supported_encryption_unsafe(value)' se desejar definir os protocolos sem nenhuma verificação de compatibilidade.

O exemplo de código abaixo mostra como definir TLS 1.3 para uma instância da classe [ImapClient](https://reference.aspose.com/email/python-net/aspose.email.clients.imap/imapclient/#imapclient-class).

```py
import aspose.email as ae

client = ae.clients.imap.ImapClient("imap.domain.com", 993, "user@domain.com", "pwd", ae.clients.SecurityOptions.SSL_IMPLICIT)

client.supported_encryption = ae.clients.base.EncryptionProtocols.TLS13
```
No caso de um protocolo de criptografia especificado não ser suportado na versão atual do .NET Framework, a diferença de comportamento entre o método 'set_supported_encryption_unsafe(value)' e a propriedade 'supported_encryption' é a seguinte:

Se a propriedade 'supported_encryption' for utilizada, o cliente de email degrada o protocolo de criptografia para um nível suportado.
Se o método 'set_supported_encryption_unsafe(value)' for utilizado, o cliente de email lança exceções.