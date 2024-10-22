---
title: "Introdução e Aplicações de Exemplo"
url: /pt/java/introduction-and-sample-applications/
weight: 260
type: docs
---


## **Cenários de Uso do Aspose.Email Mail**
Este artigo sugere uma série de usos possíveis para o Aspose.Email para Java, focando particularmente nas funcionalidades de programação de email do componente.
### **Software de Newsletter**
A API Aspose.Email Mail pode ser utilizada para criar um robusto aplicativo de newsletter. Usando o suporte do Aspose.Email para adicionar objetos incorporados (como imagens, sons etc.), é possível criar newsletters HTML ricas, completas com imagens (e outros objetos embutidos). Usando o recurso de envio em massa da API Aspose.Email Mail, também é possível enviar enormes emails em massa em um curto período de tempo. O Aspose.Email Mail também oferece um recurso de mala direta baseado em templates que pode ser usado para criar um template de newsletter. O template de newsletter pode ser usado para executar uma mala direta para enviar newsletters em massa. Existem muitas outras tarefas possíveis que o Aspose.Email Mail pode realizar em uma aplicação de marketing por email.
### **Outros Ferramentas de Marketing**
Semelhante aos aplicativos de newsletter, muitos outros tipos de software podem ser construídos usando o Aspose.Email Mail. Utilize-o para construir marketing por email, envio em massa de emails e campanhas de e-campanha, e mais.
### **Aplicações Empresariais**
O Aspose.Email Mail pode ser usado em quase todos os tipos de aplicações empresariais para realizar tarefas de utilidade:

