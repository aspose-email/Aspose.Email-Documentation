---
title: "Introdução e Aplicações de Exemplo"
url: /pt/net/introduction-and-sample-applications/
weight: 260
type: docs
---


## **Cenários de Uso do Aspose.Email.Mail**
Este artigo sugere uma série de possíveis usos para o Aspose.Email para .NET, focando particularmente nas funcionalidades de programação de email do componente.
### **Software de Newsletter**
A API [Aspose.Email.Mail](https://apireference.aspose.com/email/net/aspose.email) pode ser usada para criar um aplicativo de newsletter robusto. Usando o suporte do Aspose.Email para adicionar objetos incorporados (como imagens, sons etc.), é possível criar newsletters em HTML ricas, completas com imagens (e outros objetos incorporados). Usando o recurso de envio em massa da API Aspose.Email.Mail, também é possível enviar enormes emails em massa em um curto período de tempo. Aspose.Email.Mail também fornece um recurso de mala direta baseado em template que pode ser usado para criar um template de newsletter. O template da newsletter pode ser usado para realizar uma mala direta para enviar newsletters em massa. Existem muitas outras tarefas possíveis que o Aspose.Email.Mail pode realizar em um aplicativo de marketing por email.
### **Outras Ferramentas de Marketing**
Semelhante aos aplicativos de newsletter, muitos outros tipos de software podem ser construídos usando o Aspose.Email.Mail. Use-o para construir marketing por email, envio em massa e envio de campanhas eletrônicas em massa, e mais.
### **Aplicações Empresariais**
O Aspose.Email.Mail pode ser usado em quase todos os tipos de aplicações empresariais para realizar tarefas utilitárias:

- Alertas por email: Enviar alertas por email para informar os usuários sobre atividades.
- Solicitações de reunião: Enviar solicitações de reuniões de negócios usando o suporte a iCalendar do Aspose.Email.Mail.
- Relatórios agendados por email: Relatórios são uma parte integral da maioria das aplicações empresariais. Muitos relatórios empresariais são gerados em intervalos. Use o Aspose.Email.Mail para enviar relatórios agendados por email.
### **Clientes de Email**
O Aspose.Email.Mail também pode ser usado em clientes de email para enviar emails normais. Ele suporta anexos, objetos incorporados, eventos iCalendar, mala direta, envio de emails em massa, e assim por diante, portanto, o Aspose.Email.Mail é a melhor opção para criar aplicações cliente de email baseadas em Windows ou web.
## **Aplicativo de Exemplo do Aspose.Email.Mail**
Para ilustrar como usar o Aspose.Email.Mail, criaremos um aplicativo chamado 'Meu Primeiro Email' que demonstra como construir uma mensagem de email com a classe [MailMessage](https://apireference.aspose.com/email/net/aspose.email/mailmessage) e depois enviá-la usando a classe SmtpClient.
### **Email : Etapas do Aplicativo de Exemplo**
Por favor, siga os passos abaixo para criar o aplicativo 'Meu Primeiro Email' usando o Aspose.Email.

1. Abra o Visual Studio.
1. No menu **Arquivo**, selecione **Novo**, depois **Projeto**. (Escolha criar um aplicativo Windows C# ou VB.NET).
1. Se você tem uma licença, aplique-a para usar a versão completa do Aspose.Email.
1. Importe o DLL do Aspose.Email para o aplicativo clicando com o botão direito em **Referência** no Solution Explorer.
1. Projete seu aplicativo Windows: crie uma interface que aceite três campos: **De**, **Para** e **Mensagem**.
1. Dê um clique duplo no botão **Enviar** no modo de design e escreva seu código no editor.
1. Crie uma instância da classe MailMessage e use suas propriedades para construir uma mensagem de email. (Instâncias da classe MailMessage são usadas para construir mensagens de email que são transmitidas a um servidor SMTP para entrega usando a classe SmtpClient).
1. Crie uma instância da classe SmtpClient e use suas propriedades para enviar uma mensagem de email.
1. Teste seu aplicativo Windows pressionando F5.
1. Digite endereços nos campos **De** e **Para**.
1. Digite uma mensagem no campo **Corpo da Mensagem**.
1. Clique em **Enviar**.

As etapas acima são descritas abaixo; dê um clique duplo no botão **Enviar** no modo de design e adicione o código abaixo:



{{< gist "aspose-email" "9e8fbeb51a8cbc4129dc71ca8cd55f0b" "Examples-CSharp-Knowledge-Base-AsposeEmailMailSampleApp-AsposeEmailMail.cs" >}}



Ao conectar-se a um servidor habilitado para SSL, precisamos definir as seguintes propriedades do objeto SMTPClient:



{{< gist "aspose-email" "9e8fbeb51a8cbc4129dc71ca8cd55f0b" "Examples-CSharp-Knowledge-Base-AsposeEmailMailSampleApp-SSLEnabledSMTP.cs" >}}
### **Conclusão**
[Aspose.Email.Mail](https://apireference.aspose.com/email/net/aspose.email) é um componente muito poderoso com o qual os desenvolvedores podem realizar quase todas as tarefas de email, como enviar emails em massa multithread, usar mala direta, adicionar anexos, incorporar imagens e sons em mensagens de email, adicionar eventos iCalendar a emails, receber emails e muito mais.
## **Aspose.Email.Pop3**
[Aspose.Email.Pop3](https://apireference.aspose.com/email/net/aspose.email.clients.pop3/pop3client) implementa o Protocolo de Correio Post Office v3 (POP3) no framework .NET. Ele permite que os desenvolvedores .NET adicionem recursos de consulta e recebimento de email aos seus aplicativos .NET sem se envolverem nos detalhes do protocolo e na complexidade da programação de email e rede. O Aspose.Email.Pop3 suporta todos os comandos definidos no protocolo padrão POP3 e fornece interfaces fáceis de usar junto com um modelo de objeto compacto e intuitivo. Isso reduz significativamente a curva de aprendizado usual para os desenvolvedores .NET.
### **Pop3 : Principais Recursos**
Como parte do Aspose.Email, o Aspose.Email.Pop3 é projetado especificamente para .NET e é escrito em código C# gerenciado. Ele permite que você:

- Conecte-se e faça login em servidores POP3.
- Suporte APOP.
- Consulte mensagens.
- Recupere mensagens.
- Suporte total ao estilo de programação assíncrona.
- Suporte SSL.
### **Cenários do Aspose.Email.Pop3**
O Aspose.Email.Pop3 pode ser usado por desenvolvedores em muitos cenários diferentes. Aqui, compartilhamos alguns.
### **Automação de Email Empresarial**
O Aspose.Email.Pop3 pode ser usado para consultar caixas de entrada de email e buscar mensagens de email. Ele funciona perfeitamente com o componente de envio de email, Aspose.Email.Mail. O Aspose.Email suporta totalmente a automação de email. Envie mensagens de email com o Aspose.Email.Mail e busque mensagens com o Aspose.Email.Pop3. As mensagens de email baixadas podem ser analisadas pelo Aspose.Email.Mime.
### **Clientes de Email**
O Aspose.Email.Pop3 pode ser usado em aplicações de cliente de email para receber emails.
### **Pop3 : Aplicativo de Exemplo**
Aqui, demonstraremos como usar [Aspose.Email.Pop3](https://apireference.aspose.com/email/net/aspose.email.clients.pop3/pop3client). Esta classe tem muitos recursos, mas vamos nos concentrar em como conectar-se a um servidor POP3 e recuperar mensagens. O exemplo mostra como criar um aplicativo no Visual Studio, bem como os exemplos de código que fazem o aplicativo funcionar. Siga os passos dados abaixo para criar um aplicativo de exemplo usando o Aspose.Email.Pop3.

1. Abra o Visual Studio.
1. No menu **Arquivo**, selecione **Novo** e depois **Projeto**.
1. Escolha um aplicativo Windows C# ou VB.NET.
1. Importe o Aspose.Email.dll no aplicativo clicando com o botão direito em **Referência** no Solution Explorer.
1. Agora, projete um aplicativo Windows como mostrado abaixo.
1. Crie uma instância de Pop3Client.
1. Defina o nome do host POP3, nome de usuário e senha nesta instância.
1. Chame as funções Connect() e Login() do Pop3Client.
1. Crie uma instância de MailMessage e busque o primeiro email na sua conta, chamando a função FetchMessage(). Isso traz a primeira mensagem da sua conta de email para a instância MailMessage.
1. Use as propriedades From, Subject e HtmlBody da instância MailMessage para ver o remetente, assunto e corpo da mensagem.

As etapas acima são demonstradas nos exemplos de código abaixo. Use o código a seguir em qualquer botão ou no evento OnLoad de um formulário.



{{< gist "aspose-email" "9e8fbeb51a8cbc4129dc71ca8cd55f0b" "Examples-CSharp-Knowledge-Base-AsposeEmailPop3SampleApp-AsposeEmailPop3.cs" >}}



Para servidores habilitados para SSL, precisamos alterar as seguintes propriedades do objeto Pop3Client:



{{< gist "aspose-email" "9e8fbeb51a8cbc4129dc71ca8cd55f0b" "Examples-CSharp-Knowledge-Base-AsposeEmailPop3SampleApp-SSLEnabledServer.cs" >}}
## **Aspose.Email.Imap**
[Aspose.Email.Imap](https://apireference.aspose.com/email/net/aspose.email.clients.imap) implementa o Protocolo de Acesso a Mensagens da Internet (IMAP) em frameworks .NET. O Aspose.Email.Imap permite que os desenvolvedores .NET adicionem capacidades IMAP às suas aplicações .NET rapidamente, sem precisar entender os detalhes do protocolo. O componente suporta recuperação e upload de mensagens, verificação de status de mensagens novas/lidas/não lidas, e assim por diante.
### **Imap : Principais Recursos**
O Aspose.Email.Imap permite que você:

- Busque mensagens de email.
- Faça upload de mensagens de email.
- Liste mensagens de email em diferentes pastas.
- Verifique o status das mensagens de email.
- Trabalhe com MailMessage.
- Trabalhe com suporte a SSL.
### **Usando Aspose.Email.Imap**
O Aspose.Email.Imap implementa o Protocolo de Acesso a Mensagens da Internet em frameworks .NET. Com ele, os desenvolvedores podem facilmente consultar e gerenciar emails de servidores IMAP e criar, excluir ou renomear pastas de email. Usando o Aspose.Email.Imap, os desenvolvedores podem aproveitar o protocolo IMAP com APIs fáceis de usar. Eles podem acessar emails de qualquer PC, uma vez que os emails permanecem salvos no servidor. Usando o Aspose.Email.Imap, os desenvolvedores podem criar aplicações web ou de desktop que recebem e manipulam emails de servidores IMAP. A Aspose implementou o protocolo IMAP de acordo com as normas de autenticação da internet e RFC. Portanto, o Aspose.Email.Imap é uma implementação segura e totalmente equipada do protocolo IMAP, com um modelo de objeto e interfaces fáceis de entender.
### **Imap : Aplicativo de Exemplo**
Este artigo explica como usar [Aspose.Email.Imap](https://apireference.aspose.com/email/net/aspose.email.clients.imap). Criamos um pequeno aplicativo que obtém o número de mensagens de email na sua conta de email IMAP. Siga os passos dados abaixo para criar um aplicativo de exemplo usando o Aspose.Email.Imap.

1. Abra o Visual Studio.
1. No menu **Arquivo**, selecione **Novo** e depois **Projeto**.
1. Escolha um aplicativo Windows C# ou VB.NET.
1. Importe o Aspose.Email.dll neste aplicativo clicando com o botão direito em **Referência** no Solution Explorer.
1. Crie uma instância de ImapClient passando o nome do servidor IMAP, login e senha.
1. Chame a função Connect() da instância do ImapClient para conectar-se ao servidor.
1. Chame a função SelectFolder() da instância do ImapClient para selecionar a pasta da qual você deseja contar o número de mensagens.
1. Agora chame a propriedade CurrentFolder.TotalMessageCount da instância do ImapClient para obter a contagem de mensagens de email.
### **Imap : Exemplos de Código**
Os exemplos de código abaixo vão atrás do botão ou no evento OnLoad de um formulário. Eles mostram como implementar os passos descritos acima com o Aspose.Email.



{{< gist "aspose-email" "9e8fbeb51a8cbc4129dc71ca8cd55f0b" "Examples-CSharp-Knowledge-Base-AsposeEmailIMAPSampleApp-AsposeEmailIMAP.cs" >}}



Para servidores de email habilitados para SSL, defina as seguintes propriedades do objeto ImapClient:



{{< gist "aspose-email" "9e8fbeb51a8cbc4129dc71ca8cd55f0b" "Examples-CSharp-Knowledge-Base-AsposeEmailIMAPSampleApp-SSLEnabledServer.cs" >}}
## **Aspose.Email.Exchange**
[Aspose.Email.Exchange](https://apireference.aspose.com/email/net/aspose.email.clients.exchange/index) permite que os desenvolvedores gerenciem emails no Microsoft Exchange Server. Com este componente, você pode conectar, listar mensagens e baixar emails da caixa de correio do servidor Exchange sem entender os detalhes do protocolo subjacente. O componente suporta listagem de mensagens, envio de emails, download de mensagens e salvamento em formato eml ou msg no seu disco local, etc.
### **Exchange : Principais Recursos**
O Aspose.Email.Exchange permite que você:

- Conecte-se a Servidores Microsoft Exchange.
- Liste mensagens de email nas caixas de correio Exchange.
- Liste mensagens de email em diferentes pastas, por exemplo, na pasta Caixa de Entrada, Enviados, Excluídos ou Rascunhos.
- Exclua mensagens em qualquer pasta nos Servidores Exchange.
### **Usando Aspose.Email.Exchange**
Com o Aspose.Email.Exchange, os desenvolvedores podem acessar as caixas de correio do Exchange Server a partir de suas aplicações .NET. Ele fornece uma API fácil de usar para gerenciar emails nos Servidores Exchange. Os desenvolvedores podem criar aplicações de console, desktop ou web que gerenciam emails nas caixas de correio do Exchange.
## **Aplicativo de Exemplo do Aspose.Email.Exchange**
Este artigo demonstra como usar [Aspose.Email.Exchange](https://apireference.aspose.com/email/net/aspose.email.clients.exchange/index). Criamos um aplicativo desktop simples que se conecta a uma caixa de correio do Exchange Server, obtém a lista de mensagens na pasta Caixa de Entrada e as exibe no formulário do Windows.
### **Exchange : Etapas do Aplicativo de Exemplo**
1. Abra o Microsoft Visual Studio.
1. Crie um novo projeto. (Selecione o idioma de sua escolha, C# ou VB.NET)
1. Adicione uma referência ao Aspose.Email.dll em seu projeto, clicando com o botão direito no projeto e selecionando **Adicionar Referência** no menu.
1. Projete um formulário do Windows como o abaixo:

Para executar o aplicativo com sucesso, você precisa das credenciais corretas para acessar o Exchange Server. Aqui, obtemos as informações de credenciais - URI do Exchange Server, nome de usuário, senha e domínio - do formulário do Windows. Este é um exemplo muito básico, então as propriedades da mensagem - assunto, de e para - são simplesmente exibidas na caixa de lista.
### **Exchange : Exemplos de Código**
Adicione o seguinte código no manipulador de eventos de clique do botão **Listar Mensagens**.



{{< gist "aspose-email" "9e8fbeb51a8cbc4129dc71ca8cd55f0b" "Examples-CSharp-Knowledge-Base-AsposeEmailExchangeSampleApp-AsposeEmailExchange.cs" >}}
### **Exchange : Saída**
Esta captura de tela mostra as mensagens obtidas do Exchange Server. O método ListMessages() retorna as informações básicas como assunto, de, para e ID da mensagem. Para obter a mensagem completa, chame o método ExchangeClient.SaveMessage(). (O uso do ExchangeClient.SaveMessage() é descrito no artigo [Salvando Mensagens da Caixa de Correio do Exchange Server em Formato EML e MSG](/email/net/working-with-exchange-mailbox-and-messages/#saving-messages).)

|![todo:image_alt_text](introduction-and-sample-applications_1.png)|
| :- |
## **Aspose.Email.Mime**
As Extensões de Correio da Internet Multitarefa (MIME) são um padrão da Internet que estende o formato de email para suportar texto em conjuntos de caracteres diferentes do US-ASCII, anexos não textuais, corpas de mensagens multipartes e informações de cabeçalho em conjuntos de caracteres não-ASCII. O Aspose.Email.Mime implementa o protocolo MIMI em frameworks .NET. Ele atua como um tradutor, pois pode ler um email de um arquivo (.eml etc.) ou da memória (string). Ele então analisa o arquivo ou string de email em partes significativas. Se você quiser passar por um arquivo de email sem se envolver com os detalhes do protocolo MIME, por exemplo, para extrair um anexo de um email, use o Aspose.Email.Mime.
### **Principais recursos**
O Aspose.Email.Mime funciona perfeitamente com Aspose.Email.Pop3 e Aspose.Email.Mail.

- [Aspose.Email.Pop3](https://apireference.aspose.com/email/net/aspose.email.clients.pop3/pop3client) recupera mensagens de email de uma caixa de correio especificada.
- [Aspose.Email.Mail](https://apireference.aspose.com/email/net/aspose.email) envia mensagens de email para uma caixa de correio especificada.
- [Aspose.Email.Mime](https://apireference.aspose.com/email/net/aspose.email.mime) é a ligação entre os dois anteriores e analisa as mensagens de email.