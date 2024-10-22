---
title: "Acessando o Gmail no SSL"
url: /pt/net/accessing-gmail-on-ssl/
weight: 40
type: docs
---

## **SMTP**
Este artigo mostra como [conectar-se a um servidor Gmail](#connecting-to-gmail-smtp-server) e [enviar um e-mail](#sending-an-email-message) usando o protocolo SMTP no SSL.
### **Conectando ao servidor SMTP do Gmail**
O seguinte trecho de código mostra como se conectar a um servidor SMTP habilitado para SSL.

{{< gist "aspose-email" "9e8fbeb51a8cbc4129dc71ca8cd55f0b" "Examples-CSharp-Knowledge-Base-ConnectingGmailSMTPServer-ConnectingGmailSMTPServer.cs" >}}
### **Enviando uma Mensagem de Email**
O código acima configura o objeto SMTPClient para se conectar ao servidor Gmail. Para enviar uma mensagem usando o mesmo objeto cliente, crie um objeto da classe [MailMessage](https://apireference.aspose.com/email/net/aspose.email/mailmessage) e envie a mensagem usando o objeto cliente SMTP. O seguinte trecho de código mostra como definir as propriedades da mensagem, por exemplo, o assunto, para e corpo:

{{< gist "aspose-email" "9e8fbeb51a8cbc4129dc71ca8cd55f0b" "Examples-CSharp-Knowledge-Base-SendEmailMessage-SendEmailMessage.cs" >}}
## **IMAP**
Este artigo mostra como realizar uma série de atividades em um servidor de e-mail habilitado para SSL usando o protocolo IMAP:

- Conectar-se a um servidor de e-mail.
- Obter o número total de mensagens em uma caixa de entrada.
- Salvar mensagens localmente.
- Criar uma mensagem e adicioná-la a uma pasta.
### **Conectando ao Servidor de Email**
Use o objeto da classe [ImapClient](https://apireference.aspose.com/email/net/aspose.email.clients.imap/imapclient) da Aspose.Email para se conectar ao servidor de e-mail. O endereço do servidor, a porta, o nome de usuário e a senha são necessários para estabelecer uma conexão. O Gmail usa a porta 993 para o protocolo IMAP, o seguinte trecho de código mostra como se conectar ao Gmail usando essa porta.

{{< gist "aspose-email" "9e8fbeb51a8cbc4129dc71ca8cd55f0b" "Examples-CSharp-Knowledge-Base-ConnectToGmailUsingIMAP-ConnectToGmailUsingIMAP.cs" >}}
### **Selecionando uma Pasta e Obtendo o Número Total de Mensagens**
Verificar a pasta da Caixa de Entrada é a tarefa mais frequente ao checar e-mails. Usando a Aspose.Email, isso pode ser feito com apenas duas linhas simples de código. O seguinte trecho de código mostra como acessar a pasta da Caixa de Entrada e obter o número total de mensagens na pasta.

{{< gist "aspose-email" "9e8fbeb51a8cbc4129dc71ca8cd55f0b" "Examples-CSharp-Knowledge-Base-GetGmailMessageCountUsingIMAP-GetGmailMessageCountUsingIMAP.cs" >}}
### **Salvando Mensagens em um Disco Rígido Local**
Depois de selecionar uma pasta com o método SelectFolder, use a função ListMessages para obter uma lista de todas as mensagens na pasta em um objeto ImapMessagesInfoCollection. Percorra esta coleção e salve as mensagens de e-mail no disco local do computador da seguinte forma:

{{< gist "aspose-email" "9e8fbeb51a8cbc4129dc71ca8cd55f0b" "Examples-CSharp-Knowledge-Base-SaveGmailMessages-SaveGmailMessages.cs" >}}
### **Criando uma Nova Pasta**
O protocolo IMAP também permite criar uma nova pasta no servidor de e-mail. Isso pode ser feito usando uma chamada de função simples.

{{< gist "aspose-email" "9e8fbeb51a8cbc4129dc71ca8cd55f0b" "Examples-CSharp-Knowledge-Base-CreateNewGmailFolderUsingIMAP-CreateNewGmailFolderUsingIMAP.cs" >}}
### **Criando uma Nova Mensagem em uma Pasta**
Adicione uma nova mensagem à pasta usando as classes [MailMessage](https://apireference.aspose.com/email/net/aspose.email/mailmessage) e [ImapClient](https://apireference.aspose.com/email/net/aspose.email.clients.imap/imapclient). Os exemplos abaixo criam primeiro um objeto MailMessage fornecendo os valores de assunto, para e de. Em seguida, ele se inscreve em uma pasta e adiciona a mensagem a ela. O seguinte trecho de código mostra como criar uma nova mensagem em uma pasta.

{{< gist "aspose-email" "9e8fbeb51a8cbc4129dc71ca8cd55f0b" "Examples-CSharp-Knowledge-Base-AddingMessageToGmailFolderUsingIMAP-AddingMessageToGmailFolderUsingIMAP.cs" >}}
## **POP3**
Este artigo mostra alguns exemplos que usam o protocolo POP3 no SSL. Para se conectar a um servidor protegido por SSL, precisamos definir a porta SSL e duas propriedades extras. O restante do código é o mesmo que para conectar a um servidor POP3 normal.

Os exemplos de código abaixo mostram como:

- Conectar-se a um servidor SSL.
- Verificar o status da caixa de correio.
- Obter informações sobre a mensagem.
- Recuperar e-mails.
### **Conectando ao Servidor de Email**
Conecte-se ao servidor de e-mail habilitado para SSL usando a classe [Pop3client](https://apireference.aspose.com/email/net/aspose.email.clients.pop3/pop3client) conforme descrito abaixo.

{{< gist "aspose-email" "9e8fbeb51a8cbc4129dc71ca8cd55f0b" "Examples-CSharp-Knowledge-Base-ConnectToGmailUsingPOP3-ConnectToGmailUsingPOP3.cs" >}}
### **Verificando o Status da Caixa de Correio**
O seguinte trecho de código mostra como verificar o número de mensagens armazenadas na caixa de correio e o tamanho da caixa de correio. Use a classe [Pop3MailboxInfo](https://apireference.aspose.com/email/net/aspose.email.clients.pop3/pop3mailboxinfo) para isso.

{{< gist "aspose-email" "9e8fbeb51a8cbc4129dc71ca8cd55f0b" "Examples-CSharp-Knowledge-Base-CheckGmailMailboxStatus-CheckGmailMailboxStatus.cs" >}}
### **Verificando Informações da Mensagem**
Este exemplo verifica todas as mensagens na caixa de correio usando a classe [Pop3MessageInfoCollection](https://apireference.aspose.com/email/net/aspose.email.clients.pop3/pop3messageinfocollection). Use a função [Pop3Client.ListMessages()](https://apireference.aspose.com/email/net/aspose.email.clients.pop3/pop3client/methods/listmessages/index) para obter a coleção [Pop3MessageInfoCollection](https://apireference.aspose.com/email/net/aspose.email.clients.pop3/pop3messageinfocollection). Em seguida, percorra a coleção para ler as informações da mensagem: ID da mensagem, índice, assunto e tamanho.

{{< gist "aspose-email" "9e8fbeb51a8cbc4129dc71ca8cd55f0b" "Examples-CSharp-Knowledge-Base-CheckGmailMessageInformation-CheckGmailMessageInformation.cs" >}}
### **Recuperando Mensagens**
Para obter as mensagens da caixa de correio, use o método FetchMessage() da classe [Pop3Client](https://apireference.aspose.com/email/net/aspose.email.clients.pop3/pop3client) para obter a mensagem em um objeto do tipo [MailMessage](https://apireference.aspose.com/email/net/aspose.email/mailmessage). O seguinte trecho de código mostra como contar o número de e-mails na caixa de correio e depois percorrê-los para recuperar cada um.

{{< gist "aspose-email" "9e8fbeb51a8cbc4129dc71ca8cd55f0b" "Examples-CSharp-Knowledge-Base-RetrieveGmailMessages-RetrieveGmailMessages.cs" >}}