- Alertas por email: Enviar alertas por email para informar os usuários sobre atividades.
- Solicitações de reunião: Enviar solicitações de reunião de negócios usando o suporte a iCalendar do Aspose.Email Mail.
- Relatórios de email agendados: Relatórios são parte integrante da maioria das aplicações empresariais. Muitos relatórios empresariais são gerados em intervalos. Utilize o Aspose.Email Mail para enviar relatórios agendados.
### **Clientes de Email**
O Aspose.Email Mail também pode ser usado em clientes de email para enviar emails normais. Ele suporta anexos, objetos embutidos, eventos iCalendar, mala direta, envio de emails em massa, e assim por diante, portanto o Aspose.Email Mail é a melhor opção para criar aplicações de cliente de email.
## **Aplicação de Exemplo do Aspose.Email Mail**
Para ilustrar como usar o Aspose.Email Mail, criaremos uma aplicação que demonstra como construir uma mensagem de email com a [classe MailMessage](https://apireference.aspose.com/email/java/com.aspose.email/MailMessage) e então enviá-la usando a classe SmtpClient.
### **Email: Passos da Aplicação de Exemplo**
Por favor, siga os passos abaixo para criar uma aplicação usando o Aspose.Email.

1. Projete sua aplicação: crie uma interface que aceite três campos: **De**, **Para** e **Mensagem**.
1. Dê um clique duplo no botão **Enviar** na visualização de design e escreva seu código no editor.
1. Crie uma instância da classe MailMessage e use suas propriedades para construir uma mensagem de email. (Instâncias da classe MailMessage são usadas para construir mensagens de email que são transmitidas para um servidor SMTP para entrega usando a classe SmtpClient).
1. Crie uma instância da classe SmtpClient e use suas propriedades para enviar uma mensagem de email.
1. Teste sua aplicação.
1. Digite endereços nos campos **De** e **Para**.
1. Digite uma mensagem no campo **Corpo da Mensagem**.
1. Clique em **Enviar**.

Os passos acima são descritos abaixo, dê um clique duplo no botão **Enviar** na visualização de design e adicione o código abaixo:



~~~Java
// Declare message as MailMessage instance
MailMessage message = new MailMessage();
// Specify From, To, Subject and Body
message.setFrom(new MailAddress("#From"));
message.setTo(MailAddressCollection.to_MailAddressCollection("#To"));
message.setSubject("#Subject");
message.setBody("#Body");

// Send email using SmtpClient, Create an instance of the SmtpClient Class and Specify the mailing host server, Username, Password and Port
SmtpClient client = new SmtpClient();

// Specify the mailing host server, Username, Password and Port
client.setHost("mail.server.com");
client.setUsername("username");
client.setPassword("password");
client.setPort(25);
client.send(message);

// Notify the user that a message has been sent
System.out.println("Mensagem Enviada");
~~~


Ao conectar-se a um servidor habilitado para SSL, precisamos definir as seguintes propriedades do objeto SMTPClient



~~~Java
// Set the port to 587. This is the SSL port of Gmail SMTP server, set the security mode to explicit
client.setPort(587);
client.setSecurityOptions(SecurityOptions.SSLExplicit);
~~~
### **Conclusão**
O Aspose.Email Mail é um componente muito poderoso com o qual os desenvolvedores podem realizar quase todas as tarefas de email, como enviar emails em massa com múltiplas threads, usar mala direta, adicionar anexos, embutir imagens e sons nas mensagens de email, adicionar eventos de iCalendar aos emails, receber emails e muito mais.
## **Aspose.Email Pop3**
[Aspose.Email Pop3](https://apireference.aspose.com/email/java/com.aspose.email/pop3client) implementa o Protocolo de Correio da Internet v3 (POP3) em Java. Ele permite que desenvolvedores Java adicionem recursos de consulta e recebimento de email aos seus aplicativos Java sem se envolver em detalhes de protocolo e na complexidade da programação de email e rede. O Aspose.Email Pop3 suporta todos os comandos definidos no protocolo padrão POP3 e fornece interfaces fáceis de usar juntamente com um modelo de objeto compacto e intuitivo. Isso reduz significativamente a curva de aprendizado usual para desenvolvedores Java.
### **Pop3: Principais Recursos**
Como parte do Aspose.Email, o Aspose.Email Pop3 foi projetado especificamente para Java e é escrito em código Java gerenciado. Ele permite que você:

- Conecte e faça login em servidores POP3.
- Suporte APOP.
- Consulte mensagens.
- Recupere mensagens.
- Suporte total ao estilo de programação assíncrona.
- Suporte SSL.
### **Cenários do Aspose.Email Pop3**
O Aspose.Email Pop3 pode ser usado por desenvolvedores em muitos cenários diferentes. Aqui, compartilhamos alguns.
### **Automação de Email Empresarial**
O Aspose.Email Pop3 pode ser utilizado para consultar caixas de entrada de email e buscar mensagens de email. Ele funciona perfeitamente com o componente de envio de email, Aspose.Email Mail. O Aspose.Email suporta totalmente a automação de email. Envie mensagens de email com o Aspose.Email Mail e busque mensagens com o Aspose.Email Pop3. As mensagens de email baixadas podem então ser analisadas pelo Aspose.Email Mime.
### **Clientes de Email**
O Aspose.Email Pop3 pode ser usado em aplicações de cliente de email para receber emails.
### **Pop3: Aplicação de Exemplo**
Aqui, demonstraremos como usar [Aspose.Email Pop3](https://apireference.aspose.com/email/java/com.aspose.email/pop3client). Esta classe possui muitos recursos, mas nos concentraremos em como se conectar a um servidor POP3 e recuperar mensagens. O exemplo mostra como criar uma aplicação, bem como os exemplos de código que fazem a aplicação funcionar. Siga os passos dados abaixo para criar uma aplicação de exemplo usando Aspose.Email Pop3.

1. Crie uma instância de Pop3Client.
1. Defina o nome do host POP3, login e senha nesta instância.
1. Crie uma instância de MailMessage e busque o primeiro email na sua conta chamando a função fetchMessage(). Isso traz a primeira mensagem da sua conta de email para a instância MailMessage.
1. Use as propriedades From, Subject e HtmlBody da instância MailMessage para ver o remetente, assunto e corpo da mensagem.

Os passos acima são demonstrados nos exemplos de código abaixo.



~~~Java
// Create a POP3 client
Pop3Client client = new Pop3Client();

// Basic settings (required)
client.setHost("pop3.youdomain.com");
client.setUsername("username");
client.setPassword("psw");

try {
    // Retrieve first message in MailMessage format directly
    MailMessage msg;
    msg = client.fetchMessage(1);
    System.out.println(msg.getFrom().toString());
    System.out.println(msg.getSubject());
    System.out.println(msg.getHtmlBody());
} catch (Exception ex) {
    System.err.println(ex);
}
~~~



Para servidores habilitados para SSL, precisamos mudar as seguintes propriedades do objeto Pop3Client:



~~~Java
// Set implicit security mode
client.setSecurityOptions(SecurityOptions.SSLImplicit);
~~~
## **Aspose.Email Imap**
[Aspose.Email Imap](https://apireference.aspose.com/email/java/com.aspose.email/imapclient) implementa o Protocolo de Acesso à Mensagem da Internet (IMAP) em Java. O Aspose.Email Imap permite que desenvolvedores Java adicionem rapidamente capacidades IMAP às suas aplicações Java, sem precisar entender os detalhes do protocolo. O componente suporta a recuperação e upload de mensagens, verificação do status de mensagens novas/lidas/não lidas, e assim por diante.
### **Imap: Principais Recursos**
O Aspose.Email Imap permite que você:

- Recupere mensagens de email.
- Faça upload de mensagens de email.
- Liste mensagens de email em diferentes pastas.
- Verifique o status das mensagens de email.
- Trabalhe com MailMessage.
- Trabalhe com suporte a SSL.
### **Usando Aspose.Email Imap**
O Aspose.Email Imap implementa o Protocolo de Acesso à Mensagem da Internet em Java. Com ele, os desenvolvedores podem facilmente consultar e gerenciar emails em servidores IMAP, além de criar, excluir ou renomear pastas de email. Usando o Aspose.Email Imap, os desenvolvedores podem aproveitar o protocolo IMAP com APIs de fácil uso. Eles podem acessar emails de qualquer PC, pois os emails permanecem salvos no servidor. Usando o Aspose.Email Imap, os desenvolvedores podem criar aplicações web ou desktop que recebem e manipulam emails de servidores IMAP. Aspose implementou o protocolo IMAP de acordo com as normas de autenticação na internet e padrões RFC. Por isso, o Aspose.Email Imap é uma implementação segura e totalmente funcional do protocolo IMAP, com um modelo de objeto e interfaces fáceis de entender.
### **Imap: Aplicação de Exemplo**
Este artigo explica como usar [Aspose.Email Imap](https://apireference.aspose.com/email/java/com.aspose.email/imapclient). Criamos uma pequena aplicação que obtém o número de mensagens de email na sua conta de email IMAP. Siga os passos dados abaixo para criar uma aplicação de exemplo usando o Aspose.Email Imap.

1. Crie uma instância de ImapClient passando o nome do servidor IMAP, login e senha.
1. Chame a função selectFolder() da instância ImapClient para selecionar a pasta da qual você deseja contar o número de mensagens.
1. Agora chame a propriedade CurrentFolder.TotalMessageCount da instância ImapClient para obter a contagem de mensagens de email.
### **Imap: Exemplos de Código**
Os exemplos de código abaixo mostram como implementar os passos descritos acima com o Aspose.Email.



~~~Java
// Creates an instance of the class ImapClient by specified the host, username and password
ImapClient client = new ImapClient("localhost", "username", "password");

try {
    client.selectFolder(ImapFolderInfo.IN_BOX);
    String strTemp;
    strTemp = "Você tem " + client.getCurrentFolder().getTotalMessageCount() + " mensagens na sua conta.";
    // Gets number of messages in the folder, Disconnects to imap server.
    System.out.println(strTemp);
} catch (Exception ex) {
    System.err.println(ex);
}
~~~



Para servidores de email habilitados para SSL, defina as seguintes propriedades do objeto ImapClient:



~~~Java
// Set security mode
client.setSecurityOptions(SecurityOptions.SSLImplicit);
~~~
## **Aspose.Email Exchange**
[Aspose.Email Exchange](https://apireference.aspose.com/email/java/com.aspose.email/iewsclient) permite que os desenvolvedores gerenciem emails no Microsoft Exchange Server. Usando este componente, você pode conectar, listar mensagens e baixar emails da caixa de correio do servidor de Exchange sem entender os detalhes subjacentes do protocolo. O componente suporta listar mensagens, enviar emails, baixar mensagens e salvá-las em formato eml ou msg no seu disco local etc.
### **Exchange: Principais Recursos**
O Aspose.Email Exchange permite que você:

- Conecte-se a Servidores Microsoft Exchange.
- Liste mensagens de email nas caixas de correio Exchange.
- Liste mensagens de email de diferentes pastas, por exemplo, a Caixa de Entrada, Enviados, Excluídos ou Rascunhos.
- Exclua mensagens em qualquer pasta nos Servidores Exchange.
### **Usando Aspose.Email Exchange**
Com o Aspose.Email Exchange, os desenvolvedores podem acessar caixas de correio do Exchange Server de suas aplicações Java. Ele fornece uma API de fácil uso para gerenciar emails em Servidores Exchange. Os desenvolvedores podem criar aplicações de console, desktop ou web que gerenciam emails em caixas de correio do Exchange.
## **Aplicação de Exemplo do Aspose.Email Exchange**
Este artigo demonstra como usar [Aspose.Email Exchange](https://apireference.aspose.com/email/java/com.aspose.email/iewsclient). Criamos um aplicativo de desktop simples que se conecta a uma caixa de correio do Exchange Server, obtém a lista de mensagens na pasta Caixa de Entrada e as exibe no formulário do Windows.
### **Exchange: Passos da Aplicação de Exemplo**
Para executar a aplicação com sucesso, você precisa das credenciais corretas para acessar o Exchange Server. Aqui, obtemos as informações de credenciais - URI do servidor Exchange, nome de usuário, senha e domínio - do formulário do Windows. Este é um exemplo muito básico, então as propriedades da mensagem - assunto, de e para - são simplesmente exibidas na listbox.
### **Exchange: Exemplos de Código**
Adicione o seguinte código no manipulador de eventos de clique do botão **Listar Mensagens**.


~~~Java
// Clear the items in the listbox
lstMessages.clear();

// Create instance of IEWSClient class by giving credentials and Call ListMessages method to list messages info from Inbox
IEWSClient client = EWSClient.getEWSClient("mailboxURI", "Username", "Password", "Domain");
ExchangeMessageInfoCollection msgCollection = client.listMessages(client.getMailboxInfo().getInboxUri());

// Loop through the collection to display the basic information
for (ExchangeMessageInfo msgInfo : msgCollection) {
    String strMsgInfo = "Assunto: " + msgInfo.getSubject() + " == De: " + msgInfo.getFrom().toString() + " == Para: " + msgInfo.getTo().toString();
    lstMessages.add(strMsgInfo);
}
~~~
### **Exchange: Saída**
Esta captura de tela mostra as mensagens obtidas do Exchange Server. O método listMessages() retorna as informações básicas como assunto, de, para e ID da mensagem. Para obter a mensagem completa, chame o método IEWSClient.fetchMessage(). (Usar o IEWSClient.fetchMessage() é descrito no artigo [Trabalhando com Caixa de Correio e Mensagens do Exchange](/email/java/working-with-exchange-mailbox-and-messages).)


## **Aspose.Email Mime**
As Extensões de Correio da Internet Multipropósito (MIME) são um padrão da Internet que estende o formato de email para suportar texto em conjuntos de caracteres diferentes do US-ASCII, anexos não textuais, corpos de mensagens multipartes e informações de cabeçalho em conjuntos de caracteres não ASCII. O Aspose.Email Mime implementa o protocolo MIME em Java. Ele atua como um tradutor, pois pode ler um email de arquivo (.eml etc) ou da memória (string). Ele então analisa o arquivo ou string de email em partes significativas. Se você quiser passar por um arquivo de email sem se envolver com os detalhes do protocolo MIME, por exemplo, para extrair um anexo de um email, use o Aspose.Email Mime.
### **Principais Recursos**
O Aspose.Email Mime funciona perfeitamente com Aspose.Email Pop3 e Aspose.Email Mail.

- O Aspose.Email Pop3 recupera mensagens de email de uma caixa de correio especificada.
- O Aspose.Email Mail envia mensagens de email para uma caixa de correio especificada.
- O Aspose.Email Mime é a ponte entre os dois acima e analisa mensagens de email.